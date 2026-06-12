---
title: "grub-update not creating correct grub.cfg file."
date: 2017-03-01
forum: General Help
---

### Post by shawn.c on 2017-03-01
Hi guys,

My grub-update used to be functioning properly and I had successfully renamed my menu entries and removed the advanced options. 

However in order to edit the grub menu header, I had made changes to the source code and installed the edited grub over the original grub. Everything was working fine, I had a fully functional grub menu with a header of my choice.

It was until I wanted to remove the memtest in the boot menu did I realise that there was actually some problems with installing a new grub. 
Using the command 
```
sudo chmod -x /etc/grub.d/20_memtest86+
sudo update-grub
```
I have managed to removed the memtest in the boot menu, however at this point my Grub menu had some changes. 
What is changed: 
- Menu entries name changed to GNU/Linux
- Advanced options had returned
-Plymouth splash screen from "quiet splash" seems to be changed (not certain but am seeing lines of text after selecting OS and on power off)
What is not changed:
- Grub menu header
- Color options for grub menu
What i have tried:
- Going through the settings file, /etc/default/grub , /etc/grub.d/10_Linux to see if there was any changes and/or extra files in the folder. But there was no changes or any 'additional' files. 
- Adding back the memtest line with ```
sudo chmod +x /etc/grub.d/20_memtest86+
sudo update-grub
``` but the memtest option did not appear anymore. My boot menu did not return to its previous state.
- Changing the /etc/default/grub to not show the boot menu on start up as a test was not working. Boot menu continues to show on boot up.
- Deleting the grub.cfg and update-grub to create a new grub.cfg file. Did not work as well. 

I am not sure what else I could have done, is there anyway to return my boot menu to its original state?

---

### Post by truephoenyx on 2017-03-01
I hate to ask but have you been running update-grub as you are doing these changes?

Edit: Never mind, I didn't read down far enough.
I'm going to have to think (and sleep, it's midnight here) on this and I'll try to help.

Edit2: You said you edited the source, I am assuming you mean the source of the grub program and not any of the configs.
You may need to put the original back to get it fixed. When you made that change did you make a copy of the unedited source file
and the unedited compiled file?

---

### Post by shawn.c on 2017-03-02
Hi truephoenyx, 
Thanks for replying, really appreciate it. 

Regarding your question, I had edited the source which I had gotten from
```
apt-get source grub2
```
I do not have the source of the original code, but I could get it anytime. 
However I am quite hesitant to reinstall grub again, as it would be the third time I am installing grub without removing anything. 
If by editing the config you mean the files in /etc/default/grub and /etc/grub.d, then yes I had changed it first (and also running update-grub and rebooting) before installing my edited version of grub2. 
Hopefully it answers your question.

[B]Edit: 

Actually, there seems to be a file 20_linux_xen inside the /etc/grub.d folder. I cannot remember if this was there to begin with. Although removing execute rights followed by an update-grub did not seems to solve my issue. Just wanted to point this out in case it was an anomaly.[/B]

---

### Post by oldfred on 2017-03-02
These are the standard grub script files.
```
fred@Z170N:/etc/grub.d$ ls -l
total 76
-rwxr-xr-x 1 root root  9791 Dec  3  2015 00_header
-rwxr-xr-x 1 root root  6258 Jan 22  2016 05_debian_theme
-rwxr-xr-x 1 root root 12261 Dec  3  2015 10_linux
-rwxr-xr-x 1 root root 11082 Dec  3  2015 20_linux_xen
-rwxr-xr-x 1 root root  1992 Aug 27  2015 20_memtest86+
-rwxr-xr-x 1 root root 11692 Dec  3  2015 30_os-prober
-rwxr-xr-x 1 root root  1418 Dec  3  2015 30_uefi-firmware
-rwxr-xr-x 1 root root  1316 Jan 31 11:18 40_custom
-rwxr-xr-x 1 root root   216 Dec  3  2015 41_custom
-rw-r--r-- 1 root root   483 Dec  3  2015 README

```
Any file with execute bit on, and starts with two numbers & underscore will be run.

Generally best not to edit scripts, but add own entries to 40_custom or modify settings in /etc/default/grub.

Not sure what or why you wanted different header?

If totally not working you can totally reinstall grub. 
New versions of grub may update scripts and then your edits are in wrong place or gone.

 # purge old and reinstall new to sda (BIOS version)
sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common
sudo grub-install --recheck /dev/sda
sudo update-grub 

      
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

---

### Post by shawn.c on 2017-03-02
Hi fred,
Thanks for the reply! 

I reason for editing the script file was to remove the advanced option for Ubuntu in the boot menu. I wanted to Ubuntu to be a boot option, but I do not want the advanced option to show. Perhaps there is a workaround for it, I will continue to look up on resources for that.

The Grub header i am referring to is the top of the boot menu which says " GNU/GRUB version 2.02 ..... " I wanted to change this title/header to a custom title for aesthetic purposes. Not really a must but more like a want.

Also, regarding the steps you gave me, it seems that the original grub was not installed, I was still brought back to my "custom menu". The only error message I caught on was the command ```
sudo apt-get purge grub grub-pc grub-common
``` which says grub was not installed, so it cannot be purged.
[B]
EDIT :
I tried adding grub2-common to the mix for purging and installing, looks like it didn't fix the problem either. Will continue to fiddle around to see what is wrong, will be around for a couple of hours. Any small suggestion is much appreciated.

EDIT 2:
Hey, just to let anyone interested know, I initially managed to installed the new grub source by the following command: ```
apt-get source grub2 
./autogen.sh
./configure
make
make check
sudo make install
sudo grub-install /dev/sdX 
``` I just did the same with the original source code and manage to get back the title of the original grub menu to GNU/GRUB version 2.02 .. 
However all the problem still remains, looking into /etc/default/grub file, it seems that the old grub configuration was still being used instead of the current one. Both ```
 sudo update-grub & sudo update-grub2 
``` seems to be updating fine, but no changes is applied. At this point, I have no idea what is happening anymore. Hopefully someone could throw me a bone as I am out of ideas on what to do. [/B]

---

### Post by oldfred on 2017-03-02
The purge of grub is just to make sure the old grub legacy package is no more.
The BIOS version is grub-pc and UEFI version is grub-efi-amd64.

When grub2 was new, a lot of us did not know much about it. Explains each script.
[https://ubuntuforums.org/showthread.php?p=8191211#post8191211](https://ubuntuforums.org/showthread.php?p=8191211#post8191211)

 From Ranch hand
You only need 3 scripts for grub to tick like a clock;
00_header
05_debian-theme
06_custom (or 07, 08, 09, 25, 40)

---

### Post by shawn.c on 2017-03-03
Hi fred,
Thanks for the great read. 

However it seems that my problem comes after installing the edited Grub2 over the original Grub2 and running the command ```
update-grub
```
It seems that the moment i update grub, my /boot/grub/grub.cfg will be changed even if no edits were made to the original script or /etc/default/grub file. 
Editing the grub.cfg file works, however the moment I run the update-grub command, the changes will be reverted. 
Right now, I require a workaround to allow update-grub to work as intended after installing the new Grub2 source code. 
Hopefully I was able to describe my problem accurately, as English is not something I am good in. Thank you anyway fred!

---

### Post by oldfred on 2017-03-03
You do not edit grub.cfg.  Right at top it says not to edit it.
And any run of sudo update-grub, kernel update, or grub update will automatically run an update.

If you turn off everything but 00_header &  05_debian-theme and copy boot stanza for exactly what you want into 40_custom, it should work. But it will not update for new kernels. You have to use the link in / to newest kernel as shown in post #4 by Cavsfan.

I have just installed grub to flash drives, but without scripts had to manually create my own grub.cfg.
You probably could turn off everything, if you have the maintenance free configuration a Cavsfan discusses.

---

### Post by shawn.c on 2017-03-05
Hi fred, 

Thanks for the advice, however it seems that my problem still remains. 
On a fresh install of the Ubuntu, I disabled 10_linux and added menu entry to 40_custom. Everything works fine after I update-grub, I even managed to change the grub menu title using the steps I outlined in post #5. 

However, after installing the edited version of grub. I ran the command ```
sudo update-grub
``` On the next reboot, my custom menu is gone, and replaced with the menu from 10_linux even though execute rights on 10_linux is removed. My custom menu entries also stopped appearing. Using ```
ls -l /etc/grub.d
```it appears that all the rights is unchanged. What is actually going on?

---

### Post by oldfred on 2017-03-06
That usually is where users have multiple installs and edit one copy of grub, but boot with another copy of grub.

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by shawn.c on 2017-03-06
Hi fred, 

Thanks for sticking around. 

Here are the boot-info results.

[HTML]http://paste2.org/y1mUtgxc[/HTML]
This results was taken directly after installing the edited grub. 
It is the grub menu which I was trying to obtain. 

[HTML]http://paste2.org/06vOOdG5[/HTML]
After obtaining the first result, I immediately ran ```
sudo update-grub
```to get this result. This caused my grub menu to change drastically. It is still functional, but the aesthetic has changed. The only unchanged is the grub menu header.

---

### Post by oldfred on 2017-03-07
I noticed my grub had changed a bit. 
I saw where a new version with lots of fixes was released.

---

### Post by shawn.c on 2017-03-07
Hi fred, 
Appreciate your help. 

Does that means that this occurrence only happen on newer version of grub? If so, is there any way to fix it ?

---

### Post by oldfred on 2017-03-08
I have not had any issues with current versions of grub.

I guess I was a bit ahead of myself, it is only a new release candidate for grub 2.02.
[http://www.phoronix.com/scan.php?page=news_item&px=GRUB-2.02-RC1-Features](http://www.phoronix.com/scan.php?page=news_item&px=GRUB-2.02-RC1-Features)

---

