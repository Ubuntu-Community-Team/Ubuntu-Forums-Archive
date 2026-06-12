---
title: "How to add Android-x86 entry to GRUB2?"
date: 2015-12-26
forum: General Help
---

### Post by george133 on 2015-12-26
Hello guys. Today, I have installed Android-x86 5.1 on sda9. I have dual-booted Windows 10 and Ubuntu 14.04. So, when Android installation asked me if I want to install GRUB or not, I selected No, because I already have GRUB. But there isn't Android-x86 entry in GRUB so I'm unable to boot into Android.

Can anyone help me? Thanks in advance.

---

### Post by grahammechanical on 2015-12-26
As a preliminary action you can load into Ubuntu & run this command

```
sudo update-grub
```

That will produce a printout. What you see in the printout is what will appear in the Grub boot menu. If you see a reference to android-x86 then you may not need to do anything more.

Regards.

---

### Post by george133 on 2015-12-26
> **grahammechanical said:**
> As a preliminary action you can load into Ubuntu & run this command

```
sudo update-grub
```

That will produce a printout. What you see in the printout is what will appear in the Grub boot menu. If you see a reference to android-x86 then you may not need to do anything more.

Regards.
There is output:
```
ninja@inspiron:~$ sudo update-grub[sudo] password for ninja: 
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-42-generic
Found initrd image: /boot/initrd.img-3.19.0-42-generic
Found linux image: /boot/vmlinuz-3.19.0-25-generic
Found initrd image: /boot/initrd.img-3.19.0-25-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
error: $.
error: syntax error.
error: Incorrect command.
error: syntax error.
Syntax error at line 262
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
done



```

---

### Post by QDR06VV9 on 2015-12-26
Hi george133
 After you've installed both Ubuntu and Android-x86, you need to boot into Ubuntu and modify the "40_custom" GRUB script:
```
 gksu gedit /etc/grub.d/40_custom

```
And at the bottom of the file, add this:
```
menuentry "Android-x86" {
set root='(hd0,0)'
linux /android-4.0-RC1/kernel quiet root=/dev/ram0 androidboot.hardware=eeepc acpi_sleep=s3_bios,s3_mode SRC=/android-4.0-RC1 SDCARD=/data/sdcard.img
initrd /android-4.0-RC1/initrd.img}
```


**Please note the difference in kernels change to the one you are on. **
If you haven't installed Android-x86 4.0 RC1 but some other version, replace the lines containing "android-4.0-RC1" with your version.
For Android-x86 versions older than 4.0, use "androidboot_hardware" instead of "androidboot.hardware"
There is more here you need to see [http://www.webupd8.org/2012/03/how-to-dual-boot-android-x86-and-ubuntu.html](http://www.webupd8.org/2012/03/how-to-dual-boot-android-x86-and-ubuntu.html)
He also has a video at the top part of that link above^^^^^^^

There are some changes you'll need to make to the above menu entry (code above):
If you didn't create an sdcard image, remove the "SDCARD=/data/sdcard.img" part from the 3rd line (make sure you don't remove anything else!)
The above menu entry uses "eeepc" for androidboot.hardware, but you can replace it with your hardware, depending on the ISO you've downloaded (use "asus_laptop" for the ASUS Laptop ISO, etc.) or use "generic_x86".
If you haven't installed Android-x86 4.0 RC1 but some other version, replace the lines containing "android-4.0-RC1" with your version.
For Android-x86 versions older than 4.0, use **"androidboot_hardware" **instead of [B]"androidboot.hardware"
[/B]But the most important thing you need to change in the menuentry is the partition on which you've installed Android-x86, "(hd0,0)" in my example. If you don't know on which partition you've installed it, run the following command in a terminal:
```
sudo fdisk -l

```
so I've replaced "(hd0,0)" with "(hd0,6)" - hd0 means the first hard disk ("sda") and "6" is the partition and comes from "sda6".


Hard disk naming starts with 0 so basically, sda is "hd0", sdb is "hd1" and so on. Counting partitions doesn't start with 0, so if you've installed Android x86 on let's say "sda5", you'd use "(hd0,5).
Once you make these changes, save the file.
Now let's make the file executable and update GRUB 2:
```
sudo chmod +x /etc/grub.d/40_custom
sudo update-grub
```


That is about it, Hope this helps.
Kind regards

---

### Post by george133 on 2015-12-26
> **runrickus said:**
> Hi george133
 After you've installed both Ubuntu and Android-x86, you need to boot into Ubuntu and modify the "40_custom" GRUB script:
```
 gksu gedit /etc/grub.d/40_custom

```
And at the bottom of the file, add this:
```
menuentry "Android-x86" {
set root='(hd0,0)'
linux /android-4.0-RC1/kernel quiet root=/dev/ram0 androidboot.hardware=eeepc acpi_sleep=s3_bios,s3_mode SRC=/android-4.0-RC1 SDCARD=/data/sdcard.img
initrd /android-4.0-RC1/initrd.img}
```


**Please note the difference in kernels change to the one you are on. **
If you haven't installed Android-x86 4.0 RC1 but some other version, replace the lines containing "android-4.0-RC1" with your version.
For Android-x86 versions older than 4.0, use "androidboot_hardware" instead of "androidboot.hardware"
There is more here you need to see [http://www.webupd8.org/2012/03/how-to-dual-boot-android-x86-and-ubuntu.html](http://www.webupd8.org/2012/03/how-to-dual-boot-android-x86-and-ubuntu.html)
He also has a video at the top part of that link above^^^^^^^

There are some changes you'll need to make to the above menu entry (code above):
If you didn't create an sdcard image, remove the "SDCARD=/data/sdcard.img" part from the 3rd line (make sure you don't remove anything else!)
The above menu entry uses "eeepc" for androidboot.hardware, but you can replace it with your hardware, depending on the ISO you've downloaded (use "asus_laptop" for the ASUS Laptop ISO, etc.) or use "generic_x86".
If you haven't installed Android-x86 4.0 RC1 but some other version, replace the lines containing "android-4.0-RC1" with your version.
For Android-x86 versions older than 4.0, use **"androidboot_hardware" **instead of [B]"androidboot.hardware"
[/B]But the most important thing you need to change in the menuentry is the partition on which you've installed Android-x86, "(hd0,0)" in my example. If you don't know on which partition you've installed it, run the following command in a terminal:
```
sudo fdisk -l

```
so I've replaced "(hd0,0)" with "(hd0,6)" - hd0 means the first hard disk ("sda") and "6" is the partition and comes from "sda6".


Hard disk naming starts with 0 so basically, sda is "hd0", sdb is "hd1" and so on. Counting partitions doesn't start with 0, so if you've installed Android x86 on let's say "sda5", you'd use "(hd0,5).
Once you make these changes, save the file.
Now let's make the file executable and update GRUB 2:
```
sudo chmod +x /etc/grub.d/40_custom
sudo update-grub
```


That is about it, Hope this helps.
Kind regards

Thank you very much!

> **runrickus said:**
> Hi george133
 After you've installed both Ubuntu and Android-x86, you need to boot into Ubuntu and modify the "40_custom" GRUB script:
```
 gksu gedit /etc/grub.d/40_custom


Sir, after this, I'm getting error when I'm opening Grub Customizer. Here is it:[IMG]http://i.imgur.com/Z1Viyzb.png[/IMG] 
Can you help me?

Also, when I run
[CODE]sudo update-grub
```
I'm getting this output:
```
ninja@inspiron:~$ sudo update-grub
Generating grub configuration file ...
/etc/grub.d/40_custom: 1: /etc/grub.d/40_custom: menuentry: not found
/etc/grub.d/40_custom: 3: /etc/grub.d/40_custom: linux: not found
/etc/grub.d/40_custom: 4: /etc/grub.d/40_custom: initrd: not found
```

I'll be glad if you'll help me.

---

### Post by QDR06VV9 on 2015-12-27
Hi george133
Can you navigate to **/etc/grub.d/40_custom **and post the contents of that file here.
Better yet just put this in the terminal and post the results back here..
```
gedit /etc/grub.d/40_custom
```
So we can see what is what.

---

### Post by george133 on 2015-12-27
> **runrickus said:**
> Hi george133
Can you navigate to **/etc/grub.d/40_custom **and post the contents of that file here.
Better yet just put this in the terminal and post the results back here..
```
gedit /etc/grub.d/40_custom
```
So we can see what is what.

[IMG]http://i.imgur.com/SJfbifR.png[/IMG]

---

### Post by QDR06VV9 on 2015-12-27
Well it would seem that you also removed the top portion of that file.
It should read like my example below
> #!/bin/shexec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
So you now need to copy what I have above and add it to the top of  that file and [COLOR=#333333][FONT=Arial]remove the **"SDCARD=/data/sdcard.img"**
[/FONT][/COLOR]From there also. 
Now save that file and try again to boot to your Android-x86 OS.
One more note here I probably would have waited to install Grub Customizer.... You can still get to Gurb by tapping the shift key as your computer is booting-up. 

Just a heads up It is not recommended that you use the "sudo -i" command to open GUI applications instead use <gksu or gksudo>.

---

### Post by george133 on 2015-12-27
> **runrickus said:**
> Well it would seem that you also removed the top portion of that file

No I didn't. What can I do? Can I replace this file with the default one?

---

### Post by QDR06VV9 on 2015-12-27
Please read my post again.

---

### Post by george133 on 2015-12-27
> **runrickus said:**
> Please read my post again.

I did exactly what you wrote but I still can't access Grub Customizer. Here's error:
[IMG]http://i.imgur.com/awErvbB.png[/IMG]

---

### Post by QDR06VV9 on 2015-12-27
Ok Lets break this down to just small steps for now..
Copy and paste the results of
```
gedit /etc/grub.d/40_custom
```
Please No Screen shots just the text from that file.
And also post back the contents of this (Text only no screen shots)
```
sudo fdisk -l
```

---

### Post by george133 on 2015-12-27
> **runrickus said:**
> Ok Lets break this down to just small steps for now..
Copy and paste the results of
```
gedit /etc/grub.d/40_custom
```
Please No Screen shots just the text from that file.
And also post back the contents of this (Text only no screen shots)
```
sudo fdisk -l
```

Results of 'gedit /etc/grub.d/40_custom':
```
#!/bin/shexec tail -n +3 $0
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.

menuentry "Android-x86" {
set root='(hd0,9)'
linux /android-5.1-rc1/kernel quiet root=/dev/ram0 androidboot_hardware=eeepc acpi_sleep=s3_bios,s3_mode SRC=/android-5.1-rc1
initrd /android-5.1-rc1/initrd.img}
```

Results of 'sudo fdisk -l':
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xb7920c0f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.


```

---

### Post by QDR06VV9 on 2015-12-27
Ok the  /etc/grub.d/40_custom looks good but I do not see where you installed Android-x86 with the results of fdisk.
Did you install Android to your hard drive or usb drive??

---

### Post by george133 on 2015-12-27
> **runrickus said:**
> Ok the  /etc/grub.d/40_custom looks good but I do not see where you installed Android-x86 with the results of fdisk.
Did you install Android to your hard drive or usb drive??

On hard drive. sda9 I guess.

---

### Post by QDR06VV9 on 2015-12-27
Huumm?? all i can see is "[COLOR=#000000][FONT=Ubuntu Mono]/dev/sda1[/FONT][/COLOR]" from what you posted.

Lets do this in the terminal
```
sudo chmod +x /etc/grub.d/40_custom
```
Then also in terminal
```
sudo update-grub
```
And post back any errors.

---

### Post by george133 on 2015-12-27
> **runrickus said:**
> Huumm?? all i can see is "[COLOR=#000000][FONT=Ubuntu Mono]/dev/sda1[/FONT][/COLOR]" from what you posted.

Lets do this in the terminal
```
sudo chmod +x /etc/grub.d/40_custom
```
Then also in terminal
```
sudo update-grub
```
And post back any errors.

```
ninja@inspiron:~$ sudo update-grub
Generating grub configuration file ...
/usr/sbin/grub-mkconfig: 276: /usr/sbin/grub-mkconfig: /etc/grub.d/40_custom: not found

```

---

### Post by QDR06VV9 on 2015-12-27
Well that is not what we would of hoped for:o
I need to think a little deeper here and maybe do some reading(fact checking)
Just one more question. Are you only Booting to Ubuntu and hopefully Androidx86?? 
Or are there other operating systems installed?

---

### Post by george133 on 2015-12-27
> **runrickus said:**
> Well that is not what we would of hoped for:o
I need to think a little deeper here and maybe do some reading(fact checking)
Just one more question. Are you only Booting to Ubuntu and hopefully Androidx86?? 
Or are there other operating systems installed?

I also have Windows 10 installed. In GRUB2 menu while booting, there is Ubuntu and Windows 10 options, but there's not Android-x86.

---

### Post by QDR06VV9 on 2015-12-27
> [COLOR=#000000]I also have Windows 10 installed. In GRUB2 menu while booting, there is Ubuntu and Windows 10 options, but there's not Android-x86.[/COLOR]
I thought that might the case.
Ok give me a little time here, need to re-think my next step.
I will be back:D

---

### Post by george133 on 2015-12-27
> **runrickus said:**
> I thought that might the case.
Ok give me a little time here, need to re-think my next step.
I will be back:D

Thank you very much for help. I'll be right here.

---

### Post by QDR06VV9 on 2015-12-27
Before I make any choices here I just need to check this out to verify if grub.d/40_custom is set correctly.
In terminal post back results from
```
sudo ls -la /etc/grub.d/40_custom

```
And in your Bios do you have secure boot to disabled?

---

### Post by george133 on 2015-12-28
> **runrickus said:**
> Before I make any choices here I just need to check this out to verify if grub.d/40_custom is set correctly.
In terminal post back results from
```
sudo ls -la /etc/grub.d/40_custom

```
And in your Bios do you have secure boot to disabled?

```
ninja@inspiron:~$ sudo ls -la /etc/grub.d/40_custom
[sudo] password for ninja: 
-rwxr-xr-x 1 root root 419 Dec 27 21:30 /etc/grub.d/40_custom
```

Yes IIRC. I'll check it.

Just checked, yes, it's disabled.

---

### Post by QDR06VV9 on 2015-12-28
Well all that is OK..But this from "[COLOR=#000000]sudo fdisk -l[/COLOR]"
Where it shows
> /dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.
This is certainally proving to be a challange.
I am leaning to that Android-x86 is not installed on [COLOR=#000000]sda9.
[/COLOR][COLOR=#000000]fdisk is not always the best tool to use for finding partitions on newer disks, so lets see if Gparted is up to the task.
If it is not installed already, you can install it by
```
sudo apt-get install gparted
```
Then after it is installed,  run it and this time give me just a Screenshot of the Gparted window.

And also when you are logged in to Ubuntu with the file manager(Nautilus) can you see the Android-x86 Entry in the tree off to left?[/COLOR]

---

### Post by george133 on 2015-12-28
> **runrickus said:**
> Well all that is OK..But this from "[COLOR=#000000]sudo fdisk -l[/COLOR]"
Where it shows

This is certainally proving to be a challange.
I am leaning to that Android-x86 is not installed on [COLOR=#000000]sda9.
[/COLOR][COLOR=#000000]fdisk is not always the best tool to use for finding partitions on newer disks, so lets see if Gparted is up to the task.
If it is not installed already, you can install it by
```
sudo apt-get install gparted
```
Then after it is installed,  run it and this time give me just a Screenshot of the Gparted window.

And also when you are logged in to Ubuntu with the file manager(Nautilus) can you see the Android-x86 Entry in the tree off to left?[/COLOR]
[IMG]http://i.imgur.com/qTq0wsO.png[/IMG]

And yes, there is Android-x86 entry in Nautilus.

---

### Post by QDR06VV9 on 2015-12-28
Well there it is.:D
When you installed the Android-x86 did you use a [COLOR=#333333][FONT=Arial]sdcard image?
I am asking because I see a sd bak on your desktop.
If there was a link you used to install could you show that method also.(Or even the way you installed it)[/FONT][/COLOR]

---

### Post by george133 on 2015-12-28
> **runrickus said:**
> Well there it is.:D
When you installed the Android-x86 did you use a [COLOR=#333333][FONT=Arial]sdcard image?
I am asking because I see a sd bak on your desktop.
If there was a link you used to install could you show that method also.(Or even the way you installed it)[/FONT][/COLOR]

"sd bak" folder is just a backup of my microSD card. I backed it up because I was going to install new ROM on my Android device and format phone completely (including external storage). But I guess it's nonsense.

---

### Post by QDR06VV9 on 2015-12-28
> [COLOR=#000000][INDENT]"sd bak" folder is just a backup of my microSD card. I backed it up because I was going to install new ROM on my Android device and format phone completely (including external storage). But I guess it's nonsense.[/INDENT]
[/COLOR][COLOR=#000000][INDENT][COLOR=#222222]
Ok good to know I had you remove that from the [/COLOR] '/etc/grub.d/40_custom' So I am just covering all the base's;)
I t would really be helpful if you had the link that you used to install it with, Or if you can remember [B]EXACTLY How you installed it.
[/B]As of right now I can not see why Grub2 wont work without Errors and yes you did install it on sda9.[/INDENT]


[/COLOR]

---

### Post by george133 on 2015-12-28
> **runrickus said:**
> [COLOR=#000000][INDENT][COLOR=#222222]
Ok good to know I had you remove that from the [/COLOR] '/etc/grub.d/40_custom' So I am just covering all the base's;)
I t would really be helpful if you had the link that you used to install it with, Or if you can remember [B]EXACTLY How you installed it.
[/B]As of right now I can not see why Grub2 wont work without Errors and yes you did install it on sda9.[/INDENT]


[/COLOR]

First of all, I booted into Windows 10. I shrank some space (32GB) from D:\ partition. Then I created bootable USB drive with Android-x86 on it (Android 5.1 Lollipop to be exact). While installing, I chose option "Create or Modify Partitions" (or something like that) and created partition from unallocated 32GB space. Then it asked me if I wanted to install GRUB, I said NO! That's all I guess.

Btw, I have already backed up all my important stuff and I'm going to re-install both Windows and Ubuntu. Just one question, will removing all partitions also remove GRUB? I'm going to delete all partitions on my hard drive, re-create them, install Windows on one of them and Ubuntu on another. After this, I'll try to install Android-x86 one more time.

---

### Post by QDR06VV9 on 2015-12-28
> [COLOR=#000000]will removing all partitions also remove GRUB? [/COLOR]
Yes. But You can create partitions and file system without ever affecting the MBR or other locations where bootloaders (eg GRUB) are installed
I am not sure you need to do all that(Re-Install) unless there is something else matter.
But I am Glad to hear you keep good back-ups in place.:D
You could Just Try again installing Android-x86 to the same Partition you already have, But format it before hand.
Formatting just gets rid of any nasty and unwanted leftover code..  
And I have had alot of success with this method of installing it [http://www.webupd8.org/2012/03/how-to-dual-boot-android-x86-and-ubuntu.html](http://www.webupd8.org/2012/03/how-to-dual-boot-android-x86-and-ubuntu.html)
But give me about an hour to see if I can come-up with a solution to your problem.
But of course that is up to you. So let me know.

---

### Post by george133 on 2015-12-29
> **runrickus said:**
> Yes. But You can create partitions and file system without ever affecting the MBR or other locations where bootloaders (eg GRUB) are installed
I am not sure you need to do all that(Re-Install) unless there is something else matter.
But I am Glad to hear you keep good back-ups in place.:D
You could Just Try again installing Android-x86 to the same Partition you already have, But format it before hand.
Formatting just gets rid of any nasty and unwanted leftover code..  
And I have had alot of success with this method of installing it [http://www.webupd8.org/2012/03/how-to-dual-boot-android-x86-and-ubuntu.html](http://www.webupd8.org/2012/03/how-to-dual-boot-android-x86-and-ubuntu.html)
But give me about an hour to see if I can come-up with a solution to your problem.
But of course that is up to you. So let me know.

Don't care about the problem anymore ;) Thank you very much

---

### Post by Photon Blizzard on 2015-12-29
We might want to remove the hash tag in line one as well. :-)

---

### Post by deadflowr on 2015-12-29
> **Photon Blizzard said:**
> We might want to remove the hash tag in line one as well. :-)
you mean this
```
#!/bin/shexec tail -n +3 $0
```
aside from the echo line being added, which is probably a forum code tag thingy, the crunchbang should stay as is.
The forum code tag might have pulled the second line into the first 
(would need confirmation from the other posters if that is so,)
Should read as:
```
#!/bin/sh
exec tail -n +3 $0
```
the # in this case should look as it does with #!/bin/sh.

---

### Post by george133 on 2015-12-29
> **deadflowr said:**
> you mean this
```
#!/bin/shexec tail -n +3 $0
```
aside from the echo line being added, which is probably a forum code tag thingy, the crunchbang should stay as is.
The forum code tag might have pulled the second line into the first 
(would need confirmation from the other posters if that is so,)
Should read as:
```
#!/bin/sh
exec tail -n +3 $0
```
the # in this case should look as it does with #!/bin/sh.

[IMG]http://i.imgur.com/MFoWJqn.png[/IMG]

---

### Post by QDR06VV9 on 2015-12-29
> **deadflowr said:**
> you mean this
```
#!/bin/shexec tail -n +3 $0
```
aside from the echo line being added, which is probably a forum code tag thingy, the crunchbang should stay as is.
The forum code tag might have pulled the second line into the first 
(would need confirmation from the other posters if that is so,)
Should read as:
```
#!/bin/sh
exec tail -n +3 $0
```
the # in this case should look as it does with #!/bin/sh.
I can not believe I have missed that!#!](*,) Thanks to the both(Photon Blizzard && deadflowr):D

 of you..

> **george133 said:**
> [IMG]http://i.imgur.com/MFoWJqn.png[/IMG]

Yes [COLOR=#000000]george133[/COLOR] It should look  like deadflowr's post..
And now maybe update-grub

---

### Post by george133 on 2015-12-29
Thanks to everyone! Problem solved <3

---

### Post by eponji on 2016-06-07
This code doesn't works. When i clicked on the entry of the linux grub i had the android that launch , it was written "android" a few moment and then a black screen with a white flashing dash.
But somebody say to me how to do and it works fine.:
you have to replace
*Changeandroidboot_hardware=eeepc*
by
-if 32 bits: *androidboot.hardware=android_x86*

-if 64 bits :* androidboot.hardware=android_x86_64*

so you have to write (for me) android on sda 3 avec for name folder "android-5.1-rc1":
open custom 40 with
sudo gedit /etc/grub.d/40_custom

in "custom 40" i have written the italic text below:



[I]
#!/bin/sh
exectail -n +3 $0
#This file provides an easy way to add custom menu entries.  Simplytype the
#menu entries you want to add after this comment.  Be careful not tochange
#the 'exec tail' line above.

menuentry"Android x86" {
setroot='(hd0,3)'
linux/android-5.1-rc1/kernel quiet root/dev/ram0androidboot.hardware=android_x86
acpi_sleep=s3_bios,s3_mode SRC=/android-5.1-rc1/
initrd/android-5.1-rc1/initrd.img}
[/I]

then click on save .. and do not forget command line *sudo update-grub* at the end.  :)

---

### Post by bapoumba on 2016-06-07
@eponji : these forums are English only, except for the LoCo areas. Please post in English or use the French forums : [https://forum.ubuntu-fr.org/](https://forum.ubuntu-fr.org/), thanks.

---

### Post by eponji on 2016-06-07
hope english will understand me now.

---

### Post by bapoumba on 2016-06-08
Thanks for translating eponji :)

---

