---
title: "awk help"
date: 2008-03-24
forum: General Help
---

### Post by I.You on 2008-03-24
Hi

I'd like to split a string and I used awk :

> #!/bin/sh

string="sun,mon,tue,wed"
awk 'BEGIN { split{string, array, ",") }'
for i in 0 1 2 3
do
echo ${array[i]}
done

Is it wrong?
It doesn't work;...

Any help?

---

### Post by colo on 2008-03-24
awk variables are not shell/environment-variables. What your awk code does is splitting an awk-internal string (which is empty) at the ","-character, and return it as an awk-array (which, again, is empty).

If you would like to propagate your awk-variables to your environment, you'd have to make awk display them on stdout, formatting it in a way that it reads ```
variableN="valueN"
``` on each line, and have your shell eval that.

Like the following, maybe:
```

string="mon,tue,wed,thu";
eval $(awk "BEGIN { split(\"$string\", array, \",\"); for (var in array){printf(\"array[%d]=%s\n\", var, array[var]);}}";);
echo ${array[*]}

```

Make sure to check for malicious inpout before using eval, if your data is coming from an external source.

If you just need to split at a single char (and not a regex, as awk can do four you, you might as well use the following:
```
OLDIFS="${IFS}"; IFS=","; string="a,b,c,d"; array=($string); echo ${array[*]}; IFS="${OLDIFS}";
```

Hth.

---

### Post by ghostdog74 on 2008-03-27
> **I.You said:**
> Hi

I'd like to split a string and I used awk :



Is it wrong?
It doesn't work;...

Any help?

what is the actual problem you are trying to solve? I believe its not just displaying the contents of the stored values.
this does what your code would have done (just displaying the values)
```

# echo $string | awk -F"," '{ for(i=1;i<=NF;i++) print $i}'
sun
mon
tue
wed

```

---

