---
title: "startup failure and recovery"
date: 2018-01-16
forum: General Help
---

### Post by edstevens on 2018-01-16
I have a System76 Gazelle running Ubuntu 16.04 LTS, about 2 years old
This morning when I powered it up it displayed

```
Error: failure reading sector 0x165cfffe0 from 'hd0':
alloc magic is broken at 0x7f5c8ac0: 7f50da00
Aborted. Press any key to exit.
```

At that point, pressing "Enter" returns
```
Reboot and select proper boot device
or insert boot media in selected boot device and press a key.

```

From there I press ctl-alt-delete and get
```
*Ubuntu
 Advanced option for Ubuntu
 system setup
```

(with the * indicating the selected option)
Selecting "Ubuntu just repeats the same cycle.
Selecting "Advanced options" returns
```
Ubuntu with LInux 4.4.0-109-generic
Ubuntu with LInux 4.4.0-109-generic (upstart)
Ubuntu with LInux 4.4.0-109-generic (recovery)
Ubuntu with LInux 4.4.0-104-generic
Ubuntu with LInux 4.4.0-104-generic (upstart)
Ubuntu with LInux 4.4.0-104-generic (recovery)
```
and the list continues with the same pattern with ever decreasing values for the last node of the version number.

Selecting any of the '109' options just repeats the same cycle
Selecting "Ubuntu with LInux 4.4.0-104-generic"  (not upstart, not recovery) results in a couple of screens worth of text messages followed by completing the startup and taking me to my logon and hence to my desktop.

Ideas on what's going on and what I need to do to repair it?

---

### Post by cruzer001 on 2018-01-16
> **edstevens said:**
> 
Ideas on what's going on and what I need to do to repair it?

Take a look at this:

[https://www.google.com/search?client=ubuntu&channel=fs&q=Ubuntu+with+LInux+4.4.0-109-generic&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=Ubuntu+with+LInux+4.4.0-109-generic&ie=utf-8&oe=utf-8)

And a possible fix for Nvidia:

[https://ubuntuforums.org/showthread.php?t=2382409&p=13730101#post13730101](https://ubuntuforums.org/showthread.php?t=2382409&p=13730101#post13730101)

---

### Post by edstevens on 2018-01-16
Thanks for the reply.  My symptoms don't seem to match the Nvidia part of the puzzle, but the kernel updates seems to be an exact match.  It appears I never got the 108 update, but the 109 update.  Further, reading the the link you posted then using that information to do some more google searching, here's my current understanding.  Correct me if I'm wrong:  Canonical released the 108 as a fix for the meltdown vulnerability, quickly found that caused booting issues and so rushed out the 109, which is what I got.  Further, it appears that the 109 also has boot issues on some machines, but that point is a little less clear from what I read -- though confirmed by my own experience!

For the time being, I can continue like I have been the last couple of days, with the sequence I described in my OP.  I take it that list with all the kernel versions is the grub loader, even though I don't see where it actually identifies itself as such?  

But it would be cleaner (I'd think) if I could get it to default to the 104, but then that would leave me open to the vulnerability (?).

Have you seen anything about a recognition of the problem with 109 and possible fix?  Or a way to report it?

---

### Post by cruzer001 on 2018-01-16
Yes, things are up in the air at the moment.  As you, I am running the 104 kernel, waiting for things to flow downhill.  

Here is a link on the 108 kernel:

[https://ubuntuforums.org/showthread.php?t=2382157](https://ubuntuforums.org/showthread.php?t=2382157)

Take a look at the Meltdown/Spectre thread.  You can do a thread search or just ask the more qualified about your concerns.  At this point I'm just along for the ride :)

There is a script you can run, located in the  Meltdown/Spectre thread.

[https://ubuntuforums.org/showthread.php?t=2381801&page=6&p=13728748#post13728748](https://ubuntuforums.org/showthread.php?t=2381801&page=6&p=13728748#post13728748)

A easy way to set grub and the 104 kernel to boot (or any kernel for that matter) is the "Grub Customizer" app (updates are coming down fast, you just may want to wait).

[https://launchpad.net/~danielrichter2007/+archive/ubuntu/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/ubuntu/grub-customizer)

There are other ways

[URL="https://www.google.com/search?client=ubuntu&channel=fs&q=permanently+change+boot+kernel+ubuntu&ie=utf-8&oe=utf-8"]https://www.google.com/search?client=ubuntu&channel=fs&q=permanently+change+boot+kernel+ubuntu&ie=utf-8&oe=utf-8

[/URL]

---

### Post by edstevens on 2018-01-26
Just to bring closure to this, yesterday afternoon I had an alert for new updates.  Installed them an now problem is resolved.  Checking with 'uname -a'  I see that I am now have 4.4.0-112, superseding the previous 4.4.0-109.  So for me the fix to the fix to the fix finally fixed it.

---

