---
title: "Changing Icon themes."
date: 2014-04-21
forum: General Help
---

### Post by David_Aaron_Groves on 2014-04-21
I have added a PPA for the Faenza Icons, but I am semi-new to Lubuntu, used it before but only just to see what it was about. Now that I really am using it as a permanent solution on my old lappy, I want the Faenza Icon theme. I have downloaded and installed the theme, but how do I switch the icon theme in Lubuntu? I am using the newest LTS version of Lubuntu BTW.
David

---

### Post by Dennis N on 2014-04-22
> I have downloaded and installed the theme, but how do I switch the icon theme in Lubuntu?

You switch the theme in:

Menu > Preferences > Customized Look and Feel > Icon Theme Tab

Select Faenza from the list on the left, then press the APPLY button and they will change.

---

### Post by oscarivera9 on 2014-04-22
I just recently upgraded to 14.04 from 12.04LTS and I used to use the Faenza icons before but now they don't seem to work.  I've gone through all of the proper steps I need to make so that I can use them and yet they're still not changing.  I'm wondering if maybe this is a bug with the new release.
    I downloaded the files, extracted them, copied them over to /usr/share/icons, then I used Unity Tweak to select them and nothing happens

---

### Post by David_Aaron_Groves on 2014-04-22
> **Dennis N said:**
> You switch the theme in:

Menu > Preferences > Customized Look and Feel > Icon Theme Tab

Select Faenza from the list on the left, then press the APPLY button and they will change.

Ahh thank you! That was easier than expected!

---

### Post by David_Aaron_Groves on 2014-04-22
> **oscarivera9 said:**
> I just recently upgraded to 14.04 from 12.04LTS and I used to use the Faenza icons before but now they don't seem to work.  I've gone through all of the proper steps I need to make so that I can use them and yet they're still not changing.  I'm wondering if maybe this is a bug with the new release.
    I downloaded the files, extracted them, copied them over to /usr/share/icons, then I used Unity Tweak to select them and nothing happens

I find that adding the PPA for them is much easier than downloading and extracting.

```
sudo add-apt-repository ppa:tiheum/equinox
```
```
sudo apt-get update && sudo apt-get install faenza-icon-theme
```
Then change the icon theme in your settings. Not sure which distro you are using...

---

### Post by vasa1 on 2014-04-22
> **David_Aaron_Groves said:**
> ... Then change the icon theme in your settings. Not sure which distro you are using...
Seems to be Ubuntu and not Lubuntu.
If **your issue** is solved please mark the thread [SOLVED]. You can look at [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads) for how to do so. Thanks :)

---

### Post by oscarivera9 on 2014-04-28
> **David_Aaron_Groves said:**
> I find that adding the PPA for them is much easier than downloading and extracting.

```
sudo add-apt-repository ppa:tiheum/equinox
```
```
sudo apt-get update && sudo apt-get install faenza-icon-theme
```
Then change the icon theme in your settings. Not sure which distro you are using...

I tried to add the ppa and it wouldn't let me.
I used to use faenza with Ubuntu 12.04 but now that I've updated to 14.04 I can't get faenza to work.

---

### Post by Dennis N on 2014-04-28
> I tried to add the ppa and it wouldn't let me.
I used to use faenza with Ubuntu 12.04 but now that I've updated to 14.04 I can't get faenza to work. 

There is no Faenza package yet for Trusty in that repository, so the PPA won't accept your request. Either try later when there is one available, or you can get the same set of icons from: 

[http://gnome-look.org/content/show.php/Faenza?content=128143](http://gnome-look.org/content/show.php/Faenza?content=128143)

---

### Post by oscarivera9 on 2014-04-29
> **Dennis N said:**
> There is no Faenza package yet for Trusty in that repository, so the PPA won't accept your request. Either try later when there is one available, or you can get the same set of icons from: 

[http://gnome-look.org/content/show.php/Faenza?content=128143](http://gnome-look.org/content/show.php/Faenza?content=128143)

Thanks,
That's what I figured.  That explains everything.

---

