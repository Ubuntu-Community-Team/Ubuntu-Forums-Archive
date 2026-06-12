---
title: "Black screen at login, unable to use Ubuntu"
date: 2007-05-25
forum: General Help
---

### Post by Nehvrook on 2007-05-25
Hey there, my girlfriend recently installed Ubuntu 7.04 on her PC. She's duel booting this and Windows on two seperate hard drives.
Everything works perfectly untill she installs the Nvidia drivers. First time we did it through Desktop Effects (On my PC this automatically installed the drivers, I restarted and everything worked). When we did this we restarted, booted ubuntu, it went throught he Ubuntu loading screen then just sits at a black screen doing nothing.
After being unable to fix this we re-installed 7.04 and tried installing the nvidia drivers through the terminal with (sudo apt-get install nvidia-glx-new (I think that's right anyway)). Exactly the same problem, on restart it loads through the Ubuntu loading screen then sits at a black screen.
I've read a few people with similar problems but not quite the same. Can anyone give me any idea of what we can try to fix this?

---

### Post by dbott67 on 2007-05-25
It may be related to the refresh rate.

A few questions:

1. Can you open a terminal from the blank screen (press CTRL+ALT+F1)?
2. What kind of monitor does she have (make & model)?
3. What resolution are your trying to set (1024 x 768, etc.)?
4. Can you post the output of xorg.conf here?  Obviously, it may be difficult to get online from a text only interface, but you can re-direct her xorg.conf file to floppy/USB/whatever and then paste it up here:
a. make sure you're in her home directory:
```
cd ~
```
b. redirect the output of xorg.conf to a file:
```
cat /etc/X11/xorg.conf > xorg.conf.txt
```
c. copy the file to some removable media:
```
cp xorg.conf.txt /path/to/media/xorg.conf.txt
```
d. go to your working machine and paste it here.

-Dave

---

### Post by Nehvrook on 2007-05-25
Hi thanks for the reply.

1) No, that doesn't work. ctrl atl and backspace doesn't work either. It doesn't seem to be responding at all to the keyboard.
2) It's a Philips 170V 17" TFT. It's capable of up to 75hz and 1280x1024 resolution
3) It was running in 1280x768 resolution, I was expecting it to boot up in that again, not sure why it wouldn't. Though I was intending to change it to 1280x1024
4)Ach I can't get this to work. I've got my external hard drive plugged in and it usually goes to /mount/External 1 I think. But I can't seem to find it in the text based interface. (I tried with and without the external\ 1) and a number of different names/location wordings. I tried with a small memory pen too. Is there no way to open the text document in the console?

---

### Post by designwiz on 2007-07-27
looks like ive got a similiar problem... installed beryl and nvidia-glx drivers everything was working bliss til one fine day.. when ubuntu boots its shows loading.. followed by a black screen and the wait symbol!!
tried login into recovery mode and also ctrl+alt+f1 logged in from the terminal and typed metacity
came up with this error


> Windows manager warning:"" found in configuration database is not a valid value for keybinding "toggle_shaded"
Windows manager error:Unable to open X display

i believe you may the same response as our problem sound to be d same. I hope someone can help us both out. Any help would be appreciated. Thanks in advance. Regards Leo J.

---

