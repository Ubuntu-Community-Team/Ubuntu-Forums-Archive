---
title: "NFS slow when transferring lots of smaller files"
date: 2008-07-01
forum: General Help
---

### Post by infinitejones on 2008-07-01
I have two desktop machines and a laptop, all running Hardy. They're on a LAN via a router, with NFS set up on all of them as per this thread: ubuntuforums.org/showthread.php?t=249889

From my laptop I can mount and browse the two desktop machines via nautilus just fine, and transferring a single large file (ie. a 700MB iso) from the laptop to either desktop maintains speeds around 3MB/sec consistently. I'm happy with this speed.

However if I try and transfer lots of smaller files, eg. a few folders full of MP3s that I've ripped using the laptop, the file transfers are really slow and seem to go in fits and starts - the "file operations" window says it's transferred maybe 15mb then halts for a few minutes, then transfers a bit more. It's reporting transfer speeds of only a few hundred KB/sec but with the stopping and starting it's actually even less than that. Eventually it seems to time out and give up and the file operations window closes.

Here are my /etc/fstab entries on the laptop for the two machines:

```
192.168.0.171:/files /server nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.0.130:/share /dell nfs rsize=8192,wsize=8192,timeo=14,intr
```

My understanding from a bit of googling is that the rsize and wsize values make a difference, but I'm reluctant to change them because I do get good speeds when transferring large files. Also, videos and MP3s streaming across the LAN from the server to VLC or Kaffeine running on the laptop work just fine with no halting at all.

Any suggestions? Thanks!!

---

### Post by fsmithred on 2008-07-03
Two suggestions:

Be brave, and test it at half and double the sizes.

Check to see if there are any issues with your ethernet adapter and nfs or other file transfers. I had a problem copying large files with mine (Attansic L1) and found directions to tweak it with ethtool to get it to work right.

---

### Post by sujoy on 2008-07-03
i would say mount over ssh, or even better, a ftp server like vsftpd

---

### Post by infinitejones on 2008-07-05
sshfs works very well - I found [this tutorial]("http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/") which made it nice and simple. Thanks!

---

