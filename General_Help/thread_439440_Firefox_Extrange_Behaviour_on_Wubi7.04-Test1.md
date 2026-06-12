---
title: "Firefox Extrange Behaviour on Wubi7.04-Test1"
date: 2007-05-10
forum: General Help
---

### Post by JCakeC on 2007-05-10
Hello everyone,

I have been using Wubi for some time now on my kaptop, and I got permission at work to install ubuntu(wubi) there too, ad there i got tons of problems... 
1st. I was using minefield setup and it didn't recognized the SATA drive, so I waited until test1 to be able to actually install the OS.

now that it is installed and running pretty smoothly, I have a single probem. Firefox doesn't load **http requests**. the problem is Firefox alone, as I can telnet to port 80 and dl page content (http request test), can wget anything, I can see the network, I can and have updated the ubuntu distro...

Theweird thing is that it loads https content (thus I think there's some problems with port 80), but I don't know how to fix it... I've search around and disabled ipv6, played with the MTU, but still no effect, but with any config I still can get https on firefox, and port 80 on other connectn types.

any idea?

---

### Post by JCakeC on 2007-05-11
Hi everyone,
seems weird, but I tried a few things today without luck. I tried even uninstalling network managers / firefox and ten reinstalling them, and still no luck with http on firefox. On top of that, when presenting the OS to m boss, it froze on the screensavers area, so I will have to delete it from office if I can't make it work... too bad... any ideas so I can try them on monday?

---

### Post by tuxcantfly on 2007-05-11
this sounds more like an Ubuntu issue, perhaps hardware incompatibility or something, you'll probably get better advice if you ask in the general forum. sounds pretty strange, you might want to try installing nvidia/ati drivers if you're using those cards (restricted drivers manager) and see if that fixes the screensaver issue, and maybe delete ~/.mozilla and that might fix the firefox issue, not sure about anything else

---

### Post by JCakeC on 2007-05-14
TYVM tuxcantfly,

I had instled the drivers already, but I decided to reinstall Ubuntu All over again. This time driver worked ok. Still having the problem with firefox, but I'll post on the Ubuntu forums to see if I can get lucky.

peace.

---

### Post by JCakeC on 2007-05-18
I got the solution on the other forums. and I wanted to post it here so if anyone get here will also find the solution. here it goes:

This post solved my problem ([http://ubuntuforums.org/showthread.php?t=430855](http://ubuntuforums.org/showthread.php?t=430855)).

---

