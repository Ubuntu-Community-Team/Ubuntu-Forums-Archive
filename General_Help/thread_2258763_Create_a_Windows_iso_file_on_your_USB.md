---
title: "Create a Windows iso file on your USB"
date: 2014-12-30
forum: General Help
---

### Post by IL TRIVELLA on 2014-12-30
Hi everyone, 

I'm trying to make an usb flash file iso, to install on my laptop Windows 8.1 (due the fact that I'm buying a new laptop and I want to give this one to my cousin, but he doesn't even know what Ubuntu or Linux is, so it will be better to him to keep using Windows), and I can't.

Let me explain better, I'm trying to create with Ubuntu an Usb flash file iso, to install Windows,I searched on google and all what I can find is that everyone is suggesting to use WinUSB, but I tried many times and it won't work... every single time I get the same error message:

[IMG]http://s14.postimg.org/xfqj38ws1/Screenshot_from_2014_12_30_08_22_29.png[/IMG]

Can you help me please?

---

### Post by phidia on 2014-12-30
The problem appears to be and efi issue-that is grub is expecting to install from/to that.
Your issue is addressed [here]("http://askubuntu.com/questions/532209/how-to-fix-doesnt-look-like-an-efi-partition-with-winusb"). There are a number of links and how-tos to try within that thread.

---

### Post by IL TRIVELLA on 2014-12-31
I was trying to follow this guide: [http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html) but when I try to do the #3 make it bootable, I get an error message: 
[SIZE=2][COLOR=#000000][FONT=Bitter]
```
[/FONT][/COLOR][/SIZE]alessandro@SuperAlex:~$ sudo grub-install --target=i386-pc --boot-directory="/media/Alessandro Calello/SUPER ALEX/boot" /dev/sdXInstalling for i386-pc platform.
grub-install: error: cannot find a GRUB drive for /dev/sdX.  Check your device.map.
alessandro@SuperAlex:~$ [COLOR=#000000][FONT=Bitter]
```

[/FONT][/COLOR]I'm not quite sure I'm doing it right either, because I'm not sure I did put the right things in [COLOR=#FFA0A0][FONT=inherit]"/media/<username>/<drive_label>/boot"

[/FONT][/COLOR]I'm not very expert of Linux/Ubuntu, so I don't understand what I'm doing but I'm trying following the directions, but sometimes they get too complicate so please I need more help... 

Thanks!

---

### Post by phidia on 2014-12-31
What is the output of > fdisk -l? (you may need to use sudo in front of that command)

From the output you provided it doesn't look like you are using the correct identifier for the usbdisk you are trying to install to.
It's just a thought but would it be easier to use an external optical drive to do this?

---

### Post by IL TRIVELLA on 2014-12-31
Sorry Phibia, I really appreciate your help, but I really can't understand what you are telling... I'm very newbie in Ubuntu... oh btw Happy New Year! ):P

---

### Post by raja.genupula on 2015-01-01
1st post in this answer is what you have tried but I am suggesting you to go for all other posts too 
[http://askubuntu.com/questions/289559/how-can-i-create-a-windows-bootable-usb-stick-with-ubuntu](http://askubuntu.com/questions/289559/how-can-i-create-a-windows-bootable-usb-stick-with-ubuntu)

---

### Post by carl4926 on 2015-01-01
I take it you don't have a windows installation that you could use or you wouldn't be asking this?

---

### Post by IL TRIVELLA on 2015-01-01
I have a file .iso for install Windows 8, I know how to format my pc, just I can't put the file .iso in the usb with Ubuntu, that's all I'm asking...

---

### Post by corneliuss2 on 2015-01-01
Is this your command?

```
sudo grub-install --target=i386-pc --boot-directory="/media/Alessandro Calello/SUPER ALEX/boot" /dev/sdX
```

Didn't you replace[FONT=courier new]** /dev/sdX**[/FONT] with[FONT=courier new]** /dev/sdb**[/FONT] or**[FONT=courier new] /dev/sdc[/FONT]** or whichever your stick is?

---

### Post by yancek on 2015-01-01
It would probably be helpful if posted your commands if you are using the link in post #3 to try to do this. 

> sudo grub-install --target=i386-pc --boot-directory="/media/Alessandro Calello/SUPER ALEX/boot" /dev/sdXInstalling for i386-pc platform.

If you actually ran the command above, I would not expect it to do anything but maybe that was a typo on your part.  You would need to replace "/dev/sdX" with the actual device name which would probably be sdb or sdc.  Not sure of the end of that line was in your command, it definitely should not be.

I would go to the site and read through it carefully.  Then while you are trying to create the bootable flash drive, have a text editor open and copy each command to the file and any output which you should save and then post here.

---

### Post by IL TRIVELLA on 2015-01-01
I'm following this guide: [http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

And I got stuck on the step #3 where it says, Make it bootable, GRUB will be used for that. Open a Terminal and run:

```
[COLOR=#000000][FONT=inherit]sudo grub-install --target=i386-pc --boot-directory=[/FONT][/COLOR][COLOR=#FFA0A0][FONT=inherit]"/media/<username>/<drive_label>/boot"[/FONT][/COLOR][COLOR=#000000][FONT=inherit]/dev/sdX[/FONT][/COLOR]
```

Because in this command is all in black, apart from [COLOR=#FFA0A0]"/media/<username>/<drive_label>/boot" [/COLOR]I thought that the only part to change was this in red, but because my knowledge of Ubuntu is not very wide, I am not sure what I have to put there, that's why where it says "username" I put what I think is my username, and in "drive label" what is the name of my Usb stick, which I gave it when I formatted it.

It says as well:

```
[COLOR=#666666][FONT=Lato]Replace:[/FONT][/COLOR]

[LIST]
[*][FONT=Courier New]/media/<username>/<drive_label>[/FONT] with the path where USB drive is mounted
[*][FONT=Courier New]/dev/sdX[/FONT] with the USB drive, not the partition (e.g. [FONT=Courier New]/dev/sdb[/FONT])
[/LIST]

```[FONT=inherit][COLOR=#222222][FONT=Verdana]But seriously for me is like to read [/FONT][/COLOR]hieroglyphs, I understand so little of all what I'm reading...

That's why I'm asking for help... but then you all write to me so difficult and it's so frustrating because I appreciate your help but I can't understand...

Like for example the last comments on the [COLOR=#000000]"/dev/sdX" I seriously have no idea what you are talking about, I know that is something in that command but I still don't understand...[/COLOR][/FONT]

---

### Post by IL TRIVELLA on 2015-01-01
I think I did it!

I just checked my Usb stick on the Ubuntu app disks and it was written on the top dev/sdb, so I gave again the command, but this time changing sdX with sdb:

```
[COLOR=#000000]*sudo grub-install --target=i386-pc --boot-directory="/media/Alessandro Calello/SUPER ALEX/boot" /dev/sdb*[/COLOR]
```

And I obtained this:

```
alessandro@SuperAlex:~$ sudo grub-install --target=i386-pc --boot-directory="/media/Alessandro Calello/SUPER ALEX/boot" /dev/sdbInstalling for i386-pc platform.
Installation finished. No error reported.
alessandro@SuperAlex:~$ 
```

So if you look at the guide [http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html) now it's all correct, so what I'm wondering now, is am I done? I can finally use this Usb to format my computer or there is something else to do? because the guide continues with things like:

[IMG]http://s21.postimg.org/fkiz5uv8n/Screenshot_from_2015_01_01_22_55_18.png[/IMG]
And I have no idea how to do that, and as well under that it saying:

GPT for UEFI

I should do that as well? I don't think so, but I ask because you never know...

---

### Post by IL TRIVELLA on 2015-01-01
I'm trying to understand it on my own, and I did the part of the picture above, I create a text file using the command:

```
cat > name.text
```

because I found on google that is like this that you create text files with the Terminal, I wrote exactly what it's saying to me plus the UUID:

```
default=1timeout=15
color_normal=light-cyan/dark-gray
menu_color_normal=black/light-cyan
menu_color_highlight=white/black


menuentry "Start Windows Installation" {
 insmod ntfs
 search --no-floppy --fs-uuid <54A2FB761FF4E010> --set root 
 chainloader +1 
 boot
}


menuentry "Boot from the first hard drive" {
 insmod ntfs
 insmod part_msdos
 set root=(hd1)
 chainloader +1
 boot
}
```

It is right like that? and then it's saying to save it:

```
[COLOR=#666666][FONT=Lato]Replace [/FONT][/COLOR][COLOR=#666666][FONT=Courier New]<drive_UUID>[/FONT][/COLOR][COLOR=#666666][FONT=Lato] with the UUID from step 1.  Save the file as [/FONT][/COLOR]*grub.cfg and put it on the USB drive in the[I]boot/grub folder.*[/I]
```

But I have no idea how, on google is also not helping because I can't find how to save it...

---

### Post by yancek on 2015-01-01
> 
I just checked my Usb stick on the Ubuntu app disks and it was written  on the top dev/sdb, so I gave again the command, but this time changing  sdX with sdb:

That's correct.  You can find the actual device name (in your case sdb) by opening a terminal and running: sudo blkid or sudo fdisk -l(Lower Case Letter L) but you've apparently got that.  If you got installation finished and no error reported then you need to create the grub.cfg file as in your last post.  Open a terminal and type:  sudo gedit  gedit is a text editor. Copy the sample grub.cfg info changing your UUID.  You can then save it by clicking on the File tab in the text editor and then Save As and navigating to where your grub directory is:  
  
[COLOR=#000000][I]/media/Alessandro Calello/SUPER ALEX/boot/grub

You could try right-clicking in the /boot/grub directory of the usb and creating a text file and saving it there as grub.cfg if you have write permissions.  
[/I][/COLOR]

Ignore the info about GPT/UEFI.  You either do the part you did for MBR BIOS or you do GPT/UEFI, not both.    Another way is to use the 'touch' command in a terminal.  You could navigate to the /boot/grub directory of the flash in a terminal and just do touch grub.cfg, probably easier with gedit.

---

### Post by corneliuss2 on 2015-01-02
**No terminal method:**

You're on the right way. You have managed to install the GRUB bootloader on the USB drive and now you must create a configuration file for it.

First you must get the UUID of the USB partition. To do so, open GParted, select the USB drive in the top-right combobox, then right click the partition in the list (/dev/sdb1) and choose Information.

[IMG]http://1.bp.blogspot.com/-CCkGrJrvHt8/VBrtYOyvjTI/AAAAAAAABCk/muJ16rffTrU/s1600/step07.png[/IMG]

Copy or write down the UUID somewhere.

Now, open GEdit and paste that text from OneTransistor. Look for <drive_UUID> and replace it with the UUID you wrote earlier. Save (Ctrl+S) the file in the USB drive, go to **boot**, then **grub** folder, and save it here as [B]grub.cfg
[/B]That should be all.

---

### Post by IL TRIVELLA on 2015-01-02
> **yancek said:**
> terminal and type:  sudo gedit  gedit is a text editor. Copy the sample grub.cfg info changing your UUID.  You can then save it by clicking on the File tab in the text editor and then Save As and navigating to where your grub directory is:  
  
[COLOR=#000000]*/media/Alessandro Calello/SUPER ALEX/boot/grub*[/COLOR]

So I opened a terminal and just wrote sudo gedit

It opened the text file in which I pasted that:

```
[COLOR=#000000][FONT=inherit]**default**=1
timeout=15
color_normal=light-cyan/dark-gray
menu_color_normal=black/light-cyan
menu_color_highlight=white/black

menuentry "Start Windows Installation"{
 insmod ntfs
 search --**no**-floppy --fs-uuid <54A2FB761FF4E010>--**set** root 
 chainloader +1 
 boot
}

menuentry "Boot from the first hard drive"{
 insmod ntfs
 insmod part_msdos
 **set** root=(hd1)
 chainloader +1
 boot }[/FONT][/COLOR]
```

Exactly like that, so you can confirm that is correct? even the UUID with this < > ?

After that I did File, Save As, and after this I need help again, do I have to put any specific name to this file? I have to save it in the Usb flash or in a specific folder in it? because there is a folder called boot but in there there are no folders called grub, and as well there are two more options to save this file, character encoding which let me choose between, current locale (UTF-8) or western (ISO-8859-15) and another one, line ending which let me chose between Unix/Linux, Mac OS Classic and Windows...

What I'm supposed to do now?

---

### Post by IL TRIVELLA on 2015-01-02
> **corneliuss2 said:**
> Now, open GEdit and paste that text from OneTransistor. Look for <drive_UUID> and replace it with the UUID you wrote earlier. Save (Ctrl+S) the file in the USB drive, go to **boot**, then **grub** folder, and save it here as [B]grub.cfg
[/B]That should be all.

Thanks for your clear explanation, but I think there should be something wrong, because I have no grub folder:

[IMG]http://s27.postimg.org/v7ozevdc2/Screenshot_from_2015_01_02_12_19_14.jpg[/IMG]

---

### Post by yancek on 2015-01-02
> [COLOR=#000000][FONT=inherit]search --**no**-floppy --fs-uuid <54A2FB761FF4E010>--**set** root [/FONT][/COLOR]

The above entry is wrong.  Remove the <> from the entry and a space before --set like below.

>  search --**no**-floppy --fs-uuid 54A2FB761FF4E010 --**set** root 
[COLOR=#000000][FONT=inherit]
You need to manually create the grub directory and it needs to be in the boot directory on the flash drive.  It also needs to be all lower case as does 
the boot directory which is explained in the link you posted.
You can try right-clicking in the boot directory on the flash drive and then select create new folder or directory.  You should be able to then create 
the grub folder.
The path in quotes below beginning with /media, is that the actual user name (Alessandro Calello) and label name (SUPER ALEX) of the usb drive?
If so, open a terminal and type:  sudo gedit "/media/Alessandro Calello/SUPER ALEX/boot/grub/grub.cfg"

[/FONT][/COLOR]> [COLOR=#000000][FONT=inherit][COLOR=#000000]*/media/Alessandro Calello/SUPER ALEX/boot*[/COLOR][/FONT][/COLOR][COLOR=#000000][FONT=inherit]

Then copy the sample entry you have posted into that file and click Save.  The file will be saved with the name:  grub.cfg  That is necessary and must 
be lower case also.

Just a point of information.  It is generally a bad idea to have spaces in folder names as it creates problems in the terminal.  Look at the command I 
posted above to open a file grub.cfg with gedit and notice there are double quotes " around it.  That's because of the spaces in file names.  The command 
won't work without them. 

I had an iso file of the Windows 10 Technical Preview and followed the instructions on that site.  I was able to boot it in VirtualBox so this should work.  I had an error code when I initially booted; Error Code: 0x0000005C and doing an online search indicated it would be necessary to enable:  IO_APIC which I did in VirtualBox and it then booted.  I had problems due to having multiple labels on a flash drive so Grub would not install.  Used another flash with no labels and repeated the process.  When running the grub-install command it froze at:[/FONT][/COLOR]
Installing for i386-pc platform.

So I never saw the message below
Installation finished. No error reported.

I decided to check the /boot/grub directories and all the files seemed to be there and I rebooted and it booted the windows iso successfully.  Not sure what 
happened there but anyone trying this might keep that in mind.

---

### Post by IL TRIVELLA on 2015-01-04
> **yancek said:**
> [COLOR=#000000][FONT=inherit]The path in quotes below beginning with /media, is that the actual user name (Alessandro Calello) and label name (SUPER ALEX) of the usb drive?[/FONT][/COLOR]

Yes if I click on the right top symbol for turn off the laptop it's saying that my user name is Alessandro Calello and yes my usb flas is named SUPER ALEX...

Anyway I followed exactly what you told me to do, I restarted my laptop, I pressed F10 and I went to the boot menu, but I tried everything but I can't get it work...

---

### Post by yancek on 2015-01-04
> Yes if I click on the right top symbol for turn off the laptop it's  saying that my user name is Alessandro Calello and yes my usb flas is  named SUPER ALEX...


Open a terminal and type in this command and post the output:  ls /media

If your user name is actually Alessandro Calello, it should show there as a folder.  If it does, then in the terminal type:  ls "/media/Alessandro Calello/"  
You should see SUPER ALEX as a folder.

> I pressed F10 and I went to the boot menu, but I tried everything but I can't get it work...

Reboot the computer and watch the screen immediately after booting for the key to "Enter Setup" which should be on the screen briefly, usually 3-5 seconds.  It should tell you which key you need to repeatedly tap until you get a message "entering setup" at the bottom of the screen.  Look for a Boot tab and a Boot priority option and then look for whatever the name of the flash drive (Sandisk, Toshiba,?) then move it to the top so it is in first boot priority.  If you have already done this and it doesn't boot, something else is wrong.

What is the exact name of the windows iso file you are using?
When you went through this process, did you get any errors?
Did you create a label for the partition in GParted?  SUPER ALEX?
Did you go to Manage Flags and check the boot option?
Did you copy all the windows folders/files to the flash drive?
Did you then create a grub directory inside the windows boot directory?
Did you then copy the grub.cfg file from the template to the /boot/grub directory?
Did you verify that you had the correct UUID in the grub.cfg entry?
Did you successfully complete the grub-install and get the "Installation finished. No error reported" message?
Did you check the /boot/grub/i386-pc to see if all the files were there?  Should be about 100 files, all with a .mod extension.

Since I can't see your computer, I obviously have no idea what happened.  If you read my last post, you can see I had some problems with it but it eventually worked and I was able to boot it on my computer.  You might go through the process again if you want and make notes of exactly what you did and then post that info here.

---

### Post by yancek on 2015-01-04
Just out of curiosity, I created an ntfs primary partition on an external hard drive, marked it as bootable in GParted, copied the windows files to that partition, put an entry in the  Ubuntu 14.04 grub.cfg with the correct UUID and booted the windows iso.  No problems with that although I can't verify that it will install as I have no interest in doing it.  The windows installer did begin and I went through the first few steps prior to beginning the install.

---

### Post by carl4926 on 2015-01-05
> **yancek said:**
> Just out of curiosity, I created an ntfs primary partition on an external hard drive, marked it as bootable in GParted, copied the windows files to that partition, put an entry in the  Ubuntu 14.04 grub.cfg with the correct UUID and booted the windows iso.  No problems with that although I can't verify that it will install as I have no interest in doing it.  The windows installer did begin and I went through the first few steps prior to beginning the install.

That is basically all you would do with DISKPART and the windows USB tool

---

### Post by IL TRIVELLA on 2015-01-05
> **yancek said:**
> Open a terminal and type in this command and post the output:  ls /media

If your user name is actually Alessandro Calello, it should show there as a folder.  If it does, then in the terminal type:  ls "/media/Alessandro Calello/"  
You should see SUPER ALEX as a folder.

Sorry for the late answer, I've been very busy working, anyway my .iso file name is Windows_8.1_Pro_X64_Activated.iso and perhaps you are right, I should do it all over again and you should help me step by step to make sure it will go well...

---

### Post by yancek on 2015-01-05
> Yes if I click on the right top symbol for turn off the laptop it's  saying that my user name is Alessandro Calello and yes my usb flas is  named SUPER ALEX...


If that's the case, then you should show a user in your /home directory as well as in the /media directory.  If you decide to try this again, keep some notes step by step.
In your earlier post, you indicated that the grub successfully installed to the flash drive and then indicated it did not work.  You'll need to be more specific as to exactly what happens when you set the flash drive to first boot priority in the BIOS and reboot the computer.  Error messages, warnings, a blinking cursor??  

>  			 		 	 That is basically all you would do with DISKPART and the windows USB tool 		

carl4926.

I'm not familiar with that software and have never used it.  I usually loop mount iso files and copy in a terminal.

---

### Post by IL TRIVELLA on 2015-01-07
Ok I restarted the operation, using again this guide [http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

And so far so good, the first step is done, and now I'm on the second one:

```
[COLOR=#666666][FONT=Bitter]2. Copy Windows files[/FONT][/COLOR]
[COLOR=#666666][FONT=Lato]Quit GParted and use the file manager to copy all files from Windows ISO to USB stick. Mount the ISO using [/FONT][/COLOR]**Open with -[B]Disk Image Mounter (if you use Nautilus as a file manager). Then select all files Ctrl+A and [B]Copy to USB drive which will be automatically mounted when you click on it at [FONT=Courier New]/media/<username>/<drive_label>[/FONT]. After the copy process is finished, look in the USB root folder for the [FONT=Courier New]boot[/FONT] directory. If it is uppercase, rename it to lowercase.**[/B][/B]
```

I right clicked on the iso file and I did "open with archive mounter" after that I went on the new, I don't know how it's called, let's say folder in Network, and I copied all the files there and pasted them in the Usb flash, is that right?

Now I am at the step 3, and I need your help:

```
[COLOR=#666666][FONT=Bitter]3. Make it bootable[/FONT][/COLOR]
[COLOR=#666666][FONT=Lato]GRUB will be used for that. Open a Terminal and run:[/FONT][/COLOR]
[COLOR=#000000][FONT=inherit]sudo grub[/FONT][FONT=inherit]-[/FONT][FONT=inherit]install [/FONT][FONT=inherit]--[/FONT][FONT=inherit]target[/FONT][FONT=inherit]=[/FONT][FONT=inherit]i386[/FONT][FONT=inherit]-[/FONT][FONT=inherit]pc [/FONT][FONT=inherit]--[/FONT][FONT=inherit]boot[/FONT][FONT=inherit]-[/FONT][FONT=inherit]directory[/FONT][FONT=inherit]=[/FONT][/COLOR][COLOR=#ff0000][FONT=inherit]"/media/<username>/<drive_label>/boot"[/FONT][/COLOR][COLOR=#000000][FONT=inherit] [/FONT][FONT=inherit]/[/FONT][FONT=inherit]dev[/FONT][FONT=inherit]/[/FONT][FONT=inherit]sdX[/FONT][/COLOR]
``` 

What I have exactly to write in the red part?

```
alessandro@SuperAlex:~$ ls /mediaalessandro  Alessandro Calello
alessandro@SuperAlex:~$ ls "/media/Alessandro Calello/" 
SUPER ALEX
alessandro@SuperAlex:~$ 
```

I have done this as you asked, it helps?

---

### Post by yancek on 2015-01-07
> ls /mediaalessandro  Alessandro Calello

Do:  ls /media/

Generally in Ubuntu, when you create a user, the user name is all lower case.  For example, if your name is Alessandro, when you create the user it would show as alessandro, all lower case letters so I need to know exactly what you have in the /media directory.  It should be the same name as your user name in the /home directory.  So if you run the command you posted, shown below:

```
ls "/media/Alessandro Calello/" 
```

and you see:  SUPER ALEX that should be the name/label for your flash drive and that should be where you copied all the files.  What you need to do now is check to see if the files from the windows iso are actually there so in a terminal run this command to check:

```
ls "/media/Alessandro Calello/SUPER ALEX/"
``` 

You should see some folder/file names which should include a boot directory and a setup.exe as well as some others.  I don't have the same iso you do so I don't expect your files will be the same but they should be similar to the ones below which are from a bootable windows 10 installation iso.

> autorun.inf*  bootmgr*      efi/        sources/
boot/         bootmgr.efi*  setup.exe*  support/


If you do have those files, you need to go to the boot directory under SUPER ALEX and create a grub directory.  You might need to be root, use the sudo command.  After creating the grub directory, copy the modified grub.cfg template changing your UUID to the correct one and copy it to the grub directory. 

If you actually have a "Alessandro Calello" directory under /media and a "SUPER ALEX" directory under "Alessandro Calello", then the below entry would be correct except you would need to change the sdX at the end to the correct drive.  I think in an earlier post you indicated it was sdb?  
[COLOR=#000000][FONT=inherit]sudo grub[/FONT][FONT=inherit]-[/FONT][FONT=inherit]install [/FONT][FONT=inherit]--[/FONT][FONT=inherit]target[/FONT][FONT=inherit]=[/FONT][FONT=inherit]i386[/FONT][FONT=inherit]-[/FONT][FONT=inherit]pc [/FONT][FONT=inherit]--[/FONT][FONT=inherit]boot[/FONT][FONT=inherit]-[/FONT][FONT=inherit]directory[/FONT][FONT=inherit]=[/FONT][/COLOR][COLOR=#ff0000][FONT=inherit]"/media/Alessandro Calello/SUPER ALEX/boot"[/FONT][/COLOR][COLOR=#000000][FONT=inherit]/[/FONT][FONT=inherit]dev[/FONT][FONT=inherit]/[/FONT][FONT=inherit]sdX

After running the command, if you get a success message, check the /boot/grub directory on the flash drive.  You should have an i386-pc directory with a 
lot of files there with the extension .mod. 
[/FONT][/COLOR]

---

### Post by IL TRIVELLA on 2015-01-07
> **yancek said:**
> Do:  ls /media/

Generally in Ubuntu, when you create a user, the user name is all lower case.  For example, if your name is Alessandro, when you create the user it would show as alessandro, all lower case letters so I need to know exactly what you have in the /media directory.  It should be the same name as your user name in the /home directory.  So if you run the command you posted, shown below:

```
ls "/media/Alessandro Calello/" 
```

and you see:  SUPER ALEX that should be the name/label for your flash drive and that should be where you copied all the files.  What you need to do now is check to see if the files from the windows iso are actually there so in a terminal run this command to check:

```
ls "/media/Alessandro Calello/SUPER ALEX/"
```

That's what I got:

```
alessandro@SuperAlex:~$ ls /media/alessandro  Alessandro Calello
alessandro@SuperAlex:~$ ls "/media/Alessandro Calello/SUPER ALEX/"
boot
alessandro@SuperAlex:~$ 
```

> **yancek said:**
> If you do have those files, you need to go to the boot directory under SUPER ALEX and create a grub directory. You might need to be root, use the sudo command. After creating the grub directory, copy the modified grub.cfg template changing your UUID to the correct one and copy it to the grub directory. 

If you actually have a "Alessandro Calello" directory under /media and a "SUPER ALEX" directory under "Alessandro Calello", then the below entry would be correct except you would need to change the sdX at the end to the correct drive. I think in an earlier post you indicated it was sdb? 
[COLOR=#000000][FONT=inherit]sudo grub[/FONT][FONT=inherit]-[/FONT][FONT=inherit]install [/FONT][FONT=inherit]--[/FONT][FONT=inherit]target[/FONT][FONT=inherit]=[/FONT][FONT=inherit]i386[/FONT][FONT=inherit]-[/FONT][FONT=inherit]pc [/FONT][FONT=inherit]--[/FONT][FONT=inherit]boot[/FONT][FONT=inherit]-[/FONT][FONT=inherit]directory[/FONT][FONT=inherit]=[/FONT][/COLOR][COLOR=#ff0000]"/media/Alessandro Calello/SUPER ALEX/boot"[/COLOR][COLOR=#000000][FONT=inherit]/[/FONT][FONT=inherit]dev[/FONT][FONT=inherit]/[/FONT][FONT=inherit]sdX

After running the command, if you get a success message, check the /boot/grub directory on the flash drive. You should have an i386-pc directory with a 
lot of files there with the extension .mod. 
[/FONT][/COLOR]

with boot directory you mean the folder called boot in my Usb? I don't understand what you asked me to do after that, about the grub directory, it's means I have to create in it a folder called grub and then make a text file to save in it like I tried to do last time right?

Yeah it was ending in sdb, exactly /dev/sdb

---

### Post by yancek on 2015-01-07
Let's try this again.  Open a terminal and run this command:  ```
ls /media/
```

Post the output.  You should see a folder named alessandro.  Your user in the /home directory should be alessandro, meaning all lower case letters.  You should see a folder named alessandro in both the /media and /home directories/folders.  You should then see in the /media folder another folder with the name/label of the flash drive. SUPER ALEX? 
You're not copying the folders/files for windows to the right place as indicated by this output you posted:

> alessandro@SuperAlex:~$ ls "/media/Alessandro Calello/SUPER ALEX/" 
boot

That indicates the only folder there is the boot folder you created and none of the windows files you tried to copy so you aren't copying to the right place, the flash drive.  This is where you would create the grub directory and inside the grub directory copy the template for the boot menu and save it with the name grub.cfg.  Linux/Unix systems use the term directory and windows refers to them as folders.  I don't know why they use this naming convention.  Is SUPER ALEX the label you created in GParted following the instructions in the link you are using?

> alessandro@SuperAlex:~$ ls /media/alessandro  Alessandro Calello

I'm not sure what the above is showing.  Did you type that in as printed above?  I would not expect any output from that.  You should not have spaces.
Go to the /media/alessandro folder in a file manager WITHOUT the flash drive plugged in.  Then plug in the flash drive and see if anything changes.  If you see a new entry like SUPER ALEX, that's the flash drive.  If it doesn't show, try looking in the Alessandro Calello folder, if you have that?

You need to determine what the flash drive is and where it is because right now, you are not copying the windows files to the same place you created the boot folder in so check the /media folder as explained in the above paragraph.

---

### Post by IL TRIVELLA on 2015-01-08
> **yancek said:**
> Let's try this again.  Open a terminal and run this command:  ```
ls /media/
```

Post the output.  You should see a folder named alessandro.  Your user in the /home directory should be alessandro, meaning all lower case letters.  You should see a folder named alessandro in both the /media and /home directories/folders.  You should then see in the /media folder another folder with the name/label of the flash drive. SUPER ALEX? 
You're not copying the folders/files for windows to the right place as indicated by this output you posted:



That indicates the only folder there is the boot folder you created and none of the windows files you tried to copy so you aren't copying to the right place, the flash drive.  This is where you would create the grub directory and inside the grub directory copy the template for the boot menu and save it with the name grub.cfg.  Linux/Unix systems use the term directory and windows refers to them as folders.  I don't know why they use this naming convention.  Is SUPER ALEX the label you created in GParted following the instructions in the link you are using?



I'm not sure what the above is showing.  Did you type that in as printed above?  I would not expect any output from that.  You should not have spaces.
Go to the /media/alessandro folder in a file manager WITHOUT the flash drive plugged in.  Then plug in the flash drive and see if anything changes.  If you see a new entry like SUPER ALEX, that's the flash drive.  If it doesn't show, try looking in the Alessandro Calello folder, if you have that?

You need to determine what the flash drive is and where it is because right now, you are not copying the windows files to the same place you created the boot folder in so check the /media folder as explained in the above paragraph.

Ok first of all:

```
alessandro@SuperAlex:~$ ls /media/alessandro  Alessandro Calello
alessandro@SuperAlex:~$
```

In both my media and home directory I see the folders alessandro, the only difference is that in the media directory there is also the folder Alessandro Calello and inside there, there is the folder SUPER ALEX and inside there, there is the folder boot and inside there, the folder grub, and then three more folders, fonts, i386-pc, locale and two more files, called grub.cfg and grubenv.

> **yancek said:**
> Is SUPER ALEX the label you created in GParted following the instructions in the link you are using?

I don't understand what you mean with that.

---

### Post by yancek on 2015-01-08
The label "SUPER ALEX", if you go to the web site from which you got this information you will see the info below.  It tells you to create a label.  The label in the example is "windows".  Did you put "SUPER ALEX" there during this process? 

> Right click the unallocated space and select **New**. Make a primary NTFS partition and give it a label too. Remember the label as you will need it later.

> In both my media and home directory I see the folders alessandro, the  only difference is that in the media directory there is also the folder  Alessandro Calello and inside there, there is the folder SUPER ALEX and  inside there, there is the folder boot and inside there, the folder  grub, and then three more folders, fonts, i386-pc, locale and two more  files, called grub.cfg and grubenv

Does SUPER ALEX show only under Alessandro Calello or is it also shown under alessandro?
Do you have multiple users created?  Do you have a user Alessandro Calello as well as a user alessandro?
That means you copied the boot/grub files correctly.  From your earlier post, there are no windows files in "SUPER ALEX" so they weren't copied correctly.  I read over what you said about how you copied or rather tried to copy them and don't understand what you did.  You should have an option to Extract the files when you right click the iso.  Use that and you should then see a new folder with the files in it.  Don't know what it will be called, windows?  If you have the iso file in your /home/alessandro/Downloads directory, you probaly don't have too many folders there so just check to see what folders you have, then do the Extract and check for a new folder.  Check the folders/files inside the new folder.  You then need to open a second nautilus filemanager and go to the SUPER ALEX folder.  Copy the extracted windows files to SUPER ALEX.

First, as indicated on the web site, you need to copy the windows files to the flash drive BEFORE you do the grub files and installation.  If you have a bootable iso file of windows, it will have a boot folder in it and if you have boot/grub on the flash drive alreaady, when you copy the windows files to the flash, it will overwrite the boot/grub with its own boot folder.

The information in your last post indicates that all the grub files are in the right place.  The problem is there are no windows files there and as I said above, the windows files need to be there first.

The standard in Ubuntu when you install is to create one user.  In your case, it should be alessandro because that is the user which shows in both the /home and /media folders.  The flash drive should then show under /media/alessandro and if you named it SUPER ALEX, that should show there and be the flash drive.   Boot the computer.  Do not have your flash drive attached.  Log in as alessandro and go to the /media/alessandro folder.  Plug in the flash drive and note any change, particularly if you see SUPER ALEX.

---

### Post by IL TRIVELLA on 2015-01-08
> **yancek said:**
> The label "SUPER ALEX", if you go to the web site from which you got this information you will see the info below.  It tells you to create a label.  The label in the example is "windows".  Did you put "SUPER ALEX" there during this process?

Yes indeed I did, I always rename all my Usb like that.

> **yancek said:**
> Does SUPER ALEX show only under Alessandro Calello or is it also shown under alessandro?

in the directory home, not but in media is shown in Alessandro Calello and alessandro.

> **yancek said:**
> Do you have multiple users created? Do you have a user Alessandro Calello as well as a user alessandro?

No I don't think so, I think I have got one only user account.

> **yancek said:**
> The information in your last post indicates that all the grub files are in the right place. The problem is there are no windows files there and as I said above, the windows files need to be there first.

So how I make that? I mean how I make sure that the windows files are there first?

---

### Post by IL TRIVELLA on 2015-01-08
oh by the way:

```
alessandro@SuperAlex:~$ sudo grub-install --target=i386-pc --boot-directory="/media/Alessandro Calello/SUPER ALEX/"/dev/sdb[sudo] password for alessandro: 
Installing for i386-pc platform.
grub-install: error: install device isn't specified.
alessandro@SuperAlex:~$ 
```

---

### Post by yancek on 2015-01-08
I mentioned previously that it is a bad practice in Linux to create folders/files with spaces in them.  If you want SUPER ALEX, put a dash or underscore between SUPER and ALEX.  It simplifies things.  It obviously can be done but that adds the complication of having to use quotes around the name in a terminal.

> in the directory home, not but in media is shown in Alessandro Calello and alessandro.

I'll take that to mean you have SUPER ALEX under both /media/alessandro as well as /media/Alessandro Colello, correct.  So in your /home directory, you have only one user and that is alesssandro, correct?

To copy the windows files follow the process below

> If you have the iso file in your /home/alessandro/Downloads directory,  you probaly don't have too many folders there so just check to see what  folders you have, then do the Extract by right clicking on the iso file and selecting the option to extract, then check for a new folder.  I can't tell you what the folder will be named since I don't have the iso file you are using.  Check  the folders/files inside the new folder to see if the expected windows files are there, should have a number of files and a few folders.  You then need to open a  second nautilus filemanager and go to the SUPER ALEX folder, the one under /media/alessandro.  Copy the  extracted windows files to SUPER ALEX.


> alessandro@SuperAlex:~$ sudo grub-install --target=i386-pc --boot-directory="/media/Alessandro Calello/SUPER ALEX/"/dev/sdb[sudo] password for alessandro:  Installing for i386-pc platform. grub-install: error: install device isn't specified.

If that is the exact command, the reason it did not work is because you have no space prior to /dev/sdb, after the double quotes.
I think you need to copy the windows files first before the grub as windows will have a boot folder also and will likely overwwrite the boot/grub folders .

Are you able to extract the windows file from your windows iso and view the folders/files in it so that you can then copy them to the flash?  If you are having trouble with that you should be able to do it with the following command which worked for me with my windows iso.  First create a directory in the Downloads directory or whichever directory in which you have your windows iso file.  sudo mkdir windows.  Then make sure you are in that directory to run the command below.  You should then see all the windows files in the windows directory and be able to copy them to the flash.

> sudo mount -o loop Windows_8.1_Pro_X64_Activated.iso windows/

---

### Post by IL TRIVELLA on 2015-01-09
> **yancek said:**
> I mentioned previously that it is a bad practice in Linux to create folders/files with spaces in them.  If you want SUPER ALEX, put a dash or underscore between SUPER and ALEX.  It simplifies things.  It obviously can be done but that adds the complication of having to use quotes around the name in a terminal.

Sorry I didn't understood the first time, ok I tried to put an underscore, but the result is the same... 

```
alessandro@SuperAlex:~$ sudo grub-install --target=i386-pc --boot-directory="/media/Alessandro Calello/SUPER_ALEX/"/dev/sdb[sudo] password for alessandro: Installing for i386-pc platform.
grub-install: error: install device isn't specified.
alessandro@SuperAlex:~$ 
```

> **yancek said:**
> I'll take that to mean you have SUPER ALEX under both /media/alessandro as well as /media/Alessandro Colello, correct. So in your /home directory, you have only one user and that is alesssandro, correct?

No is not correct, in media I have got both Alessandro Calello and alessandro, but under home I got nothing, I mean only the folders, audiobooks, desktop, documents, downloads, music, pictures, podcast, public, templates, ubuntu one, videos, and examples, and if I click on public because is the only one that seem can contain a user profile because on the imagine of a little man on it, I find it empty.

> **yancek said:**
> [COLOR=#000000]*If you have the iso file in your /home/alessandro/Downloads directory, you probaly don't have too many folders there so just check to see what folders you have, then do the Extract by right clicking on the iso file and selecting the option to extract, then check for a new folder. I can't tell you what the folder will be named since I don't have the iso file you are using. Check the folders/files inside the new folder to see if the expected windows files are there, should have a number of files and a few folders. You then need to open a second nautilus filemanager and go to the SUPER ALEX folder, the one under /media/alessandro. Copy the extracted windows files to SUPER ALEX.*[/COLOR]

My iso file is in my downloads directory and there is nothing else there, the laptop is completely empty except for the iso file, and when I right click on it I can't extract it somewhere else, I have the option to extract it only there, I mean the option "extract here" what I can do with that file is open it with archive mounter, or disk image mounter, or disk image writer, or compress it or extract it there, right in that folder, anyway if I understood right you are telling me that I can extract that folder there in downloads, which is gonna be the folder Windows_8.1_Pro_X64_Activated.iso and then copy that folder in my usb using the simple process of copy paste?

> **yancek said:**
> If that is the exact command, the reason it did not work is because you have no space prior to /dev/sdb, after the double quotes.

You were right, now it worked out.

```
alessandro@SuperAlex:~$ sudo grub-install --target=i386-pc --boot-directory="/media/Alessandro Calello/SUPER_ALEX/" /dev/sdb
[sudo] password for alessandro: 
Installing for i386-pc platform.
Installation finished. No error reported.
alessandro@SuperAlex:~$ 
```

> **yancek said:**
> I think you need to copy the windows files first before the grub as windows will have a boot folder also and will likely overwwrite the boot/grub folders .

Following the guide it makes you do so, right?

> **yancek said:**
> Are you able to extract the windows file from your windows iso and view the folders/files in it so that you can then copy them to the flash? If you are having trouble with that you should be able to do it with the following command which worked for me with my windows iso. First create a directory in the Downloads directory or whichever directory in which you have your windows iso file. sudo mkdir windows. Then make sure you are in that directory to run the command below. You should then see all the windows files in the windows directory and be able to copy them to the flash.

Yes as I showed you already I am, I tried to run the command you told me and:

```
alessandro@SuperAlex:~$ sudo mount -o loop Windows_8.1_Pro_X64_Activated.iso windows/
Windows_8.1_Pro_X64_Activated.iso: No such file or directory
alessandro@SuperAlex:~$ 
```

I will like to thank you for your patient and help, I know we are getting there and I really appreciate that.

---

### Post by yancek on 2015-01-09
>                             Sorry I didn't understood the first time, ok I tried to put an underscore, but the result is the same...

What I meant was when you create the label in GParted as shown in your link, you could put a dash or underscore in it or, more simply just do SUPERALEX with no spaces.  You can leave the label as is and just continue using double quotes around the command.  This was just a suggestion for future use to simplify things.

> No is not correct, in media I have got both Alessandro Calello and alessandro, but under home I got nothing,

You are referring to /home/alessandro right.  Since the prompt in your commands shows the user alessandro.  Those are the expected folders/files in the /home/user directory.

After posting last night, I checked and was unable to use the Disk Image Mounter suggested in the link.  I got a message saying the iso file was too large.  Have you tried the Disk Image Mounter?  What happens?  I've never used it so I don't know what to expect.  I also tried Ark and the Extract and neither work which is why I suggested the mount method which did work for me.  The reason it did not work for you and you got the message 'No such file or directory' is because you were in /home/alessandro.  You need to change to the Downloads directory:

```
cd /home/alessandro/Downloads
``` 

I'm not sure if you missed the part about creating the windows folder in the Downloads folder.  You need to do this before you run the mount command so in the Downloads directory, do this command?

>   mkdir windows

After doing that and still in the Downloads directory, run the mount command as you did previously.  Then open the windows folder there and you should see several folders/files.  You can then copy them to the flash drive.  I would expect it to show under /media/alessandro.  To verify, go to the /media/alessandro folder and plug in the flash drive and you should see SUPER ALEX.

Also, if this is a bootable windows iso image, I would expect it to have a boot folder in it.  When you copy the folders/files from the Downloads/windows folder to your SUPER ALEX flash drive, it will overwrite the boot folder you previously created so you will need to create the grub folder and the grub.cfg file again.  If you have the grub.cfg file elsewhere on the computer you can just copy it to a newly created grubfolder in the boot folder on the flash.

---

### Post by corneliuss2 on 2015-01-09
> **IL TRIVELLA said:**
> Hi everyone, 

I'm trying to make an usb flash file iso, to install on my laptop Windows 8.1 (due the fact that I'm buying a new laptop and I want to give this one to my cousin, but he doesn't even know what Ubuntu or Linux is, so it will be better to him to keep using Windows), and I can't.

Let me explain better, I'm trying to create with Ubuntu an Usb flash file iso, to install Windows,I searched on google and all what I can find is that everyone is suggesting to use WinUSB, but I tried many times and it won't work... every single time I get the same error message:

[IMG]http://s14.postimg.org/xfqj38ws1/Screenshot_from_2014_12_30_08_22_29.png[/IMG]

Can you help me please?


Seeing that you have trouble following that guide, I suggest you fix the WinUSB error. All you have to do is to replace a line in a file. Open a Terminal and paste:

```
[FONT=Ubuntu Mono]gksu gedit /usr/bin/winusb [/FONT]
```

Look at line 401, it should start with **grub-install**. If not search for **grub-install** in that file and replace the whole line with:

```
grub-install --target=i386-pc --boot-directory="$partitionMountPath/boot" "$device"
```

Press Ctrl+S to save. Install a package:

```
sudo apt-get install grub-pc-bin
```

and try to use WinUSB. It should work now.

The source is [http://askubuntu.com/a/539803/269282](http://askubuntu.com/a/539803/269282) .

---

### Post by IL TRIVELLA on 2015-01-11
> **yancek said:**
> What I meant was when you create the label in GParted as shown in your link, you could put a dash or underscore in it or, more simply just do SUPERALEX with no spaces.  You can leave the label as is and just continue using double quotes around the command.  This was just a suggestion for future use to simplify things.



You are referring to /home/alessandro right.  Since the prompt in your commands shows the user alessandro.  Those are the expected folders/files in the /home/user directory.

After posting last night, I checked and was unable to use the Disk Image Mounter suggested in the link.  I got a message saying the iso file was too large.  Have you tried the Disk Image Mounter?  What happens?  I've never used it so I don't know what to expect.  I also tried Ark and the Extract and neither work which is why I suggested the mount method which did work for me.  The reason it did not work for you and you got the message 'No such file or directory' is because you were in /home/alessandro.  You need to change to the Downloads directory:

```
cd /home/alessandro/Downloads
``` 

I'm not sure if you missed the part about creating the windows folder in the Downloads folder.  You need to do this before you run the mount command so in the Downloads directory, do this command?



After doing that and still in the Downloads directory, run the mount command as you did previously.  Then open the windows folder there and you should see several folders/files.  You can then copy them to the flash drive.  I would expect it to show under /media/alessandro.  To verify, go to the /media/alessandro folder and plug in the flash drive and you should see SUPER ALEX.

Also, if this is a bootable windows iso image, I would expect it to have a boot folder in it.  When you copy the folders/files from the Downloads/windows folder to your SUPER ALEX flash drive, it will overwrite the boot folder you previously created so you will need to create the grub folder and the grub.cfg file again.  If you have the grub.cfg file elsewhere on the computer you can just copy it to a newly created grubfolder in the boot folder on the flash.

I tried again the process, everything went well, but when I restart the laptop and I go in the the setting menu pressing F10, there is no way I can make it work, it doesn't even appear the option Windows or something, there is only Ubuntu, and two more voices, but nothing to make start the Windows installation.

> **corneliuss2 said:**
> Seeing that you have trouble following that guide, I suggest you fix the WinUSB error. All you have to do is to replace a line in a file. Open a Terminal and paste:

```
[FONT=Ubuntu Mono]gksu gedit /usr/bin/winusb [/FONT]
```

Look at line 401, it should start with **grub-install**. If not search for **grub-install** in that file and replace the whole line with:

```
grub-install --target=i386-pc --boot-directory="$partitionMountPath/boot" "$device"
```

Press Ctrl+S to save. Install a package:

```
sudo apt-get install grub-pc-bin
```

and try to use WinUSB. It should work now.

The source is [http://askubuntu.com/a/539803/269282](http://askubuntu.com/a/539803/269282) .

I did and as you said this time it worked out, so now I can reboot my laptop and try again?

```
alessandro@SuperAlex:~$ gksu gedit /usr/bin/winusb

(gedit:4825): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
alessandro@SuperAlex:~$ sudo apt-get install grub-pc-bin
[sudo] password for alessandro: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grub-pc-bin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
alessandro@SuperAlex:~$ 
```

---

### Post by IL TRIVELLA on 2015-01-11
[IMG]http://s18.postimg.org/w723nez08/10933898_10204087377923440_7900153521062980070_n.jpg[/IMG]

It's still doesn't work... I'm so frustrated...

---

### Post by IL TRIVELLA on 2015-01-11
I don't know anymore what to do...

---

### Post by LostFarmer on 2015-01-11
It is very likely the problems are due to your spaces in names. With your usb partition mounted, in terminal```
sudo mount
ls/media/alessandro/
``` post outputs, that should show just where it is being mounted and if there is some mount point problem in /media/alessandro/


Are you trying to make a MBR or EFI bootable Win8 ?  If it is MBR booted it will only install in MBR  partitioned disk and MBR boot mode, if EFI booted will only install on GPT partitioned disk and EFI booted.  One makes the USB differently, if you want EFI boot then you are doing it the wrong way.

---

### Post by yancek on 2015-01-11
If you see only Ubuntu as an option when you boot the laptop that means you are booting from the hard drive and not from the flash drive.  What you need to do when you boot is to watch the screen for a key to "enter setup".  It should show for a few seconds, usually at the bottom of the screen.  F10 is the key for HP and some other systems but there are a number of keys that will work, it depends upon the manufacturer.  The only key that will work for you is the one shown on the screen so watch for it.  When you get the key, you should get a message saying "entering setup" and then you should see a number of options.  This also varies with the manufacturer but you should see an option labelled Boot and selecting that should give you a "boot priority" option.  You need to select the proper disk.  Usually you will see the name, if you have a Sandisk flash drive it will probably show Sandisk, if it is Toshiba, it will show Toshiba.  You need to set the flash drive to first boot.  Again, this varies with the manufacturer but there should be something showing telling which keys to press to move up/down.  Sometimes the arrow keys, sometimes the Page Up, Page Down keys and it could be others.  Until you get this set, you won't boot the flash drive.

Did you get the windows files copied to the flash drive and were you able to verify that?
I tried the Disk Image Mounter on a smaller iso and it extracted the files from the iso and put them in a folder in the /media/user directory with the name of the iso.  In your case, if you used this you should have seen a folder probably named window or similar in the /media/alessandro directory.  You would copy these to your flash drive which should also have been in the /media/alessandro/SUPER ALEX folder.

From your previous posts, it seems you successfully copied and installed Grub but you never gave any indication that the windows files were copied, in fact the output you posted indicated that you definitely did NOT copy them.  Until you are sure the windows files are copied to the flash and you then do the grub-install successfully and put the grub.cfg file in the flash drive under /boot/grub, you cannot expect success.

It's been interesting, post back with results.

---

### Post by IL TRIVELLA on 2015-01-11
> **LostFarmer said:**
> It is very likely the problems are due to your spaces in names. With your usb partition mounted, in terminal```
sudo mount
ls/media/alessandro/
``` post outputs, that should show just where it is being mounted and if there is some mount point problem in /media/alessandro/

```
alessandro@SuperAlex:~$ sudo mount[sudo] password for alessandro: 
/dev/sda3 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda1 on /boot/efi type vfat (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=alessandro)
/dev/sdb1 on /media/alessandro/Windows USB type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
alessandro@SuperAlex:~$ ls/media/alessandro/
bash: ls/media/alessandro/: No such file or directory
alessandro@SuperAlex:~$
```

> **LostFarmer said:**
> Are you trying to make a MBR or EFI bootable Win8 ? If it is MBR booted it will only install in MBR partitioned disk and MBR boot mode, if EFI booted will only install on GPT partitioned disk and EFI booted. One makes the USB differently, if you want EFI boot then you are doing it the wrong way.

I have no idea what all this means... 

> **yancek said:**
> If you see only Ubuntu as an option when you boot the laptop that means you are booting from the hard drive and not from the flash drive. What you need to do when you boot is to watch the screen for a key to "enter setup". It should show for a few seconds, usually at the bottom of the screen. F10 is the key for HP and some other systems but there are a number of keys that will work, it depends upon the manufacturer. The only key that will work for you is the one shown on the screen so watch for it. When you get the key, you should get a message saying "entering setup" and then you should see a number of options. This also varies with the manufacturer but you should see an option labelled Boot and selecting that should give you a "boot priority" option. You need to select the proper disk. Usually you will see the name, if you have a Sandisk flash drive it will probably show Sandisk, if it is Toshiba, it will show Toshiba. You need to set the flash drive to first boot. Again, this varies with the manufacturer but there should be something showing telling which keys to press to move up/down. Sometimes the arrow keys, sometimes the Page Up, Page Down keys and it could be others. Until you get this set, you won't boot the flash drive.

Did you get the windows files copied to the flash drive and were you able to verify that?
I tried the Disk Image Mounter on a smaller iso and it extracted the files from the iso and put them in a folder in the /media/user directory with the name of the iso. In your case, if you used this you should have seen a folder probably named window or similar in the /media/alessandro directory. You would copy these to your flash drive which should also have been in the /media/alessandro/SUPER ALEX folder.

From your previous posts, it seems you successfully copied and installed Grub but you never gave any indication that the windows files were copied, in fact the output you posted indicated that you definitely did NOT copy them. Until you are sure the windows files are copied to the flash and you then do the grub-install successfully and put the grub.cfg file in the flash drive under /boot/grub, you cannot expect success.

It's been interesting, post back with results.

I did pressed F10 because I have an HP, and entered the setup and change the boot order, I know how to do it, because i always format my laptops on my own, but I tried anything and it doesn't work...

How I make sure that I copied the Windows files?

---

### Post by LostFarmer on 2015-01-11
"/dev/sdb1 on /media/alessandro/Windows USB"  Your sdb1 is Labled 'Windows USB' not SUPER ALEX.  That is why it is not working.

Need clarification : Is the computer that you want to reinstall Win8 to, is it the one you are running the commands on and posting from ?   If yes, it has GPT partitioning and boots in EFI mode ( /dev/sda1 on /boot/efi) and what you are doing will not work unless you want to change the partition type to MBR.  For GPT partitioning and EFI booting it is done differently.

sorry I wrote the one command wrong "ls/media/alessandro/" , it should have a space " ls /media/alessandro/"  Please run and post corrected command.

> I have no idea what all this means. read: [http://www.maketecheasier.com/differences-between-mbr-and-gpt/](http://www.maketecheasier.com/differences-between-mbr-and-gpt/)  and [https://wiki.manjaro.org/index.php?title=Some_basics_of_MBR_v/s_GPT_and_BIOS_v/s_UEFI](https://wiki.manjaro.org/index.php?title=Some_basics_of_MBR_v/s_GPT_and_BIOS_v/s_UEFI)

Edit:  I may be wrong on having to boot in EFI mode to install in that mode, it might just be the type of hdd partitioning that matters.

---

### Post by yancek on 2015-01-11
> How I make sure that I copied the Windows files? 				

You have to copy them to a specific location so look in that location to see if they are there.  You have not indicated what method you are using to get the windows files or how you are copying them.  Are you using the Disk Image Mounter then copying from that location to your flash drive?  They aren't going to copy by themselves, you need to copy them. 

> /dev/sdb1 on /media/alessandro/Windows USB type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

You indicated earlier that the usb drive you were trying to copy the files TO and install Grub TO, was on sdb.  The line above is the only one in the output you posted that is relevant so don't worry about what the others are. The above line shows that sdb1 is mounted at /media/alessandro/Windows which is also where your windows files should be, on the usb drive.  To see if they are, run the following command:

```
ls /media/alessandro/Windows/
```  

If there are no windows files there, that means you didn't copy them to the correct location.  So try it again.

If you are setting the usb to first boot priority and saving that change and it still doesn't boot, that's because it isn't bootable.  Even if you successfully install Grub, it won't boot if there isn't anything to boot.  Once again, you need to explain how you copied the windows files to the flash and use the method above to check if they are there.  

You don't need to worry about the comments lostfarmer made until you get the usb to boot.  He is referring to when you actually start doing the install.  If you can't get a bootable usb, you won't be able to install.  I know this method can work as far as booting a windows installation medium since I did it using this method.  I don't know if it will install because I didn't install because I have no interest in installing windows.

---

### Post by IL TRIVELLA on 2015-01-14
> **LostFarmer said:**
> "/dev/sdb1 on /media/alessandro/Windows USB"  Your sdb1 is Labled 'Windows USB' not SUPER ALEX.  That is why it is not working.

Need clarification : Is the computer that you want to reinstall Win8 to, is it the one you are running the commands on and posting from ?   If yes, it has GPT partitioning and boots in EFI mode ( /dev/sda1 on /boot/efi) and what you are doing will not work unless you want to change the partition type to MBR.  For GPT partitioning and EFI booting it is done differently.

sorry I wrote the one command wrong "ls/media/alessandro/" , it should have a space " ls /media/alessandro/"  Please run and post corrected command.

 read: [http://www.maketecheasier.com/differences-between-mbr-and-gpt/](http://www.maketecheasier.com/differences-between-mbr-and-gpt/)  and [https://wiki.manjaro.org/index.php?title=Some_basics_of_MBR_v/s_GPT_and_BIOS_v/s_UEFI](https://wiki.manjaro.org/index.php?title=Some_basics_of_MBR_v/s_GPT_and_BIOS_v/s_UEFI)

Edit:  I may be wrong on having to boot in EFI mode to install in that mode, it might just be the type of hdd partitioning that matters.

Hi guys, sorry for the very late reply, I had some big stress at work I may need to quit my job soon, but anyway...

Yes the laptop from which I'm writing, and doing all, is the one that I will like to format, I tried to run the command you told me, and that's what happened:

```
alessandro@SuperAlex:~$ ls /media/alessandro/">
```

Nothing else, even if I waited for more than an hour, no joking...

And about the EFI and MBR thing, I have really difficulties in understand how to do it...

> **yancek said:**
> You have to copy them to a specific location so look in that location to see if they are there. You have not indicated what method you are using to get the windows files or how you are copying them. Are you using the Disk Image Mounter then copying from that location to your flash drive? They aren't going to copy by themselves, you need to copy them.

Yes first I do, open with disk image mounter, then once done that, I just copy all the files in the usb, that's also what the guide says...

> **yancek said:**
> You indicated earlier that the usb drive you were trying to copy the files TO and install Grub TO, was on sdb. The line above is the only one in the output you posted that is relevant so don't worry about what the others are. The above line shows that sdb1 is mounted at /media/alessandro/Windows which is also where your windows files should be, on the usb drive. To see if they are, run the following command:

```
ls /media/alessandro/Windows/
```

so you mean that line must end with sdb1 instead than sdb? and that's the result of the command:

```
alessandro@SuperAlex:~$ ls /media/alessandro/Windows/
ls: cannot access /media/alessandro/Windows/: No such file or directory
alessandro@SuperAlex:~$
```

> **yancek said:**
> If there are no windows files there, that means you didn't copy them to the correct location. So try it again.

If you are setting the usb to first boot priority and saving that change and it still doesn't boot, that's because it isn't bootable. Even if you successfully install Grub, it won't boot if there isn't anything to boot. Once again, you need to explain how you copied the windows files to the flash and use the method above to check if they are there. 

You don't need to worry about the comments lostfarmer made until you get the usb to boot. He is referring to when you actually start doing the install. If you can't get a bootable usb, you won't be able to install. I know this method can work as far as booting a windows installation medium since I did it using this method. I don't know if it will install because I didn't install because I have no interest in installing windows.

When I go in the system setting to change the boot order, there is down the EFI boot if I'm not wrong, which I can't change because is in grey and only if I enable something I can... but I should write down exactly this stuff because I know that like that, this info are useless...

---

### Post by yancek on 2015-01-14
[QUOTE/dev/sdb1 on /media/alessandro/Windows USB type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)][/QUOTE]

The line above from your earlier post indicates your flash drive, which is device sdb1, is mounted at /media/alessandro/Windows USB
Copy and paste the following into your terminal with the flash drive plugged in and post it here.

> ls /media/alessandro

You indicated you put the entry below in a terminal and got no output.  I wouldn't expect any, compare it to the line I posted above.  You need to not put: ">

> ls /media/alessandro/">

Don't worry about the EFI stuff.  That will only be applicable after you have created the flash drive and made it bootable.

> Yes first I do, open with disk image mounter, then once done that, I  just copy all the files in the usb, that's also what the guide says...

How do you copy them?  From the file manager?  From a terminal?  Where do you copy them to?  What is the mount point you are copying to, be specific please.

> so you mean that line must end with sdb1 instead than sdb? and that's the result of the command:

I'm not sure what you are referring to with the above quote?

---

### Post by IL TRIVELLA on 2015-01-17
```
alessandro@SuperAlex:~$ ls /media/alessandroWindows USB
alessandro@SuperAlex:~$ 
```

About how I copy them, well, I just as I said did right click on the .iso file, then open with disk image mounter, as the guide say and on the left, where there is computer it's appearing another device, like an usb flash, or external hard drive, and it's called IRM_CCSA_X64FRE_EN-US_DV5 exactly like that, once done that, I simply go inside that directory/device and I do ctrl+A and ctrl+C and then I go into the usb directory and I do ctrl+V, that's is how I'm copying the files, and if I'm not wrong is also how the guide it's saying to do...

About the sdb and sdb1 my question was that before I was writing:

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo grub-install --target=i386-pc --boot-directory="/media/Alessandro Calello/SUPER ALEX/boot" /dev/sdX[/FONT][/COLOR]
```

Then I changed it with:

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo grub-install --target=i386-pc --boot-directory="/media/Alessandro Calello/SUPER ALEX/boot" /dev/sdb[/FONT][/COLOR]
```

And now you are saying to me that the right way to write it is:

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo grub-install --target=i386-pc --boot-directory="/media/Alessandro Calello/Windows USB/boot" /dev/sdb1[/FONT][/COLOR]
```

is that right?

---

### Post by yancek on 2015-01-17
> alessandro@SuperAlex:~$ ls /media/alessandroWindows USB

I don't know what that means.  Did you do:  ls /media/alessandro as I suggested and the only output was:  Windows USB?

When you right click the iso file and select Disk Image Mounter, it should open a nautilus window showing the files inside the iso.  If it doesn't, then it should be in the /media/alessandro directory and should have a folder named something with windows in it.  You copy the files and folders from inside whatever that folder is named.  It doesn't matter how you copy them but you have to copy them to the correct mount point for the flash drive which you say has the label name SUPER ALEX.  That should also be under /medai/alessandro.

>  IRM_CCSA_X64FRE_EN-US_DV5

I have no idea what that is.  When you open it, do you see windows folders/files?  You should see at least a boot folder, a bcd file and a setup.exe as well as others.  Do you?

So now what is the mount point for your flash drive?  Is it still SUPER ALEX and is it showing under /media/alessandro?
If it is, this is where you need to copy the windows files to.  THEN, you need to create the grub folder inside the windows boot folder and then put your grub.cfg file inside the /boot/grub folder.

If you are copying the entire windows folder that was mounted with the Disk Image Mounter, that won't work.  You need to copy the files inside to the root directory of the flash drive.

> [COLOR=#000000][FONT=Ubuntu Mono]sudo grub-install --target=i386-pc --boot-directory="/media/Alessandro Calello/SUPER ALEX/boot" /dev/sdX[/FONT][/COLOR]

I don't know where the "Alessandro Calello" is coming from?  You said earlier that you only had one user and that user name was alessandro.  Your SUPER ALEX should show under /media/alessandro so the correct entry to install grub would be as below, if your flash drive still is sdb:


> [QUOTE][COLOR=#000000][FONT=Ubuntu Mono]sudo grub-install --target=i386-pc --boot-directory="/media/alessandro/SUPER ALEX/boot" /dev/sdb[/FONT][/COLOR][/QUOTE

What exactly is the mount point for the flash drive?  /media/alessandro/SUPER ALEX?  After you copy the windows files, do you go there and check to see that they are there?

What happens after you do this and run the grub-install?  You have indicated previously that you had a success message with grub-install.  
I would suggest that after you use Disk Image Mounter and open the folder with windows, you post a list of the contents, the files and folders.

---

### Post by yancek on 2015-01-17
> alessandro@SuperAlex:~$ ls /media/alessandroWindows USB

I don't know what that means.  Did you do:  ls /media/alessandro as I suggested and the only output was:  Windows USB?

When you right click the iso file and select Disk Image Mounter, it should open a nautilus window showing the files inside the iso.  If it doesn't, then it should be in the /media/alessandro directory and should have a folder named something with windows in it.  You copy the files and folders from inside whatever that folder is named.  It doesn't matter how you copy them but you have to copy them to the correct mount point for the flash drive which you say has the label name SUPER ALEX.  That should also be under /medai/alessandro.

>  IRM_CCSA_X64FRE_EN-US_DV5

I have no idea what that is.  When you open it, do you see windows folders/files?  You should see at least a boot folder, a bcd file and a setup.exe as well as others.  Do you?

So now what is the mount point for your flash drive?  Is it still SUPER ALEX and is it showing under /media/alessandro?
If it is, this is where you need to copy the windows files to.  THEN, you need to create the grub folder inside the windows boot folder and then put your grub.cfg file inside the /boot/grub folder.  After that, you need to run the grub-install command.

If you are copying the entire windows folder that was mounted with the Disk Image Mounter, that won't work.  You need to copy the files inside to the root directory of the flash drive.

> [COLOR=#000000][FONT=Ubuntu Mono]sudo grub-install --target=i386-pc --boot-directory="/media/Alessandro Calello/SUPER ALEX/boot" /dev/sdX[/FONT][/COLOR]

I don't know where the "Alessandro Calello" is coming from?  You said earlier that you only had one user and that user name was alessandro.  Your SUPER ALEX should show under /media/alessandro so the correct entry to install grub would be as below, if your flash drive still is sdb:


> [QUOTE][COLOR=#000000][FONT=Ubuntu Mono]sudo grub-install --target=i386-pc --boot-directory="/media/alessandro/SUPER ALEX/boot" /dev/sdb[/FONT][/COLOR][/QUOTE

What exactly is the mount point for the flash drive?  /media/alessandro/SUPER ALEX?  After you copy the windows files, do you go there and check to see that they are there?

What happens after you do this and run the grub-install and try to boot the flash drive?  You have indicated previously that you had a success message with grub-install.  
I would suggest that after you use Disk Image Mounter and open the folder with windows, you post a list of the contents, the files and folders.

---

