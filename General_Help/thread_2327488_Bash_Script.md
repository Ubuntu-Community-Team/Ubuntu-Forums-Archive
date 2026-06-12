---
title: "Bash Script"
date: 2016-06-11
forum: General Help
---

### Post by sujitrjadhav on 2016-06-11
Hi Friends,

I have written a bash script which reads values from a csv file. The script runs fine until it encounters a floating point number in the CSV file. My code has following "if condition" statement inside  a "while read .... done<$input" loop. What I am trying to do here is put negative sign before the number if certain conditions are met.

```
if [[  Some Condition ]]; then 

Txn_amount=-$(( $Txn_amount ))

fi

```

I get following error

[I]ParseCsv.sh: line 33: 36524.41 : syntax error: invalid arithmetic operator (error token is ".41 ").
[/I]
Here the script is crashing when it encounters a floating point number 36524.41 in the CSV file. Please suggest me what change in code is required to ensure that script process floating point number to correctly. Thanks.

---

### Post by steeldriver on 2016-06-11
The bash shell is fundamentally not the right tool for this job - you could try something like

```

Txn_amount=$( bc <<< "-$Txn_amount" )

```

however I suspect there will be other places where your script either doesn't work or will give unexpected results (truncation, rounding, unexpected base conversions due to leading zeros, ...)

---

### Post by sujitrjadhav on 2016-06-11
Thanks. 

It worked but like you said it generated an unexpected result. 

If the Txn_amount read from the CSV is already negative then it generates following error and the output file shows blank value for that particular cell

(standard_in) 1: syntax error

---

### Post by sujitrjadhav on 2016-06-11
Following Code gave me desired output

```
if [[ $Txn_amount != *"-"* ]]; then
       Txn_amount=$( bc <<< "-$Txn_amount" )
else
      Txn_amount=$( bc <<< "-1*$Txn_amount" )
fi

```

Thanks Again.

---

