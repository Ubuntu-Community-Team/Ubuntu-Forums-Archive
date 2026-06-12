---
title: "xorg.conf ignoring my native resolution"
date: 2007-08-13
forum: General Help
---

### Post by trevgreenbank on 2007-08-13
after reading some other resolution-related posts I learned a few things, but not enough to solve my problem, which is: i took out all the resolutions except 1280 x 1024 out of my config file. I put a custom modeline in. I know the exact specs of my monitor, and have put them in the conf file. Still though, kubuntu (kde?) seems to get its resolution from some sort of random number generator. Or the devil. It seems to give me everything i DON'T want, randomly. Right now its got its mind set on 1152 x 867. Looking at this logically...

"it" (and is that kde or lower down the chain?) isn't reading the information from xorg.conf because the resolution it's pulling out of it's @ss isn't contained ANYWHERE within that file.

where IS it getting this information from?

In this thread,
[http://ubuntuforums.org/showthread.php?t=189618](http://ubuntuforums.org/showthread.php?t=189618)

there is talk of the OS using the info within the server layout section in the conf. I don't understand the info in this area. Mine says:

Identifier "Default Layout"
screen 0 "Default Screen" 0 0

and some other stuff, but that bit intrigues me. Are those zeros the resolution? Basically i don't know what i'm talking about, and i need help. There should be an EASY way to make the OS use the NATIVE RESOLUTION of your monitor. Editing these configuration files in archaic text editors, only to have them ignored is super annoying.

Also, i'll mention this because there's an outside chance it may pertain to my problem: Has anyone else noticed that A) you don't have to be in administrator mode to change things in system settings > monitor & display as it says you must? and B) the Colour and Gamma tab does absolutely nothing, regardless of admin status. What's up with that?

(kubuntu 7.0.4)

---

### Post by jephrandall on 2007-08-13
when you run *dpkg-reconfigure xserver-xorg*, do you at least end up with a standard resolution of some sort?  Personally, I had to install the nvidia-common drivers to get anything other than 800x600...  What video hardware are you running?

---

### Post by trevgreenbank on 2007-08-14
i could pretty much always end up with either 1024x768, or 1176x ??, i can't remember. That was the one that it pulled seemingly from the ether. (not net haha) So, i solved that problem by editing the config file a zillion times, ending up putting in only the resolution i wanted, and using the 'virtual' line matching my desired resolution. **Now if I could just get kubuntu to actually BOOT **after i shut it down, i'd be a happy man. I've heard stories about *nix computers running for years- now i know why. They were running ubuntu and the admins were too afraid to ever shut them down. Mine falls into the same BS every time i shut it down. [COLOR="DeepSkyBlue"]A loop of: the kubuntu logo with a progress bar, then a blank screen, then the 'logging in with option to escape' text, then the logo again, then a blank screen with a flashing cursor.[/COLOR] HELP ME OBI WAN KENOBEEEEEE.

---

