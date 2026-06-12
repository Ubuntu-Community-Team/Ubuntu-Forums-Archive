---
title: "update to 14.04, now password doesn't work"
date: 2014-10-19
forum: General Help
---

### Post by garyed on 2014-10-19
I just updated to 14.04 from 10.04 and I can't get in with the password I was using before the update.
Is there a simple solution before I start going through steps that may cause more problems?

---

### Post by garyed on 2014-10-19
For a little more info:

I've found that if I use Ctrl/Alt/F1 and get to the console it accepts my username and password. I can log in as root and do what I want in the full terminal. It just will not accept the password to let me into the GUI. The other thing is that I have other versions of Ubuntu on different partitions that still work fine on the same computer with the same username and password. This update to 14.04 is the only problem.

---

### Post by Bucky Ball on 2014-10-19
When you are logged in to the CLI, can you type 'startx' and get to a desktop?

---

### Post by garyed on 2014-10-19
> **Bucky Ball said:**
> When you are logged in to the CLI, can you type 'startx' and get to a desktop?

No, I tried that but it doesn't work. It just hangs on a black screen and I have to reboot.

---

### Post by garyed on 2014-10-20
It looks like I'm going to have to save what i can and do a clean install. I've always done clean installs when moving to a new version.  I've never updated to a new version before and have heard of quite a few problems but I figured I would try anyways. My setup is rather tricky. I've got five different versions of Ubuntu, one of Puppy Linux plus Windows XP across four different HD's so Grub and myself get kind of confused. The only way I know which partition Grub looks to at boot up is by looking at my custom files in griub.d directory of all the partitions. Even the bootinfo script isn't sure which one is used.

---

### Post by Bashing-om on 2014-10-20
garyed; Hi !

Booting grub with multiple installs is also of interest to me.
I have all my partitions labeled AND
I have made  - ill advised - edits to " /etc/default/grub " that works well for my use case !
```

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR="My-Work-14.04"
GRUB_CMDLINE_LINUX_DEFAULT="text"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1600x900

```

Of particular note is " GRUB_DISTRIBUTOR="My-Work-14.04 " Your mileage may vary ! It does identify the grub boot ! - ( also the debian splash screen is executed ).

But to the problem at hand .. accessing the GUI .. make sure 'YOU" have authorization to access it:
```

From the install, booted to terminal:
ls -al .Xauthority
ls -al .ICEauthority
ls -al /home
ls -al /home/garyed

```
Where "garyed" is the user name on the system. All should be in your name .. 
else: Will have to make it so and/or create files or maybe even have to go so far as to export $XAUTHORITY.
Will have to see what is, then do whatever.

[INDENT][INDENT]small things
[INDENT][INDENT][INDENT]can mean so much
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by garyed on 2014-10-26
Sorry i haven't been back to update this post.
I ended up backing up my home directory, doing a full install on the partition & everything works fine.  
Another thing that I do is only use a custom menu file for grub so none of the other files in /etc/grub.d are executable. 
It's possible that could have caused a problem but I don't think so because I used the same custom menu after the full install as I did with the update with the exception of the kernel version. The only difference was the full install let me into the GUI with my password. They both took me to the same 14.04 partition but the kernel version was a little different in the full install than the update.

---

### Post by Bucky Ball on 2014-10-26
Good news. Please mark the thread as solved by follwoing the second link in my signature and post a new thread for any further issues.

Good luck. ;)

---

