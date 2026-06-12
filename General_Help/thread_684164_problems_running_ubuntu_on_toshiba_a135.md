---
title: "problems running ubuntu on toshiba a135"
date: 2008-01-31
forum: General Help
---

### Post by yezzir on 2008-01-31
hey guys. i switched over from windows XP after the millionth time i had to reformat and am now running dual OS (Vista/Ubuntu). I have been having lots of problems with Ubuntu and its been a huge turn off, especially since i cant fix it. ive come here in hopes that you guys can help me. here are some of the annoying problems im faced with...

Major Problems:

1. They keyboard seems to jump around when i type on forums or type something up on the internet. it randomly jumps to another line and starts typing there. its just really annoying. (it doesnt do this on vista, so hopefully its not the keyboard)

2. sometimes when i close my laptop lid and it goes on suspend, i come and open it up, but yet the screen stays black and it doesnt seem to be loading anything (i stare at the hd light, and it doesnt even turn on). i have to hold the power button to turn it off and turn it back on. i punched my last computer because it kept doing this on XP, definitely not good ....good thing i got the warranty though

Minor problems:

3. Sound. i had to set up the sound myself, because the sound wouldnt work. i searched it up in google, found some thread here, and the speakers work but my headphone jack still doesnt work. also the volume control swivel is really sensitive. it takes a huge chunk off when i twist it a little bit. this is minor, so im not really worried about it.

4. default network connection - for some reason it connects to the wrong network, so i have to manually change it. i know there is no fix for this yet, as i have searched endlessly, but i may have missed something

3 and 4 are not as annoying as 1 and 2. so if anyone can help me out, that would be great. i have a Toshiba Satellite A135-S4487. thanks for your time

---

### Post by orbish on 2008-01-31
I don't have a solution for any of your technical problems, but i'll say this much:

People here want to help you get everything working perfectly.  If you aren't having success with this thread, try creating a thread for each problem in the more specific forums.  If you aren't having luck here, try the IRC channel #ubuntu on irc.ubuntu.com.  People there are helpful too.

Once you get ubuntu up and running without the problems, you'll absolutely love it... try to keep your patience.

Here are some stab in the dark ideas if you want to google around:
1) keyboard setup is in the /etc/X11/xorg.conf. you can google your model with xorg.conf to see if you get any hits, compare the two configs.
2) power settings. acpi ubuntu (laptop model number) might show some good results
3) not sure, this would make a good thread topic
4) probably would make another thread about this.  specify if it's a wireless connection that's picking up the wrong network, or if it's choosing the wrong network adapter on your computer, etc etc...


good luck

---

### Post by yezzir on 2008-02-01
thanks for the reply.  i googled the first 2 and nothing really useful came up.

---

### Post by genodad on 2008-02-01
I'm a newbie myself, but I have a a135-s2276 and used this change to get the sound and headphones to work.

gksu gedit /etc/modprobe.d/alsa-base

at the end of the file type:
options snd-hda-intel position_fix=1 model=lenovo

I rebooted at this point.

Also you may need to use  System - Preferences - Sound
and change track to 'Front' to make thumbwheel work

As far as the keyboard, whenever that happens to me - its because I accidentally hit the touchpad.  I don't use suspend.  I changed the power management settings to blank screen when I close the lid

---

### Post by yezzir on 2008-02-01
thanks man..headphone jack works now...volume knob is still very sensitive, but i can definitely live with that.  

as for the keyboard deal, ill watch my hands and see if that is the problem.

blank screen can be a nice temporary solution, ill try that out until i find out what the problem is

---

### Post by ryanparrish on 2008-05-26
Thanks this got the volume wheel to work I just need to figure out how to enable root so I can change the file.

---

