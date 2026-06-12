---
title: "Firefox Hijacked - plays audio"
date: 2012-10-22
forum: General Help
---

### Post by bbrhuft on 2012-10-22
My Firefox browser plays, at random times about twice a day, audio of an  interview with Janis McKinnon (mother of hacker Gary McKinnon). I'm not  making this up! Hearing the same news conference several times a day is  getting a bit silly. 

It's this interview - [https://www.youtube.com/watch?v=y4lecD44F5E](https://www.youtube.com/watch?v=y4lecD44F5E)

I can be on any page and the audio will start, it goes on for about 4 minutes. I first thought it was banshee player, playing a radio station, but I soon realized it was FF. I  looked in System Monitor and noticed that my FF Plugin Container was  running the flash plugin at 20% while the audio played (see included screen capture). Killing the  process stopped the audio.

Ubuntu 12.04 (resent installation)
Flash 64bit Adobe beta 11.2.202.233
Java Version 1.7.0_07
FF 16.0.1
NoScript 2.5.8

Possible  culprit is Flash Video Downloader add-on. The audio started playing  very soon after I installed it a few days ago, but uninstalling it hasn't fixed the  problem.

Or, I left my computer in to be repaired last week (falty  PSU), however the audio didn't start playing for a few days after I got  it back. I didn't visit any doggy websites in the mean time, just BBC  News, Youtube and a few others. I use NoScript.

It seems that FF has been hijacked, somehow an audio file downloaded and is played every few hours via the flash plugin. I'm quite security conscious; I keep Java, flash other software up to date, I use NoScript etc.

[IMG]https://dl.dropbox.com/u/2055577/Screenshot3.jpg[/IMG]

---

### Post by daslinkard on 2012-10-22
The first thing that I would suggest doing is to purge firefox completely, then reinstall firefox to see if this fixes it....

```
sudo apt-get purge firefox
```

then
```

sudo apt-get install firefox
```

then```

sudo apt-get update firefox
```

Then see if you get the same issue...

---

### Post by pqwoerituytrueiwoq on 2012-10-22
```
firefox -ProfileManager
```
try a new ff profile

---

### Post by Sonsum on 2012-10-22
My roommate had this happen with the audio of the 1st episode of the Jackie Chan Animated Series. It's bizarre.

---

### Post by bbrhuft on 2012-10-23
Well, it just played again.  Seems to play approx. every 12 hours. This time, as it was playing I disconnected the Internet, it stopped. So it's streaming off the Internet. Really bizarre, love to know what it was, how it hijacked my browser.

Here's a video I recorded of it - [http://dl.dropbox.com/u/2055577/Virus_Video.avi](http://dl.dropbox.com/u/2055577/Virus_Video.avi)

I just created a new profile, I'll let you know if that cures it in due course.

---

### Post by pqwoerituytrueiwoq on 2012-10-23
run [FONT=Courier New]crontab -e[/FONT] and see if it is in there, check your startup applications
the most likely was you could get something is a rogue java applet, it should be limited to your user account

---

### Post by bbrhuft on 2012-10-24
I created a new profile, so far so good. No news conference. I suspect it was Flash Video Downloader, here's a thread claiming it was adding malware:

[http://forums.linuxmint.com/viewtopic.php?f=47&t=97951](http://forums.linuxmint.com/viewtopic.php?f=47&t=97951)

---

### Post by dino99 on 2012-10-24
when you ear that stuff, is it always with the same url used ?
or have you added some FF addon/plugin that could play it ?
or a social network running in the background, and someone play it for you, "hey i'm there" ?

by the way, you logs might help you to locate the issue: who play it ?

---

