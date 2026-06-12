---
title: "Ubuntu will not start"
date: 2013-02-15
forum: General Help
---

### Post by gorezerker on 2013-02-15
I am a bit of a beginner with Ubuntu and so I need some help.

I am running Ubuntu 12.04.2 and just installed Steam as well as the latest update (I ha  not updated in about a week) and now Ubuntu will not load the GUI. The COMPUTER starts and loads a select screen with Ubuntu, recovery mode, memory tests all that. When I select Ubuntu, the screen goes black and sits there. 

I have gone into recovery mode and run fsck, dpkg, all that have been suggested in other threads and startx fails.

I have googled to the best of my abilities and nothing has worked so far. At one point when I selected Ubuntu, it loaded the terminal and asked for login/password, but it has stopped doing that now. All help is appreciated, thank you for your time.

---

### Post by linuxsyst on 2013-02-15
Do you have your drivers installed correctly? 
type ```
mount -o rw,remount /
``` and then ```
jockey-text --list
```

**EDIT:** I've found older thread he had a same problem...
First do ```
mount -o rw,remount /
```
Theory 1: It is a problem with the login manager.

```
sudo dpkg-reconfigure lightdm
```
Theory 2: Need to tidy up packages

```
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get update
sudo apt-get upgrade
```
Theory 3: Remove timidity

```
sudo apt-get purge timidity
```

---

### Post by gorezerker on 2013-02-15
I was messing around with the video drivers recently to get Steam running. Last used the updated one. 

I typed in the first code ```
mount -o rw,remount /
``` and it came back with 'only root can do that'

---

### Post by linuxsyst on 2013-02-15
> **gorezerker said:**
> I was messing around with the video drivers recently to get Steam running. Last used the updated one. 

I typed in the first code ```
mount -o rw,remount /
``` and it came back with 'only root can do that'
Where did you type that in recovery mode?
Or in tty? 
go to the recovery mode and choose root option and write that command
or do sudo -s 
or run that command with sudo ```
sudo mount -o rw,remount /
```

---

### Post by kc1di on 2013-02-15
Type it like this 
```
sudo mount -o rw,remount /
```

---

### Post by grahammechanical on 2013-02-15
This might be a clue

> I was messing around with the video drivers recently to get Steam running. Last used the updated one. 

Try to use Recovery Mode Resume to get to a desktop and use Additional Drivers to activate another video driver.

Regards.

---

### Post by gorezerker on 2013-02-15
I was in try, went to recovery mode and typed it in root and nothing happened. A new command line popped up so I went ahead and the other commands, restarted, and now I am looking at a black screen with the blinking cursor. Nothing types.

Trying sudo, one moment sorry!

Edit: still did nothing

---

### Post by linuxsyst on 2013-02-15
> **grahammechanical said:**
> This might be a clue



Try to use Recovery Mode Resume to get to a desktop and use Additional Drivers to activate another video driver.

Regards.

Do you mean the Safe X Mode? It wont boot if he messed it up, I had some similar problem I installed wrong driver..

What do you have right now? are you in recorver mode? in root?

Type this command: ```
jockey-text --list
``` , what does it return?

---

### Post by gorezerker on 2013-02-15
Resume takes me to Ubuntu 12.04.2 LTS (computer name) try1 and asks for login information.

---

### Post by linuxsyst on 2013-02-15
yes login and write that command ```
jockey-text --list
```

---

### Post by gorezerker on 2013-02-15
> **linuxsyst said:**
> Do you mean the Safe X Mode? It wont boot if he messed it up, I had some similar problem I installed wrong driver..

What do you have right now? are you in recorver mode? in root?

Type this command: ```
jockey-text --list
``` , what does it return?

Typed in ROOT and got org.free desktop.dbus.error.filenotfound: failed to connect to socket /var/run/dbus/system_bus_socket: no such file or directory

---

### Post by linuxsyst on 2013-02-15
In terminal enter ```
ps -ejH
``` to see if the DBUS daemon is running.
Ok tell me please how did you install the drivers... what tutorial's did you use because it probably happened because of the drivers, what video card do you have and what drivers are currently installed.

---

### Post by gorezerker on 2013-02-15
Okay logged in, typed jockey-text and got a list of four different drivers. The nvidia accelerated graphics driver (post release updates) is enabled and in use. 

Sorry my responses are slow, posting from my kindle and typing + auto correct are crappy.

EDIT dbus daemon is on that list, 1228 1228 1228 next to it.

---

### Post by gorezerker on 2013-02-15
I installed the drivers when the computer was working. Just went to the additional drivers section and double clicked on the update driver. After the restart for the update is when it started going downhill.

---

### Post by linuxsyst on 2013-02-15
Good, if you did all the commands I posted before, tell me the drivers listed there and your graphic (video) card model. The only good thing you can do now is install the appropriate driver for your video card that works.
To check the video card type ```
fglrxinfo
```
or better ```
sudo lspci | grep -i vga
```

---

### Post by gorezerker on 2013-02-15
NVIDIA Corp GF119 GEFORCE GT 520 (card)

And I am going to apologize for this, but I am not typing out all the code on a tablet, battling constantly against the autocorrect, so here is a picture, sorry for the quality. 

[IMG]http://i.imgur.com/GhKMbjl.jpg[/IMG]

Once again, sorry and thank you so much for the help.

---

### Post by linuxsyst on 2013-02-15
That's better the screenshot ^ :) and just type this ```
sudo jockey-text -e xorg:nvidia_experimental_304
``` and let's hope it will work :X

btw. if one time in future you will have a problem [here]("http://www.androidauthority.com/how-to-disable-spelling-auto-correct-tool-on-kindle-fire-40527/") <3 Android :lol:

---

### Post by gorezerker on 2013-02-15
Entered it and it displayed: 
Searching for additional drivers...
And then command prompt popped back up... is that it? 

Also, is there a command to restart the computer? Hard resets feel so dirty...

---

### Post by linuxsyst on 2013-02-15
This ```
sudo reboot
``` 
don't know ...

---

### Post by gorezerker on 2013-02-15
Of course, reboot. The one version of restart I didn't try. 

SUCCESS! Thank you so much for your time and patience! Sorry I was so troublesome.

---

### Post by linuxsyst on 2013-02-15
No problem, happy it worked for you :)
Oh and mark the thread as solved please up right corner Thread Tools.

---

