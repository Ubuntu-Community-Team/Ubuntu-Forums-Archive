---
title: "Help! Dell Laptop (WINDOWS) Hard Drive Failure - Data Recovery With Live CD?"
date: 2007-05-22
forum: General Help
---

### Post by jfrancis on 2007-05-22
Greetings all,

My friend just phoned me in distress.  He is running a Dell 510m Laptop with Windows XP.  He told me his Hard Drive started making strange noises (!) and then his laptop crashed.  When he rebooted the machine, it would not load XP, Instead, it sits there and asks for a password to be entered (not in XP, at boot).

He has phoned Dell support, who explained this was normal (when HDD goes wrong, it does this for protection...) and they said they could give him the password.  However, the password they gave was not the right one - it does not accept it.  Dell told him that they can do no more to help and advised he purchased a new Hard Drive and if he wished to attempt to recover his Data, he should hire a Data Recovery specialist (?).

Now... I am a Ubuntu user myself, though a beginner.   I am putting this problem out here to see if you can help my friend.  I have a Feisty LiveCD handy and was pondering whether it would be possible to use it on my friends laptop to attempt to access his hard drive - he has much Data he would like to retrieve if possible.

Can anyone advise what I of he can do?  Is it possible to access a windows Hard Disk from the LiveCD?  

I appreciate your time and energy on this.


Many thanks!

---

### Post by energiya on 2007-05-22
> **jfrancis said:**
>  Is it possible to access a windows Hard Disk from the LiveCD?

Yes. Just try booting the liveCD (don't forget to make the CD-ROM bootable from bios) and copy the data from the windows shares on another storage media. If the windows shares aren't mounted try mounting yourself:
- see how are the partitions named
```

ls /dev/sd*

```
- mount the one(s) you want
```

sudo mkdir /media/sdYX (or whatever, it doesn't matter, its just a folder)
sudo mount /dev/sdYX /media/sdYX

```
- copy data

I hope this helps you... (I've written all from memory... I really don't know how are the namings in 7.04)

**edit:**
I don't know anything about this password stuff from Dell, but I hope it doesn't interface with Ubuntu.
About the strange noises from HDD, I've heard a few cases (desktop users) and unfortunately recoverying the data would had  required some specialist help, but it was quite expensive so they just recovered from old backups. I hope this will not be the case. Try first using Ubuntu and then you could try putting the HDD on another computer and trying to recover the data using some of the apps build to do this... you can find a few for windows.

---

