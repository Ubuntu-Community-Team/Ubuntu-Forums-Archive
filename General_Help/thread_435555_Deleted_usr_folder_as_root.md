---
title: "Deleted /usr folder as root"
date: 2007-05-07
forum: General Help
---

### Post by stewpot64 on 2007-05-07
I accidently deleted the usr folder as root, tried booting up the live cd and tried to go to /home/.trash to restore it but it says I don't have permission. I have also tried recovery mode but startx command doesn't work..
Im running Feisty Fawn and xp dual boot

---

### Post by tgalati4 on 2007-05-07
That's the beauty of Linux.  You can delete the entire operating system while you are running.  And it will keep running as long as you don't reboot.

You could go to /root/.trash and do a restore, but a better method would be to back up the /home/yourusername directory and the /etc directory to CD or USB flash drive.

Then wipe the disk and do a fresh install of Feisty.  rsync your files from /home and /etc and hope that you don't have to do too much tweaking to get a working system.

/usr is kind of critical.  It contains the userspace binary programs that you run--everything from utilities to the desktop manager.

If you have another Feisty machine you could copy /usr over and then run a dpkg check to make sure your binary programs have the appropriate libraries available.  

I bet you freed up a lot of space.  

The real mistake was rebooting.

---

### Post by zvacet on 2007-05-07
Make another user with administrator privileges an see if you can save your folder.Go to the recovery and type

```
adduser user_name admin
```

user_name don´t have to be your old username.Pick any username but you have to be in admin group.After you are finish with your work chek if your old user is in admin group.If it is not use above command to do it and after that you can delete user that you create in begining of this post.Good luck.

---

### Post by stewpot64 on 2007-05-07
> **tgalati4 said:**
> That's the beauty of Linux.  You can delete the entire operating system while you are running.  And it will keep running as long as you don't reboot. 
Yes it was still running but nothing worked lol

> **tgalati4 said:**
> You could go to /root/.trash and do a restore,
When I try that it says
**The folder contents could not by displayed**
You do not have the permissions necessary to view the contents of ".Trash".

> **tgalati4 said:**
> but a better method would be to back up the /home/yourusername directory and the /etc directory to CD or USB flash drive.
How would I back it up to a CD if im currently using the live CD
I just thought if i could mount my feisty partition in windows i might be able to back it up would that be possible?

---

### Post by public_void on 2007-05-07
I'd try to recover /usr with the LiveCD approach. Get a Knoppix LIveCD and boot to run level 2, so you just have a shell. You hard drive should have be mounted, in /mnt (I think). Then you will be able to browser to .Trash and copy the contents back to /usr. I'm not sure of permissions, however you could use the su command to gain the right permissions. I'm not totally sure that would work, because of dependencies and such. But the best option, as other have suggested is to backup and reinstall.

---

### Post by steve.horsley on 2007-05-07
This absolutely has to be a job for a live CD. No way will Linux boot without  /usr.

If the usr folder is sitting there in /root/.Trash then it would be better to simply move it (mv) back to the right place. Knoppix is a good CD for this since it offers all the partitions on the desktop. But you can do the job with an Ubuntu live CD if you know how to make a mount point directory and how to mount a partition by hand.

---

### Post by tgalati4 on 2007-05-07
1.  Boot the Ubuntu Live CD
2.  Open a terminal
3.  sudo mkdir myhopelesssystem
4.  sudo mount /dev/hdb1 myhopelesssystem   (your drive device may vary)
5.  cd myhopelesssystem
6.  cd root
7.  sudo su
8.  ls -la .Trash
9.  If usr exists then 
mv usr /home/yourlivecdusername/myhopelesssystem/usr
10.  reboot and remove CD.  (Oh and pray.)

Sorry, most of my machines have 2 CD drives, one a reader, the other a writer.  You boot off of the reader, then you can do recovery with the writer.

Yes, you can also do recovery from within Windows.  But if it crashes, well, then it won't do much good.  Besides, unless you formatted the drive as FAT32, Windows won't know what it is.

---

