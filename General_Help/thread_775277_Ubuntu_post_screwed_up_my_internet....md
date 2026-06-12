---
title: "Ubuntu post screwed up my internet..."
date: 2008-04-30
forum: General Help
---

### Post by AdrianStrays on 2008-04-30
So I was having a simple problem.  Every login I would get prompted for my admin password for the network manager to work.  I tried to fix it by doing the following:

[http://ubuntuforums.org/showthread.php?t=463639&highlight=Network+Manager+asking+for+your+password](http://ubuntuforums.org/showthread.php?t=463639&highlight=Network+Manager+asking+for+your+password)

Now my internet doesn't work, even though I went back and removed what I added....

Can anyone help me with this?

---

### Post by AdrianStrays on 2008-04-30
bump

---

### Post by hardyn on 2008-04-30
What version ubuntu are you running, was the guide for a compatible version?

Can you connect though a cable?

use synaptic and "completely remove" network-manager
use synaptic again to reinstall network manager.

(ps wait a little longer than 1.5h for a bump)

---

### Post by noiseordinance on 2008-04-30
> **hardyn said:**
> What version ubuntu are you running, was the guide for a compatible version?

Can you connect though a cable?

use synaptic and "completely remove" network-manager
use synaptic again to reinstall network manager.

(ps wait a little longer than 1.5h for a bump)

I'm in the middle of a similar problem with 8.04. I am attempting reinstall of network manager and wicd didn't work. I just uninstalled via synaptic package manager and when I go back to reinstall, they are gone. Any advice? (Sorry to thread hijack, I figure it's similar enough...)

---

### Post by AdrianStrays on 2008-04-30
> (ps wait a little longer than 1.5h for a bump) 

The version number didn't seem relevant.  It was adding one layer of coding to the pamd.d/gmd file.  

Yes, I did what you said and it didn't work.

I've got like 10 unanswered posts, I've been all over the IRC channels and have been ignored, I've spent hours reading through guides and archived posts and I've been fighting with Hardy ever since I upgraded.  I'm tired of being patient.  I'll save you a rant about the usability of Ubuntu and the irony of spending the last three days trying to get my driver to work if you help me with this....

---

### Post by AdrianStrays on 2008-04-30
bump

---

### Post by AdrianStrays on 2008-04-30
Bump

---

### Post by jimmy the saint on 2008-04-30
It would be a lot easier to help you if you answered the questions that were asked and gave a little more information.  For example, I assume it is wireless that you are having issues with, but can you connect via wired?  What kind of network card do you have?  What behavior is Ubuntu exhibiting?  does it attempt to connect and fail, or does it just do nothing?

---

### Post by jimv on 2008-04-30
sudo apt-get install wifi-radar

OR

Download the file from here and copy it to your Ubuntu machine:

[http://packages.ubuntu.com/hardy/all/wifi-radar/download](http://packages.ubuntu.com/hardy/all/wifi-radar/download)

Once you have Wifi-Radar installed, it will show up under the Internet menu.

---

### Post by AdrianStrays on 2008-04-30
I've answered every question asked, except for one.

Hardyn
> but can you connect via wired?
You
> Can you connect though a cable?
Me before you posted:
> Yes

--------
You
> What behavior is Ubuntu exhibiting?
My original post:
>  Every login I would get prompted for my admin password for the network manager to work.
> Now my internet doesn't work
 -
> What kind of network card do you have?
I do not see how this is relevent. Obviously it has absolutely nothing to do with my card, as it is implied that I could connect to the internet previously, and the fix didn't even touch my driver.

> sudo apt-get install wifi-radar
I didn't like wifi-radar, I'd prefer not to use it, although it seems like at this point I may have too....

---

### Post by jimv on 2008-04-30
I don't particularly like Wifi-Manager myself...just tossing options out there.

Have you tried WICD?  That's what I've been using and I love it.

---

### Post by AdrianStrays on 2008-04-30
WICD couldn't find networks either! WTF is going on..... I even uninstalled/reinstalled the restricted driver.

---

### Post by AdrianStrays on 2008-04-30
Bump...

---

### Post by Ripfox on 2008-04-30
> **AdrianStrays said:**
> Bump...

Back up your files and do a fresh install. It seems you upgraded, which I personally do not ever recommend. Flame me if they want.

---

### Post by AdrianStrays on 2008-05-01
Or I could just erase Ubuntu completely, and never have to spend days at a time trying to get the basic functions of my computer to function properly.:roll:

---

### Post by Ripfox on 2008-05-01
> **AdrianStrays said:**
> Or I could just erase Ubuntu completely, and never have to spend days at a time trying to get the basic functions of my computer to function properly.:roll:

:lolflag: Good luck with that on any OS buddy. Linux isn't a magical pill, it just gives you an opportunity to see exactly WHY something is malfunctioning.

---

