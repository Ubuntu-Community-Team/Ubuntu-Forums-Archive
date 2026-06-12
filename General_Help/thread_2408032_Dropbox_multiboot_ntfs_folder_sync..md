---
title: "Dropbox multiboot ntfs folder sync."
date: 2018-12-12
forum: General Help
---

### Post by rionwolf7 on 2018-12-12
In an earlier  closed thread by vanadium people we're wanting solution to sync Dropbox on multiple boot systems in one ntfs directory. Vanadium had a good suggestion that I tweaked a little bit to solve.
1. First you must install it in Windows or other system and setup Dropbox folder from Dropbox.
2. Second reboot into Linux system. (I used Ubuntu 18)
3. Third install Dropbox to Ext 4 partition.
4. Fourth Open file manager to Home folder and delete Dropbox directory. Leave this file manager open.
5.  Fifth Open a new file manager to the main directory ntfs or other that other os Dropbox folder is in.
6. Sixth hit ctr + h then drag the Dropbox folder to the directory you deleted it from. (This creates a symbol link shortcut to the Dropbox folder you want) 
7. Now sync Dropbox in Linux.
8. If you want Dropbox to load at startup you must set the partition folder is in to auto mount on startup in terminal by: (
down vote
1 - Write down the UUID of the drive that you want to mount by executing the following command:

sudo blkid
2 - Then edit the fstab:

sudo gedit /etc/fstab
3 - Add at the end of the file fstab:

UUID=D638F77338F7514B /media/baraldi/win_www ntfs defaults 0 0
Be sure the UUID matches what you recorded in the first step

4 - Restart)

Or Use the "Disks" app.

Load the Disks app (In System) and select the disk with the filesystem you want to mount on startup.

Then select the filesystem on that disk and click on the gears (for configuration).

Select "Edit Mount Options" from the popup menu.

On the setup options, click to check the "Mount on Startup" box. (This will add the entry to fstab when you click on "OK").

Reboot, and your filesystem should be available.

I agree with other comments here regarding manually adding lines to fstab via CLI/text editor. If you take the time to look at your fstab file it will help you understand what changes have been made and, ultimately the CLI method will become faster for you.

---

