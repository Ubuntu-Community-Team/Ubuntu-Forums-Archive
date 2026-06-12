---
title: "Adept Updater &amp; Manager Crashing?"
date: 2007-10-23
forum: General Help
---

### Post by handy on 2007-10-23
I have been having the Adept Manager problem for a couple of days on one machine, I have reinstalled on the other, & fresh as can be it won't download from the Manager without crashing?

Fresh machine did do an Adept Update, the other will not, attached a picture for all that its worth.

This is a serious bug, my 2 machines are very different hardware, my internet has no problems at the moment, my wife's Mac is functioning perfectly on the web.

It gets hard to fix bugs when you can't auto download a fix.

---

### Post by eudemus on 2007-11-17
any sign of an answer to this? my adept applications crash as well - they're convinced that there's another adept application already running, which (having checked) there isn't.

What's going on? 
Eudemus

---

### Post by Paul Gilster on 2007-11-17
Same problem here. Started two days ago when trying to run Adept to bring in the latest updates. The update process started, then crashed. Ever since, Adept won't start, claiming it's already in use.

---

### Post by Paul Gilster on 2007-11-17
OK, solved at least at this end via terminal. Had tried:

sudo apt-get update
sudo apt-get upgrade

and was told to reconfigure dpkg. 

sudo dpkg --configure -a

System asked for one choice re replacing a package. The default was to leave it alone, and that's what I chose. Problem seems to be fixed.

---

### Post by hangfire on 2007-11-17
Same problem. **sudo apt-get update** and **sudo apt-get upgrade** do not fix it. **sudo dpkg --configure -a** does not fix it. 

When I run **sudo adept_ **(anything), all programs in the adept_* family seg fault:
adept_batch      adept_manager    adept_updater
adept_installer  adept_notifier

I have a brand-new Kubuntu 7.10 install from DVD that can't update itself, at least not with Adept.

-HF

---

### Post by hangfire on 2007-11-17
Fixed the problem... haha... installed synaptic with the command line:

**[FONT="Courier New"]sudo apt-get install synaptic[/FONT]**

Works great.

On 6.06LTS I only used Adept because of the desktop notifier for updates, for everything I used Synaptic. It looks like for 7.10 I will use Synaptic for everything!

---

### Post by mastergunner on 2007-12-20
.......

---

### Post by theZoid on 2008-04-22
My Adept crashes constantly with Kubuntu Hardy Heron RC....I've finally given up and similarly have installed Synaptic which is flawless.  Whey can't they correct this, or just give us synaptic?

---

