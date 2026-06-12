---
title: "Netflix app? Update Silverlight?"
date: 2013-04-17
forum: General Help
---

### Post by newbi462 on 2013-04-17
OK while it is unofficial and basically a specialized WINE box.... a needless silverlight update has broken the netflix application in the software center... I click install update and right click run from the FF DL list but of cource it still wants me to update....

Is there a way to actualy add this Siverlight update to the netflix app bottle properly.... or should I just cancel netflix for good and switch to Amazon prime?

---

### Post by oldos2er on 2013-04-17
Run these commands only if you don't run any other Windows' apps: ```
sudo apt-get purge netflix-desktop

sudo apt-get clean

rm -rf ~/.wine-browser/

sudo apt-get update

sudo apt-get install netflix-desktop
```

---

### Post by newbi462 on 2013-04-17
Is there a way to do it if I do?

One system do using both WINE and CROSSOVER... The other do not

---

### Post by oldos2er on 2013-04-18
Backup ~/.wine-browser, you can always restore it if there's a problem with the other Windows app.

---

### Post by Cincinnatux on 2013-04-18
There's a separate thread with a solution that worked for me this evening.
[http://ubuntuforums.org/showthread.php?t=2029336&page=2](http://ubuntuforums.org/showthread.php?t=2029336&page=2)

Specifically, I saved the shell script posted there by topdisc as 'netflixfix.sh' and ran it from terminal.  It took a couple minutes, but Netflix ran thereafter.  According to topdisc, this is not a real fix; it is a momentary work-around that has to be repeated each time Netflix-desktop thinks to check whether Silverlight needs to be updated.

I've stumbled across another suggestion folks might wish to try if the above-proffered options fail to work:

Erich E. Hoover on [https://bugs.launchpad.net/netflix-desktop/+bug/1164453](https://bugs.launchpad.net/netflix-desktop/+bug/1164453) wrote:
> I'm not having this problem, even with a fresh profile. It might be that you started with a profile from before when I had the installer disable automatic updates. So, I would suggest wiping the profile folder to see if that fixes it:
rm -Rf ~/.wine-browser

At least 5 people claim that this fix did it for them; the next time my Netflix fails, I'll try this out and report back.

Well, that was quick.  After the home server decided to stop running Netflix, too, I applied Erich Hoover's solution.  I am happy to report that on my 64-bit 12.04 LTS installation, Hoover's fix seems to work!

---

### Post by oldos2er on 2013-04-19
That script contains basically the same commands as I gave in post #2. Again, if you run the script make sure you have good backups first.

Also I noticed there was an netflix-desktop and wine-browser update this morning, so I'm hoping having to repeatedly run the above commands has been fixed.

---

