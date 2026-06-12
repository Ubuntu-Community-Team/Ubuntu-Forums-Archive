---
title: "AVG Reinstall Fails"
date: 2007-11-23
forum: General Help
---

### Post by mcedata on 2007-11-23
Hi, I installed AVG with the .deb package on Ubuntu, had it working, and just had to screw around with it. End result: I broke it.  I then (foolishly) deleted some of the directories the installer created, and now I can't re-install... I get a "failed to install package" when I try. Is there a way to recover from this?

Thanks for any suggestions

mcedata

---

### Post by maddog39 on 2007-11-23
Well first of all, why do you even need antivirus. Its almost completely useless on linux. The only thing people use antivirus for really, is cleaning incoming emails of potential malware on a mail server. Because of the design of linux and the fact that your running as a regular user 99% of the time, your probably never going to get a virus. So I wouldn't even bother.

---

### Post by mcedata on 2007-11-24
>[QUOTE=maddog39;3825429]Well first of all, why do you even need antivirus. <

Not suggesting I need an antivirus; as we both know, only Windows actually needs that. However, I'm learning to work with Linux, and when I run up against something I can't get done in Linux, my natural curiosity requires me to find out why. I just want to *know*.

mcedata

---

### Post by PmDematagoda on 2007-11-24
Could you tell us what the error message contains exactly.

---

### Post by mcedata on 2007-11-24
> **PmDematagoda said:**
> Could you tell us what the error message contains exactly.

I click on the avg installer, and Package Installer runs. DOS box opens, messages shown:

(Reading database...160550 files and directories currently installed)
Preparing to replace avg75fld 7.5.49_all30. (using .../avg 75fld-r49-all30.i386.deb)
Invoke -rc.d: unknown initscript, /etc/init.d/avgd not found.
dpkg: warning- old pre-removal script returned error exit status 100.
dpkg: trying script from the new package instead...
invoke -rc.d: unknown initscript, /etc/init.d/avgd not found.
dpkg: error processing /home/mcedata/desktop/avg75fld-r49-all30.i386.deb (--install).
subprocess new pre-removal script returned error exit status 100.

mcedata

---

### Post by mcedata on 2007-11-24
> **PmDematagoda said:**
> Could you tell us what the error message contains exactly.

Oh, incidentally...if I use the instructions to install it shown on the main page of the forum, I get the error:

dpkg: error processing avg75fld-r49-all30.i386.deb (--install)
Cannot access archive: no such file or directory.
Errors were encountered while processing: avg75fld-r49-all30.i386.deb

Sure sounds like the install archive isn't present...but it is!  I even deleted the original one, and downloaded it again to my desktop. When I drop to root and move to Desktop, I can look via the
dir command and can see it in the Desktop directory.

mcedata

---

### Post by PmDematagoda on 2007-11-24
Try this:-

1) Navigate to where the .deb file is found.

2) Then do:-
```

sudo dpkg -i --force-overwrite nameofdeb.deb
```

and see if that can solve your problem.

---

### Post by mcedata on 2007-11-25
> **PmDematagoda said:**
> Try this:-

1) Navigate to where the .deb file is found.

2) Then do:-
```

sudo dpkg -i --force-overwrite nameofdeb.deb
```

and see if that can solve your problem.

Unfortunately, that did not work...same error message as before.

mcedata

---

### Post by mcedata on 2007-11-26
[QUOTE=PmDematagoda;3832721]Try this:-

Garn!  Well, forget this thread; I've trashed the install. <sigh>  Tried a reboot, won't, appears I removed something I shouldn't have. 

Thanks for the assist...I guess trying the suggestions made here on a broken Linux install is doomed to failure...I'm in the process of reinstalling Ubuntu, so I'll be back for some more help, no doubt.

mcedata

---

