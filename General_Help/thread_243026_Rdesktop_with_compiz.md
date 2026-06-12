---
title: "Rdesktop with compiz"
date: 2006-08-24
forum: General Help
---

### Post by corefile on 2006-08-24
I grabbed this from a dapper dev forum that was closed, but I was having the same problem and wanted to see if anyone has the answer, so this quote fixes the problem of rdesktop being semi-transparent (all the time) when using compiz.

"You can use the XLIB_SKIP_ARGB_VISUALS=1 command instead!

So I start remotedesktop with a starter linked to that script:
Code:

#!/bin/bash XLIB_SKIP_ARGB_VISUALS=1 rdesktop -a 16 -k de -g 1024x768 192.168.1.33

while in a terminal just typing
Code:

XLIB_SKIP_ARGB_VISUALS=1 rdesktop -a 16 -k de -g 1024x768 192.168.1.33

is enough...
(why doesn't that command work as a starter....?)"

So the command line works for me, but as in the orginal post, how do I get this to work in a lancher?

---

### Post by hoosfoos on 2006-09-05
Create the script
copy and paste these two lines into a blank text editor.

#!/bin/bash
 XLIB_SKIP_ARGB_VISUALS=1 rdesktop -a 16 -k de -g 1024x768 192.168.1.33

 You might want to change the "de" line to "en" or else you will get a german keyboard and of course change the IP address to the IP address of the machine you're rdping to.
I saved the file into my home folder, but /usr/bin/ is a good home as well.
I called the script rdesktop_script.
Make sure the script is executable

chmod +x rdesktop_script

I got it to work by creating a new launcher, (Add to Panel, custom application launcher)  For the command I just put

./rdesktop_script

It "should" work..

---

