---
title: "Need Bash script line interpreted"
date: 2008-02-07
forum: General Help
---

### Post by ed-koala on 2008-02-07
I have a Bash script line that I do not understand. It is:

#str=`echo '\033[01;32m29'`

The script is pulling info from Cal, but I can't see how it is printing new lines.  I suspect this line does it, but I dunno.  I'll post the rest of the short script if this line isn't what I suspect it is.

---

### Post by pointone on 2008-02-07
That line just changes the colour, I believe.

---

### Post by bilge.tutak on 2008-02-07
Echo means something is written, but it does not mean the lines are written by this echo. Some of the HEX numbers seems to be color codings I used before in my prompts, but I am not sure.

---

### Post by ed-koala on 2008-02-07
Thanks for the info.  I may delete the line temporarily to be sure ... didn't think of doing that earlier lol.  I'll keep hacking away at the script and will find the answer, even if it takes awhile.

---

