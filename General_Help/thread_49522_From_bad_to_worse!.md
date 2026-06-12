---
title: "From bad to worse!"
date: 2005-07-16
forum: General Help
---

### Post by granite230 on 2005-07-16
Since I installed Ubuntu (Warty) everything was good. I don't remember having a lot of trouble. But then Hoary came out and I dist-upgraded to Hoary. Some things I changed in Warty were now changed back and I changed it back again!
There were some other weird problems but they were very very small. It was acceptable.

But now, more and more strange things happen. 

- XMMS sometimes spontaneously stops playing and clicking twice on Pause makes it play again. 

- Then sometimes Firefox automatically shuts down when I press a link on a website. 

- Then I launched World of Warcraft using Cedega 4.3. Last night everything was working fine like it always did... today I suddenly had no sound in World of Warcraft (XMMS worked fine). Then I restarted World of Warcraft and the sound was back again.

These were all very small problems I did not really mind.

But now World of Warcraft started to stutter and Firefox wouldn't even start when I tried to launch it. So that's when I decided to reboot my system. Here's the worst part:

I now got an errormessage and couln't fully boot Ubuntu!!! It was checking my harddisk and spitting out some errors. I was brought to my command prompt and X did not start. I was trying to find my boot.log but I discovered there isn't one on my system!! So I rebooted and there it was back again! Then came some other weird errors and I rebooted again!
Now all of a sudden Ubuntu DID boot like it should. And now I'm telling you people this using my Firefox browser... I can't show you my boot.log since there's no boot.log on my system. I'm absolutely sure I once saw a logfile containing all the lines you can see when you boot up your system. Anyone knows which file that is? I'll post it if you can tell me.

And now I don't even DARE to shut down my system again... 

What's the next thing that will happen to my Ubuntu system? Will it blow up if I reboot one more time? Please help me out 'cause this doesn't look good at all...

---

### Post by TravisNewman on 2005-07-16
sounds like your hard drive might be trying to flake out on you. for that last part. The individual application errors have their own reasons, but this seems like something hardware related. I could be wrong, but I'd try running some disk diagnostic software on it.

---

### Post by granite230 on 2005-07-16
Hm that would really be a shame because this harddisk is only half a year old and Ubuntu is the first (and only) thing this harddisk ever saw.

---

### Post by Kimm on 2005-07-16
I had some problems with Hoary when I did dist-upgrade, I suggest you download new ISO's or order from shipit and make a completely clean install, this increased the speed of my system extremely.

Also, when it comes to the firefox problem, if you have both firefox and mozilla installed try copying the plugins folder from the mozilla folder to the firefox folder, but remember to backup the old plugins folder for firefox.

type this in console:

```

mv ~/.mozilla/firefox/plugins ~/.mozilla/firefox/plugins_backup
mv ~/.mozilla/firefox/pluginreg.dat ~/.mozilla/firefox/pluginreg.dat_backup
cp ~/.mozilla/plugins ~/.mozilla/firefox/plugins
cp ~/.mozilla/firefox/pluginreg.dat ~/.mozilla/firefox/pluginreg.dat

```

I had a similar problem with firefox, it usualy happend when I tried to watch video or listen to sound from embeded plugins in the browser after I had installed mozilla, but it worked perfectly in mozilla so this is how I went, now it works fine. You need to restart firefox though.

To get sound working better, first do this:

```

sudo apt-get install libpolyp0 libpolyp-dev polypaudio polypaudio-alsa libpolyp0-glib2.0 libesd0-dev

```

Then follow the following howto:

[http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063)

That should allow you to play several sounds at the same time. If it still does not work, try typing:

```

killall polypaudio

```

in the console before you start the game in cedega.

Just note, if thise f00ks the computer up... I wount take responisability for it, it shouldnt, but just in case.

Anyway, I suggest a **clean hoary install** to begin with :)

*Edit: and I agree, you seem to have some harddisk problems, if your drive is that new you should be able to get a new one from where ever you bought it!*

---

### Post by RJARRRPCGP on 2005-07-16
You probably gotten a faulty (defective) HDD.

---

### Post by granite230 on 2005-07-16
You know... that would be A LOT of work... I used to do that back in the days I was using Windows... like... reinstall it every six months.

What if it is my harddisk failing? Then there's no point reinstalling everything.

I don't use Mozilla and I already have multiple sounds working.

What harddisk diagnostic tools would you recommend?

---

### Post by Kimm on 2005-07-16
> 
What if it is my harddisk failing? Then there's no point reinstalling everything.


Theres no point to not reinstall everything

> 
You know... that would be A LOT of work... I used to do that back in the days I was using Windows... like... reinstall it every six months.


Avvtually its about 15 minutes of work... tops!

---

### Post by granite230 on 2005-07-16
yeah, then I got the OS up and running... then I also need to reinstall the updates, the Nvidia driver, FTD4Linux, Mono, XMMS, Xine, Mplayer, Cedega, World of Warcraft, some plugins and a lot more applications.
I need to fix that multiple sound issue, my Firefox logo, find my wallpaper, back up a lot of data, change tons of settings, including my sources.list and my internet-banking-stuff... etc etc.

I think it's a better idea to try a diagnostic tool first. So... any recommendations?

---

### Post by Wolki on 2005-07-16
[QUOTE=granite230]I think it's a better idea to try a diagnostic tool first. So... any recommendations?[/QUOTE]

Most hard disk brands offer their own diagnostic tool. It's probably best to use that one.

I've also had errors apper because of a faulty hard disk cable.

---

### Post by poofyhairguy on 2005-07-16
On the Firefox thing...I am a hard core Ubuntu Firefox user (average 5 hours a day) and I can tell you from experiance that Firefox just loves to crash and hang sometimes.

If it really bugs you install Epiphany (its much more stable, uses less resources)

---

### Post by twigsby on 2005-07-16
[QUOTE=granite230]
- XMMS sometimes spontaneously stops playing and clicking twice on Pause makes it play again. 

- Then sometimes Firefox automatically shuts down when I press a link on a website. 
[/QUOTE]

The first point happened to me quite regularly after i'd altered the swappiness setting in the kernel from 60 (the default) to 10. Do
> sudo cat /proc/sys/vm/swappiness  
to see what it is set at.

The second also happened to me with the flash plugin for Firefox. Though now it only happens when i accept certificates.  :???: 

Have you reset your computer by the button without shutting linux down properly? the ext filesystem doesn't seem to like that one bit.  :|

---

### Post by super on 2005-07-16
yeah, try the disk diognostics utility in your bios.

two of your other problems - xmms pauses, and firefox hangs - i had those same things going on after a dist-upgrade. so i stopped using xmms and instead started using some other media players. (eclair, rhythmbox, totem, etc)

the firefox thing is still a source of annoyance for me tho. whenever i select "save image as" or "save link target" the browser just closes itself. (gah! the frustration!)

your other problems definitely sound like hardware failure. :-?

---

### Post by damonw5 on 2005-07-16
For HD diagostics tools, try downloading and burning [the Ultimate Boot CD](http://www.ultimatebootcd.com). Restart with it in the drive. I haven't tried it, but it looks good.

---

### Post by granite230 on 2005-07-17
Thanx!

The error I get while booting is now something like: the file system contains errors.
I think the harddisk is making some weird noises but not very loud. Then there goes some kind of progress indicator from 0 to 100 and then it boots (thank god).

This is not really ideal, so right now I'm gonna try the Ultimate bootdisk and some diagnostic tools. I already backed stuff up.

Now I hope a reinstall fixes the bad file system, that way I won't have to purchase myself a brand new harddisk.

---

### Post by mookie2125 on 2005-07-17
Do you have MS windows available on your hard drive also ? If so boot to windows and check if it is stable. A bad ram chip can also play havoc and give similar indications to a hard drive failure. eg  sometimes the system will boot up normally , sometimes it will commence to boot then freeze or crash and reboot - reboot- error messages, BSOD (blue screen of death) etc.
If you have 2 chips try swapping them  one at a time to see if it helps. I have had a reasonable amount of experience with windows but not linux, logic dicatates if windows is stable ( and a ram chip is not the culprit) then it is within the linux OS  and not your hard drive.
Good hunting!!

---

### Post by granite230 on 2005-07-20
I reinstalled Ubuntu a few days ago, then I was reinstalling the applications I use. But while trying to get FTD4Linux to work, I somehow messed up my browser and didn't get it back to work. My dad needs that browser so after installing 85% of the applications I use I had to reinstall Ubuntu again! That's two times in two days...
Now I have installed only the applications I really need. The rest can wait...

I think the filesystem problem is gone... It seems like my harddisk is now working properly again. Good thing!

[B]
EDIT:[/B]

Now I disconnected my Linux harddisk and connected my Windows harddisk because I had to do some homework in Visual Studio. When I was done, I changed the harddisk back to boot Ubuntu. I got this message: Disk Boot Failure, but there was no boot disk in the drive. I think Grub failed or something...
After resetting the computer a couple of times it booted perfectly.

I really don't like these kind of messages... I don't trust it at all and if something goes wrong, my dad will be furious!

Ideally I don't have to backup everything he does before he shuts down the system. I'm thinking about dual booting but that means installing A LOT of things again!

---

### Post by bruin03 on 2005-07-28
[QUOTE=mookie2125]Do you have MS windows available on your hard drive also ? If so boot to windows and check if it is stable. A bad ram chip can also play havoc and give similar indications to a hard drive failure. eg  sometimes the system will boot up normally , sometimes it will commence to boot then freeze or crash and reboot - reboot- error messages, BSOD (blue screen of death) etc.
If you have 2 chips try swapping them  one at a time to see if it helps. I have had a reasonable amount of experience with windows but not linux, logic dicatates if windows is stable ( and a ram chip is not the culprit) then it is within the linux OS  and not your hard drive.
Good hunting!![/QUOTE]

I found this the most helpful post in this thread. I installed Ubuntu yesterday and was having a similar problem and Ubuntu would crash every 5 minutes. I removed one of my ram chipes and I have been running error free for about 2 hours! Thanks! :smile:

---

