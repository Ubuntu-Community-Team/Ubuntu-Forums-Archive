---
title: "DBan Help"
date: 2017-12-06
forum: General Help
---

### Post by shane_faulkinbury2 on 2017-12-06
I'm trying to run DBan on a hard drive that has Ubuntu on it.  DBan fires up and I see all the options.  However when I select "Autonuke" I get the attached screen shot.  Does anyone have any idea what it means and have a possible fix?  I've trid it on my flashdrive and on CD and get the same message.  I've used the disk about 10 times with success.   The computer is a Dell Xperion 3550 laptop.

```
cat:  can't open'/proc/cmdline':  No such file or directory
```

---

### Post by ajgreeny on 2017-12-07
I suspect the error is because that file /proc/cmdline is a virtual file, ie it does not really exist in the way that, for example, a txt file does, but is only present when the OS is booted.

I do not know DBan in detail, though I do know what it is for, but I suspect that the error you see is of no consequence and can be ignored; wait for others to answer if you must be totally certain about this, or consider using other means of blanking the disk.

See
[https://ubuntuforums.org/showthread.php?t=2124829](https://ubuntuforums.org/showthread.php?t=2124829)
[https://ubuntuforums.org/showthread.php?t=2327752](https://ubuntuforums.org/showthread.php?t=2327752)
and search generally for "securely erase hard disk" and I think you will find a huge amount of info, though often people worry more than is necessary about this problem, depending, of course, on what is happening to the disk they wish to erase.

---

### Post by shane_faulkinbury2 on 2017-12-07
Thanks for the response Aj, but what gets me is I get that error on this new laptop and turn around and use the same Dban on my desktop and it works.  I think something is up with this laptop which is a Dell Inspirion 3567.  The thing is, is that I had the same laptop last year that I spilled a cup of water on hence the new one.  The same disc worked on the old one, but not then new!

---

