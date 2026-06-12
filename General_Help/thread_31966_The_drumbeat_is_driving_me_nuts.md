---
title: "The drumbeat is driving me nuts"
date: 2005-05-05
forum: General Help
---

### Post by Efwis on 2005-05-05
I don't know if its an event sound or not, but when I am on Ubuntu, I keep hearing this drumbeat sound file, i have looked in the sound events but I have no idea which one it might be, I tried disabling everyone in succession to find it, but to no avial. 

i would like to hear something besides that drumbeat. any ideas would be great.

---

### Post by bored2k on 2005-05-05
Upper panel > system > preferences > sound > disable sound server

---

### Post by Efwis on 2005-05-05
[QUOTE=bored2k]Upper panel > system > preferences > sound > disable sound server[/QUOTE]
Just tried that, and rebooted, didnt' help

---

### Post by ganatronic on 2005-05-05
Then just remove the offending ones individually. Sound Preferences - Sound Events. There's a list. Is "question dialogue" under "system events" the one that bugs you?

---

### Post by Efwis on 2005-05-05
all sound files are disabled and the events are also individually removed for good measure, still doing it. i even rebooted 2 times to make sure.

Edit: forgot to mention that the only way I can have the peace and quiet of the thing is by muting the PCM slider bars under applications>sound & Video>Volume control

---

### Post by neighborlee on 2005-05-05
[QUOTE=Efwis]all sound files are disabled and the events are also individually removed for good measure, still doing it. i even rebooted 2 times to make sure.

Edit: forgot to mention that the only way I can have the peace and quiet of the thing is by muting the PCM slider bars under applications>sound & Video>Volume control[/QUOTE]
--------
the gents are right you know ;)..its an event that is triggering and can be toggled off in sound events where they mentioned..i'd guess its the one under : system events : question dialog.

cheers
neighborlee

---

### Post by Efwis on 2005-05-05
well, I have narrowed it down somewhat doing a little troubleshooting of my own. upon doing as suggested above, i was able to narrow down the fact that the "drumbeat" wav file is not a triggered event in the sound events panel.

I'm able to discern this because the sound file starts playing just befor showing the initial logon screen. this leads me to believe that something somewhere has gotten scewed up in the startup process. 

Any Help would be appreciated

---

### Post by Efwis on 2005-05-06
ok, as of this point I have reinstalled ubuntu 3 times, and everytime its the same thing. so let me ask this. 

How can I delete the wav file so I don't have to hear it? I know where it is, but everytime I go to delete it, either I get a "permission denied" message, or in root terminal I get "file not found" message. 

any help would be appreciated.

---

### Post by swj on 2005-05-06
If you are still having problems finding the 'setting' thats turns off the drumbeat-look in Computer -> System Configuration -> Login Screen Setup -> (graphical greater?)

-In any case its in the login screen setup-

I am currently at work on Windows boxes and not at my Ubuntu box...but there is a check box to turn off login (GDM) sounds, which is the drum beat.

* I disable all system beeps, bloops and beats (very annoying)

---

### Post by Efwis on 2005-05-06
[QUOTE=swj]If you are still having problems finding the 'setting' thats turns off the drumbeat-look in Computer -> System Configuration -> Login Screen Setup -> (graphical greater?)

-In any case its in the login screen setup-

I am currently at work on Windows boxes and not at my Ubuntu box...but there is a check box to turn off login (GDM) sounds, which is the drum beat.

* I disable all system beeps, bloops and beats (very annoying)[/QUOTE]
 I found that too, but when I disable that setting I can no longer sign in to the system to use it, It doesn't even give the sign in box for username and password

---

### Post by Efwis on 2005-05-06
[QUOTE=Efwis]I found that too, but when I disable that setting I can no longer sign in to the system to use it, It doesn't even give the sign in box for username and password[/QUOTE]
 update, got it taken care of. 

this is what I had to do, system> Admin>login screen setup>disabled the check mark, but had to enable accessibility modules. Also you have to make sure all event sound triggers are turned off. so now to access the login screen setup I have to enter my password which is fine, I don't mess in there anyway

---

### Post by Efwis on 2005-06-04
alright, now I have a stable distro and no sound, which is a bummer, my wife and kids love playing frozen bubble, but because of the sound issue. at least as far as I can tell, it freezes up. I then have to switch over to another workspace to run it and be able to play, without sound.

It also sucks because I can't play any MP3's or listen to the online radio when I am working on my website designing.

so my question is this, 

How can I go about fixing this issue so that I can have my sounds back? Do I have to recompile the kernal, or what?

I like this distro and it seems I'm the only one that has had this problem from searching around on the board. Here is the info I have in regards to my sound card, yes I know its lame, but I don't have the money to put out for a new sound card just to work around this issue.

its an onboard sound card
 VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)

it works with the distro, but it gets stuck on the graphical greeter/sound events area in the login screen in a continuous loop. If i just remove the check from the graphical greeter, system freezes, if I remove both graphical greeter and sound events, I have no sound, which, IMO, is not fun.

---

### Post by Mustard on 2006-04-27
It's probably a bit late to post a possible workaround for this, but I added irqpoll to the kernel options in grub and it allows me to get to gdm without the looping drumbeat problem.  I suspect its an IRQ allocation problem.  I haven't completely worked it out yet.

---

### Post by Efwis on 2006-04-27
not sure what it was, I have since had to install a new motheboard and haven't had the problem since. and I'm still using the viatech onboard sound card, however this board uses the Realtec engine rather then the Via one. so it is something in regards to the via drivers.

---

