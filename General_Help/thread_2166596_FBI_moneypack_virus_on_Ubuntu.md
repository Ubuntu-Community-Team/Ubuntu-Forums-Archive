---
title: "FBI moneypack virus on Ubuntu"
date: 2013-08-10
forum: General Help
---

### Post by mercer_hayes on 2013-08-10
but somehow i have managed to get the FBI moneypack virus on my HP Pavillion running ubuntu 12.04lts. amd even stranger is that im on the infected machine right now! my browser is chromium. and the FBI page , that would cripple windurs, is on another tab. i cant close it but it has not denied me service, and i have restarted twice already. i have beat variants of this before. pretty easily too. but i dont have a clue where it might hide in ubuntu. has anyone else ever heard of this happening before??? i could not find any thing about it on google, but it has happened on a mac ,now,too. this is the exploit that demands $450. in 24 hours or huge fine and 10 or 20 years in jail. i just cant believe that this machine is functioning at all.  i hope somebody can shed some light on this, because it looks like we will be seeing more of this sort of thing. and i cant be the first one to get this virus on linux, can I??? im still laffing, i like fixing stuff. i could easily just reload the os, but that would be too easy. and of course , i have never backed anything up. but not too much to lose on this box. i have only had linux running on this one for a month or 2. even if its the hard way, id rather fix it right,than overwrite it . thanks

---

### Post by Netstatus on 2013-08-10
That sure is interesting.
Could you maybe make a screenshot of the 'ransom' screen? There appear to be many versions going around and they don't all work the same way.
That this would appear on ubuntu is something new to me.

---

### Post by bapoumba on 2013-08-10
Subscribed.

---

### Post by 3rdalbum on 2013-08-10
What if you create a new user account and log in via that? It's probably not the actual malware, but just a website that's managed to change Chromium's settings to open that page in a new tab. Not the same as actually having malware running on your system - Chromium is nicely sandboxed.

---

### Post by Bashing-om on 2013-08-10
Had that - or a similar occurrence on the wife's machine, took it as a hijacking from "FaceBook".
Was able to close out the browser, restart and have to this time seen no adverse effects.

Now that there is another report of that incidence in the light of a virus, I will pay more attention to what might happen now.

[INDENT][INDENT]just goes to show, never can tell
[/INDENT][/INDENT]

---

### Post by Sailfrog on 2013-10-09
Hard to beleive? Not on your life! I'm also running the 64bt. Ubuntu 12.04 lts., and guess what? I got the FBI virus too....no windows...but I do run Wine. 

First I got the pop-up and it wouldn't let go of my browser...it had it locked up. So I shut the system down, gave it a few minuits and rebooted. 

Things looked good, I was able to run system settings so I removed Firefox, restarted again and reinstalled it to see how that would work. As soon as I opened it up the pop-up came back. 

Now, I was angry. My 12.04 lts install was fairly new so I decided to clean house. I repartitioned and installed from a dvd. I fired it back up and it all looked good ...no more pop-up! The next day I'm on one of my forums and my curser starts moving around on it's own!!! You ever fight with someone over control of your own machine? I won, and gave it a rest. 

That night I received a phonecall. Whoever it was.. seemed unsure of themselves, like a new telemarketer on their first  call. He mumbled something I couldn't understand, and then I heard him say as his voice got louder (it sounded as if someone was prompting him) "You have a computer..a Windows computer?" I said "no" He said "you have a Windows computer, a Windows compuer, it doesn't run good. I can give you the comands to make it run better." I said "What the h*ll are you talking about? I don't want your commands!" and I hung up. 

 The next thing I did was to get Clam TK running. I found 4 files and I deleated them. They were within /home/c/.wine/drive_c/program files (x86)/ This disabled Wine. So I reinstalled Wine.  I was back on a forum writing a lenthy post and then my text started to disappear, the same way as if the backspace key on the board were stuck. I returned to my desktop and opened a junk text file I had laying around, and it started to disappear too. Now when I run Clam TK It shows up again.

 I've also noticed that my spell checker has stopped working. Is there a section on this forum where I can get help?

---

### Post by Bashing-om on 2013-10-09
Sailfrog; Hey ,

Your post is the only other mention I have seen in this respect. Would not hurt a thing if you were to carry this concern to the "security discussion" sub forum.

[INDENT][INDENT]shared info for shared solutions
[/INDENT][/INDENT]

---

### Post by mörgæs on 2013-10-09
The 'support' phone calls are a well-known scam and happens on a regular basis. There's no proof that the trick is connected to malware, it is only about social engineering.

---

### Post by Frogs Hair on 2013-10-09
If it is a browser exploit and not a virus no operating system would be immune.

---

### Post by fantab on 2013-10-09
Interesting. What happens if .browser (like .mozilla or .chromium) is deleted? Do these 'infected' machines have functional 'iptables' or 'UFW' running? What kind of Browser security addons/extensions were being used?
Subscribed.

---

### Post by Bucky Ball on 2013-10-09
See also here:

[http://ubuntuforums.org/showthread.php?t=2179789](http://ubuntuforums.org/showthread.php?t=2179789)

---

### Post by Amorphous Serendipity on 2013-10-10
Hi mercer_hayes,

All variants of this ransomware that I have seen and analyzed were not  designed to run natively in Linux. I assume you are using Wine?

You most likely got this from:
[LIST]
[*]Infected software you installed in Wine. 
[*]Drive-by-download (found Wine and threw itself in there [probably running, but not well]). 
[/LIST]

Lets try to do some things to resolve this:
[LIST=1]
[*]Clone your HDD for fun analysis later. 
[*]Uninstall Wine. ```
sudo apt-get remove wine1.*
``````
sudo apt-get remove wine-*
``` 
[*]Delete the ".wine" folder from Home. 
[*]Delete the "chromium" folder from the ".cache" directory in Home. 
[*]Install an alternate browser if you do not already have one. 
[*]Uninstall Chromium. ```
sudo apt-get remove chromium-browser
``` 
[*]Delete the "chromium-browser" folder from "/etc" and the "chrome" folder that's in ".config" in Home. 
[*]Run ```
sudo apt-get autoclean
``` and ```
sudo apt-get clean
``` 
[*]Install Chromium. 
[*]Let us know if it worked. 
[/LIST]

I hope I am right assuming you have Wine installed. If not, we have a bigger problem.

---

### Post by Bucky Ball on 2013-10-10
Uninstall Wine? I didn't know that was possible. I never could when I made the mistake of installing it five years ago. Always left something hanging around.

---

