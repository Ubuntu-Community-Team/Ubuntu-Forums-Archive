---
title: "Files getting lost/not being copied"
date: 2013-04-21
forum: General Help
---

### Post by sbcontt on 2013-04-21
I am at a complete loss with this. 
In last one month I had to reinstall Ubuntu more times than I have ever had to reinstall Windows in my life, so please bear with me if I sound frustrated.

Twice when I tried to backup everything in my filesystem using nautilus, it did not copy everything, and I am not talking about hidden files; first time whole /usr was missing, making the backup useless, next time several subdirectories of /usr were missing. Noiw I strictly avoid GUI for copying and use cp ./

Then I attempted dd image. This time things worked, except when I overwrote a new installation of linux with all the files from the dd image several default files went missing. Overwrite should not delete. The reason I did not directly restore the image is, it was partially unreadable. During dd imaging I had come to know that the drive had 198 uncorrectable sectors on it and nobody told me? I would just sometimes see fsck running during boot and nothing else, no warning even though /usr was nearly charred.

I replaced the 4 months old nearly dead WD drive with a new one instantly, but this time .bashrc  and .bash_profile went poof (located on my Debian powered NAS) with several valuable scripts that were in it. In its place some xyz@root nonsense was there that I could not decipher. I had backup though.

After I was able to recover my system by mixing the image and a new installation,  but found out that too many permissions were messed up. I don't know how linux copies permissions, but I can confirm that passwd file was near identical to that of old installation. (I had the idea that as linux does not have the infernal registry of Windows recovering a system would be easy. Turns out, not)
Anyway I did a fresh install that came with Bug #947638 and I use NFS.
All this time my backup drive was attached to the PC. So I thought of just copying the img file to local drive and detaching the external drive.
sudo rsync -rvh --progress /media/sd1/backs.img /media/files

The image was 46 GB in size and rsync was going strong even after 80 GB. So I stopped it with ^C.  Then I checked and found out that the destination file is only 300MB in size and source file is gone.

Is my PC haunted or something?

---

