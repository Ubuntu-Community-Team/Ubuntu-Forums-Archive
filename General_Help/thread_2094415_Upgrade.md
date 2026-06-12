---
title: "Upgrade"
date: 2012-12-13
forum: General Help
---

### Post by waltwin on 2012-12-13
I guess it is time to update my ubuntu 10.10. Can I just go to 12.01 or do I  need to do it in steps?

Also, is it possible to maintain the same format as 10.10? I did upgrade one machine to 11.1 but didn't much care for the format.

Thank you in advance.

waltwin

---

### Post by snowpine on 2012-12-13
I recommend that you back up all your data to an external drive and then test-drive a Live DVD/USB of 12.04 or 12.10 (there is no 12.01 release). If you enjoy it then go ahead and do a fresh install (either replacing or side by side with your current install).

Here is complete information on upgrading an "end of life" release, if you decide not to take my advice about doing a test drive & fresh reinstall: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by Pjotr123 on 2012-12-13
A clean upgrade is always best, for all operating systems under the sun. Do it like this:
[https://sites.google.com/site/easylinuxtipsproject/reinstallation](https://sites.google.com/site/easylinuxtipsproject/reinstallation)

---

### Post by Kirk Schnable on 2012-12-13
> **waltwin said:**
> I guess it is time to update my ubuntu 10.10. Can I just go to 12.01 or do I  need to do it in steps?
Like snowpine, I believe a fresh install is the best way to approach this. 

> **waltwin said:**
> Also, is it possible to maintain the same format as 10.10? I did upgrade one machine to 11.1 but didn't much care for the format.
By "format" I assume you mean the new Unity desktop interface?

Unity has come a long way since 11.10, I myself was not a fan of it then at all.  I am, however, currently running Unity on my laptop as well as my desktop at work, and I now find it quite well suited to my needs.

If you would like to have Ubuntu 12.04 without the Unity interface, you have the option of installing one of the other distributions such as Kubuntu (has KDE), Xubuntu (has XFCE), or Lubuntu (has LXDE).

As snowpine suggested, you're welcome to download and try Live CDs of each of these flavors of Ubuntu.

---

### Post by Cheesemill on 2012-12-13
Firstly there is no such thing as 12.01, you're probably thinking of 12.10.

There is no direct upgrade path, you would have to do 4 separate upgrades:

10.10 > 11.04 then 11.04 > 11.10 then 11.10 > 12.04 then 12.04 > 12.10.

I really wouldn't recommend attempting this as it more than likely wont succeed, it will be a lot easier and quicker to just back up your data and do a fresh installation of 12.10.

The default environment that you are thinking of (Gnome 2) is no longer available. You can either use Gnome 3 in fallback mode which looks similar or switch to a different desktop environment such as XFCE (Xubuntu) or LXDE (Lubuntu).

---

### Post by oldfred on 2012-12-14
I believe before 12.04 it was gnome fallback. But with 12.04 & gnome3 it is called gnome-panel but almost the same thing.

       gnome3 classic
sudo apt-get install gnome-panel
On login screen click on cog-wheel/star and choose 
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)
12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) 
[http://ubuntuforums.org/showthread.php?t=2090021](http://ubuntuforums.org/showthread.php?t=2090021)
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

---

