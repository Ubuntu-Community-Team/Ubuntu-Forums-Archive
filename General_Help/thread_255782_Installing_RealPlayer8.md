---
title: "Installing RealPlayer8"
date: 2006-09-12
forum: General Help
---

### Post by ross22 on 2006-09-12
hello,

I'd really like to install realplayer8.  Unfortunately when I try to install apt-get gives me the following error message: -

sudo apt-get install realplayer
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  realplayer: Depends: xlibs but it is not installable
E: Broken packages

Does anyone know how I can correct this?

Thanks for any help
Ross

---

### Post by yopnono on 2006-09-12
Is there any special reson that you like to use just ver 8 of real?

If not download the latest from real.
[http://www.real.com/linux?pcode=rn&am](http://www.real.com/linux?pcode=rn&am)

---

### Post by ross22 on 2006-09-12
hi yopnono,

yes, I prefer to use realplayer 8 as realplayer 10 has choppy video when playing realmedia videos, and unresponsive controls when I play BBC radio (on my system).  Real player 8 plays bbc radio perfectly.

I've managed to get realplayer 8 working by simply downloading the rpm and extracting it to my home directory.  This extracts a driectory called usr => bin => x11 => realplay I double click and I can open the file locations easily.  I realise that it's not properly installed! But i'm happy as long as it works.  If I type realplay in a terminal it doesn't execute, and also the plugin for firefox also doesn't automatically load, so at the moment I'm copying the link location and opening it from realplayer.

I can't install from apt-get because of the missing xlibs.

If anyone knows how I can get real8 properly installed please let me know, thanks, ross

---

### Post by yopnono on 2006-09-12
Ok. You can also try the latest beta.
[http://forms.helixcommunity.org/helix/builds/?category=realplay-current](http://forms.helixcommunity.org/helix/builds/?category=realplay-current)

Have you all the rep in the source.list?

Also if you real from the rpm have a folder called postinst, and there is script in that folder. Then run them as sudo/root, that will install it in the proper way.


EDIT: archive realplayers

[http://forms.real.com/real/player/blackjack.html?&](http://forms.real.com/real/player/blackjack.html?&)

---

### Post by ross22 on 2006-09-13
hello,

I'm very happy to say that I've installed the new beta version, and it works (almost) perfectly!

Thankyou for your help, I wish I'd thought of trying it earlier, I was very suprised how well it works in comparison with the last version

:) 
Ross

---

