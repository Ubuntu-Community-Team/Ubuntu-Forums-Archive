---
title: "Archive Splitting/Backup and Restore; Kernel Not Included"
date: 2014-09-26
forum: General Help
---

### Post by SciGuy1872 on 2014-09-26
I have multiple DVD's and cannot fit the backup of / (that includes  /home, /Downloads, /Documents, etc., right?  I can browse the File  System and browse the aforementioned folders through the Home folder  once double-clicked) onto my single, 4GB USB.  The reason I need to do  this is that the kernel on this hdd is EOL, so on the other disk, I have  a fresh install of 12.04 with the 3.2 kernel being supported to 2017;  so, I need to backup everything EXCEPT the kernel and graphics stack.  

Since the DVD holds 4.7 GB of data, I am restricting the size of the splits to 4500m:

tar -cvpz backup.tar.gz --exclude=/backup.tar.gz / | split -d -b 4500m - /home/anthony/Desktop/backup.tar.gz. 

Is this command correct?  Then the individual files, I can burn to DVD's and paste them to the Desktop on 
the other hdd and reconstitute them, after the cd to Desktop, with the command:

cat *tar.gz* | tar -xvpzf - -C /  

Is this command correct?  

After this, I use the following command to restore the other hdd, so that it is just like this one, except 
the kernel and graphics stack, correct?

sudo tar -xvpzf /home/anthony/Desktop/backup.tar.gz -C /media/whatever --numeric-owner

What should I include for the term "/media/whatever"?  Do I need to restore GRUB?--I changed the files, but
I am still booting into Ubuntu. Is this command correct if I do need to restore GRUB:

sudo -s for f in dev dev/pts proc 
mount --bind /$f /media/whatever/$f 
chroot /media/whatever dpkg-reconfigure grub-pc

I found these instructions on (the part about GRUB was not very detailed, so I'm hoping I can skip
it--because I don't really understand the commands):

[https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

After all this is done, is there a command I can issue in the CL to hold the kernel--I figured I would just
add the question since I am already posting.

Thanks for your time! 				

P.S.  I was warned by ian-weisser about this process: 

"You can certainly try your original idea to restore older package files  onto a newer system. But be quite prepared for it to not work, to  possibly break your package manager, and perhaps even to crash your  system." 

I replied that the other hdd is not newer--just the same OS (Precise) and an older kernel (3.2)--this hdd I wish to backup has a 3.5.0-54 kernel that is EOL.  I have files in /usr/games, /usr/share/games, and usr/share/celestia,  about different programs--don't these files need to be backedup/restored  to the other drive so that, well, Celestia, for example, can function  with all the data I've added on to the program?  There may be other directories that I do not know I need to copy and paste--Opera, for example.

Why should backup/restore crash my Ubuntu system?  I thought that process on Linux machines was supposed to be easy--I read a post (looked for the original How To--an old thread, but couldn't find it) that stated that Linux wouldn't even need to do the things Windows does--like enter a special boot to restore.

I'd rather use the splitting procedure I wrote about, if it would be fine, because I understand it and have no trouble with the CL.  I would need help with GRUB if I'm going to have trouble with it.  What do you all make of this process--would it work, or is there a chance it would destroy my system; other options?  Would the kernel and graphics stack be left out with tlhis splitting procedure?

---

### Post by Irihapeti on 2014-09-26
Thread closed. Duplicate of [http://ubuntuforums.org/showthread.php?t=2245752](http://ubuntuforums.org/showthread.php?t=2245752) Please continue the conversation there.

Please don't start multiple threads on the same topic. It makes it harder to offer help when the details are in different places.

If you want a thread to be moved to a different sub-forum, please ask by using the report thread tool.

---

