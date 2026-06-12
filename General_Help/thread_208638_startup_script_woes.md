---
title: "startup script woes"
date: 2006-07-03
forum: General Help
---

### Post by shanet on 2006-07-03
Hello! I was wondering if I could ask for assistance in what I'm sure is an obvious semi-newbie problem. I'm running Xubuntu 6.06 on an old PII at home, which is running  apache and php just fine. What I want is for **webcam** to run at startup. Normally I have to ssh into the Xubuntu box and do

sudo webcam /etc/webcam.conf

followed obviously by entering my password and away I go. webcam makes JPGs and puts them in /var/www. the only thing is that when I run webcam like this it takes over the terminal (for want of a better word, such that I see the prompts from webcam until I press control-c and it returns to the prompt. like running gedit from a terminal, say. I'm sure there's a better word)

I had a lot of trouble understanding how to make startup scripts, so I followed the guide at [http://www.fperkins.com/HowToCreateaStartupScriptinDebian.html](http://www.fperkins.com/HowToCreateaStartupScriptinDebian.html)
and made a new startup script "webcam" which simply contained

webcam /etc/webcam.conf

and then I did update-rc.d webcam defaults 20

and rebooted the machine

however, when I rebooted the machine the webserver appeared not to be running. I have no display attached to it, so I ssh'd in again and ran "top", and saw that webcam was running okay but saw no references to apache2. I presume that somehow the webcam script stopped apache2 from running. Could this be because webcam is not running in the background...? I tried putting & at the end of the line referring to webcam in the "webcam" script in /etc/init.d/ but that didn't work. also, I notice that if I try to sudo anything with an & at the end it will get a bit screwy and tell me the process has stopped. So I am at a loss - how can I do 

webcam /etc/webcam.conf

at bootup without stopping apache2 (and possibly other things, although vsftpd and sshd run fine) from running? It's definitely the case, because when I commented out the webcam line apache and everything else started fine. Thanks!

---

### Post by shanet on 2006-07-04
my /etc/init.d/webcam just contains the line
"webcam /etc/webcam.conf"

(should this be sudo? but won't that prompt for a password?)

and the usual output of 

sudo webcam /etc/webcam.conf

is 

"
reading config file: /etc/webcam.conf
video4linux webcam v1.5 - (c) 1998-2002 Gerd Knorr
grabber config:
  size 320x240 [24 bit TrueColor (LE: bgr)]
  input (null), norm pal, jpeg quality 100
  rotate=0, top=0, left=0, bottom=240, right=320
write config [ftp]:
  local transfer /var/www/imageup.jpg => /var/www/webcam.jpg
"

and the prompt does not return until I press control-C (or open a new terminal)

alternatively, is there a way I can schedule webcam to be run after apache2, such that apache2 starts as well? I have searched for answers everywhere, but I just can't understand how these startup scripts work

---

### Post by kb2wdi on 2006-07-04
[QUOTE=shanet]my /etc/init.d/webcam just contains the line
"webcam /etc/webcam.conf"

[B]Try "/full/path/to/webcam /etc/webcam.conf &" to fork into the background.
Just add the line to "/etc/rc.local". It may be executing too early in the startup process. This also gets executed after Apache[/B]

(should this be sudo? but won't that prompt for a password?)

[B]No, startup scripts executed by the root account
[/B]
and the usual output of 

sudo webcam /etc/webcam.conf

is 

"
reading config file: /etc/webcam.conf
video4linux webcam v1.5 - (c) 1998-2002 Gerd Knorr
grabber config:
  size 320x240 [24 bit TrueColor (LE: bgr)]
  input (null), norm pal, jpeg quality 100
  rotate=0, top=0, left=0, bottom=240, right=320
write config [ftp]:
  local transfer /var/www/imageup.jpg => /var/www/webcam.jpg
"

and the prompt does not return until I press control-C (or open a new terminal)

**Try "Ctrl-Z, then type BG" or, add a " &" to the end of the command line to fork into the background.**

alternatively, is there a way I can schedule webcam to be run after apache2, such that apache2 starts as well? I have searched for answers everywhere, but I just can't understand how these startup scripts work

[/QUOTE]

**I hope this helps.**..

---

### Post by shanet on 2006-07-04
behold, it works! thanks very much. bizarrely, webcam doesn't need to be run as root anymore even in a normal terminal (it definitely did before, despite what I've read elsewhere) I can't imagine what changed to make that the case. but that doesn't matter, it works! thank you.

---

### Post by kb2wdi on 2006-07-04
I am glad I could help.

---

