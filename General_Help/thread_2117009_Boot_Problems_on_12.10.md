---
title: "Boot Problems on 12.10"
date: 2013-02-17
forum: General Help
---

### Post by buddyhusted77 on 2013-02-17
Hello...I am new to Ubuntu 12.10 and have many questions....first though, when booting under advanced options for Ubuntu four items show: Ubuntu, with Linux 3.5.0-24-generic,  Ubuntu, with Linux 3.5.0-17-generic, and then "recovery" for both....can I remove one of those???   Also under normal boot, just selecting Ubuntu, the side bar never shows up with the applications? I have to boot from the recovery mode option???  Also Ubuntu 12.10 is terribly slow...its a long wait for every selection I make?? I would appreciate any help and advice, thank you.

---

### Post by Bucky Ball on 2013-02-17
[I][B]Post moved to its own thread.
[/B][/I]
Firstly, welcome to the forums. 

The 'Introduce Yourself' thread you posted this in originally is for new users to introduce themselves to the community, not for support for technical issues. The ***Communtiy Cafe*** forum is NOT a support sub-forum, as is clearly stated in its description at the top of the page.

If you want help with a problem, please post in the appropriate forum section using a descriptive thread title and briefly describing one issue at a time (and no duplicate posting, thanks). In your post here you are trying to cover several issues at once (boot, sidebar, slowness). That can get confusing unless they are directly related and these don't appear to be.

I suggest you edit your first post in this thread to suit the new title and deal with only the boot issues. Put the rest in new threads in appropriate forum sections. This will improve your chances of getting help. Thanks and good luck. ;)

BB

---

### Post by schragge on 2013-02-17
> **buddyhusted77 said:**
> ...can I remove one of those???
Open a terminal (**Ctrl**+**Alt**+**t**) and try
```

sudo apt-get purge '^linux-image-[0-9]' linux-image-`uname -r`+

```This will remove all Linux kernels on your system, but the current one. In doing so, the boot menu will be updated, too.

---

### Post by buddyhusted77 on 2013-02-17
Okay, thank you, I could not find a way to Post my own thread so wasn't sure what to do...just new at a lot of stuff and looking for help.

---

### Post by Bucky Ball on 2013-02-17
> **schragge said:**
> Open a terminal (**Ctrl**+**Alt**+**t**) and try
```

sudo apt-get purge '^linux-image-[0-9].*' linux-image-`uname -r`+

```This will remove all Linux kernels on your system, but the current one.

Not good. Better to have the current and previous and their recovery kernels.

Better choice to move things around easily by installing and running Grub Customizer:

[http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183)

I'd keep the first four (two kernels and two recoverys) so if one kernel breaks you can drop to the previous one. Over time the kernel will be updated and this list will grow. Then you can get rid of some of them with Grub Customizer (or other methods you will learn along the way) but rule of thumb is generally to keep the current kernel and the one previous to that and their recoverys.

---

### Post by schragge on 2013-02-17
Maybe I was not clear enough. After the command above your boot menu will contain only two entries: one for the normal boot, another for the recovery. Both with the current kernel.

---

### Post by Bucky Ball on 2013-02-17
> **schragge said:**
> Maybe I was not clear enough. After the command above your boot menu will contain only two entries: one for the normal boot, another for the recovery. Both with the current kernel.

Yes, and not the previous so if the current breaks and you can't get into it or your machine you have no options but to wrangle with the terminal or commands unfamiliar to a new user. 

You were crystal clear. ;)

---

