---
title: "Ubuntu Not Starting Up (Low File System Memory)"
date: 2021-12-11
forum: General Help
---

### Post by aw1182 on 2021-12-11
Hi,

I tried to start my laptop this morning which has Ubuntu installed in it.  I forget which version it is exactly but I had installed the latest Ubuntu version about 2-3 months ago.  I had been getting an error in the past few days that my system has low file system memory and this morning it booted up all the way to the login screen and I saw a pop up window that said I only had about 150 mb of memory in the file system.  When I tried to log on by entering my password for my user account the screen would go black and then return to the login screen.  I decided to restart my laptop now it only boots to a black screen with this line on the top:

/dev/sda5: clean, 234498/30466048 files, 11583186/121833472 blocks

Would someone be able to kindly assist me with this issue?  The only thing I care about at this moment is to get my document files and some home made videos/pictures and save them.  Is there any solution to fixing this or if not is there any way to access my personal files (not many but important) and back them up to a usb drive/external drive?

Thanks.

---

### Post by oldfred on 2021-12-11
Many here say your data is not valuable if you are not regularly backing it up.
[off topic]
As an old farm boy, I was taught to close the barn door.
Something about closing the barn door after the horses have left. We did not have horses. Grandpa sold them when I was 3 and used the new fangled gas powered tractor. [/off topic].

Do you have the live installer you used to install Ubuntu?
If so boot that. You should then be able to mount & backup/copy your data to another device.
You then may be able to houseclean some old data.
But black screen is often a video issue.

Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO (unless 21.10)
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

What brand model system?
What video card/chip?
If you want lots of details on hardware you can run this new script. Do not copy data from the screen as it may include data you do not want to share. The upload to pastebin site removes that type of data. Spacebar thru the screens & q to exit screens.
wget -N -t 5 -T 10 [https://github.com/UbuntuForums/system-info/raw/main/system-info](https://github.com/UbuntuForums/system-info/raw/main/system-info) && \
chmod +x system-info && \
./system-info

---

### Post by yancek on 2021-12-11
Did you actually get the specific error?  In most cases it will be a matter of the / (root) filesystem being full.  This is often a resut of not having logrotate set up correctly.  Use a live linux system on a usb and mount the / filesystem partition and take a look at the /var/log directory for many large files and delete them.  If your not confident with doing that, follow the advice of oldfred above.

---

### Post by aw1182 on 2021-12-11
Ahh I was in the process off backing everything up last night but then my laptop died due to low battery and I was actually going to do it this morning and then this problem occurred.  :*(

I don't think its a video issue something but something to do with the low memory error I got for the filesystem.

My laptop is a Dell Latitude, Nvidia card (I think), i7 processor, with 8GB ram.

I do have the USB flash drive that I used to install ubuntu on the laptop and I did the live boot before I read your posts here to see if I could somehow access my files.  I'm not to good at ubuntu and I just want to clarify when you say live boot from USB that would be the trial run of ubuntu from the USB where it doesn't install anything correct?  If so would be able to walk me through the steps of mounting/backing up/copying to an external drive?  I didn't see an option.

Thanks.

---

### Post by aw1182 on 2021-12-11
Actually I got it to work and I'm in the process of copying all the files I need to a external flash drive!  I did the trial run of Ubuntu from the USB and was able to access the files by going to other locations when going into the file system via clicking on the folder icon.  Thanks for all your help!

---

### Post by aw1182 on 2021-12-11
I had marked this thread as solved but now I've put it back to unsolved.  I was in the process of copying my files to an external drive but some of my files are read only and will not copy over.  Also I'm denied permission to delete any files to free up space.  I have some home made videos that I need to transfer over but many of them are read only.  Is there any way to get into my Ubuntu account using safe mode?  I've tried looking up safe mode on this forum but I can't find how to activate it.  Or if not is there another option?

---

### Post by oldfred on 2021-12-11
Can you boot recovery mode?
Or second kernel as it keeps two normally or its recovery mode?
Recovery mode would be to a terminal where you can run repair commands.

Issue with live installer is that it is user 999 where your first user in Ubuntu is user 1000.
And system is ubuntu not your user name then associated with user number.

---

### Post by aw1182 on 2021-12-11
Yes I figured how to get to the recovery mode options by pressing and holding down the shift key during boot up.  I ran the clean files options and it looked like it removed some files.  I then tried to proceed to start ubuntu in recovery mode however it just stays on a black screen with a blnking cursor on the top left corner of the screen.  So it looks like there may be not enough memory to start Ubuntu even in recovery mode.  I can access the command line by pressing alt+F2 while its on the black screen which then brings up the command (terminal?) interface.  I can then login into ubuntu using my user name and password.  However, I'm not the administrator so I can't run any commands (permission denied).  I'll have to wait to get the admin. user name and password.  Which then now leads me to ask how do I delete files using terminal commands? Or in other words what terminal commands would I be able to use to free up some space?

---

### Post by oldfred on 2021-12-11
You have to be the admin to do any real fixes.
A user can only delete files in his /home folder.

And black screen is normally a video driver issues. 
Often some update did not include nVidia in the kernel for whatever reason.
But to run commands from terminal in recovery mode, you must use sudo to become the admin.

---

### Post by aw1182 on 2021-12-11
I only need to delete a few files from my home folder to free up some space.  Do you know how to do that from terminal/command line interface?

---

### Post by oldfred on 2021-12-11
ls -l or l  (el) to show files.

You need to use the rm command which can be dangerous. A minor typo like an extra space can delete entire system, so always double check what you have typed.

man rm
looks like -i adds some confirmation.

I do this to houseclean some older files in cache.
I first test find command then add the exec.
find /home/fred/.cache/thumbnails -type f -atime +5 -print
--------------------
find /home/fred/.cache/thumbnails -type f -atime +5 -print -exec rm -f {} +

---

### Post by dragonfly41 on 2021-12-12
Perhaps easier to run a file manager GUI in LiveUSB .. such as Thunar or Nautilus .. right click on target external file/folder to be removed .. and choose first Properties (to check size) and then Delete. Check that you select the correct mounted Device.
You can also Send selected files/folders to another backup device.

---

### Post by aw1182 on 2022-05-19
Hi all,

I was able to get into my laptop and recover everything  using some of the above methods.  The problem was caused by the syslog  file getting too big.  I then tried to prevent the issue from happening  again by editing my logrotate.conf limiting the log files to 500mb, 1  week, and rotated daily.  This worked until 2 weeks ago as I noticed I  lost over 100+ gb of space on my hard drive.  I looked to see what  happened and noticed that in the var/log folder there is a syslog.1 file  and the size of the file is 189 gb.  This morning I looked again and I  noticed there are more syslog files going from syslog.2 all the way up  to syslog.7.  Would anyone have input as to why ubuntu is creating more  syslog files and how to fix and prevent this from happening again?   Thanks and also thanks to all those who helped me address the original  issue on this thread.

---

### Post by Holger_Gehrke on 2022-05-19
The syslog files are collected error and warning messages. An "exploding" syslog is a sure sign that something is wrong, either some hardware failing (for example lots of errors from a failing hard disk) or a serious misconfiguration (might be something as simple as a program set to send debugging messages to syslog instead of just the gravest of errors or a program configured to restart on errors and getting restarted every few milliseconds ...). Logs are not there just for fun, they are a warning of something going wrong and you're supposed to read them. Read the logs, find the problem, correct it and the logs won't grow out of control again (until the next time something goes wrong).

Holger

---

