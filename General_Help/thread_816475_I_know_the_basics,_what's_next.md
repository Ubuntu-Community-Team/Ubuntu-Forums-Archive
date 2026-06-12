---
title: "I know the basics, what's next?"
date: 2008-06-02
forum: General Help
---

### Post by dboot on 2008-06-02
Hello,

I've successfully and completely moved over to using only Ubuntu 8.04 x86_64. I love it. With every problem or snag, there's a free solution that teaches me about the OS. I'd like to know more. In the past, I would skim the howto section and learn about something to make my experience even better. Now, however, I'm completely out of ideas.

Here's a list of a few projects that I've looked into and learned about:

Desktop:
- wine
- conky
- network bridging
- video drivers/xorg.conf (dual screens)
- compiz/AWM
- mounting and creating ISO's
- virtual box (for needed Windows only Engineering programs)
- xbmc on 64-bit
- UT/UT2004/Steam games
- dual booting (for new Windows only games, I swear)
- some scripting (bash, sh, ksh)
- using aliases/personalizing the terminal
- vi
- general desktop knowledge
- confident CLI use
- start/kill processes

Server:
- apache/lighty/web servers
- SSH
- email servers
- active directory integration
- instant messaging server
- webmin
- php/mysql
- CMS
- server networking

I'd like to learn about more projects. What's next? 

Thanks for any suggestions!

---

### Post by HalPomeranz on 2008-06-03
Some items that are good to know about that aren't on your list:

-- Syslog (and/or Syslog-NG), log monitoring, etc
-- IDS: Snort and Tripwire/AIDE/Samhain
-- Cron/at and automating jobs, particularly automated remote jobs with SSH
-- Scripting languages (Python or Perl)
-- "Advanced" SSH usage: X11 forwarding, tunneling, ssh-agent, agent-forwarding
-- rsync, unison, etc
-- Security: IP Tables, AppArmor, Bastille, etc
-- Samba
-- Spam filtering and email anti-virus: Spamassassin, ClamAV, MIME-Defang, Greylisting, etc

That should keep you busy for a while...  :-)

---

### Post by Samhain13 on 2008-06-03
Hummm... that's a lot already.

Why not do some work/school related stuff using your box. After some time, I'm sure some apps and features will grow on you. Then you can look more deeply into those apps and features. :)

---

### Post by dboot on 2008-06-03
Thanks HalPomeranz! That's exactly the kind of list I'm looking for. 

> **Samhain13 said:**
> Why not do some work/school related stuff using your box. After some time, I'm sure some apps and features will grow on you. Then you can look more deeply into those apps and features. :)

What kind of apps do you mean? Most of the things I've learned have been necessary for work or from interests already.

---

### Post by andrew.46 on 2008-06-03
Hi,

Have you considered delving a little deeper into Usenet and using such programs such as Leafnode 2 and slrn? There is both a guaranteed learning curve with both of these as well as detailed walkthroughs on these forums.

         Andrew.

PS OK so I wrote the walkthroughs :-).

---

### Post by Samhain13 on 2008-06-04
> **dboot said:**
> What kind of apps do you mean? Most of the things I've learned have been necessary for work or from interests already.

It depends on what you work on. For instance, if you're a video enthusiast, you can use the video editing apps like Cinelerra or LiVES, etc. As you go along, you're bound to form opinions on specific aspects of those apps: what things work, what things may work well, what things don't really work. From there, you have the choice between participating in that app's community (reporting bugs, contributing code, etc.), and simply choosing to use another app (where you start another cycle of using, forming an opinion, etc.).

---

### Post by dboot on 2008-06-09
The reason I've looked into the things that I have is because I'm interested in them. Now, I'm out of ideas. 

I am interested in testing or finding bugs for common applications, but I'm not sure how to get involved: which application, what experience I need, how to help in general.

Is it worth it to learn perl or python?

---

### Post by ryanhaigh on 2008-06-09
If you want to get involved with contributing to the community with bug squashing etc this might be a great way to start: [https://wiki.ubuntu.com/5-A-Day](https://wiki.ubuntu.com/5-A-Day)
I like to try and help out in the forums, passing on whatever knowledge I have gained and trying to solve other peoples problems (in the process learning a little more bash/python and general linux stuff).

---

### Post by ladr0n on 2008-06-09
> **dboot said:**
> 

Is it worth it to learn perl or python?

Yes, learn python.  Python will bring new meaning to your life, it will invigorate your daily routine, it will make your wife more beautiful, it will make your car get better gas mileage, it will lower your blood pressure, and it will make writing devilishly simple yet profoundly useful applications seem like second nature.

---

### Post by dburnett77 on 2008-06-09
> **dboot said:**
> Hello,

I've successfully and completely moved over to using only Ubuntu 8.04 x86_64. I love it. With every problem or snag, there's a free solution that teaches me about the OS. I'd like to know more. In the past, I would skim the howto section and learn about something to make my experience even better. Now, however, I'm completely out of ideas.

Here's a list of a few projects that I've looked into and learned about:

Desktop:
- wine
- conky
- network bridging
- video drivers/xorg.conf (dual screens)
- compiz/AWM
- mounting and creating ISO's
- virtual box (for needed Windows only Engineering programs)
- xbmc on 64-bit
- UT/UT2004/Steam games
- dual booting (for new Windows only games, I swear)
- some scripting (bash, sh, ksh)
- using aliases/personalizing the terminal
- vi
- general desktop knowledge
- confident CLI use
- start/kill processes

Server:
- apache/lighty/web servers
- SSH
- email servers
- active directory integration
- instant messaging server
- webmin
- php/mysql
- CMS
- server networking

I'd like to learn about more projects. What's next? 

Thanks for any suggestions!



[http://www.gnu.org/](http://www.gnu.org/)

[http://sourceforge.net/](http://sourceforge.net/)

are the main influences where free-code is developed with input.

Many authors appreciate suggestions, and complaints that are crafted well.

---

### Post by dboot on 2008-06-12
I'll definitely have to look into python. :)

Is it worth it to compile my own kernel or try other distros?

---

### Post by dboot on 2008-06-30
Are there training courses for advanced ubuntu desktop/server management?

---

### Post by aktiwers on 2008-06-30
I used to skim the Howto section as well, and feel the same way :)
Found some nice stuff skimming this block:
[http://tombuntu.com/](http://tombuntu.com/)

That I had not seen before. 
Emacs should be fun to learn as well. And good to write Python through.

Also, have you playd with the different soundservers? PulseAudio(the new soundserver in Hardy) has lots of cool stuff..  use soundcard from another computer over network and so on..

---

### Post by forger on 2008-06-30
> **ladr0n said:**
> Yes, learn python.  Python will bring new meaning to your life, it will invigorate your daily routine, it will make your wife more beautiful, it will make your car get better gas mileage, it will lower your blood pressure, and it will make writing devilishly simple yet profoundly useful applications seem like second nature.

I wouldn't bet on that "lower your blood pressure" part, especially if you get stuck somewhere while programming :KS

---

### Post by dboot on 2008-06-30
> **aktiwers said:**
> I used to skim the Howto section as well, and feel the same way :)
Found some nice stuff skimming this block:
[http://tombuntu.com/](http://tombuntu.com/)

I have tombuntu on my google reader. :) It's a great site. 

I also have:
[Debian/Ubuntu Tips and Tricks]("http://www.debuntu.org/")
[Digg Linux/Unix]("http://http://digg.com/linux_unix")
[HackITLinux]("http://www.hackitlinux.com")
[Only Ubuntu Linux]("http://onlyubuntu.blogspot.com")
[Ubuntu Geek]("http://www.ubuntugeek.com")
[Ubuntu Tutorials]("http://ubuntu-tutorials.com/")
[Ubuntu Unleashed]("http://www.ubuntu-unleashed.com/")

---

