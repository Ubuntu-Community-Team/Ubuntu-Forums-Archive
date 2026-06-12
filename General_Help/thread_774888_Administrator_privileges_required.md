---
title: "Administrator privileges required"
date: 2008-04-29
forum: General Help
---

### Post by perarild on 2008-04-29
Each time I mount a Truecrypt volume a message pops up, "Administrator privileges required", and asks for the sudo password.

I'm wondering if there's a way to mount Truecrypt volumes without having to type the sudo password each time.

I thought at first that truecrypt maybe needed root permissions when creating the folder in /media to mount the volume, so I tried creating the folder before mounting, but that didn't make any difference.

Maybe there's a way to give truecrypt administrative rights so it doesn't need a password each time?

---

### Post by undecidable on 2008-04-30
I have just installed truecrypt and am testing it.
Same issue.

I don't think it is a truecrypt permissions issue as I can run from the command line:  truecrypt -l  tosee mounted devices.

I think it is because admin privileges are required to mount a volume unless it is specified in /etc/fstab.   But given this is not a real volume, I am not yet sure how to get around that.  Am cogitating it.

---

### Post by undecidable on 2008-05-02
Solution. 
Add the following to your sudoers  file  (edit with visudo)
      unme	ALL = NOPASSWD: /usr/bin/truecrypt
where unme is your user name.

Some Observations for the Detail Oriented:
1.  I don't think this adds any extra insecurity,
as truecrypt enables me to run most commands without a sudo p/w anyway.  
And to mount a volume, still need the disk mounting p/w.

2.  I don't think the p/w requirement is a big issue anyway as
If call truecrypt, it only asks for the sudo p/w 1st time I mount a disk.
If I dismount but don't exit, it doesn't ask for the sudo p/w the 2nd time I mount.

3.  However it does become an issue if I want a user 
who I didn't want to have any sudoers priveleges to be able to mount a truecrypt disk.  
Solution is as above. 

4.  It is nok to run
  sudo truecrypt
Works OK on the 1st mount, then if you dismount and remount,
truecrypt locks up on the remount and the processes have to be killed.  

5.  I don't think there is an fstab solution.
(ie specifying the disk as user,noauto)
  mount output shows the volume as /dev/loop0
but you could not guarantee loop0 would always be the device available.

---

### Post by grashdur on 2008-05-10
This looks like a great idea, as I've always found this annoying about Truecrypt. Where do I find the sudoers file? I searched in my "File System" for this filename and came up with zero results.

---

### Post by not_surt on 2008-05-10
sudoers is in /etc but you should make sure you only edit it with visudo.
```
sudo visudo
```

---

### Post by ronjouch on 2011-12-24
Exactly what I was looking for! Thanks everybody!

One important detail though, you must put your entry at the bottom, [otherwise the %admin line will override whatever you specify]("https://napkins.wordpress.com/2009/02/18/using-nopasswd-in-sudoers-on-ubuntu/").

---

### Post by oldos2er on 2011-12-24
Closed, necromancy.

---

