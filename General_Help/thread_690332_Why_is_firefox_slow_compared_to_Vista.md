---
title: "Why is firefox slow compared to Vista"
date: 2008-02-07
forum: General Help
---

### Post by Big Dan on 2008-02-07
Hey Guys, 

  First time poster with this screen name, I've been a Ubuntu user since Breezy. Anywho, I'm miffed by a problem with Firefox. It so slow compared to Firefox under Vista. I noticed the same problem on my old computer but figured it was my hardware. Last week I bought a new computer, specs [here]("http://www.bigdan.us/just-me/new-computer.html"), and one of the first things I did was partition and install Ubuntu.

   I just don't get it, I followed the advice for disabling ipv6 and I even installed Swiftfox which didn't help.. I copied my FF profile from Windows so it's using the same couple of addons. Yet Vista aka the memory hog is rending pages a heck of a lot faster. 

  It's gotten so bad that I've been using Vista for my surfing since I got the computer. I don't care for Vista much so I just ordered a copy of XP Pro off NewEgg, this way I'm able to surf with some speed and in peace. 

  Is there anything else I can do to speed things up? I don't mean to bash but I don't understand how in this day and age something as essential to user experince as an internet browser can be released with sub-par performance.

---

### Post by Gannin on 2008-02-07
I'm not sure why you're experiencing that issue.  For me, Firefox is just as fast on Linux as on any other OS.

---

### Post by ezm on 2008-02-07
The interesting thing that I experience using Firefox in Ubuntu is that there is a delay after the click.  Once that page begins to load, however, it is lightning quick.  That same delay doesn't exist in Vista.

---

### Post by Eddie Wilson on 2008-02-07
Very strange. I use Win2k at work and I do have Xp at my home. I installed firefox on Xp to see what would happen and I didn't notice any difference. At work on 2k Firefox is slower. I know this doesn't help but its whats happening with me.
Eddie

---

### Post by macogw on 2008-02-07
Could have to do with the "more people use Windows" thing resulting in them getting more testing done on Windows.  

Have you tried Firefox 3.0 on them?  Is that also slower on Ubuntu than on Vista?  

You can also try running ```
/usr/lib/firefox/firefox -safe-mode
``` on Ubuntu and ```
"C:\Program Files\Mozilla Firefox\firefox.exe" -safe-mode
``` on Vista and see if Ubuntu's Firefox runs at the same speed as Vista's when both are in safe-mode.  Safe-mode temporarily disables the addons (don't mark any checkboxes when it starts up or it'll permanently disable them..well, until you manually re-enable them).  It's possible some addons behave differently on Ubuntu than on Vista.

---

### Post by nilarimogard on 2008-02-07
Try Fasterfox extension, and set it to 'Turbo Charged'. Works perfect for me.

---

### Post by astrotech226 on 2008-02-07
Did you try Firefox on Ubuntu *before* copying the Windows profile.  I exclusively use Firefox on multiple OS's and have had profile issues when moving them around between operating systems.  It would be interesting to see what happens if you start with a clean profile.  Close all of your Firefox windows and then do this so you can put it back if you need to:

$ mv ~/.mozilla ~/.mozilla-copy

The first time it starts will be painful while it sets the profile up, but should be fine after that.  Does it seem any faster after the new profile?

---

### Post by der_joachim on 2008-02-09
AFAIK the emphasis for FF developers is the windows environment, altheugh I cannot quote any sources. In KDE, firefox is slower than both Konqueror (which is logical since KDE preloads konquerer at startup), and Opera. I use the 9.5 beta now and it is lightning fast.

If you prefer to stay with Firefox, try [Swiftfox]("http://www.getswiftfox.com/"). My 10 year old laptop with 128 Megs  of internal memory starts Swiftfox in a mere 7 seconds.

---

### Post by jimmyjean on 2008-02-09
What graphics card are you using and have you got the correct driver installed for it? 

I had the same probem with Firefox under ubuntu until Nvidia drivers were supported. I use to have problems with pages with alot of graphical content on. When I installed the Nvidia driver for my card it really speeded up the display of some pages.

---

### Post by DoktorSeven on 2008-02-09
I compile my own version of Firefox ([my mozconfig for the curious](http://doktorseven.miskie.net/files/Firefox%20Mozconfig)) that runs **much** faster than the default version and even faster than "Swift"fox.

---

### Post by zwanzig on 2008-02-10
I also had a very slow firefox on my ubuntu 7.10. I just installed Swiftweasel instead and it works like a charm. After automatically copying my 1GB profile from firefox, swiftweasel is just like my firefox used to be but really fast.

---

