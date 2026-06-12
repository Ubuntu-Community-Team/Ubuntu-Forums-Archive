---
title: "I think this could be bad..."
date: 2006-11-05
forum: General Help
---

### Post by bazz on 2006-11-05
I install a fresh copy of Kubuntu (Edgy) and started to check things out. I went and selected "recovery mode" at startup and it drops me right in root....no password needed. So what&#8217;s the point of locking root or having to use sudo in a normal session if I can do this?
Anyway I didnt know where to pass this info on or if this has been reported, so I thought I'd post it.

---

### Post by taurus on 2006-11-05
That is a normal thing for recovery mode.  What if you use your regular account and accidently remove or modify something important with the sudo, then you have a dead machine.  Now, you need to get into root to fix the problem so that's whyt the recovery mode is for!  And if you don't want people to boot your machine into the recovery mode, then comment out the entry in /boot/grub/menu.lst.  Then, you need to use the LiveCD if you want to fix something on your machine now...

---

### Post by 23meg on 2006-11-05
In short, *you* are responsible from the physical security of your computer, not the security scheme of your OS.

Note that if you designate a root password, it will be required in recovery mode.

---

### Post by Ramses de Norre on 2006-11-05
Just get it out of grub, when needed you can always use 'e' to edit the normal ubuntu entry and add 'single' to the end of the kernel line.

And for real paranoia: set a password on grub so you need to enter it before you can edit entries.

---

### Post by bazz on 2006-11-05
I'm just saying its good there is a recovery mode....but no password?

Ok duhhh I know we can set a password for root, however dont ya think it should be set at install? Just asking.

---

### Post by bsussman on 2006-11-05
> **bazz said:**
> I'm just saying its good there is a recovery mode....but no password?

Ok duhhh I know we can set a password for root, however dont ya think it should be set at install? Just asking.
No because no password set at install means root cannot log in AT ALL

Booting from a recovery system is booting from a separate set of system, security and app files and does not use your installed system.

I guess if I really wanted to keep you up at night, I might tell you that if I can sneak into your house, with a recovery disk, I get to access anything on your system, unless you are doing something like encrypted filesystems.

Time to chill and understand what physical security is, what the absence of a password means and what a recovery system can do.

---

### Post by Ramses de Norre on 2006-11-05
As far as I know the recovery mode runs the exact same system as your normal one, but the difference is that only one user is allowed and I think networking is also disabled.
So no change that a hacker could get in or something.
It's only possible to get in recovery mode when you get physical access to the pc and as said before people can easily steal your hard disk or something then.

---

### Post by bsussman on 2006-11-05
> **Ramses de Norre said:**
> As far as I know the recovery mode runs the exact same system as your normal one, 

I doubt it, since recovery mode allows you to repair a system.  Some repairs cannot be done on a mounted filesystem.

---

### Post by taurus on 2006-11-05
If you are so paranoid about no root password for recovery mode, do like what cooperations do.  Lock your computer in a secure room and hide the key!  Don't let anybody who is not authorized to enter that room because even if you have a password for root, you can still destroy your machine with a LiveCD...  ](*,)

---

### Post by Jason_25 on 2006-11-05
Maybe you should have done a search of the security forum and the like before posting this.  The question gets asked once a month or so.

---

