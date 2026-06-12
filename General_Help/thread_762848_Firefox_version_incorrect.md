---
title: "Firefox version incorrect"
date: 2008-04-22
forum: General Help
---

### Post by anna_vt on 2008-04-22
I've been migrating from windows, and am trying to install some of the add-ons that I use on Firefox.  I am having a problem with the version of Firefox.  The about Firefox window says:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20071008 Ubuntu/7.10 (gutsy) Firefox/2.0.0.6

But a lot of the addons I require need 2.0.014.  I have tried uninstalling and reinstalling 2.0.0.14 with synaptic, but I keep getting version 2.0.0.6.

Any ideas on how to get 2.0.0.14?
Cheers

---

### Post by Het Irv on 2008-04-22
```
sudo apt-get install firefox
```
installs FireFox
```
sudo apt-get update
```
gets updates
```
sudo apt-get upgrade
```
installs updates

This should get you the latest version for Firefox.

---

### Post by phidia on 2008-04-22
Download the version you require [here]("http://www.mozilla.com/en-US/firefox/all.html#en").
You can install that version along with the one synaptic installs. 
Just create a seperate launcher for the newer version so you can select that  when you need to.

---

### Post by RainCT on 2008-04-22
I just wanted to say that I don't recommend you using an older version, especially since them you won't benefit from the security updates.

---

### Post by phidia on 2008-04-22
I am running an up-to-date gutsy and it doesn't have the .14 version.
The OP didn't say what version of ubuntu is installed.

---

### Post by Het Irv on 2008-04-22
When was .14 released? Sometimes it takes a few days for the updates to be repackaged for Ubuntu.

---

### Post by anna_vt on 2008-04-22
None of these solutions have worked :(

I think maybe it is v...14 but thinks its 6

Any more ideas?

---

### Post by phidia on 2008-04-22
Have you been able to run this > sudo apt-get update command successfully?

After I posted here the package manager notified me of updates and now the .14 Firefox version is available.

What version of Ubuntu are you using?

> I think maybe it is v...14 but thinks its 6


What thinks it's version 6? What plug in are you trying to install?

---

### Post by Archmage on 2008-04-22
Wait a week than upgrade to Hardy. You'll have a much newer Firefox.

---

