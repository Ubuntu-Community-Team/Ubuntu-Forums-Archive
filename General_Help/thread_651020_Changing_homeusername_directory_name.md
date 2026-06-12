---
title: "Changing /home/username directory name"
date: 2007-12-27
forum: General Help
---

### Post by FoxHappy on 2007-12-27
I've read a few other threads about this, but I'm still fairly new to linux and not 100% on all the commands. All I know is a few of the commands that are dangerous to play around with, so wanted to get a more official answer before I went punching things in.

Basically, I just changed my user name on my computer. Got all that sorted out fine, but my main directory is still /home/oldname and I want to change it to /home/newname.

1. how do I do that and 2. is changing the name of that directory going to effect how anything runs?

Like I said I know there are several other threads about this, please don't link me to them, just trying to do a cut and dry name change without repercussions and the other threads confuse me.

---

### Post by bodhi.zazen on 2007-12-27
Open a shell and become root (or boot to recovery mode)

```
sudo -i
```

Then :

```
mv /home/newname /home/newname.bak
cp /home/oldname /home/oldname.bak
mv /home/oldname /home/newname
chown -R new_user.new_user /home/newname
chmod -R 770 /home/newname
usermod -d /home/newname new_user
```

That's it. Reboot and try out your new home

It it works you can delete the backups :

```
sudo rm -rf /home/*.bak
```

Careful with that rm -rf :twisted:

---

### Post by FoxHappy on 2007-12-27
> **bodhi.zazen said:**
> 
```
mv /home/newname /home/newname.bak

```


I got:

```
mv: cannot stat `home/*newname*': No such file or directory
```

---

### Post by dcstar on 2007-12-27
> **FoxHappy said:**
> I got:

```
mv: cannot stat `home/*newname*': No such file or directory
```

*newname* is an example that **you** are supposed to replace with the name you want to use.

---

### Post by FoxHappy on 2007-12-27
> **dcstar said:**
> *newname* is an example that **you** are supposed to replace with the name you want to use.

Yes, I know. I did use my own, I was just using an example back. It didn't work with my own, that's the error I got.

---

### Post by dlegend on 2007-12-27
> **FoxHappy said:**
> Yes, I know. I did use my own, I was just using an example back. It didn't work with my own, that's the error I got.

Are you sure that the /home/newname exists? The "newname" should be replaced with the current username you are using. Also make sure you didn't mistype the command and leave out a "/" before the path.

---

### Post by derek45 on 2007-12-30
I tried this and now I can't login.

I think I got fat-fingered and miss-named everything.

What do I do now ?

---

### Post by bodhi.zazen on 2007-12-30
You will need to boot to recovery mode or a live CD and fix it :)

ls /home will give you the directory name , then see my first post.

---

### Post by derek45 on 2007-12-30
I went into XP, removed the partition, and rebooted with the 7.04 CD.

(7.10 wouldn't go on this machine)

I'm reinstalling ubuntu 7.04 now.

:confused:

---

### Post by ~LoKe on 2007-12-30
> **derek45 said:**
> I went into XP, removed the partition, and rebooted with the 7.04 CD.

(7.10 wouldn't go on this machine)

I'm reinstalling ubuntu 7.04 now.

:confused:

No one said you had to re-install...

---

### Post by derek45 on 2007-12-30
too late :)

I figure it's time to start fresh again.

It's installed, GRUB is working again,  and it's doing 170 updates.



What should I have done?

---

### Post by ~LoKe on 2007-12-30
You **should** have installed 7.10. ;)

But for your previous problem, there was a post made explaining what to do.  Boot up the LiveCD and correct the errors there (either by restoring the backup or correcting the initial naming mistake).

---

### Post by derek45 on 2007-12-30
I burned an 7.10 ISO, tried to boot,  but it gave me a black screen of death.

This same 7.10 CD will boot on my desktop fine, so I know the CD is OK.

I figured I'd install 7.04, do the 174 updates, then update to 7.10.


thanks for you help.:)

---

