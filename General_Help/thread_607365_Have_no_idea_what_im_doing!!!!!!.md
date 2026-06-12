---
title: "Have no idea what im doing!!!!!!"
date: 2007-11-08
forum: General Help
---

### Post by sent17inel on 2007-11-08
Okay. I upgraded to ubuntu gutsy gibbon and when i restart for a certain amount of time my screen tells me that the frequency is out of range. I went about reading random posts and the last thing i did was edit my xorg file and put mode into my screen:  section. and next to mode i put the resolution 1024x768 in quotes. I restarted and now when the login screen should come up i just get a little cursor in the top right hand corner and thats it. it just keeps blinking. Any ideas ppl?

---

### Post by BoneKracker on 2007-11-08
Edit your xorg.conf file again and undo what you did to break it.

If you can't figure it out, I believe there are instructions at the top of the file that tell you how to regenerate the default configuration for your machine.

You should be able to get to a terminal window by pressing Alt+F1.
From there you can log in and do what needs to be done (without starting X).

---

### Post by sent17inel on 2007-11-08
Ya... nope... i press alt + F1 and it doesnt give me anything... the cursor just keeps blinking......its like the little minus sign  -  and its blinking in the top left hand corner.... thats it... it just stays there.....

---

### Post by NT4usB on 2007-11-08
Restore your backup xorg.conf
What? you didn't back it up before you edited?
Then Ctrl+Alt+F1 and log into the terminal.
run```
sudo dpkg-reconfigure -phigh xserver-xorg
```restart gdm```
sudo /etc/init.d/gdm restart
``` How long did you wait for x to start when you got the out of range error?
iirc, there's a bug in Gutsy that the splash screen is out of range but soon as it gets past that in the boot process, the screen comes up.

---

### Post by sent17inel on 2007-11-08
ya... i didnt back up my xorg file.. i know its dumb and now im paying the price.. but ya also when i press ctrl alt F1 it doesnt do anything i still keep getting the cursor... and that bug u mentioned is exactly what was going on. that was what i was trying to fix and now i fear i wont even be able to back up all my files before restorring everything..... this sucks!!! anyone any ideas??? anyone?? i just pressed ctrl alt backspace and ctrl alt delete and my computer restarted so some commands are working... i dont know why it wont bring up the login screen or anything...

---

### Post by sent17inel on 2007-11-08
Hahahahahhahahhaha this is sooooo awesome!!! ok heres wuts going on!!! i guess ctrl alt F1 does bring me to the login prompt cuz i just logged in even though nothing displays and did a sudo power off and it worked!!! hahahahaha its like being blind!! but anyway can someone tell me what to do to replace my xorg file with one that was i think called xorg.bak.conf  i think... i think there was another backup in the same folder called xorg1.conf.... umm can someone check to verify if they have that same file? umm... so how would i go about replacing it? would i need to rename the xorg1.conf? plz and thank you.

---

### Post by sent17inel on 2007-11-08
thanks bonekracker!!! u rock!!! dpkg reconfigure and what not fixed it!! i had to do it all blindly since the cursor in the left hand corner was the only thing that was showing!! but luckily i knew when it would ask for my sudo password and what not and did everything from memory and the commands u told me to use and it all worked!!! umm so now the question is how to fix that bug u were talking about.... do u know how i could fix that?

---

### Post by sent17inel on 2007-11-08
my mistake i ment to give more credit to NT4usb... thanks dude!! u helped all kinds!!!

---

