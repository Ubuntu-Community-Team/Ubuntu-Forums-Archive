---
title: "22-year-old X Window bug: Get root with newly uncovered flaw"
date: 2014-01-09
forum: General Help
---

### Post by borgward on 2014-01-09
I was made aware the X Window bug by my local LUG and refered to:

[http://www.theregister.co.uk/2014/01/09/x11_has_privilege_escalation_bug/](http://www.theregister.co.uk/2014/01/09/x11_has_privilege_escalation_bug/)

That article suggests running - if (sscanf((char *) line, "STARTCHAR %99s", charName) != 1) {

Does Ubuntu updates deal with this. I will not run the above command until I get some feedback.

---

### Post by Impavidus on 2014-01-09
That line is not a command to run, it's the change in the source code to remove the bug. You don't need to change the source code yourself. It's all done by the developers and pushed through the update channels. If we keep your systems up to date, I think we should already have that update.

---

### Post by deadflowr on 2014-01-09
> [COLOR=#000000]Does Ubuntu updates deal with this. I will not run the above command until I get some feedback.[/COLOR]

Sure.
Here
[http://www.ubuntu.com/usn/usn-2078-1/](http://www.ubuntu.com/usn/usn-2078-1/)
from here
[http://www.ubuntu.com/usn/](http://www.ubuntu.com/usn/)

---

### Post by grahammechanical on 2014-01-09
The version of libxfont1 in Trusty Tahr is 1:1.4.6-1ubuntu1.

This report is a reminder of why the Ubuntu developers want to switch to MIR.

Regards

---

