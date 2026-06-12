---
title: "Kubuntu Dapper help?"
date: 2007-01-30
forum: General Help
---

### Post by nerval on 2007-01-30
Hello there, if anyone could help you'll get my blessings.

Here is my problem :

1) K3b doesn't work, it doesn't recognize my cdrw yet i can read if i insert a full cd.
2) I can't use Kpackage, Adept Package Manager or even "apt-get" under my username using sudo command.
2b) I can use "su" command and download and install things yet some ends up being broken and it quite simply refuses.
3) I tried to install kubuntu to the empty partion of my hd, yet it doesn't recognize my current partitions and wants to delete everything.
4) Using "su" being root i installed ubuntu-base and gnome (thinkin' my problem was kde); yet similar problems occurs over there. 
5) I tried to install Windows (my legal old CD from 2001), yet I can't partition my hard drives; and simply restarting with the CD on doesn't work. (and yes I know you need a boot disk, yet I can't burn a CD)
6) I didnt have a back up for about 3 months, and I just can't give up my pictures, documents and song recordings.

+alongside with those problems, MSN, my web cam doesn't work; and KXMAME, Gimp, Firefox kind of programs crushes regularly. 

Could anybody please help ?

Thank you ...

---

### Post by jimbren on 2007-01-30
Here's the first thing I would do:

1) check out this link to address your sudo problem: [http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

By the way, this is an excellent site that I refer back to often.  You might want to bookmark it.

2) since su works, become root and do:
```
apt-get install -f
```

This will find and attempt to fix any broken packages you have.  That may fix the k3b problem and the other random issues you're having, but I'm not sure.

Once you have that done, you should have a fairly stable system.  From there, I'd do a back up, just so you have a current one.  

Then you can either tackle your remaining problems with some new posts to the forum, or reinstall.

---

### Post by Lil_Eagle on 2007-01-30
The situation you describe sounds rather strange.  By default Ubuntu doesn't enable the root account and you can't su.  You CAN get a root terminal (sudo -i, sudo /bin/bash) but you can't login unless you enable the root account.  This is done by design.

As for your problem.  If your data (/home) is on a different partition then it's relatively safe to do a fresh install.  However, if not, then perhaps you can use a USB stick or external drive to backup  your data.

Question, is your normal user account UID=1000?  That could be your problem with sudo.  If you have SU access, you can do a visudo command and fix the sudoers file to allow your normal account's access to sudo.

The permissions of your user account can effect k3b's access to the cdrom.

---

### Post by kebes on 2007-01-30
I think all your problems originate from a single source... somehow sudo/su got screwed up, or your user account had its privileges changed. If, in a terminal, you type:
groups

It will list the groups that your user account belongs to. On a default Kubuntu install, your user account should belong to "admin" and this should give it access to "sudo", you should also be part of groups like "plugdev" and "cdrom" which give you access to mounting external devices, writing to the CD device, etc.

For instance, this is what mine returns (for user "kebes"):
```
kebes@ubuntu:~$ groups
kebes adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin
```

If your groups are screwed up (or you've lost all of your group memberships), then you can switch to root and add them to your user account. This may fix some of your problems.

---

### Post by nerval on 2007-01-30
yes, it just says "nerval audio" 
that's why then ..

gby ! :)

---

