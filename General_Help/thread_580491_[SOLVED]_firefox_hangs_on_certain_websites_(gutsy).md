---
title: "[SOLVED] firefox hangs on certain websites (gutsy)"
date: 2007-10-18
forum: General Help
---

### Post by mooglinux on 2007-10-18
**EDIT! FIX 2**
Alright, revise this: oyu need only install the package flashplugin-nonfree
you have to enable universe or multiverse (dunno which, just enable both)

**EDIT: Fixed!** i jsut installed these 4 packages in synaptic:
flashplugin-nonfree
gnash
gnash-common
mozilla-plugin-gnash

[here]("https://bugs.launchpad.net/ubuntu/+source/mozilla-firefox/+bug/154164") is the bug report in launchpad



Upgraded to Gutsy late last week, and quickly have come to find that many of my favorite websites now cause firefox to hang for several minutes, and it does not always work properly afterwards. I made sure that java is installed, and i have also tried disabling all my add-ons, but none of them appear to be causeing the issue. 

The following websites consitantly cause it to hang:
ign.com
using gmail
endgadget.com
tomshardware.com 
pbs.org
anandtech.com
photobucket.com
youtube.com

there are many others as well. as you can imagine this cripples my web-surfing considerably, and i have been using epiphamy, but i much prefer firefox. Any ideas and suggestions are greatly appreciated!

---

### Post by mrvertigo on 2007-10-18
some of those are using flash, you can try gnash or the adobe offering btw how much ram is in the box? is desktop effects enabled? are you having other hanging or sluggish issues?

---

### Post by mooglinux on 2007-10-18
i have 1 gb of ram with desktop effects enabled, and system monitor lists only 49% used. i have the adobe flash installed with nspluginwrapper (am using 64-bit, hence the wrapper) 

I did solve it however. i installed the following packages in synaptic:
flashplugin-nonfree
gnash
gnash-common
mozilla-plugin-gnash

obviously not having htese installed causes serious hangs in firefox, a bug that needs fixed. I believe there is an ubuntu plugin that is sopposed to find compatible plugins? how would i narrow it down to make out a good bug report?

---

### Post by mrvertigo on 2007-10-18
I like you already a good bug report is short, sweet with all the facts like
*system specs*
Adobe flash hangs in firefox unless packages X,Y,Z are installed 
plugin finder did not recomend these.....

something to that effect

---

### Post by mooglinux on 2007-10-19
Last question: is this a problem that needs to be reported in launchpad as ubuntu-specific or upstream in the mozilla bugzilla?

---

### Post by mrvertigo on 2007-10-19
this is one of those few that you may want to report to both

---

### Post by Galls on 2007-10-19
I am having the same problem.  

I am on x64.

Is there anyway I can downgrade?  This upgrade has been as use full as vista so far.

---

### Post by mooglinux on 2007-10-19
Have you tried installing those packages? 

try installing these in synaptic and let me know what happens:
flashplugin-nonfree
gnash
gnash-common
mozilla-plugin-gnash

If that does fix is drop by [here]("https://bugs.launchpad.net/ubuntu/+source/mozilla-firefox/+bug/154164")
and confirm it and add any information that might be relevant.

---

### Post by Galls on 2007-10-19
that fixed me, thanks for your time.

---

### Post by conehead77 on 2007-10-19
> **Galls said:**
> I am having the same problem.  

I am on x64.

Is there anyway I can downgrade?  This upgrade has been as use full as vista so far.

You cant downgrade from 64bit to 32bit, you need a reinstall for that. I myself use the Gnash plugin, but as its beta many thinds arent working (i dont need flash so bad, so i dont care).

I dont know about ndiswrapper though.

---

### Post by eg0n on 2007-10-19
I had the same problem. After that helpful post I don't :)

---

### Post by napster2500 on 2007-10-20
it worked! Thanks mooglinux. my firefox hanged on hi5 and youtube.

---

### Post by morghi76 on 2007-10-21
Hey! This thread save me!!! THANK YOU VERY MUCH! I upgraded to Gutsy two days ago and I soon realised that something were very wrong with Firefox... installing the packages you listed fixed the issue for me!
It's a pity though that things like this happen: I mean, how many newcomers will understand that in case Firefox hangs you have to installa a number of packages via synaptic?
By the way, I'm happy you fixed it for me!

---

### Post by Grellin on 2007-10-21
Agreed, it worked for me as well. I had tried the other suggestions but this was a very simple fix that worked. Thanks :guitar:

---

### Post by mrhirsh on 2007-10-23
How do you do that install in the Synaptic Pkg Mgr?

Can you take me through the steps as if I knew nothing (and you won't be far off)?

Thanks,

---

### Post by mooglinux on 2007-10-23
Using synaptic is an essential skill you will need to learn to fix many issues. Its simple too, just go to system->Administration->synaptic package manager, enter the administrator password and your all set. just hit search to find a particular package, and check the box to install, uninstall, reinstall, and a few other things. in this case you want to type in 'flash' and all of those packages listed above will be on that list.

 if your new to linux (ive only been using it a few months myself) i would recommend getting a book about using the terminal. theres just a few basics that really make it easier to understand all the fixes people supply, which typically are terminal code.

---

### Post by mrhirsh on 2007-10-24
Thanks so much for all your help.  That actually fixed several problems.

Have a great day.

---

### Post by Nallison on 2007-10-24
same problem here on AMD64 version.  I did the following 
sudo apt-get install flashplugin-nonfree
sudo apt-get install gnash
sudo apt-get install gnash-common
sudo apt-get install mozilla-plugin-gnash 

and it worked .  Thanks mooglinux!

---

### Post by Crafty Kisses on 2007-10-24
Nice fix...

---

### Post by rmigo on 2008-01-06
I have Gutsy X64.

The posts here solved my problem. Thanks.

---

### Post by bmtphoenix on 2008-02-02
Yep, this fixed my issues too.  Just as a side note, when doing all those apt-get installs a few of them said they were either already installed or weren't installing because something was already done or something...but after doing them all, it still works. ;)

---

### Post by micksatana on 2008-04-15
It works! Thanks.

...If you've already installed them, just re-install them. it will work just fine~

---

