---
title: "How do you re-initialize your sound card?"
date: 2005-10-15
forum: General Help
---

### Post by Zad_ok on 2005-10-15
After restore from hibernation, my Ensoniq Sound Blaster compatible sound card refuses to work. I've tried re-starting ALSA, but that makes no difference. Is there any way of waking it up again? I think the hardware needs to be re-initialized or something.

---

### Post by Riot5 on 2005-11-08
I'm having the same problem; I hibernated my computer, then when I powered it back up, my sound was no longer working.  I have a Sound Blaster Audigy 2 ZS, if that helps.

---

### Post by Dr. Nick on 2005-11-08
Yeah I have the same problem with my wireless. Its an easy fix but i cant tell you the exact command to use.

It will be ```
sudo modprobe *Module*
```

What you will need to do to get the module name to use is; restart fresh, and before hibernation type lsmod in a terminal and look for your soundcard and see what module it uses.

I have always know the name of the module to reload so I am not sure the easiest way to get the module name that you dont know.

I think that will work and hopefully get you both started. I dont know of a way to make it reload auomatically though. Hopefully someone knows how to, as I could benefit aswell

Let me know what you find

---

### Post by Riot5 on 2005-11-08
It doesn't work for me, it won't even show me anything when i click on hibernate, it just shuts down without outputting anything.

---

### Post by Dr. Nick on 2005-11-09
oops, forget about hibernation for a second, I misworded that.

Just do a full resart so your sound works than run lsmod in a terminal and save the result in a text file. You can just copy/paste to a new file and save it.

Then hibernate and resume so your sound doesnt work, then re run lsmod like before and paste to another text file and compare them.

If my thoughts are correct their will be a line or two missing from the second. Thats what you need to use modprobe on. If you find the missing line post it here or just label and post both outputs for others to see and I may be able to give you a specific command.

Does anyone know how to get the current module in use for sound as to save the above trouble?

---

### Post by Riot5 on 2005-11-09
My sound still doesn't work, even after a full restart :(

---

### Post by Dr. Nick on 2005-11-09
just taking a guess based on what ive seen online but type this into a terminal
sudo modprobe snd-emu10k1

---

### Post by Riot5 on 2005-11-09
Still nothing.  Is there anything I can post that will help?

---

### Post by Dr. Nick on 2005-11-09
Hmm

Has it ever worked? It sounds like it has by your first post

You can post lsmod output which may help some, but look at this link which may help more as it sounds very similar and worked for a few people.

[http://www.linuxquestions.org/questions/archive/63/2005/07/4/337513](http://www.linuxquestions.org/questions/archive/63/2005/07/4/337513)

---

### Post by Winge on 2005-11-09
I have the same problem as the original poster: After a fresh reboot, my sound card works perfectly, but after I have hibernated the computer and resumed, I get no sound. I have also tried to restart ALSA (to the best of my knowledge), without success.

The command lsmod gives the same result before and after hibernation.

I have a SB Live 5.1.

---

### Post by Riot5 on 2005-11-09
Thank you, thank you, thank you, thank you, thank you!  The LinuxQuestions guide worked perfectly :D Time to listen to some Gorillaz

---

### Post by Dr. Nick on 2005-11-09
Glad you got it Riot5

@Winge - Did you try the linuxguide aswell, It sorta a similar soundcard. Not sure if it applies to the Live cards aswell,

Unfortunately I dont have either of them cards , just onboard and havent had any trouble, You say lsmod lists your sound devices after resume from hibernate but it still doesnt work. The lsmods will be very similar so if you havent you may have to do a line by line look at before and after.

I found a nice link for alsa but its based heavily on gentoo. I will pull the relevant data and post below

Full Read - Alot is not applicable 
[http://www.gentoo.org/doc/en/alsa-guide.xml](http://www.gentoo.org/doc/en/alsa-guide.xml)


------------------------------------------------------------------
To restart alsa correctly 
sudo /etc/init.d/alsa-utils restart

To correctly identify your card
lspci -v | grep -i audio

then if you need to find the module name go 

[http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) 
Their you can get the module name, It seems yours is emu10k1
so you could try sudo modprobe emu10k1 to load it.


I posted alot of info just incase others stumble upon here and have the same issues and are not sure what soundcard they have they can find out

Then run alsamixer and make sure the volume isnt muted - Navigate with the arrow keys then slider up/down with arrows aswell.

---

### Post by Winge on 2005-11-10
I have done some more investigation into the matter. I turned up the volume on my speakers to max, and then I can hear exactly when the sound card is initialized at a clean start up, since I can hear statics in my speakers from then on. This happens when the system reports "Setting up ALSA card 1". (Then, some lines after that comes "Setting up ALSA".) However, when I resume from hibernation, the card doesn't seem to initialize correctly, since I never even hear the statics then. I don't know, but this leads me to believe that the problem may be solved if I can replicate what the system does during "Setting up ALSA card 1". How can I know what this is? Is there a boot log somewhere?

[QUOTE=Dr. Nick]
@Winge - Did you try the linuxguide aswell, It sorta a similar soundcard. Not sure if it applies to the Live cards aswell,
[/QUOTE]

Yep, I played around with Alsamixer, but without success.

[QUOTE=Dr. Nick]
You say lsmod lists your sound devices after resume from hibernate but it still doesnt work. The lsmods will be very similar so if you havent you may have to do a line by line look at before and after.
[/QUOTE]

Yes, it contains the same entries, no more, no less. The only difference is that uhci_hcd and 8139too have moved to the top of the list.

[QUOTE=Dr. Nick]
To restart alsa correctly 
sudo /etc/init.d/alsa-utils restart

To correctly identify your card
lspci -v | grep -i audio

then if you need to find the module name go 

[http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) 
Their you can get the module name, It seems yours is emu10k1
so you could try sudo modprobe emu10k1 to load it.

I posted alot of info just incase others stumble upon here and have the same issues and are not sure what soundcard they have they can find out

Then run alsamixer and make sure the volume isnt muted - Navigate with the arrow keys then slider up/down with arrows aswell.[/QUOTE]

No success with any of this... :( 

Thanks for your help though! It is appreciated!

---

### Post by Dr. Nick on 2005-11-11
after a fresh resume from hibernate run ```
dmesg
``` in a terminal. It is a log file which may or may not give you any insight. Do this before getting online since sometimes network activity loads this log file up. 

I would think that restarting alsa would solve it but maybe not. I have the same sort of problem with my wireless card and just using modprobe fixes it though. Hopefully the log gives some info and if not hopefully someone wih the same problem knows and can post a solution

---

### Post by Winge on 2005-11-14
Well, I managed to get sound after a hibernate, at last. First of all I tried to plug in another sound card instead, but the same problem remained.

The way I solved it (or at least went around the problem) was as follows:
First I edited /etc/libao.conf and changed from esd to alsa09. Then I get sound if I every time after a resume I do
sudo /etc/init.d/alsa force-reload

This will end processes using sound, so it is not really that satisfactory, but at least it works. Hopefully it will help someone else, or give someone with a more knowledge than me some insight into what may be the underlying problem... I'm still looking for a better solution.

---

### Post by Dr. Nick on 2005-11-14
glad you got it sorta working, I think since hibernate is still realtively new for linux that future kernels will handle it better, I hope so atleast.

---

### Post by cowlip on 2005-11-16
[QUOTE=Winge]Well, I managed to get sound after a hibernate, at last. First of all I tried to plug in another sound card instead, but the same problem remained.

The way I solved it (or at least went around the problem) was as follows:
First I edited /etc/libao.conf and changed from esd to alsa09. Then I get sound if I every time after a resume I do
sudo /etc/init.d/alsa force-reload

This will end processes using sound, so it is not really that satisfactory, but at least it works. Hopefully it will help someone else, or give someone with a more knowledge than me some insight into what may be the underlying problem... I'm still looking for a better solution.[/QUOTE]

Thanks!!!  The linux-questions.org guide didn't help but this worked greatly.


Hibernate finally works in my kernel, 2.6.12-9, but if I can sound to work by just doing this it's fine.  I hope it improves too.

---

### Post by Alev on 2005-11-26
In my case, the cause for not having sound after hibernation (and subsequent boots)  was that the Wave track  was muted somehow.  Double click the volume control on your panel, Edit>Preferences, find wave, select it and then unmute it.  If that's not it, maybe another one of those tracks will do it.

I dont't know if that'll be the problem on every case, but it's so simple I think its worth checking.

---

### Post by lurch2012 on 2006-01-12
Thanx for the help...for those that are curious as to what fixed my Sound Blaster Audigy  ZS 2...type alsamixer in a terminal...press left/right arrow keys until I got to Item:Audigy Analog/Digital Output Jack...press "M" to unmute....This happened after a hibernate...Thank You for the help

---

