---
title: "Screen resolutions in X.org"
date: 2007-03-24
forum: General Help
---

### Post by ShirishAg75 on 2007-03-24
Hi all,
      I had been trying to install a ubuntu off-shoot derivative called Ubuntu Ultimate Gamer's Edition (UUGE) the install comes as 640*480 screen. I'm using i845 chipset. When talking to the developer, he told me to reconfigure X using the now infamous ```
sudo dpkg-reconfigure xserver-xorg
```        I went through the settings & managed to **** up the display. The next restart dumped me on the cmd prompt.The error was "No Video BIOS modes for chosen depth". Tht too only with the Ctrl+Alt+F1 combo but tht's for another day. I tried & tried everything but just couldn't get it running. Then I started hunting around for a solution on the wiki & everything which lead me to this place. [http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html](http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html) . I wished this kind of driver should have been integrated inside of X.org hence looked at the mailing list there as to who was sending patches for intel drivers. Turns out there is a Keith Packard who is trying/submitting patches for Intel chipsets. Also it seems he is employed by Intel for tht specific purpose. Anyway, so I sent him an e-mail :-

> Hello Mr. Keith,
                 This mail might bounce back or reach upto u. I saw the lists @ freedesktop.org & see tht u are the guy who's responsible or likes to submit patches. Anyway I wanted to know what is the state of i845 chipset in the X.org . I'm running a custom Ubuntu distribution called Ubuntu Ultimate Gamer's edition which uses xorg 7.2 & i845 is supported at 640*480 only. I would like to know if ever tht could change to 800*600 or best 1024*768 similar to what's provided on MS windows. I do understand tht everything has to be reverse-engineered but just if there is any page/link where which chipsets would be supported & which would be not would be clear. Then I would also know the upgrade path to take. Thnx in advance    Which was replied to by Mr. Keith :-

> 845 should already work great at most any resolution; the only limit in
the 1.7 series is that it only supports resolutions hard-coded in the
BIOS. The 2.0 series will support all resolutions that your monitor can
manage. So now I'm only left with few questions which although I have also asked him would also ask the community :-

1. What is he talking about when he is saying 1.7 series & 2.0 series?
2. Would the drivers be integrated into X.org say 7.3 or something or would end-users have to do something similar like 915 resolution fix as given by Mr. Roland above (which is admittedly risky for noobs)

    This is when the i845 chipset is atleast 3 yrs. old & at tht time it was like another 6 months & the issue would be solved . I'm sure it is solved on other distros. but seems either debian is lagging behind or ubuntu needs to catch up. Lemme know your comments/suggestions/additions & experiences to this :)

---

