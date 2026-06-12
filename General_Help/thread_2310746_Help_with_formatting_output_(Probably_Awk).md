---
title: "Help with formatting output (Probably Awk)"
date: 2016-01-21
forum: General Help
---

### Post by vong on 2016-01-21
I would like to format the numbers in the following output to be human readable.  I am pretty sure it can be done with AWK but I am too much of a noob to figure it out!

Here is the command and the output:

```
$ sudo drobom info capacity
---------------------------------------------------------
Info about Drobo     Name: Drobo disk pack       Devices: /dev/sdc
---------------------------------------------------------
query capacity result:
(1728358100992, 3238632378368, 4966990479360, 0)
Physical space... used:  3238632378368  free:  1728358100992  Total:  4966990479360
```

I would like each number converted, ideally to the highest bit (TB) with two decimal places of accuracy.

For reference, this is the utility installed from [http://drobo-utils.sourceforge.net/](http://drobo-utils.sourceforge.net/)

Thank you in advance

I don't mind if the result is an SH program that I can execute, as I will just be putting the result into my .bashrc for ease of future use :)

---

