---
title: "Format output format number in Terminal using awk command?"
date: 2008-05-14
forum: General Help
---

### Post by abcuser on 2008-05-14
Hi,
in Ubuntu 8.04 I have a file with two numbers:
10000000000 10000000000
After summing them out with command:
awk '{print $1 + $2}' myfile
I get output: 2e+10. How to format output number to: 20000000000?
Thanks,
Abcuser

---

### Post by abcuser on 2008-05-14
Hi,
I have found out the answer at [http://www.unix.com/shell-programming-scripting/24198-how-convert-scientific-notation-normal.html](http://www.unix.com/shell-programming-scripting/24198-how-convert-scientific-notation-normal.html)

awk '{printf "%8d\n",$1+$2}' myfile

Regards,
Abcuser

---

