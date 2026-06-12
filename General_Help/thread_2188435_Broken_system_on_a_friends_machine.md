---
title: "Broken system on a friends machine"
date: 2013-11-17
forum: General Help
---

### Post by rapattack on 2013-11-17
Hi i was trying to install a few things the other day at a friends house. I am not an expert and she has no basic knowledge at all. Not sure how to fix this as i can't seem to install anything via synaptic or the add/remove software center. Hope the images help

---

### Post by Bucky Ball on 2013-11-17
Disable third-party repositories and run:
```

sudo apt-get install -f
```

... as the fourth screen shot suggests.

This is where it generally gets difficult and confusing when someone is trying to troubleshoot for a friend because I am presuming you are not sitting in front of that machine?

These shots look like they were taken eleven days ago and there was some trouble with the launchpad repos at the time from memory. Have you been anywhere near that machine since and do you know the current state of play with it?

---

### Post by rapattack on 2013-11-17
Hi thanks yes i am not in front of the machine and your right about the date. Been swamped and don't know when i will have time to get back there. I cant instruct her over the phone or anything as she is too skitish about anything tech and won't listen to instructions. Thats what i get for convincing her to use Linux instead of windows lol. Well windows was installed but the sound was mute. I checked everything(hardware/software) and no progress. Installed Ubuntu and no problems with the sound at all. Oh and yes got the driver from the manufacturers website and a clean install of windows. Anyway she is so new to computing she doesn;t know the difference.

---

### Post by Bucky Ball on 2013-11-17
Well, try what I mention in my first post when you're in front of the machine. Launchpad repos were down at the time of pics so everything may be back to normal now. Get here to try an update with update manager and find out.

Not a lot to do if you're not at that machine, though. ;)

---

### Post by rapattack on 2013-11-17
Yes thanks I am hoping to get there in the next few days :0)

---

### Post by rapattack on 2013-11-25
i am in front of the computer now and did the command above in the terminal then update and upgrade. Its worked! Thanks so much. Will post if theres further issues. Managed to also install a couple of things and ran them. Firefox seems to still have some issue. I forgot to post about that but chrome is working as in a browser so that will do for now

---

### Post by Bucky Ball on 2013-11-25
Great news! Please mark thread as solved using the instructions in my signature and post a new thread regarding any further issues. Good luck. ;)

PS: Not sure what release you have installed but just a tip: always a good idea to use LTS releases for these 'at a distance' installs you do. They are the most stable and with five years support. 

The interim releases (from 13.10 on) have only nine months support which presents the hassle of having to somehow get to the machine and upgrade it to a supported release every nine months (and my mother-in-law's Ubuntu machine is 750Kms away so that is very inconvenient!).

---

### Post by rapattack on 2013-11-25
Yes thanks will do that. Thanks for the tip :0) I have seen LTS but didnt know what it was about. Now i know...thanks again

---

### Post by Bucky Ball on 2013-11-25
All good. Incidentally, with the LTS releases, rather than saying having to upgrade from 12.10>13.04>13.10>14.04 LTS you can leap frog the interims and simply go from one LTS to the next, i.e. 12.04 LTS>14.04 LTS>16.04 LTS etc. via the Update Manager. ;)

LTS releases are every two years but supported for five.

---

### Post by rapattack on 2013-11-25
Oh ok i see. So this is not fraut with problems like years ago? I remember i tried to do that and too many things went wrong. I always download the iso/live version then install from that.

---

### Post by Bucky Ball on 2013-11-25
> **rapattack said:**
> I always download the iso/live version then install from that.

Me too. Stick with that method. Most reliable. Just mentioned it because the upgrade method is do-able by a non-computer person, and with the LTS they only need to do it once every five years.

---

### Post by rapattack on 2013-11-25
Ahhh cool thanks for the clarification. Knowing this friend she would stuff that up he he. She only gets on the internet and its been a nightmare to teach her how to sync a phone via bluetooth to get pics over to the computer he he. I had to install the multifunction printer, usb camera and everything else too. Well at least she has never known windows so is none the wiser that its out there

---

### Post by Bucky Ball on 2013-11-25
If they are here basic needs you could get even simpler; do a minimal install, chuck on a lightweight desktop environment like xfce4 or lxde and install only the apps she needs. Limits the possibilities of what can screw up (as there is a lot of stuff in a full Ubuntu install which she probably will never use and can break on an update). ;)

Once a mini is set up and tweaked to purring there's really not much else to do bar upgrading to another release when the time comes, especially with an LTS. Something to think about. I think that's what I'll be installing on my mother-in-law's Ubuntu machine when I see it over christmas (it is 750kms away so I only see it twice a year).

---

### Post by rapattack on 2013-11-25
He he thanks i am not so good at all that tweaking...plus i just dont have much time.
Gee that must be a pain only being able to look at the machine so rarely. I wanted to get my mum onto ubuntu some years back but my uncle that had a computer shop got her on windows and she is so restricted on it. She doesn't realise to do the things she wants she has to pay for software(music production). Being so far away i can't help her with the free programs and if she wants the product support she has to pay for that. I do video and audio production on all 3 platforms so was trying to help ....anyway not much i can do. Even if she brings the machine to me(i dont drive) and i install what she needs she will need instructions on how to use whatever program. She doesnt like to spend enough time here so i can show her :0( ah well

---

