---
title: "sudo does nothing"
date: 2008-04-30
forum: General Help
---

### Post by evanct on 2008-04-30
i type sudo [something], in this case dpkg-reconfigure ipod-convenience, and nothing happens. no error messages or anything, it just immediately goes back to the prompt. can anyone help? this is a headache..

---

### Post by Nunu on 2008-04-30
> **evanct said:**
> i type sudo [something], in this case dpkg-reconfigure ipod-convenience, and nothing happens. no error messages or anything, it just immediately goes back to the prompt. can anyone help? this is a headache..

Try using sudo -s dpkg-reconfigure or gksu dpkg-reconfigure.

---

### Post by evanct on 2008-04-30
> **Nunu said:**
> Try using sudo -s dpkg-reconfigure or gksu dpkg-reconfigure.

it asked me for the password, i entered it, and THEN it did nothing.

---

### Post by evanct on 2008-04-30
oh, that was when i used sudo -s. when i used gksu i got an alert box with this:

"Failed to run dpkg-reconfigure ipod-convenience as root.

The underlying authorization mechanism(sudo) does not allow you to run this program. Contact the system administrator."

---

### Post by Nunu on 2008-04-30
Bump...

Ok I have not played with dpkg or ipod software so i am not sure what the results should be and if it is going to display any results. i take it ipod-convenience  has something to do with synchronizing your ipod. what is dpkg used for?

---

### Post by evanct on 2008-04-30
> **Nunu said:**
> Bump...

Ok I have not played with dpkg or ipod software so i am not sure what the results should be and if it is going to display any results. i take it ipod-convenience  has something to do with synchronizing your ipod. what is dpkg used for?

well, when i installed ipod-convenience it prompted me for my ipod's IP, however i think i mis-typed it. dpkg-reconfigure ipod-convenience is supposed to let me change it.

but sudo doesn't work with any command, apt-get or anything.

---

### Post by Nunu on 2008-04-30
And there is no other software in the repositories that gives you a gui based system to sync your ipod? 

I know Amarok connects to ipod's... like i said i haven't tested it yet but maybe that would be an easier solution. It's suppose to work like WMP when you connect your ipod.

---

### Post by Nunu on 2008-04-30
try this maybe this will help

[http://ubuntuforums.org/showthread.php?t=645848](http://ubuntuforums.org/showthread.php?t=645848)

---

### Post by evanct on 2008-04-30
well i've been using this guide

[http://www.ipodtouchfans.com/forums/showthread.php?p=260605](http://www.ipodtouchfans.com/forums/showthread.php?p=260605)

---

### Post by evanct on 2008-04-30
the thing is in both that guide and the thread you posted, a crucial step is typing ipod-touch-mount, which tells me that it cannot PING the ipod's IP, which is mistyped. so, i need to sudo dpkg-reconfigure ipod-convenience, but sudo doesn't work, which brings me back to my original question.

how do i fix sudo?

---

### Post by Nunu on 2008-04-30
very peculiar

Sorry man I have no idea from here on

---

### Post by RAOF on 2008-04-30
> **evanct said:**
> well, when i installed ipod-convenience it prompted me for my ipod's IP, however i think i mis-typed it. dpkg-reconfigure ipod-convenience is supposed to let me change it.

but sudo doesn't work with any command, apt-get or anything.

Are you in the 'admin' group (you should be, if this user was set up as a part of the install process)?  Only users in this group can use sudo - it should say 'user $USERNAME is not in sudoers - incident will be reported' or somesuch if you're not in the admin group.

---

### Post by Nunu on 2008-04-30
Have you tried reinstalling the software?

---

### Post by Nunu on 2008-04-30
> **RAOF said:**
> Are you in the 'admin' group (you should be, if this user was set up as a part of the install process)?  Only users in this group can use sudo - it should say 'user $USERNAME is not in sudoers - incident will be reported' or somesuch if you're not in the admin group.


How would I go buy adding a user to the admin group?

---

### Post by evanct on 2008-04-30
> **RAOF said:**
> Are you in the 'admin' group (you should be, if this user was set up as a part of the install process)?  Only users in this group can use sudo - it should say 'user $USERNAME is not in sudoers - incident will be reported' or somesuch if you're not in the admin group.

yeah, i have admin privleges.

---

### Post by evanct on 2008-04-30
> **Nunu said:**
> Have you tried reinstalling the software?

i'd rather not have to go and backup all my files :/ this isn't a fresh install, it's an upgrade.

---

### Post by RAOF on 2008-04-30
Hm.  I can't think of any time when sudo has silently failed like this.  Does it persist across reboots?  If you boot into single-user mode, can you use apt, etc?

---

### Post by evanct on 2008-04-30
> **RAOF said:**
> Hm.  I can't think of any time when sudo has silently failed like this.  Does it persist across reboots?  If you boot into single-user mode, can you use apt, etc?

rebooting didnt help

---

### Post by Nunu on 2008-04-30
RAOF Could it be a problem with the dpkg-reconfigure  package itself?

---

### Post by evanct on 2008-04-30
...like i said, sudo doesn't work with anything. not just dpkg-reconfigure.

---

### Post by Nunu on 2008-04-30
> **evanct said:**
> ...like i said, sudo doesn't work with anything. not just dpkg-reconfigure.

True that

And you upgraded from Gutsy through the update manager right?

---

### Post by jocko on 2008-04-30
Did you try RAOF's suggestion?> **RAOF said:**
> If you boot into single-user mode, can you use apt, etc?
If single-user mode does not work, a reinstall is the only thing that will help, but if it works there may be ways to fix it.
If you didn't know: To get to single-user mode: Reboot and hit Esc when grub loads to see the boot menu. Select a line that ends with "(recovery mode)".

---

### Post by evanct on 2008-04-30
I did what you suggested, booted into single-user mode and sudo worked. i re-set the IP of ipod-convenience. i get back into normal mode, connect the ipod, type ipod-touch-mount and it tells me:
/var/mobile/Media: No such file or directory

hmm

---

