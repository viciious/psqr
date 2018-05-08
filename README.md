# psqr
Implementation of P-Square algorithm for golang, as presented in "The P-Square Algorithm for Dynamic Calculation of Percentiles and Histograms without Storing Observations," Communications of the ACM, October 1985 by R. Jain and I. Chlamtac.

## P-Square algorithm
Please refer to https://www1.cse.wustl.edu/~jain/papers/ftp/psqr.pdf for details

## Usage example

```go
package main

import (
	"fmt"
	"github.com/viciious/psqr"
)

func main() {
	pp := make([]*psqr.Psqr, 4)
	pp[0] = psqr.NewPsqr(0.10)
	pp[1] = psqr.NewPsqr(0.50)
	pp[2] = psqr.NewPsqr(0.90)
	pp[3] = psqr.NewPsqr(0.99)

	for i := 0; i < cap(pp); i++ {
		p := pp[i]
		p.Add(0.013163238)
		p.Add(0.711542201)
		p.Add(-2.131796046)
		p.Add(0.244640008)
		p.Add(-0.211374733)
		p.Add(4.493872061)
		//...
	}

	for i := 0; i < cap(pp); i++ {
		p := pp[i]
		fmt.Println(p.Get())
	}
}
```
