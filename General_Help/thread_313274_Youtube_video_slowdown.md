---
title: "Youtube video slowdown?"
date: 2006-12-05
forum: General Help
---

### Post by Kittie Rose on 2006-12-05
When I watch videos in Youtube, it kinda freezes for a frame every few seconds... this is incredbily annoying! What could be causing it? I'm using an ATI RAdeon 9600 Pro with the latest Linux drivers I could find... anything else I might need?

---

### Post by Sef on 2006-12-05
1) How much memory do you have?  

2) How big is your swap file?

3) Are you running any other programs when this happens?

---

### Post by Kittie Rose on 2006-12-05
512 megs

Not sure, probably just under 2 gigs... possible I set it to one but pretty sure it's 2.

Nothing major. Closing stuff doesn't affect it.

---

### Post by Sef on 2006-12-06
> Not sure, probably just under 2 gigs... possible I set it to one but pretty sure it's 2.


From the terminal (Applications > Accessories > Terminal), type this:

free -m

that will tell you how much swap  you have.  If it's like mine, it may need to be turned on.

---

### Post by Kittie Rose on 2006-12-06
fredrael@Teletraan8:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           503        491         12          0          9        143
-/+ buffers/cache:        338        165
Swap:         1004        355        648


Not much of it being used up, could have sworn I set it to 2 gigs though.

---

### Post by Serpentinsek on 2008-01-15
I have the same problem. I don't think I understand what I have to to with my swap ...

Here is my output for: free -m
             total       used       free     shared    buffers     cached
Mem:           503        495          8          0          3        172
-/+ buffers/cache:        318        184
Swap:         1474         33       1441

---

### Post by rocman01 on 2008-01-15
hey there, i had the same issue a couple of days ago and i agree it is very annoying. newayz the solution i found was to uninstall the gnash swf plugin and install the adobe flash player 9.

solution=sudo apt-get remove gnash, then sudo apt-get install flashplugin-nonfree.

hope that helps yous out sorted my system out good as;-)

---

### Post by Serpentinsek on 2008-01-16
Thank you very much for such a quick reply. I've just upgraded to gutsy so the video works fine - for now.

If I'll experience the same problem in the future, I'll sure use your advice.

Kind regards.

---

