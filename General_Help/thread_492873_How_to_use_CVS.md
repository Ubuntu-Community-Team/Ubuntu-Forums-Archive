---
title: "How to use CVS?"
date: 2007-07-05
forum: General Help
---

### Post by andrew.46 on 2007-07-05
Hi,

 I have been searching for a tutorial or walkthrough for using cvs to download 'bleeding edge' applications. Could not find anything on the forums or much material from Google.Can anybody help?

                    Andrew

---

### Post by kuja on 2007-07-05
Umm, most programs using cvs will give you something to do with cvs that you can copy & paste, like this for example:

cvs -d:pserver:anonymous@tork.cvs.sourceforge.net:/cvsroot/tork login 
 
cvs -z3 -d:pserver:anonymous@tork.cvs.sourceforge.net:/cvsroot/tork co -P modulename

I'd assume that the actual command to do it for what you want shouldn't be far off of this, just with different URLs.

---

