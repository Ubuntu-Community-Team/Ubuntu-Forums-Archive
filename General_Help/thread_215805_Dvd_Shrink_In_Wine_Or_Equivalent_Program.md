---
title: "Dvd Shrink In Wine Or Equivalent Program"
date: 2006-07-14
forum: General Help
---

### Post by ahaslam on 2006-07-14
Hi,

I used to use a program called dvd shrink under windows. It enables you to remove undesired options like special features, menus & sound options, to  fit a dvd movie onto a standard dvd. If removing undesired components wasn't enough, it would reduce quality to fit the movie onto a standard disc.

This program installs and runs under wine but it does not recognise my dvd drive, so it' not working.

My questions are:

1. Does anyone know of a way to make it recognise the dvd drive?
2. Is there a Linux equivalent to this package? I don't want to convert to divx/xvid/mpeg and then convert back to dvd (that would take a lot of time on my laptop).

Thank you, I look forward to your suggestions.

Tony.

---

### Post by hesser on 2006-07-14
Add the German kubuntu repo to your sources.list file and install k9copy and the dvd libraries. The one in the official repo is 1.0.2 but the other is 1.0.4. Much better support.

---

### Post by ahaslam on 2006-07-14
> **hesser said:**
> Add the German kubuntu repo to your sources.list file and install k9copy and the dvd libraries. The one in the official repo is 1.0.2 but the other is 1.0.4. Much better support.

Thank you for your suggestion.

I downloaded the source for the latest stable version and ran into errors during ./configure. I then added their breezy repo and version 1.0.2 is now available via synaptic but has a load of dependancies, with it being a kde program 'n' all.

Any advice for instaling the latest version? Is there a version for gnome?


Tony.

---

### Post by briguy on 2006-07-14
Have you tried DVD rip?  Not sure it's exactly what you're looking for, I find it very useful.

---

### Post by PapaWiskas on 2006-07-14
I think I know where you are coming from....I am a Ubuntu convert from December and had a heck of a time trying to get a program like that to work right.

This link should get you going in the right direction...


[http://ubuntuforums.org/showthread.php?t=78611](http://ubuntuforums.org/showthread.php?t=78611)

You could also do a search here for DVD Decrypter...:) not sure if pgcedit plugin will work under wine though, never tried it.

---

### Post by ahaslam on 2006-07-14
> **briguy said:**
> Have you tried DVD rip?  Not sure it's exactly what you're looking for, I find it very useful.

Am I right in assuming that it encodes to divx/xvid and doesn't compress the dvd into an iso suitable for burning to a standard dvd?

Thanks,

Tony.

---

### Post by ahaslam on 2006-07-14
> **PapaWiskas said:**
> I think I know where you are coming from....I am a Ubuntu convert from December and had a heck of a time trying to get a program like that to work right.

This link should get you going in the right direction...


[http://ubuntuforums.org/showthread.php?t=78611](http://ubuntuforums.org/showthread.php?t=78611)

You could also do a search here for DVD Decrypter...:) not sure if pgcedit plugin will work under wine though, never tried it.

Thanks, 

It looks just like what I need. I'll try it out in a while and report back.

Tony.

PS. I like your avatar ;)

---

### Post by briguy on 2006-07-14
> **Anthony Haslam said:**
> Am I right in assuming that it encodes to divx/xvid and doesn't compress the dvd into an iso suitable for burning to a standard dvd?

Thanks,

Tony.

That's right.

---

### Post by ape on 2006-07-14
I've got DVD Shrink v3.2 working just fine under wine.  You need to run winecfg and add a custom application entry for DVD shrink so that you can set the OS emulation to Windows 2000 and also set your specific drive(s) to be recognized as CD-ROMs.

---

### Post by ahaslam on 2006-07-14
> **PapaWiskas said:**
> This link should get you going in the right direction...

[http://ubuntuforums.org/showthread.php?t=78611](http://ubuntuforums.org/showthread.php?t=78611)
Thanks it seems to be doing the trick. I never knew that there was a configuration utility for wine. 
I had to uninstall DVD Shrink and set up the dvd drive in wine as specified in your link, then reinstall.
I've just re-authored a dvd and it's going through the motions now. I'm sure it'll be ok.

Thanks again,

Tony.

---

### Post by PapaWiskas on 2006-07-14
No problem, also just so you know, I did run some tests today with pgcedit in wine and also the psl2 plugin for pgcedit and they both work in wine.

pgcedit also has a linux version if you are interested in that, but I havent used it, I still use the wine version, along with dvdshrink because that is what I am most familiar with being a ex-windows user.

So until I learn more about Linux, this is how I do it for now.

Eventually I want to get away from wine and use only native Linux apps.

p.s.  Thanks for the compliment on my avatar.:D

---

### Post by ahaslam on 2006-07-14
> **PapaWiskas said:**
> Eventually I want to get away from wine and use only native Linux apps.

Same here, currently this is the only app that I'm using with wine.
DVD Shrink is quick, effective & simple. I hope that a Linux equivalent is produced in the near future. Ripping, encoding, re-encoding & burning is a very tiresome task.

Thanks again,

Tony.

(currently backing up dvd no.2) ;)

---

### Post by cre8ivgil on 2006-07-24
For native linux you have k9copy for kde and dvd95 for gnome, although k9copy will work in gnome just as well, there's no longer a need for wine and DVD Shrink. I am not just mentioning this, I use both of them and they are both very reliable and reasonably fast. As a test I made two backups of the same movie (Firewall) for the first copy I used k9copy to shrink and k3b to burn and on the second copy I used dvd95 to shrink and gnomebaker to burn. The first copy took about 34 minutes from start to finish and the second took about 31 minutes, and both played flawlessly on three different DVD players and on my desktop. I have now totally made the switch to linux since I've figured out how to backup my DVDs, I still keep a copy of XP for the kids, and they too are logging into linux more often, my goal is to reclaim my XP partition by the end of this year and say bye to all the bugs, viruses, crashes, malware, spyware etc... etc... etc...

---

### Post by JoWilly on 2006-07-24
> **cre8ivgil said:**
> For native linux you have k9copy for kde and dvd95 for gnome, although k9copy will work in gnome just as well, there's no longer a need for wine and DVD Shrink. I am not just mentioning this, I use both of them and they are both very reliable and reasonably fast. As a test I made two backups of the same movie (Firewall) for the first copy I used k9copy to shrink and k3b to burn and on the second copy I used dvd95 to shrink and gnomebaker to burn. The first copy took about 34 minutes from start to finish and the second took about 31 minutes, and both played flawlessly on three different DVD players and on my desktop. I have now totally made the switch to linux since I've figured out how to backup my DVDs, I still keep a copy of XP for the kids, and they too are logging into linux more often, my goal is to reclaim my XP partition by the end of this year and say bye to all the bugs, viruses, crashes, malware, spyware etc... etc... etc...

Thanks for the report.

It would be interesting to see a picture quality comparison between dvdshink and these 2 apps, when you compress a movie to ~60%.

Image quality is the most important for me. I will use dvdshrink until someone can show me that the linux apps are as good.

---

### Post by orb9220 on 2006-07-25
I still use dvd shrink nothing in the linux apps compares. 

Yes the others I have tried and tested. But shrink allows me to customize compressions to extra's giving me a bit more room for the main movie. Also can do customize like max on two disc movie then reauther them into one long 4hr movie. Also the reauther allows me to set begin and end rip points, Or I can replace the annoying beginning crap with stills of my own   chosing. I can do alot more in shrink than the others I have tried.

I am not knocking the linux programs some of them look quite promising, But there are still some major problems that many people are having with them.

I will keep my mind open and keeping up with trying them. I just wish people would stop trying to talk me out of shrink just because it's a window program. Saying things like k3b rocks and gnomebaker is the knee's bee's well I have tried them and found them to be lacking,

Just now I was trying out the burn ISO in kb3 which was a movie and stuck in my 16x DVD+R and it would not accept it. It wants a -R disc I mean come on what is going on here. So I tried it in Gnomebaker and it burned it fine. Then k3b won't let me burn 16x but gives option 12x tho gnomebaker burned it at 16x.

I think what I am getting at is thier seems to be a lack of stability and standard way to burn cd and dvd. Hope this changes but until it does make strides in multimedia,photo,audio,video I will still use shrink and using the windows version of xnview for photos too.

---

