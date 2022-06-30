package coverage

import (
	"os"
	"testing"
	"time"
)

// DO NOT EDIT THIS FUNCTION
func init() {
	content, err := os.ReadFile("students_test.go")
	if err != nil {
		panic(err)
	}
	err = os.WriteFile("autocode/students_test", content, 0644)
	if err != nil {
		panic(err)
	}
}

// WRITE YOUR CODE BELOW

var (
	person1 = Person {
		firstName: "Ivan",
		lastName: "Ivanov",
		birthDay: time.Date(2000, time.April, 20, 9, 0, 0, 0, time.UTC),
	}
	person2 = Person {
		firstName: "Pyotr",
		lastName: "Petrov",
		birthDay: time.Date(1993, time.June, 22, 13, 0, 0, 0, time.UTC),
	}
	person3 = Person {
		firstName: "Semen",
		lastName: "Semenov",
		birthDay: time.Date(1982, time.January, 1, 3, 0, 0, 0, time.UTC),
	}
	person4 = Person {
		firstName: "Nikolay",
		lastName: "Kuznetsov",
		birthDay: time.Date(1999, time.August, 7, 15, 0, 0, 0, time.UTC),
	}
	person5 = Person {
		firstName: "Andrey",
		lastName: "Kuznetsov",
		birthDay: time.Date(1999, time.August, 7, 20, 0, 0, 0, time.UTC),
	}
    person6 = Person {
		firstName: "Ivan",
		lastName: "Ivanov",
		birthDay: time.Date(1999, time.August, 7, 20, 0, 0, 0, time.UTC),
	}
	person7 = Person {
		firstName: "Pyotr",
		lastName: "Sobolev",
		birthDay: time.Date(1993, time.June, 22, 13, 0, 0, 0, time.UTC),
	}
) 
var (
	testMatrixStr string = "1 2 3 4\n 5 6 7 8\n 9 10 11 12\n 13 14 15 16" 
	testMatrixCorrect = Matrix {
		rows: 4,
		cols: 4,
		data: []int{1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16},
	}
	testMatrinxIncorrect = Matrix {
		rows: 4,
		cols: 3,
		data: []int{1, 5, 9, 13, 2, 6, 10, 14, 3, 7, 11, 15},
	}
	testRows = [][]int{{1, 2, 3, 4}, {5, 6, 7, 8}, {9, 10, 11, 12}, {13, 14, 15, 16}}
	testCols = [][]int{{1, 5, 9, 13}, {2, 6, 10, 14}, {3, 7, 11, 15}, {4, 8, 12, 16}}
	testSetMatrix = Matrix {
		rows: 4,
		cols: 4,
		data: []int{1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 12, 14, 15, 16},
	}
)

type testValueLess struct {
	i, j int
	expValue bool
}


func TestLength(t *testing.T) {
	var newPeople People = []Person{person1, person2, person3, person4, person5, person6}
	length := newPeople.Len()
	if length != 6 {
		t.Errorf("The expected length is 6, actual length is %d", length)
	}
}

func TestLess(t *testing.T) {
	var newPeople People = []Person{person1, person2, person3, person4, person5, person6, person7}
	testSet := map[string]testValueLess{
		"Date is different": {
			i: 1,
			j: 4,
			expValue: false,
		},
		"Date is simmilar, different names": {
			i: 4,
			j: 5,
			expValue: true,
		},
		"Date is simmilar, same names, different last names": {
			i: 1,
			j: 6,
			expValue: true,
		},
	}
	for testName, values := range testSet {
		t.Run(testName, func(t *testing.T) {
			resultOfTestedFunction := newPeople.Less(values.i, values.j)
			if resultOfTestedFunction != values.expValue {
				t.Errorf("Expected value %t, result value %t", values.expValue, resultOfTestedFunction)
			}
		})
	}
}

func TestSwap(t *testing.T) {
	var newPeople People = []Person{person1, person2, person3, person4, person5, person6, person7}
	i := 4
	j := 6
	iMemo := newPeople[i]
	jMemo := newPeople[j]
	newPeople.Swap(i,j)
	if iMemo != newPeople[j] || jMemo != newPeople[i] {
		t.Errorf("%+v should equal %v, %+v should equal %v", newPeople[i], jMemo, newPeople[j], iMemo)
	}
}

func TestMatrixCreation(t *testing.T) {
	testMatrix, error := New(testMatrixStr)
	if error != nil {
		t.Error(error)
	} else if testMatrix.cols != testMatrixCorrect.cols || testMatrix.rows != testMatrixCorrect.rows {
		t.Errorf("Columns or rows number is not correct")
	} else if len(testMatrix.data) != len(testMatrixCorrect.data) {
		t.Errorf("Result matrix (length %d) has different length than expected (lentgth %d)", len(testMatrix.data), len(testMatrixCorrect.data))
	}
	// Check equality of matrices
	for i := 0; i < len(testMatrix.data); i++ {
		if testMatrix.data[i] != testMatrixCorrect.data[i] {
			t.Errorf("Data is not equaled, %d element", i)
		}
	}	
}

func TestRows(t *testing.T) {
	testMatrix, error := New(testMatrixStr)
	
	if error != nil {
		t.Error(error)
	}
	resultRowsTestMatrix := testMatrix.Rows()
	if len(resultRowsTestMatrix) != len(testRows) {
		t.Errorf("Size of the matrix is not correct")
	}
	for i:=0; i<testMatrix.rows; i++ {
		for j:=0; j<testMatrix.cols; j++ {
			if resultRowsTestMatrix[i][j] != testRows[i][j] {
				t.Errorf("[%d],[%d] elements are not equal", i, j)
			}
		}
	}
}

func TestCols(t *testing.T) {
	testMatrix, error := New(testMatrixStr)
	
	if error != nil {
		t.Error(error)
	}
	resultRowsTestMatrix := testMatrix.Cols()
	if len(resultRowsTestMatrix) != len(testCols) {
		t.Errorf("Size of the matrix is not correct")
	}
	for i:=0; i<testMatrix.cols; i++ {
		for j:=0; j<testMatrix.rows; j++ {
			if resultRowsTestMatrix[i][j] != testCols[i][j] {
				t.Errorf("[%d],[%d] elements are not equal", i, j)
			}
		}
	}
}

func TestSet(t *testing.T) {
	testMatrix, error := New(testMatrixStr)
	if error != nil {
		t.Error(error)
	}
	i := 1
	j := 0
	value := 12
	setOperation := testMatrix.Set(i,j, value)
	if setOperation {
		if testMatrix.data[i*testMatrix.cols+j] != value {
			t.Errorf("[%d],[%d] element is not equal to %d", i, j, value)
		}
	} else {
		t.Errorf("Nothing to set")
	}
}