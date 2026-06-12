---
title: "Volume trouble 8.04"
date: 2008-04-27
forum: General Help
---

### Post by steeny124 on 2008-04-27
I'm running Ubuntu Hardy Heron 8.04 on a dell inspiron 1420.  I upgraded to Hardy just a few days ago and I'm unable to get my volume working.  I've ran alsamixer to make sure everything is turned up and unmuted.  I've also searched similar postings here and nothing has worked. Any help would be greatly appreciated.

---

### Post by Bubba64 on 2008-04-27
In volume and the Gnome alsa mixer it will tell you which sound card it is using this information is in sound in system-preferences, also I have found that this sound set up under devices can be inaccurate in mine in devices I have specific set ups that don't produce a sound on test or show an error yet my whole system can always generate sound and record with sound recorder and capture live streaming with video downloader a Mozilla plugin. I have found that the sound card set up for Gnome alsa mixer or sounds or volume controls have to be accurate to work. Do you have alsa mixer or Gnome alsa mixer, and also it helps to install alsa/oss in synaptic

---

### Post by steeny124 on 2008-04-27
The sound tests won't work, along with video files and audio files, links on the internet, etc. I *think* I have just alsa, not gnome alsa. Also, I installed alsa/oss and still nothing, but I'm gonna restart my system and see if anything kicks in.

---

### Post by Bubba64 on 2008-04-27
> **steeny124 said:**
> The sound tests won't work, along with video files and audio files, links on the internet, etc. I *think* I have just alsa, not gnome alsa. Also, I installed alsa/oss and still nothing, but I'm gonna restart my system and see if anything kicks in.

I am far form being an expert on anything Linux but I have about 2 years of usage to find answers. Do you know what sound card you have and does it register in any of my 1st posting as what is being used, Hopefully somebody will chime in with at least the terminal stuff to find your card and maybe an answer, I think it probably is not set up to recognize the card in your system, but that is my semi educated guess.

---

### Post by steeny124 on 2008-04-27
Yeah, I'm pretty clueless.  It's possible that it's not recognizing my soundcard, because everything's definitely turned up and whatnot.  I just don't know how to fix that.

---

### Post by Bubba64 on 2008-04-27
> **steeny124 said:**
> Yeah, I'm pretty clueless.  It's possible that it's not recognizing my soundcard, because everything's definitely turned up and whatnot.  I just don't know how to fix that.

As per a google search of your computer the best description of you sound card is a High Definition Audio 2.0, and I think you might need a driver for it or make sure at the least that in the 1st posts that I listed as the sound card being used, I would check these 1st otherwise you can go to this web sit and input the info and let it detect your card then down load if you want. Good Luck I hope I am not making it worse for you, this is such a common problem on the forum that I think people get tired of trying to help when if you search the forum or Google which can direct you back to posted threads, they get tired of helping. For a new person on Linux or the forums it can be frustrating.

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
I am not sure but this may be the graphics driver link I have old computers so I never have had to do custom driver downloads . here is a site that gives a better description I think of the actual sound card, but I am not sure. if it was me I would write the name down and look at the 1st posts listed areas where a sound card should be shown and see if it matches any listed the sound in system preferences has a dropdown at default device in the device part of sound. Look to see if any of the two names are there.
[http://wiki.archlinux.org/index.php/Dell_Inspiron_1420](http://wiki.archlinux.org/index.php/Dell_Inspiron_1420)

---

### Post by Bubba64 on 2008-04-27
So it appears that your sound card is a Intel Corporation 82801H (ICH8 Family) HD Audio Controller. Right click on the volume control then file which will show you the sound card being used if it isn't the one here then you can change it there and in system-preference-sound. Setting up the sound card is a frustrating process but once you figure it out you will know how to do it again on other releases if needed Good Luck

---

### Post by steeny124 on 2008-04-27
I appreciate all your help.  I've spent the last while trying alot of forum threads and whatnot to no avail.  [_This thread_]("http://ubuntuforums.org/showthread.php?t=616845&highlight=hda+intel+alsa") looked promising, but i've run into problems trying to open the folder to add the line he said to add.  It's getting really frustrating so I guess I'm just gonna have to give up for now 'cause I have a final tomorrow I need to study for. :(

---

### Post by steeny124 on 2008-04-27
I managed to fix it using[the aforementioned thread]("http://ubuntuforums.org/showthread.php?t=616845&highlight=hda+intel+alsa") however, my sound buttons on my laptop don't work.  I found [this thread]("http://ubuntuforums.org/showthread.php?p=4817931#post4817931") which addresses it briefly, but it did not help me. 

When I run alsamixer, the master volume isn't controlling anything, it is the PCM that appears to be the sound coming out of my speakers.  If I adjust that, the sound adjusts accordingly.  So I'm not sure how to fix it to where the buttons on my laptop control the sound coming out of my speakers.

---

### Post by Bubba64 on 2008-04-27
[QUOTE=steeny124;4817983]I managed to fix it using[the aforementioned thread]("http://ubuntuforums.org/showthread.php?t=616845&highlight=hda+intel+alsa") however, my sound buttons on my laptop don't work.  I found [this thread]("http://ubuntuforums.org/showthread.php?p=4817931#post4817931") which addresses it briefly, but it did not help me. 

When I run alsamixer, the master volume isn't controlling anything, it is the PCM that appears to be the sound coming out of my speakers.  If I adjust that, the sound adjusts accordingly.  So I'm not sure how to fix it to where the buttons on my laptop control the sound coming out of my speakers.[/QUOTE/)

If you right click on preferences on the volume control you can assign whatever you want to control the volume. I always go to right click on the top panel then add to panel and put the volume from the list as my control on the top panel. I don't know if reassigning in volume preferences will get any actual physical keys on your laptop to work though. Mine uses PCM as a volume control but I have the master clicked in preferences so both work when I open the volume control with a right click on the volume icon I have added.

---

### Post by steeny124 on 2008-04-28
I fixed it where the volume control on the top panel works, which I appreciate you helping me with.  That doesn't affect the actual buttons on my laptop.  I'm sure there's *some* sort of control somewhere that specifies what the volume buttons control, but it's just a matter of knowing how to find it.

---

