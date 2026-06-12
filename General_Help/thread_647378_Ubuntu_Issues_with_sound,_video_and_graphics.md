---
title: "Ubuntu Issues with sound, video and graphics"
date: 2007-12-22
forum: General Help
---

### Post by MetalheadGautham on 2007-12-22
[SIZE="4"]Hello all[/SIZE]:guitar:

I am now a regular ubuntu user since I last posted in the n00b section some months back. I can use stuff in ubuntu better than before and I also have done lots of customisations. I have a few issues currently, with my system.

First, let me give my system configuration, of a PC called PoweBox2000(I names it because it may have looked powerful back in year 2000, but not now:mad:)

Pentium 4 Processor with Clock speed 2.66 GHz
256 mb DDR ram @ 400 MHz, but system monitor shows 241.4 mb
Intel 915G Motherboard
Onboard Intel GMA 900 for graphics
Samsung 80 Gig HDD
486.3 mb swap
Ubuntu Feisty Fawn
Windows XP SP2
:lolflag:

And now the issues:

[SIZE="4"]1. [/SIZE]My XV driver is buggy. In Xine, it shows just plain lines. In MPlayer, videos fail to start. I am trying to manage with xshm, but its slow, as we all know. How can I fix it? Is it possible to recompile it?
[SIZE="4"]
2.[/SIZE] What are the packages I need to install to enable installing from source? I also want a clear cut and simple procedure of how to install via source, as I still didn't get the hang of it.

[SIZE="4"]3.[/SIZE] I installed the package for PulseAudio and the replace esd with pulse package. Then sounds in the system stopped working.

I tried a tip I found online to uninstall, purge then reinstall alsa, and then install GDM and ubuntu-desktop which were removed in the process.

Then, with no effect, I tried this:
```
sudo apt-get remove --purge pulseaudio pulseaudio-module-hal pulseaudio-module-x11 pulseaudio-esound-compat pulseaudio-module-jack pulseaudio-module-zeroconf pulseaudio-module-gconf pulseaudio-module-lirc pulseaudio-utils  libpulse0 libpulsecore5 libpulse-mainloop-glib0 libpulse-browse0 libpulse-dev
```

then
```
sudo apt-get autoclean && sudo apt-get autoremove --purge
```

then
```
sudo apt-get update && sudo apt-get install libesd-alsa0 --reinstall
```

still, there is no effect. The programs Xine, MPlayer and Audacius which can use PulseAudo, function properly. The rest are blank. Also, the login music does not play.

Pease help me.

[SIZE="4"]3.[/SIZE] I notice that when I click enable desktop effects, my screen turns white and it takes a while then it returns normal(thanks to the desktop effects preview feature requiring us to click another button before enabling the effects for good). Why is it so?

[SIZE="4"]4.[/SIZE] When I installed beryl via
```
sudo apt-get install beryl-manager
```
I selected beryl as the windows renderer. Then metacity. Then compiz. when I tried compiz, my screen whent all white and only mouse was visible just like what happened with desktop effects. I then did restarted and opened beryl again. Again I got that white screen.

I restarted and did this to remove beryl:
```
sudo apt-get remove --purge beryl-manager
```
even after that, when I reinstalled it with
```
sudo apt-get install beryl-manager
```
And I started beryl, the same problem automatically happened.(as compiz had been selected before)
I again tried uninstalling/purging, then reinstallng. I still found no cure. Whats the problem? Before suggesting a way to solve the compiz issue, please suggest a way to re-set the beryl configuration files. I need to install beryl in a state where it feels like beryl has been just installed, and it was never installed before.

[SIZE="4"]5.[/SIZE] Many games run very slowly and hang a lot in ubuntu, though they run fine in windows. While I play Unreal Tournament 2003 comfortably in windows, I face hangs even in Lincity-NG. Why?

[SIZE="4"]6.[/SIZE] I thought that all these can be fixed by reinstalling and starting afresh. But my DVD-Drive is temporarily unusable. So is there any way I can bring back the system to the immidiate post-install state? I also thought about recompiling the kernel. How do I do it?
[SIZE="4"]
Finally, A few screenshots of the Install I am talking about:[/SIZE]:popcorn:
[http://img266.imageshack.us/my.php?image=ubuntucustomdesktophi3.png](http://img266.imageshack.us/my.php?image=ubuntucustomdesktophi3.png)
[http://img254.imageshack.us/my.php?image=mledjg4.png](http://img254.imageshack.us/my.php?image=mledjg4.png)
[http://img267.imageshack.us/my.php?image=aqubffgdrr9.png](http://img267.imageshack.us/my.php?image=aqubffgdrr9.png)
[http://img156.imageshack.us/my.php?image=japanesedragonmac4linicwe6.png](http://img156.imageshack.us/my.php?image=japanesedragonmac4linicwe6.png)
[IMG]http://img136.imageshack.us/img136/4690/myubuntuvl6.png[/IMG]

I seriously need some help here....

---

### Post by TidusBlade on 2007-12-22
Sorry If I cant answe everything but I can try.
For installing from source, try [this](http://monkeyblog.org/ubuntu/installing/) guide, helped me install almost everything.
As for sound, I think you can only enable OSS or ALSA, and it might be configureable in the system settings or whatever (I use Kubuntu so my Ubuntu knowledge is getting rusty.) 
For the white screen, my only guess would be that your computer cant support it or something? 
Not sure why even Lincity would lag, but my only thought could be that your graphic drivers are not installed properly?
If you wanna reinstall Ubuntu, why not ask a friends or somebody your know or even at the public library to use their CD Drive to burn another Ubuntu CD... Oh yeah your drive cant read it :S You can try using Wubi, heard it runs Ubuntu from Windows or something? And theres no need for any burning.
Nice desktop ;) Any idea where I can find that wallpaper though?

---

### Post by MetalheadGautham on 2007-12-23
^^
1. I am planning to leave ubuntu till the LTS hardy comes out, so that I can explore other stuff. So no reinstall.

2. I am going to be buying an extra GB of ram in a few days to give my comp another year of life, after that I will connect my DVD Drive properly, which BTW, I can't as I am a hardware n00b as of now.

3. I have the following::lolflag:

Ubuntu 7.10 Gutsy Gibbon - i386 DVD
Ubuntu 7.04 Feisty Fawn i386 Desktop CD
Ubuntu 5.10 Breezy Badger
Kubuntu 5.10 Breezy Badger
Xubuntu Gutsy Gibbon - i386 Desktop CD
nUbuntu 7.04 - Live CD
Linux MiNT 4.0 Daryna - Live 32 bit CD
Mandriva One Spring 2007 - Live CD
Fedora 7 DVD
Fedora 8 DVD
Freespire 1 - Live CD
Dyne:Bolic - Live CD
Vector Linux 5.1 SOHO Live CD
Slax Kill Bill Edition
Damn Small Linux
Puppy Linux
Feather Linux
NimbleX
MCN Live Toronto
Open SuSE 10.2 Live

what do I install next :p I want to expreiment with something else for now...

I need this problem in Ubuntu finxed for now, as it may take longer to get my system upgraded.:mad:

---

### Post by MetalheadGautham on 2007-12-23
Update:

I have noticed that gxine's ALSA output works. Does it have any relevance here? even when the system sounds have been set to ALSA?

---

