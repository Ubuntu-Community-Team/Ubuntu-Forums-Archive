---
title: "Instaling Windows XP after ubuntu is installed"
date: 2012-12-25
forum: General Help
---

### Post by ironcomics on 2012-12-25
Hello, Is there anyway I can install Windows XP on my ubuntu laptop so that it can dual boot (So I can choose which operation system i want on system boot) I know people usually install windows first but i cant do that because i dont have access to a usb and my laptop has no cd slot. So is there a way to create a second partition or something and then download a windows XP iso on to that partition so then i can dual boot on my laptop. I dont want to use Wine, Or Virtual box they are very slow :(
Thanks, I dont have usb or cd :L

im using ubuntu 12.04 lts and i want windows xp :(

---

### Post by snowpine on 2012-12-25
Yes, of course... we have an entire article in the Wiki on this topic:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by ironcomics on 2012-12-25
Thanks but the problem with that is i have to install windows first and (I have m windows 7 and xp cd) But i have no cd slot on my laptop. On my laptopvit only has ubuntu and so i need to do it the other way round (Installing windows after Ubuntu) So im gonna try summin never done before. I will create a new partition with an windows program (Which will be opened using wine) And use easy bcd for windows (Using wine). I will be following this tutorial and fulfilling all its tasks using wine :)

[http://www.youtube.com/watch?v=PmdjcxnBfQQ](http://www.youtube.com/watch?v=PmdjcxnBfQQ)

Do you think it will work????

---

### Post by Cheesemill on 2012-12-25
That tutorial wont work in your situation. First of all none of the required applications will work using Wine, and second you can't install XP using this method, it's only for Windows 7.

To install XP you will either need a USB stick or an external CD drive.

Depending on what you are going to be using Windows for another option might be to install it in a VM.

---

### Post by ironcomics on 2012-12-25
But... but.. I believe!!! I BELIEVE I CAN DO IT!!!! Thomas Edison failed 2000 times before he made the light bolb but that was because he didn't believe!! I will fail 0 times!! I WILL DO THIS!!! YESS!!! :D

---

### Post by MishaX2 on 2012-12-25
How did you install ubuntu on this machine?

---

### Post by ironcomics on 2012-12-26
It had an empty hard drive, So i popped in the usb and installed ubuntu. I dont have a usb anymore though

---

### Post by hawthornso23 on 2012-12-26
The USB connector fell off? Or did you just lose your thumb drive. 

If the former then I am in awe that the machine still runs as serious violence must have been done to it. If the latter then why not just buy another thumb drive - they are not expensive.

---

### Post by ironcomics on 2012-12-26
The program Power ISO worked, But now im going to create a new partition using ubuntu and then hopefully i can do the easy bcd stuff on wine

---

### Post by Cheesemill on 2012-12-26
As I mentioned above EasyBCD ***will not work*** with Wine. To start with it doesn't have direct access to the drive, and second it is used for adding entries to an existing Windows bootloader ***which you don't have as Windows isn't installed***, thirdly you won't be able to browse to the .wim file from your extracted .iso as XP didn't use .wim files, these were introduced with Vista.

The tutorial you linked to will only work for setting up a Windows installation drive from Windows.

I know your going to keep trying anyway but don't waste your time, it really isn't going to work.


Another thing to think about is even if you do somehow install XP it will overwrite the Ubuntu bootloader, meaning you wont be able to boot Ubuntu again until you've fixed grub for which you will need a CD or USB drive.

---

### Post by Rebelli0us on 2012-12-26
You could temporarily disconnect the Linux disk so that XP doesn't mess with the boot loader. If it's all on the same disk, then it's more work:popcorn:

---

