---
title: "share Truecrypt partition with Windows"
date: 2017-11-13
forum: General Help
---

### Post by leslia on 2017-11-13
I have a dual-boot laptop (Ubuntu 16.04 and Win7) with a Truecrypt encrypted NTFS partition that I’d like to share with my Win7 desktop when the laptop is booted into Ubuntu.  I added the Win7 user of interest as a samba user so the desktop sees the laptop.  Any folder I share with Nautilus shows up on the desktop machine, no problem whatsoever.  When I mount the TC partition to one of the slots, say truecrypt1, I can only do this with root permissions.  I see the truecrypt1 share on the desktop, but when I try to open it I get
 
“Windows cannot access \\laptop\truecrypt1
You do not have permission to access \\laptop\truecrypt1”
 
I also tried creating a folder both within the home directory of the same user as the desktop and outside, then mounting the partition in the folder, but I still get
 
“Windows cannot access \\laptop\truecrypt_folder
You do not have permission to access \\laptop\truecrypt_folder”
 
Once mounted, no amount of changing permissions seems to grant permission to the desktop user to see the mounted partition or the contents of the folder I mount it in.
 
As you can probably guess this is my absolutely first post here (newbie) so please be kind!

---

### Post by leslia on 2017-11-14
I’m not sure I used the best approach, but I ended up solving the problem by creating a user on the laptop with the same name and credentials as the desktop, giving it admin rights, and then mounting the partition to a folder in this new user’s home folder.  Probably not the most secure way to do it, but it works.  Now if I could only get Windows to stop showing me old non-existent shares from the laptop!

---

