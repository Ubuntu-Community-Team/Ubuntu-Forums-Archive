---
title: "sudo broken"
date: 2006-12-30
forum: General Help
---

### Post by sulla on 2006-12-30
Hi all!

I am having a severe problem since yesterday!
Yesterday I did a graphical upgrade and since then sudo is broken!

System: Kubuntu 6.10 (only non-standard packages are nvidia binary and beryl)

Symptoms:
1) from a terminal login "Alt-F1" (or from a terminal session from within KDE) I can log in to my account (the primary account) without problems. If I do a "sudo something", e.g. "sudo apt-get update" it asks me for the password, but then *nothing* happens.
From the graphical KDE, if I do a "K ==> run command ==> kdesu konqueror" kdesu asks me for the password and then returns the error message "the password is wrong, please try again" and then I enter the same password again and I get the message "the communication with su failed".

Somehow sudo is broken.

2) the KDE sound does not work any more. KMix reports that no sound mixer was found.

one other thing I did yesterday (just after the upgrade) was that i created a "groupadd 1004" and did a few groupmod and i added my primary user to that group 1004. Somehow this did not work, because I think my sudo was broken already then...

Only if I boot to recovery mode I can run apt-get update and upgrade commands.

WHAT SHOULD I DO???
I believe that the problem is in "the system" itself, i.e. it is not kde.
Something broken in the kernel, in the user management???
Should I just reinstall Kubuntu from scratch? Can I do this without loosing any of my user settings and data? (Then I might just make this, might be simpler than diagnosing and fixing...)

Thanx, sulla

PLEASE HELP ME OUT!!! I'M TOTALLY S(T)UCK!! ](*,)

---

### Post by sulla on 2006-12-30
Hi all!

Ups, I found out WHY it went wrong (This forum is a wonderful place, i dug a little into it and found a few things that i could check!!!):

My fiddling with user groups was catastrophic:
my primary user "sulla" now has only 2 groups: "sulla" and a group that i created yesterday, "share" (for accessing a nfs server).

So, all other groups are missing. What should they be? How can I put those group memberships back??? I think booting to safe mode and do a "usermod --groups admin,adm,... sulla"

But what other groups must I add for a Kubuntu system??

then I checked my /etc/hostname which has a single line the name of my pc, I think that is allright.

Question to /etc/hosts: it reads
127.0.0.1 localhost
127.0.1.1 computername

Is that correct?? 127.0.1.1 ??

---

### Post by taurus on 2006-12-30
Your /etc/hostname should have the same name, **computername**, too.

---

### Post by sulla on 2006-12-30
****. I even know how it happened: I wanted to add my user to a new group "share". I did a
sudo usermod --groups share sulla
That was my last sudo command.
I should have done a "sudo usermod --groups share --append sulla"

Hm...

---

### Post by sulla on 2006-12-30
Hi!

Thanx for help.
YES, my /etc/hostname reads:
computername<RETURN>
so that seems fine.

---

### Post by taurus on 2006-12-30
> **sulla said:**
> Hi!

Thanx for help.
YES, my /etc/hostname reads:
computername<RETURN>
so that seems fine.
Yip.

---

### Post by sulla on 2007-06-09
Just for completeness:

I got my rights back by
1) boot into safe mode
2) usermod -a --groups adm,dialout,cdrom,floppy,audio,dip,video,plugdev,scanner,lpadmin,admin USERID

sulla

---

