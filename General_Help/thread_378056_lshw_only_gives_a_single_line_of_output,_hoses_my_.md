---
title: "lshw only gives a single line of output, hoses my terminal"
date: 2007-03-06
forum: General Help
---

### Post by monocongo on 2007-03-06
When I run lshw in a konsole terminal window I see some output flash by on a single line, finally resulting in "USB".  I get nothing after that and I can't kill the command using Ctrl-C, Ctrl-Z, etc.  For example here's what it looks like after I run a lshw command:```
$ sudo lshw
USB

```

I am running lshw in order to work out why I don't have USB support, so maybe these two issues are related (since "USB" is the last thing I see)?

Thanks in advance for any ideas as to what may be the problem, how to fix this, etc.

---

### Post by Kateikyoushi on 2007-03-06
It should be like that but when it finishes displays a tree of your hardware.
Try this
```
sudo lshw > lshw
```

Then check the content of the lshw file.

---

### Post by monocongo on 2007-03-06
Actually I've used lshw in the past and had it give much different looking output than this (see [**this thread**]("http://ubuntuforums.org/showthread.php?t=361540") for examples).  Something must be amiss because when I redirected the lshw command output to a file as suggested I got the same result as before, and the resulting file was empty.

---

### Post by Kateikyoushi on 2007-03-07
I know it was different but it works the same way for me as well.
I see changing character in that line and when it ends it displays a tree o the hardware.
Maybe this is a new version. See here how it is displayed. [LINK]("http://ezix.org/project/wiki/HardwareLiSter")

lshw -short is still looks the old way.

Nevertheless it crashes for you at USB that's why you get no output in either way.

---

### Post by monocongo on 2007-03-07
Thanks Kateikyoushi for the further info on how lshw works, and for the page link which introduced me to lshw-gtk, which is a really nice GUI for lshw (and it appears to work well for me, better than lshw at the command line anyway).

I have fixed my USB troubles, and lshw is now stopping at SCSI, so maybe I now have some SCSI issues to address?  In any event now when it stops at SCSI I can at least escape out of the program (Ctrl-C) and keep going with the shell.

---

### Post by Ifaistos on 2007-12-22
Hello :-)

Well for a more readable (and permanent form) of the the output of lshw I do this :

sudo lshw -html > lshw.html

Then I go to my browser and give the address of lshw.html usually :

/home/....../lshw.html

you put your username in the place of the dots.

Hope it will help you in the future

Have a great Holiday Season :)

---

