---
title: "New install - 3 minor usability issues"
date: 2015-11-06
forum: General Help
---

### Post by steve234 on 2015-11-06
Hi there,

My main PC is a Mac. My mac is "old" so has had Skype, Dropbox and Gdrive support pulled this  year - and the browsers available are slow and unstable.
 
For fun I have installed Lubuntu 14.04 LTS (dual booting with Win10) installed on a Toshiba NB250 - An Atom x64 processor, 1gb ram netbook - it runs nice, and is used for going on public wifi and general browsing (it's a bit faster than my mac for browsing). 

This forum has been an amazing resource to get the netbook up and running, and tweaked to be a bit quicker, so thanks for that. There are a few issues remaining though where I can't get my head round the fixes, or need advice.

(1) - Sylpheed is a nice light mail client, but won't save IMAP email body text offline (just the headers) - which is annoying... Can anyone reccomend an alternative - I hear conflicting things about Thunderbird and mostly just want lightness?

(2) - The nm-applet dying and saying "no connection" on 50-60% of hibernations is annoying and I've got bored of killing it, hibernating again, and then re-starting it (which works) - is there a more elegant solution?

(3) this forum is incompatible with my mobile phone browser (Opera Mini on Android) mostly it just loads a blank white page - Is there a compatible app?

Grateful for any help,

Steve

---

### Post by mörgæs on 2015-11-07
1) You could try Evolution.

2) I don't know about hibernation but 14.04 had network problems in general. I use 15.10 with good experiences.

3) I don't think there is an app. How does Dolphin work?

---

### Post by Irihapeti on 2015-11-07
Re 3), I use Firefox for Android and Lightning browser. The latter is probably the more lightweight of the two.

---

### Post by steve234 on 2015-11-07
Thanks Guys,

Evolution seems to be a Gnome client, and I'm reluctant to pull a load of Gnome dependencies onto my Lubuntu (LXDE) install. I may be wrong but is it not a bad idea to cross pollinate desktop environments on a machine with low resources?

I'm confused about 14.04 having network issues - I thought the LTS edition is stable? I was drawn to it as I got fed up of the Apple cycle of > support withdrawn > upgrade > sort many many issues > suport withdrawn again > repeat.

Dolphin and FF run like cr*p on my phone and are buggy. I'm using the slower stock Android browser as a workaround.

---

### Post by Bucky Ball on 2015-11-07
Welcome. Evolution is bulky, not lightweight. I've tried the lightweight clawsmail. Don't know if that will be good for you. Thunderbird is fine and what I always use. Cross-pollination shouldn't be a problem, but if you start dragging in stuff from Kubuntu/KDE (they generally start with a K like Kompozer) that will drag in heaps. Avoid. I have stuff from all over the shop, but all lightweight (except a couple of standards like Firefox, Thunderbird, Gimp).

14.04 LTS is stable. You appear to be having trouble with your wifi only from your post. If you are only having trouble with your wifi, then probably best to post about that in the Networking and Wireless section. This will significantly increase your chances of support (and wireless questions don't belong here). Always best to keep to one support question a thread to avoid confusion. :)

So, carry on with 1 and 3 but post a specific thread for 2, the networking issue, and include the output of this in your first post, please, to get us started. In a terminal input:

```
sudo lshw -C network
```

Hit return, post the output to your new thread between code tags (see last link in my signature). Good luck and possibly see you there.

---

### Post by mörgæs on 2015-11-07
> **steve234 said:**
> I thought the LTS edition is stable?

It's stable in the sense that it's rarely changing. This also means that non-critical bugs are stable, meaning non-fixed. 

One can only expect annoying-but-not-critical bugs like the one you describe to be fixed in the latest release, that is 15.10.

---

### Post by steve234 on 2015-11-07
Cheers guys - I've got T-Bird now so will see how I get on - will read a tutorial on lxde launchers later so I can launch it from outside the cli.

Will get the networking issue onto another post, and I'll do antoher post for other "annoying, but not critical" issue - the 120sec screen dim timeout. The system dims the screen after 120s of no input even if I'm watching a fullscreen video - annoying!

Thanks again,

S

---

### Post by Mike_Walsh on 2015-11-07
@Steve234:-

If you're using Lubuntu, it's quite easy to get launchers onto the desktop. In the Menu, bring up what you want to put on the desktop; **right**-click on it, and you should get something along the lines of 'Add to desktop'. Click on this, and there's your launcher. Then, just move it to where you want it.

It's** that** simple.

I use T-Bird all the time on a 13-yr old old Dell lappie, with a Pentium 4 and 1 GB RAM. Runs fine. I also remember the short screen-dim timeout, but I forget how I fixed it now; haven't used Lubuntu for a while.


Regards,

Mike. ;)

---

### Post by Bucky Ball on 2015-11-07
Yea, I was running ThunderBird and Firefox on Xubuntu on my P4 with 1Gb RAM faultlessly. Those two programs alone should run fine. It's a combination of them and a heavy distro flavour that generally brings things crashing down.

---

