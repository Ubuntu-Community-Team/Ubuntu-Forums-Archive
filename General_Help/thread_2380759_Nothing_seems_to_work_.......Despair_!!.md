---
title: "Nothing seems to work .......Despair !!"
date: 2017-12-21
forum: General Help
---

### Post by steve7772 on 2017-12-21
My lap top is nearing "end of life" and I have parked it after 10 years of flawless ubuntu service. I have a new clean pc now but downloding the latest 16/17 something version of ubuntu ISO file has proved impossible by stick. Theres no "exe" file to install with.  It refused to be read and install, 
I have an original ubuntu disk ( 14.10) from Canonical, and although working fine , Firefox is out of date which other web sites remindme, and ebay does not load properly. Yahoo is telling me its missing plugins. I had hoped that ubuntu and Firefox would UPDATE automatically to the latest versions everything would be fine, Too simple ! Open a terminal and typing "Sudo apt" etc results in gibberish. I like Ubuntu but this would test the patience of a Vicar.

 If advising me, keep it simple

Steve

---

### Post by Frogs Hair on 2017-12-21
Hello and Welcome

> [COLOR=#000000]Theres no "exe" file to install with.[/COLOR] The windows installer has had no official support since 12.04 . Please post some information about the computer's hardware.

---

### Post by leunam12 on 2017-12-21
If you have a Windows PC download Rufus and burn the ISO file to a blank USB stick.
If you are on Ubuntu you may download Etcher to burn the ISO to the USB drive, 
another option is Unetbootin. Once you have your bootable USB drive you have to boot
from it, you have to invoke the temporary boot menu at boot time or change your BIOS 
to boot from USB stick as the first option. Then you will be able to install. 

If you are dual-booting there are other things to take into consideration, if that is the case, please post
what operating system are you going to dual-boot with.

---

### Post by steve7772 on 2017-12-21
I am not dual booting. I have loaded 14.10 from an official CD that does upgrade and update!

Sorry ! Does not upgrade or update

---

### Post by speartip on 2017-12-21
> **steve7772 said:**
> Sorry ! Does not upgrade or update
It won't 14.10 is way past end of life. You need 16.04LTS or 17.10.

---

### Post by yancek on 2017-12-21
If your previous install of Ubuntu used and .exe windows file, then you were using WUBI (Windows UBuntu Installer) which installed Ubuntu inside your windows operating system as a program.  As pointed out above, wubi is no longer supported and will not be in the future.  If you have some windows OS on the new computer and want to run Ubuntu inside windows you can download and install virtual software and install Ubuntu that way.  Even if wubi were supported, it is not expected to work with windows 8 or 10.  Do you have either installed on the new computer.

Do you have an operating system on the new computer?

Ubuntu releases in October are short term support, approximately 9 months so that ended July, 2015.

If you have another OS, you can download an Ubuntu iso and then put it on a flash drive or DVD, boot it and install it.

>  had hoped that ubuntu and Firefox would UPDATE automatically to the latest versions everything would be fine]

Yes, that would happen with a supported version but it won't work now with 14.10 because all the software in the repositories have been moved.

> Open a terminal and typing "Sudo apt" etc results in gibberis

Terminal commands on all Linux system are case-sensitive so using "Sudo" is meaningless but using "sudo" is not.  Even sudo apt would not do anything, you would have to tell it what to do, i.e.  sudo apt install someprogram for example.

---

### Post by steve7772 on 2017-12-22
Can we try something else please!!

 I have 14,10 on my machine that wont upgrade or update because it is end of life, I am told. 

How do i get to the current version of ubuntu - 16.04 or 17.10 and Firefox on to my machine. I have downloaded those versions (ISO)  from the Canonical website to a stick and tried to boot using F12 - Nothing!.....  Duh . And which version do you advise I use and how do I do it? Please guys, I just want a "plug and play" solution, simple as!

---

### Post by vasa1 on 2017-12-22
> **steve7772 said:**
> My lap top is nearing "end of life" and I have parked it after 10 years of flawless ubuntu service. I have a new clean pc now but downloding the latest 16/17 something version of ubuntu ISO file has proved impossible by stick. Theres no "exe" file to install with.  It refused to be read and install, 
I have an original ubuntu disk ( 14.10) from Canonical, and although working fine , Firefox is out of date which other web sites remindme, and ebay does not load properly. Yahoo is telling me its missing plugins. I had hoped that ubuntu and Firefox would UPDATE automatically to the latest versions everything would be fine, Too simple ! Open a terminal and typing "Sudo apt" etc results in gibberish. I like Ubuntu but this would test the patience of a Vicar.

 If advising me, keep it simple

Steve
1: Stay with Ubuntu 16.04 LTS
2: After downloading the iso, you need to use it to create a Live USB stick. Just copying the iso to a usb stick won't help.
3. Read leunam12's post.

---

### Post by leunam12 on 2017-12-22
> **steve7772 said:**
> Can we try something else please!!

 I have 14,10 on my machine that wont upgrade or update because it is end of life, I am told. 

How do i get to the current version of ubuntu - 16.04 or 17.10 and Firefox on to my machine. I have downloaded those versions (ISO)  from the Canonical website to a stick and tried to boot using F12 - Nothing!.....  Duh . And which version do you advise I use and how do I do it? Please guys, I just want a "plug and play" solution, simple as!
If you are on Windows you have to download Rufus ([https://rufus.akeo.ie](https://rufus.akeo.ie)) and burn the ISO to a USB drive, 
if you simply copy the ISO file to the USB drive you will not be able to boot.
If you are on Ubuntu you need to download Etcher ([https://etcher.io](https://etcher.io)) and burn the ISO to USB.
If you do that and still are unable to boot, then you probably have to go to your BIOS settings and
make sure that booting from USB is enabled, also disable fast boot and secure boot. It depends on your
hardware, so please provide some information about your new computer.

---

### Post by speartip on 2017-12-22
As alternatives to Etcher you could use usb-creator-gtk or unetbootin.
Both are in Ubuntu's repositories.
See here for detailed instructions on how to proceed.
[https://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](https://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/)

---

### Post by leunam12 on 2017-12-22
> **speartip said:**
> As alternatives to Etcher you could use usb-creator-gtk or unetbootin.
Both are in Ubuntu's repositories.
See here for detailed instructions on how to proceed.
[https://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](https://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/)
Does he have access to the repositories on 14.10?

---

### Post by steve7772 on 2017-12-23
I have finally burnt the Iso to 16,04 to a CD, rebooted, pressed F12 and chosen CD to boot fromand put the CD in. That took two days making Brasio work.
For hours all I got was the Unbuntu logo on a purple screen. Pressing escape shows of pages of line code with I/o errrors !!! 

For a week now I have been trying to make this rubbish work. Thats in the bin, and unless some can highlight where I can buy a WORKING  LTS 16.04, I'm off to PC World to buy Windows 10.and PC Unless someone lives near Coventry that is...........................

Not worth all the pain and frustration

---

### Post by leunam12 on 2017-12-23
Have you tried booting with nomodeset or acpi=off parameters to see if that makes a difference? try the instructions on the link below.

[https://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](https://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

Some observations: The Ubuntu ISO does not fit on CD, I imagine you mean DVD.
There is no magic way to make things work, instead of trying something for hour and hours, take a picture of the 
error message that you are getting and post it here; it is impossible to help without information. If your errors are caused by
hardware problems, buying windows is not going to make any difference. Post your hardware information, the specific
error messages that you are getting, and also at what point in the process are you getting those errors. But try the different boot parameters first.

---

### Post by Frogs Hair on 2017-12-23
The old versions of Ubuntu would have fit on cd , but DVD has been the standard for some time now.

---

