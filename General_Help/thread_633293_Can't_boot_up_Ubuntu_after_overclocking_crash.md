---
title: "Can't boot up Ubuntu after overclocking crash"
date: 2007-12-06
forum: General Help
---

### Post by LukeV on 2007-12-06
Ok so I just overclocked my cpu by about 5% (just to see if I could get some more performance out of it) and at first ubuntu seemed to handle it well, but after a few minutes my pc crashed so I had to restart. I set my bios settings back to default so its not overclocked anymore. I boot up ubuntu and like always, whenever I quick restart, I get this black screen checking my Hard drive for errors. But this time after it finished the check, I get a list of errors concerning "bash:" and "command not found".

Anyone know how to fix this?

---

### Post by LukeV on 2007-12-06
Bump...

Please help guys I really don't want to format again :(

---

### Post by Happy_Man on 2007-12-06
Well, that's not very good. First off, what specific errors? If it was stuff along the lines of "bash: apt-get not found", then wait until it drops you to a prompt that looks like ```
root@ubuntu-home#
``` Then, enter ```
fsck /dev/hda
``` and let that work out the kinks in the HDD for you.

---

### Post by LukeV on 2007-12-07
> **Happy_Man said:**
> Well, that's not very good. First off, what specific errors? If it was stuff along the lines of "bash: apt-get not found", then wait until it drops you to a prompt that looks like ```
root@ubuntu-home#
``` Then, enter ```
fsck /dev/hda
``` and let that work out the kinks in the HDD for you.

I tried doing what you said but it gies me anoter error stating that the device is already mounted or its being used by another program or something of that sort. 

Any ideas?

---

### Post by Happy_Man on 2007-12-07
Which partition was being checked? Just substitute that one for /dev/hda. For example, if /dev/sda5 is the problematic one...

```
fsck /dev/sda5
```

---

### Post by sirdilznik on 2007-12-07
The filesystem being checked should really be unmounted or mounted as read only.  Probably your best bet is to run the LiveCD then fsck the hard drive from there,

---

### Post by LukeV on 2007-12-07
I tried run fsck from the LiveCD but it still returned the same error concerning the file system being mounted or being used by a program.

And I did not see any reference to sda# on the error screen. I did however notice that hda2 was the the one being check for errors so I tried typing in

> fsck /dev/hda2

but this still didn't work. Gave me the same error as above.

The good news is I found a way to retrieve all my data from my Ubuntu partition so its not that big of a deal. Although I'd really appreciate it if you guys could help me fix it.

---

