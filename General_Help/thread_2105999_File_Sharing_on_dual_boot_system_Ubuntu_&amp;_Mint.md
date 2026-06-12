---
title: "File Sharing on dual boot system: Ubuntu &amp; Mint"
date: 2013-01-17
forum: General Help
---

### Post by eipapp on 2013-01-17
Is it possible to set up file sharing on a dual boot system consisting of Ubuntu 12.10 & Mint 14 ?

Regards,
Bruce

---

### Post by Tralce on 2013-01-18
Your question needs to be a little more specific. How exactly do you want to share files? 

If this was my system, I'd go about the sharing of files between two OSes one of two ways:

Option 1: Create a separate partition for all your shared files, and share that way. Pretty simple. Example:

say a 200GB hard drive
/dev/sda1 (20GB) is Ubuntu
/dev/sda2 (20GB) is Mint
/dev/sda5 (160GB) is your shared partition. Mount it in /mnt or something for both OSes. 

If this was the case, for me, I'd put your typical Homedir directories (Documents, Music, Pictures, Videos) in the shared partition and symlink them back to your home dir on both OSes. 

Option 2: Store everything in one OS's partition and symlink the dir containing those files over to the other OS's partition. 

Example: 

Ubuntu has the larger partition so you store all your things in /home/eipapp/Documents, /home/eipapp/Music ... etc
in mint, mount your Ubuntu partition. then in a terminal, do this:
ln -s /path/to/ubuntu/home/eipapp/Documents/ /home/eipapp/Documents
ln -s /path/to/ubuntu/home/eipapp/Music/ /home/eipapp/Music
... etc

I used to do this all the time when I was dualbooting Ubuntu and Windows.

---

### Post by helpee on 2013-01-18
You can always mount the unmounted partition ( the lazy man's way ), even without the shared data partition ( the best way ). Be careful doing the lazy man's way, as you could damage your other installation by editing the wrong file(s).

---

