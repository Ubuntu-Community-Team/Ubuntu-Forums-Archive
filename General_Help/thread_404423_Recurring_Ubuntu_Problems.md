---
title: "Recurring Ubuntu Problems"
date: 2007-04-08
forum: General Help
---

### Post by Mr_Mischif on 2007-04-08
OK, first off, I have been using Ubuntu for a while, but I've been having some problems that made me switch to Fedora for a while, but after too many high-temp shutdowns, I'm back. But now I remember the problems that made me move away in the first place; and hopefully I'll be able to get some support now.

First off, java seems to want to be a little punk, since every app I try to open that uses Java seems to fail.

Second, sometimes when I boot I get the message > [17179574.208000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[17179574.208000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[17179574.208000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
Cannot kill pid '1811': no such process and the boot hangs there, and I have to CAD to restart it. If it makes any difference, I'm using the ReiserFS system.

Third, I'm on a HP Pavilion DV4000, and when I press the Wireless button, a light should come on, and it worked on openSUSE, but not on Ubuntu and Fedora.

Fourth is more of a question than a problem though. Is it possible it link the volume output of the headphones to the main volume output instead of having to adjust them seperately?

Well, that's all I can think of right now, but if anything else comes up, I'll be sure to add to this thread.

EDIT: I just thought of something else: is it possible to disable the disk cache on USB drives so you don't have to manually unmount them? I know that it's been asked many times before, but I've never seen a definitive answer.

EDITx2: I seem to be having a problem with wine: I can open a locknote document, but I can never add anything to it, does anyone else have the same problem?

EDITx3: God why didn't these things come up when I first wrote this? How do you hide folders? I would think chmod +h would work, but you know, Murphy's Law and all that.

---

### Post by ihavenoname on 2007-04-08
> **Mr_Mischif said:**
> 

First off, java seems to want to be a little punk, since every app I try to open that uses Java seems to fail.

Do you have sun-java installed? If so which version? Also try opening in the application from a terminal so we can see what the error is.



> **Mr_Mischif said:**
> 
Second, sometimes when I boot I get the message  and the boot hangs there, and I have to CAD to restart it. If it makes any difference, I'm using the ReiserFS system.

There is a bug filed about this here
[https://launchpad.net/ubuntu/+source/xorg/+bug/54294](https://launchpad.net/ubuntu/+source/xorg/+bug/54294) you should follow the progress there.

> **Mr_Mischif said:**
> 
Third, I'm on a HP Pavilion DV4000, and when I press the Wireless button, a light should come on, and it worked on openSUSE, but not on Ubuntu and Fedora.

What card is it? Does the card work on Ubuntu/Fedora at all? (Is it just the light that does not work?)

> **Mr_Mischif said:**
> 
Fourth is more of a question than a problem though. Is it possible it link the volume output of the headphones to the main volume output instead of having to adjust them seperately?

This is interesting, I would like to do something similar. Maybe if no such thing exists then I/We can make a script that does this. (Are you on gnome or kde?)

---

### Post by KyleCardoza on 2007-04-08
I can help you with the hiding thing, if you're using Gnome: create a plain text file in the same directory as the files you want to hide, called ".hidden" (the dot at the beginning is important!), and put a newline-separated list of the files you wish to hide in it.

---

### Post by ihavenoname on 2007-04-08
> **Mr_Mischif said:**
> 

EDITx3: God why didn't these things come up when I first wrote this? How do you hide folders? I would think chmod +h would work, but you know, Murphy's Law and all that.

put a . infront of them. For example if you want to hide a folder name hey then you would change the name to .hey. From the terminal that is ```
mv hey .hey 
``` from the gui you just right click. and add a . infront of the file name. Make sure to change the path to anything that needs that file. There maybe a better way but I don't know of it.

---

### Post by ihavenoname on 2007-04-08
> **KyleCardoza said:**
> I can help you with the hiding thing, if you're using Gnome: create a plain text file in the same directory as the files you want to hide, called ".hidden" (the dot at the beginning is important!), and put a newline-separated list of the files you wish to hide in it.

you beat me to it!  and with a more elegant approach, kudos to you.

---

### Post by Mr_Mischif on 2007-04-08
> **ihavenoname said:**
> Do you have sun-java installed? If so which version? Also try opening in the application from a terminal so we can see what the error is.

Actuall, I'd been using the j2re, but I'll try it.

> **ihavenoname said:**
> What card is it? Does the card work on Ubuntu/Fedora at all? (Is it just the light that does not work?)

The Card itself works fine, it's just that the light isn't working

> **ihavenoname said:**
> This is interesting, I would like to do something similar. Maybe if no such thing exists then I/We can make a script that does this. (Are you on gnome or kde?)

I'm running Gnome.

---

### Post by ihavenoname on 2007-04-08
> **Mr_Mischif said:**
> Actuall, I'd been using the j2re, but I'll try it.
if you have backports enabled on edgy then it's 
sudo aptitude install sun-java6-plugin sun-java6-jre sun-java6-bin
At least that's what I do. What applications are you trying to run?


> **Mr_Mischif said:**
> 
The Card itself works fine, it's just that the light isn't working

Count yourself lucky :). What type of card is it? It could be that opensuse patched something. We could get the source rpm for that driver apply  the same patches, make a deb and test it for Ubuntu. Or you could file a bug report. 


> **Mr_Mischif said:**
> 
I'm running Gnome.
OK, if I get time, I'll try and work on something. (You should too). I wonder if there is a command for increasing the volume? Does anyone know?

Edit: Ah, amixer set "device" "% of volume" example
```
 amixer set Master 40%  
```
So all that is needed is to make a script that sets the Master and the "other" device to the same volume level, or  at least increases the volumes at the same time.

---

### Post by Mr_Mischif on 2007-04-08
OK, now I was trying to load Azureus, but every time I try, I get this error:
> #
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb0598d02, pid=13618, tid=3085158064
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0x8d02]
#
# An error report file with more information is saved as hs_err_pid13618.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)


Like I said, I think Java is messing up.

---

### Post by Mr_Mischif on 2007-04-08
> **ihavenoname said:**
> Count yourself lucky :). What type of card is it? It could be that opensuse patched something. We could get the source rpm for that driver apply  the same patches, make a deb and test it for Ubuntu. Or you could file a bug report. 

It's an ipw2200.

---

### Post by ihavenoname on 2007-04-08
> **Mr_Mischif said:**
> OK, now I was trying to load Azureus, but every time I try, I get this error:

Like I said, I think Java is messing up.

post the output of 

```
 sudo update-alternatives  --config  java  
```

---

### Post by Mr_Mischif on 2007-04-08
> **ihavenoname said:**
> post the output of 

```
 sudo update-alternatives  --config  java  
```

```
There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*+        2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 

```

When I choose 2, it says
```
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java' to provide `java'.
```

Then takes me back to the prompt.

---

### Post by ihavenoname on 2007-04-08
ok that's good. And when you start azureus it still says the same thing? Try using synaptic. Search for azurues right click it and choose remove completely. Then hit apply. Once it is removed. Reinstall it with synaptic. And test it again.

Edit: nvm that. I just got azureus and tested it and got the same results. Run sudo update-alternatives --config java again and this time choose 1 or 3(though it seems you don't have the gcj java installed.

To install the gcj-java type sudo apt-get install java-gcj-compat 
That should get it for you.


 The azureus that I installed was titled azureus-gcj in the repo. Maybe that is the same for you. Where did you get yours? If it was the *-gcj one then it will not run on sun-java.

---

### Post by ihavenoname on 2007-04-08
> **ihavenoname said:**
> ok that's good. And when you start azureus it still says the same thing? Try using synaptic. Search for azurues right click it and choose remove completely. Then hit apply. Once it is removed. Reinstall it with synaptic. And test it again.

Edit: nvm that. I just got azureus and tested it and got the same results. Run sudo update-alternatives --config java again and this time choose 1 or 3(though it seems you don't have the gcj java installed.

To install the gcj-java type sudo apt-get install java-gcj-compat 
That should get it for you.


 The azureus that I installed was titled azureus-gcj in the repo. Maybe that is the same for you. Where did you get yours? If it was the *-gcj one then it will not run on sun-java.
ok look here [https://launchpad.net/ubuntu/+source/azureus/+bug/57875](https://launchpad.net/ubuntu/+source/azureus/+bug/57875)
the bug is common. There are several workarounds.

---

### Post by ihavenoname on 2007-04-08
about the changing both volumes at the same time issue. I made a cli script that can do that for you. In the future I will make it so that you can bind the script to a short cut and have it work that way. 
This is attached. Just cd into the directory where you place it and chmod +x vol-app and then sh vol-app. Type  the percentage you want to set the volume to and it will do it for both the Master and the Headphones. (Which I assumed are called Phone in alsamixer, I don't know if I have a headphone jack on my computer). Test it and tell me if it works. If it does I'll see if I can make it work incrementally.

Edit: now it's attached. Just unzip and try it out.

---

### Post by ihavenoname on 2007-04-09
Ok, heres a better version of the script. This will add 5% volume to both Master and Phone everytime you click/run the vol-up script. (From the terminal you sh vol-up in the directory where you extract the script. vol-down will lower the volume 5%. And vol-set-equal will set the volumes for your Phone and Master to 10% (you should run this first and then use the other scripts to increase to the desired level. You can use gconf-editor to bind your volume keys to these two scripts so that you can just push to set the volumes. > Go to tty1 (ctrl+alt+f1), login and  and type showkey -s. Then press the volume up key. Wright down the last group of numbers/letters. Then press the volume down key and write down the last group of numbers/letters. The go back to the desktop (ctrl+alt+f7, though it might be an f# after 7) type alt+f2 and type gconf-editor. From there I think the key bindings can be set at apps-->metacity. If you need help there feel free to ask.



---

### Post by Iowa Dave on 2007-04-09
In the vol-set-equal script is there a typo? Says "umute", should be "unmute"?

---

### Post by watstein on 2007-04-21
For the wireless light I found a fix for that months ago.
Go to the terminal and type.

sudo modprobe -r ipw2200
sudo modprobe ipw2200 led=1

If that works then
sudo echo "options ipw2200 led=1" > /etc/modprobe.d/ipw2200

That is all, very easy fix.

---

### Post by ihavenoname on 2007-04-21
> **Iowa Dave said:**
> In the vol-set-equal script is there a typo? Says "umute", should be "unmute"?
yes I think it is a typo.

---

