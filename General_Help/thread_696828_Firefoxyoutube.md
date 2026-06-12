---
title: "Firefox/youtube"
date: 2008-02-14
forum: General Help
---

### Post by perhhk on 2008-02-14
Hi in Win XP on my 750mhz 256mb ram computer in Firefox, I can scroll down while a video is loading and i have developed a habit of doing so, problem is in Ubuntu (gg) with Firefox, if I scroll with the video loading, firefox freezes and has to be restarted.

solutions please

---

### Post by Het Irv on 2008-02-14
I'm sorry to say but if you have flash installed correctly the only thing that I can say is not to scroll.  Sometimes when Firefox freezes it will come back after a few seconds, I usually wait 30 sec before trying anything.  Your problem sounds like your compuer cannot handle the amount of information that is coming in at once.  It may work in WinXp and not Ubuntu just because of the way the different OS handle information.

You can try reinstalling flash and firefox to see if that helps, but I would not hold your breath.

---

### Post by jan quark on 2008-02-14
try to run firefox through the terminal

just type in firefox and enter

and post any error messages when ff crashes the next time

---

### Post by daemon_corrupt on 2008-02-15
Hi all!

Well, I've my notebook (It's a HP Pavillion dv6308 ) crashed plenty of times when I was watching anything on YouTube. I read somewhere in this forum it could be something related to flash... so I went on and remove the Gnash using Synaptic (actually, I removed Gnash and Gnash-common)... then I restarted my Firefox and voilá \\:D/

Hope I helped somehow.

Hugs!

---

### Post by ayampanggang on 2008-02-16
my simplest alternative would be to try different browser and see if the problem persist. You might want to try Opera browser and see if the flash runs better there. If it is, then it's surely browser probs. If not, it might be flash driver or even hardware driver problem

---

### Post by Glugglug on 2008-02-16
This was one of the main problems I had with Gutsy   no problems with Feisty 7.04  so  I've gone back to that  .

---

### Post by perhhk on 2008-03-20
hopefully it may be fixed in hardy heron

I am still having this problem only in Ubuntu on this system but now it has 1.8ghz processor and new motherboard so in essence it is a new system.
 
i did the terminal thing:

fatima@fatima-ubuntu:~$ firefox
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Killed


But that particular error came up as firefox loaded up and killed was when I force exited. The problem happens now even if I don't scroll. I will test out some other browsers, but this really puts me off trying to get anybody who loves firefox to use ubuntu

Is there an easy way to downgrade to 7.04?

Thanks for your help

---

### Post by perhhk on 2008-03-24
Desperate bump...

---

### Post by perhhk on 2008-03-26
I never really get solutions on this forum, only the odd shot in the dark answers, :sad::sad:

---

### Post by AndyCooll on 2008-03-26
> **perhhk said:**
> I never really get solutions on this forum, only the odd shot in the dark answers, :sad::sad:
The easy way to "downgrade" is to do a fresh reinstall of Feisty. 

Just "downgrading" is not possible because one version of the OS will have different settings to an earlier (or newer) version and hence "downgrading" would likely break the OS. Just the same way that you can't expect to install Vista and then downgrade to XP without problems, it's the same with Gutsy back to Feisty. In both cases it's best to wipe the newer version and start again if you want the older version.

:cool:

---

### Post by perhhk on 2008-03-28
Marvellous, so to see if I can get flash working i have to reinstall the OS \\:D/

I'm guessing nobody has any idea how to fix this...

thank god for windows

---

### Post by strabes on 2008-03-28
Saying things like "thank god for windows" is not going to get you help on these forums. If windows is so great, by all means, use it. Most people on these forums are volunteers and use their free time to help you. Adobe's flash is proprietary software, and therefore instability with open source should be unsurprising, if not expected.

With that said, how did you install flash? Did you install it from the ubuntu repositories or by downloading the installer from adobe? If the former, run this command:```
sudo aptitude remove flashplugin-nonfree
``` Then download the installer from adobe's website, here: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

Install it and restart firefox and you shouldn't have any problems.

---

### Post by AndyCooll on 2008-03-29
> **perhhk said:**
> Is there an easy way to downgrade to 7.04?
I was giving you re-install information in response to this comment you made.

:cool:

---

### Post by perhhk on 2008-05-18
> **strabes said:**
> Saying things like "thank god for windows" is not going to get you help on these forums. If windows is so great, by all means, use it. Most people on these forums are volunteers and use their free time to help you. Adobe's flash is proprietary software, and therefore instability with open source should be unsurprising, if not expected.

With that said, how did you install flash? Did you install it from the ubuntu repositories or by downloading the installer from adobe? If the former, run this command:```
sudo aptitude remove flashplugin-nonfree
``` Then download the installer from adobe's website, here: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

Install it and restart firefox and you shouldn't have any problems.

I had originally used the installer to install flash.
 
Anyway, yesterday I purged that package and reinstalled it using apt-get (I did try and use the installeragain but nothng happened when I ran it).

Flash worked wonderfully and I was on the computer for ages with loads of firefox tabs open, youtube videos and rhythmbox playing a shoutcast radio station. All was fine.

Today, I went back on and it has locked up multiple times. Rhythmbox keeps freezing, firefox has been freezing, flash has been laggy and on one startup it froze when i clicked the ff icon.

On this computer, windows takes a while to start up but once it has everything opens quickly and runs smoothly. On ubuntu startup is nice and quick but then programs take a while to load and can be quite laggy.

---

