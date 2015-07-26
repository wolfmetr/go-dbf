# go-dbf
[Updated] A pure Go library for reading and writing [dBase/xBase](http://en.wikipedia.org/wiki/DBase#File_formats) database files.

Fork from "code.google.com/p/go-dbf"

## Updates
Removed dependency: "code.google.com/p/mahonia".

## Usage
```go
go get github.com/wolfmetr/go-dbf/godbf
```

```go
import (
  "github.com/wolfmetr/go-dbf/godbf"
)
```

There's no real documentation as yet. Here is a very simple snippet of example 'load' code to get you going:
```go
  type MyRow struct {
    ColumnId string
    ColumnValue string
  }

  dbfTable, err := godbf.NewFromFile("example_file.dbf", "cp866")

  resultList := make([]MyRow, dbfTable.NumberOfRecords())

  for i := 0; i < dbfTable.NumberOfRecords(); i++ {
    resultList[i] = new(MyRow)
    resultList[i].ColumnId, err = dbfTable.FieldValueByName(i, "COLUMN_ID")
    resultList[i].ColumnValue, err = dbfTable.FieldValueByName(i, "COLUMN_VALUE")
  }
```
