---
title: "Is there a way to boot a disk from the root shell prompt?"
date: 2015-10-05
forum: General Help
---

### Post by sebastianfel on 2015-10-05
Hello, friends. I am not entirely new to ubuntu, though i just started experiencing issues which has forced me to get in deeper. Its not a bad thing, though i am very confused most of the time. Some of the language used by ubuntu users to try and explain a solution is like chinese to me (no offence to chinese people) 
My whole problem started when upgrading from ubuntu 11 to 12.04. I honestly have regretted doing this every day since. At first glance i was very happy. Ubuntu started up as usual, everything went fine up until the login screen. As usual i put in my password. And it brings me back to the login screen. I try again and again. Nope, so my first instinct is to restart my computer. Didnt work, now i'm thinking of solutions. Anything to make my computer work again. 
I google every solution possible using the login terminal, eventually i realized my silverlight was crashing, so once again i thought maybe someone knows a solution. Turns out people do. Just not for my particular problem because what i do is change my graphics to dsi or dmi dim maybe, sorry im running through this by memory. So now im thinking, sure thisll work! I downloaded it, and if something goes wrong ill just change it back to silverlight. It did not go my way. 
Now my computer starts up with a purple screen then loops a black screen with a blinking - 
Yes a blinking (-) this thing
Okay i say to myself, i still have grub to work with
Turns out grub doesnt let me change back to silver light because it's in read only mode. Changing it is out of the question for my computer. Something about not being able to find the mount - -all prompt. Ive burned a recovery tool on a disk, but it does not load automatically. Same old blinking -. 
Not sure if it's possible, but i would love to know if there is a command to run the disk. If not, is there a way to just completely reinstall ubuntu with the old disk image, before the upgrade? And all this needs to be done through grub (because thats the only thing working) I didnt have anything special on this computer. It was used mostly for gaming. So you can feel my pain when i say, ive been trying to fix it for the past 2 weeks with no success. 
If anyone could help me with any of the problems i stated or just the two solutions i cant quite figure out how to do, i would suck your.. Maybe just do it for the sense of helping another ubuntu user who will surely be greatful and in return will help other users with the knowledge he has been given through numerous hours of headachs and self harm.. Okay now this is getting out of hand.

---

### Post by yancek on 2015-10-05
Silverlight is just microsoft software to run certain types of video and isn't even being developed any longer although it is still in use.  I'm not sure why you think it has anything to do with your inability to boot.

The blinking cursor means a major problem with the Grub bootloader.  What recovery disk are you using?  If you want to run a bootable DVD/flash drive, you first need to enter the BIOS setup on boot and change the boot priority to boot from the DVD drive or the usb drive.  Are you seeing any message during boot?  You might be better off if you have another computer to use, downloading a version of Ubuntu 12.04 or 14.04 and burning it to a DVD or putting it on a flash drive and reinstalling.

---

### Post by sebastianfel on 2015-10-05
Oh, well. I actually thought it was a big part of starting up the computer.. I was using Boot-Repair-Disk, the 'must-have' rescue CD. How is one to enter the bios and change the Boot priority? I've only managed to get as far as putting the cd in and clicking boot ubuntu normally. Which didnt work,  i just got the blinking curser. 
I cant help but feel a little dumb, i wish you were my cousin so that i wouldnt feel like such a tool asking you, who in return are a very generous person to help me get through these issues ive been having. Thanks for caring

---

### Post by yancek on 2015-10-06
Is there any functioning operating system on the computer or is the failed Ubuntu all you have?
If you have the boot repair CD you should be able to get information from that if you can boot it and select the option to Create Bootinfo Summary.  In order to do that, you would have to enter the BIOS and change the boot priority.  There is no single way to do that.  I have an HP Desktop and need to use the F10 key to access BIOS.   On an Acer notebook it is the F2 key.  I've also seen the Delete key as an option as well as others.  

You need to put the CD in the drive and reboot the computer.  You might try shutting it down completely and booting.  You should see a manufacturer's logo and at the bottom of the screen you will generally see a message saying which key to use to enter BIOS or enter setup.  Some info on your hardware might give us an idea, for example is it an HP, Dell, Toshiba?  If you are cold booting and not seeing any options it could be a hardware failure.

---

### Post by sebastianfel on 2015-10-06
[IMG]<a href="http://tinypic.com?ref=2u77fkj" target="_blank"><img src="http://i62.tinypic.com/2u77fkj.jpg" border="0" alt="Image and video hosting by TinyPic"></a>[/IMG]

---

### Post by sebastianfel on 2015-10-06
Yes! I pressed f2 and sure enough there it was, switched the order to boot from disk. First i tried the boot repair utility, didnt work. Then i placed my good old ubuntu 11 in there and wuahla. Like magic, im installing a fresh ubuntu as we speak. 
 Thank you so much, i had no idea after installing ubuntu there'd be any trace of my old system. You've saved me a lot of time and i hope your post helps other people figure out what the heck is going on with there computer.

---

### Post by yancek on 2015-10-06
The problem you will have now is that using Ubuntu 11?, there is no longer any support for either 11.04 or 11.10 so you will not get any updates or be able to install new software in the standard manner.  I don't know what caused your problem after the upgrade.  I've upgraded Ubuntu twice and didn't have any problems but often a new install is a better option.  Having a separate partition for your personal data is a good idea as you can keep that.  If you do install a new system in the future, check the minimum hardware requirements on the Ubuntu site first and do an md5 checksum on the downloaded iso so you know that it is good.

---

