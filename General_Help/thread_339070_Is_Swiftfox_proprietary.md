---
title: "Is Swiftfox proprietary?"
date: 2007-01-15
forum: General Help
---

### Post by floke on 2007-01-15
Have just been trying out swiftfox (blooooody fast!), but read on one of the threads here that it was proprietary. Does anyone know if this is true? I though Firefox was FLOSS and released via the GPL, so how can swiftfox be proprietary? Also, if it isn't, then why don't more people switch to Swiftfox given the speed benefits?

Not sure if this is posted in the right place, so sorry if its not really a 'general help' issue.

---

### Post by lyceum on 2007-01-15
It's FOSS, MPL 1.1

[http://en.wikipedia.org/wiki/Swiftfox](http://en.wikipedia.org/wiki/Swiftfox)

And it has a sweet logo!

---

### Post by floke on 2007-01-15
Except for the binaries and the logo (which Mozilla also restricts). 
So why isn't this as popular as F/fx? Its certainly a lot faster on my box 8)

---

### Post by lyceum on 2007-01-15
> **Steve.K said:**
> Except for the binaries and the logo (which Mozilla also restricts). 
So why isn't this as popular as F/fx? Its certainly a lot faster on my box 8)

I just hear about it a week ago. I really don't know. I tried to check it out, but had trouble with the install. Havn't had time to try again yet. Still to new? I just wonder if it does get big, will there be a swifticeweasel? :-D :-k

---

### Post by floke on 2007-01-15
Maybe they'll call it Swicel?

---

### Post by lyceum on 2007-01-15
> **Steve.K said:**
> Maybe they'll call it Swicel?

lol! nice

---

### Post by useResa on 2007-01-15
> **lyceum said:**
> I just hear about it a week ago. I really don't know. I tried to check it out, but had trouble with the install. Havn't had time to try again yet. Still to new? I just wonder if it does get big, will there be a swifticeweasel? :-D :-k

I only heard about Swiftfox only very recently.
I found the installation very easy, particularly since you can very easily install it with the *apt-get* command. I basically followed the instructions for installation as also described for Debian on this [page](http://www.getswiftfox.com/debian.htm).

Furthermore I also believe it is faster and until now I did not get the unexpected and unexplainable crashes that I use to get with FF2.

---

### Post by floke on 2007-01-15
And I love the way it just nicks all your Ffx settings so it looks exactly like your Ffx :D 

How did the apt-get work btw - I thought you had to select the right version for your processor.

I just downloaded the installer for my chip from here

[http://getswiftfox.com/installer.htm](http://getswiftfox.com/installer.htm)

and followed the instructions (sh install-swiftfox.sh) - it went and downloaded and installed the right version for me.

---

### Post by useResa on 2007-01-15
Yes you are correct, you have to select the right version for your processor.
I simply used Applications --> System Tools --> Sysinfo and selected CPU to determine - for certain - my processor.
Next I used [this chart](http://www.getswiftfox.com/proc.htm) to determine the version I required.

Additionally I added the following lines to my sources.list
> ## SWIFTFOX REPOSITORY
deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free
All what is left then is to issue the command (in my case)
```
sudo apt-get install swiftfox-prescott
```
[color=red]NOTE:[/color] **prescott** has to be replaced with the version that is required for your PC. A separate list with the available swiftfox versions is indicated [here](http://www.getswiftfox.com/builds/debian/packages).

Hope that all this makes some sense and that it helps.

---

### Post by floke on 2007-01-15
I was a bit stumped before coming across the chart, since there's no oibvious list for an Intel Core Duo on the main page. But the Prescott version works fine. I still reckon the installer method's quicker - you don't have to add sources to repository etc, - But who cares, its all good fun!

---

### Post by lyceum on 2007-01-15
> **useResa said:**
> I only heard about Swiftfox only very recently.
I found the installation very easy, particularly since you can very easily install it with the *apt-get* command. I basically followed the instructions for installation as also described for Debian on this [page](http://www.getswiftfox.com/debian.htm).

Furthermore I also believe it is faster and until now I did not get the unexpected and unexplainable crashes that I use to get with FF2.

I wasn't trying very hard when I did it. I was in a hurry. Thanks for the links though, that will make it alot easier when (if) i get the time. I did not realize I needed to know my CPU type.

---

### Post by CowzRule on 2007-01-15
I installed it via Automatix 2. It detected my Athlon XP and installed the correct version.

---

### Post by floke on 2007-01-15
Its this that makes it faster. 
As i understand it, swiftfox is basically firefox configured for different processors.

---

