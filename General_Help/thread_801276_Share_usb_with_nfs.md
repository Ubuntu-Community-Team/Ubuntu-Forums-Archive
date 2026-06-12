---
title: "Share usb with nfs"
date: 2008-05-20
forum: General Help
---

### Post by silvagroup on 2008-05-20
I have a WD MyBook(external drive) that I bought for keeping backups. pictures, dvd's and the such. 
What I want to do is to also set it up so that my wife and my daughter can also use it.
I need a very simple how to for using this usb device with nfs.
Thank you.

---

### Post by .nedberg on 2008-05-20
Have a look here: [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NFS_Server](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NFS_Server)

That should work just fine if you have Hardy

---

### Post by silvagroup on 2008-05-20
.nedberg,
Thanks all that is already in place, and currently using 7.1o.
I actually have nfs share setup using a hdd on the my system but can not get the usb drive to do the same. I can use the usb but I can not get the nfs to work with it.
Been hammering myself with this for several months now with no resolution yet.
I am sure it some simple thing but can't figure out why nfs will not work with usb.

---

### Post by .nedberg on 2008-05-21
Have you made a mountpoint for the drive? Or are you using "media:/<something>" when you browse the drive? Place a line in fstab for the drive and mount it, configure exports and the issue 'sudo exportfs -a' in a terminal.

USB and NFS should be no problem. What filesystem is the disk? I only use ext3 for my exports. Might be a problem with FAT, I don't know. Sorry!

---

### Post by silvagroup on 2008-05-21
> Have you made a mountpoint for the drive?on the client /media/backups. Client fstab includes this line: 192.168.1.11:/media/MyBook/stacey  /media/backups nfs rw,hard,intr 0    0 On my computer where usb drive is /media/MyBook.
My fstab for the drive is: UUID=fe19c423-1d7b-449a-ab3e-23f46ffa422b /media/MyBook ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2.
When I do 'sudo exportfs -a' I get /media/MyBook/stacey does not exist, yet I can see it in my media folder?
Also when mounted in fstab I can not access the drive, if I try I get permission denied. And it still shows the drive as a removeable media in the media folder and desktop icon.

---

### Post by .nedberg on 2008-05-21
What does your /etc/exports look like?

It could be a permission problem. Is the /media/MyBook/stacey directory writable by your normal user?

---

### Post by silvagroup on 2008-05-21
/media/sdb1/Pictures 192.168.1.8(rw,async) 192.168.1.9(ro,async)
/media/sdb1/Childrens_Ministry 192.168.1.8(ro,async)
/media/sdb1/Church 192.168.1.8(rw,async)
/media/sdb1/WindowsXp 192.168.1.8(rw,async) 192.168.1.9(rw,async)
/home/carlos/.kde/share/apps/kabc/std.vcf 192.168.1.8(rw,async)
/media/MyBook/stacey 192.168.1.8(rw,async)
> Is the /media/MyBook/stacey directory writable by your normal user? Yes.

---

### Post by .nedberg on 2008-05-21
Stop the NFS server, unmout and then mount the USB disk and restart NFS.

I did some searching and could not find anything related to this. Sorry I can't help you anymore :(

---

### Post by silvagroup on 2008-05-21
Thanks for trying. I too have been searching for several months with little success.
I found a program called Usb Server that says it makes this process easy but since I am not sure what it really does, and since for the most part my system works really well, I am reluctant to try it out. I haven't even upgraded to 8.04 yet for that reason.
Again thank you for your help.

---

