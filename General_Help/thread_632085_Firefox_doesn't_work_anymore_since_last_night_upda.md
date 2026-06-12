---
title: "Firefox doesn't work anymore since last night update..."
date: 2007-12-05
forum: General Help
---

### Post by limaunion on 2007-12-05
As the subject says, last night I did an apt-get upgrade and the new firefox (2.0.0.11) doesn't work (I'm using dillo right now). This is what I get:

$ firefox 
Floating point exception

$ dpkg -l | egrep -i firefox
ii  firefox                                    2.0.0.11+2nobinonly-0ubuntu0.7.10         lightweight web browser based on Mozilla
ii  firefox-gnome-support                      2.0.0.11+2nobinonly-0ubuntu0.7.10         Support for Gnome in Mozilla Firefox
ii  mozilla-firefox-locale-en-gb               2.0.0.7+1-0ubuntu2                        Mozilla Firefox English language/region pack
ii  ubufox                                     0.4~beta1-0ubuntu6                        modifications for ubuntu firefox (default) i

I renamed my .mozilla directory but nothing has changed. I'm using the amd64 branch.

Any ideas ?
Thanks!

---

### Post by treris on 2007-12-05
You're not the only one with this problem, what seems to have worked for me is using the [ubuntuzilla]("http://ubuntuzilla.wiki.sourceforge.net/") script to install the official build of firefox instead of the ubuntu one. 
This fix, however, does not seem to work for everyone but you could give it a try, the script also provides a way to undo itself, so no harm no foul I suppose.

---

### Post by limaunion on 2007-12-05
Thanks for your reply, but I've more bad news as described:

After posting this thread I decided to log-off/log-on from my GNOME session in order to check if this could help to solve the firefox problem. Unfourtunately I've found a much worst scenario, now GNOME is having major problems. Inmediately after the session begins the top panel starts to blink continuously for 10 - 15 seconds, after that I cannot open any menu and the right mouse click doesn't work, in others words my GNOME is unusable! I tried to start GNOME is 'safe mode' but doesn't help. I'm right now at work but this night I'll try to log-on with another user account. 
(I'm starting to think if it's time to switch to Debian testing ?)

Any one is having the same problem ?
Thanks!

---

### Post by mahiyar on 2007-12-05
OMG is there a problem with the current 100 Mb of update posted today?

---

### Post by djuniah on 2007-12-05
same issue here....i tried with ubufox installed and uninstalled and nothing helped.  I'm using a different browser for now, but i would really like to get this fixed fast.

(however mine was not a floating point error, it just says segfault)

---

### Post by oscarsfriend on 2007-12-05
Is there anyone who **has** got it working?

---

### Post by limaunion on 2007-12-05
regarding the firefox problem, is there a bug report ?

---

### Post by mahiyar on 2007-12-05
I use the Ubuntuzilla scrip, after the update I even rebooted to check there seems to be no obvious problem.

---

### Post by metalheart on 2007-12-05
Try to run Firefox
```
firefox -safe-mode
```
This disables all plug-ins.
My Firefox runs fine after update.

---

### Post by djuniah on 2007-12-05
ok safe mode works for me....now i just need to figure out whats causing it.  Thanks a million!

EDIT:
FOUND THE ISSUE!
The addon "colorzilla" was causing it.  After disabling it firefox loaded just fine.  (colorzilla never fully worked in linux anyway)

---

### Post by oscarsfriend on 2007-12-05
To answer my own question I just updated and am posting this from FF 2.0.0.11.  Also, I am running Kubuntu Feisty, amd64, if that is of any use to anyone.

EDIT: And it works fine too on Kubuntu Feisty 32bit.  Looks like it may be a plugin issue after all -- I'm running FF with numerous plugins, but not using "colorzilla" on either machine.

---

### Post by stryderjzw on 2007-12-05
I did the update and now I am getting Floating point exception (core dumped) when I am going to Google Docs and scrolling all the way down the documents list. 	](*,)

Anyone else seen this? Where do I post bugs for Ubuntu's Firefox?

Thanks!

---

### Post by treris on 2007-12-06
Hi stryderjzw

I had a similar experience with google news, everytime I scrolled all the way to the bottom of the page, Firefox would just disappear. When I ran Firefox from the terminal (to check for errors and such) I'd just see that floating point exception mesage and that's it.

I don't know exactly where to report this, but I think it is an Ubuntu error because I have used the ubuntuzilla script to install the official mozilla build of firefox and haven't had a single crash yet.

I know it might not be the perfect way of doing things, but for me it got the job done and with regards to internet browsing that's most important for me.

Hope this helps

Edit: It seems to be related to the libcairo package, see here: [https://bugs.launchpad.net/ubuntu/+source/libcairo/+bug/173861](https://bugs.launchpad.net/ubuntu/+source/libcairo/+bug/173861)
you could try downgrading to the previous version of libcairo2 by using Synaptic and then Force version and lock version, if the problem really is in the latest libcairo2 package then that should solve the problem, hopefully, haven't tried it yet though since I've already switched to the mozilla build of firefox instead of the ubuntu version.

---

### Post by fangx1980s on 2007-12-06
Thanks a lot treris, that solution works for me, it really save my day

---

### Post by stryderjzw on 2007-12-06
Thanks treris for looking for that bug.  It's fixed my problem too.  Now hopefully they put out a fix for that soon.  :)

---

### Post by stell86 on 2007-12-07
Thanks treris, the solution works for me - 36 hrs ago I was ready to catch all snakes barehand - now I'm calm enough to recognize that I am actually afraid of most :)
And OpenOffice was sorted out by replacing my xorg.conf with a backup and de-activating and activating 'fglrx'-driver - why updates has to make life unexpectedly difficult is a mystery - like a sudden curve in a normally straight road....

---

### Post by treris on 2007-12-07
You're all very welcome, although all I did was look through the forums, I'm just glad that you've all been able to solve the problem with FF. 

Now it's just waiting for a fixed version of that libcairo package......unfortunately I'm not a programmer or anything so fixing a package is way beyond me.

EDIT: The problem should be solved with the new version of the libcairo2 package that came through the repo's today.

---

