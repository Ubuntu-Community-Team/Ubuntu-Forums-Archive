---
title: "How to upgrade nvidia drivers?"
date: 2017-08-08
forum: General Help
---

### Post by russkyca on 2017-08-08
I can only find (What looks like outdated) steps to upgrade Nvidia drivers but they seem quite complicated or unnecessary - not that they wouldn't work but I was wondering if Ubuntu or Nvidia has a utility or program/application that might do it without having to do it manually?

Here's my info:
card:   EVGA GTX750
driver installed:  375.66

I use Synaptic Package Manager since it's still the easiest and best laid out program for 'looking' at versions, packages (files/applications) and options.   I'm not sure if it's better than the other installers but it has worked in the past.   But, I am using it in this instance to see what options there are for upgrading.   

I noted that the latest drivers are available in the Ubuntu 17.04 packages which is interesting and surprising.   That's good.  But, if I wanted to upgrade to it which is the best method now?   I was hoping there was a simpler method.   When I google it, I usually come up with what appears to be, outdated methods....for e.g., a method that was written a year ago.   

Synaptic shows that Nvidia ver. 359.84 (long-lived version) is available.   I figure it's better to have a more recent version so I should upgrade to either 381.22 or 384.59?

But, how?   I want to choose the method that won't result in problems later on.  :)    The manual way is usually a pain? :)

EDIT:  I want to add, or edit to say that there's *nothing* (that I could find, anyway) about upgrading drivers.   It's mostly instructions how to install drivers.   That is straight forward enough but what if you want to upgrade to drivers (most recent) but the 'Software Updates' only goes to the 'next' package version.   For e.g., 375.22 to 375.82

---

### Post by Autodave on 2017-08-08
If you have not installed any driver yet, or if you did through Synaptic, just go ahead and pick the one you want and let synaptic do it for you. You have to do nothing but permit it to update to the one you pick.

---

### Post by Autodave on 2017-08-08
Looking at Nvidia's website, it is recommending the 304.135 driver. Perhaps your best bet is to go into Settings -> Additional Drivers and see what that recommends.

---

### Post by vocx on 2017-08-08
> **russkyca said:**
> I can only find (What looks like outdated) steps to upgrade Nvidia drivers but they seem quite complicated or unnecessary - not that they wouldn't work but I was wondering if Ubuntu or Nvidia has a utility or program/application that might do it without having to do it manually?

Here's my info:
card:   EVGA GTX750
driver installed:  375.66

I use Synaptic Package Manager since it's still the easiest and best laid out program for 'looking' at versions, packages (files/applications) and options.   I'm not sure if it's better than the other installers but it has worked in the past.   But, I am using it in this instance to see what options there are for upgrading.   

I noted that the latest drivers are available in the Ubuntu 17.04 packages which is interesting and surprising.   That's good.  But, if I wanted to upgrade to it which is the best method now?   I was hoping there was a simpler method.   When I google it, I usually come up with what appears to be, outdated methods....for e.g., a method that was written a year ago.   

Synaptic shows that Nvidia ver. 359.84 (long-lived version) is available.   I figure it's better to have a more recent version so I should upgrade to either 381.22 or 384.59?

But, how?   I want to choose the method that won't result in problems later on.  :)    The manual way is usually a pain? :)

EDIT:  I want to add, or edit to say **that there's *nothing* (that I could find, anyway) about upgrading drivers.**   It's mostly instructions how to install drivers.   That is straight forward enough but what if you want to upgrade to drivers (most recent) but the 'Software Updates' only goes to the 'next' package version.   For e.g., 375.22 to 375.82
See this thread for a bit of an explanation on video drivers [https://ubuntuforums.org/showthread.php?t=2367744&p=13672333#post13672333](https://ubuntuforums.org/showthread.php?t=2367744&p=13672333#post13672333)

In general, there is no way of upgrading the video drivers. I hope you installed the drivers in the normal way, that is, by going to Settings > Software & update > Additional drivers.

Once you install the nvidia-375 package, you will have the latest drivers for your card and Ubuntu distribution. There is no reason for you to manually upgrade to the latest drivers; the system checks itself if a new package is released and then shows you there are updates, which you would then install. This is the proper way of getting the new drivers.

Do not be fooled about the numbering version, the numbers 359, 375, 381, etc. do not necessarily mean incremental updates. It may be that your card only works with the 375 but not the 381 driver, as that may actually target another family of cards.

If your system is currently working fine, then you should be happy with it and let it be. When you upgrade to the next Ubuntu version, a new set of drivers will be installed, so you will receive newer video drivers, but if it works fine now, you probably won't notice a significant change, and it will continue working fine.

---

### Post by russkyca on 2017-08-08
You guys are right, I just needed to go to 'Additional Drivers' and see what is available as installable options.   I did upgrade/update to 375.82 which the Nvidia Linux board states was part of the 'long-lived branch' version.  I do have the option of using 381.22 and 384.54 for my card, though.   I think the current driver I have installed is a version behind but I don't know whether it's better to have one of the most recent drivers or not.   

Under supported products, my card is supported - so, I could use either of those drivers.   I have a GTX 750, currently.

I think Ubuntu is doing a good job keeping up-to-date with drivers and having a relatively easy method for updating/upgrading.   I don't know if I should upgrade but I have had some crashes lately but I don't think it's related to video drivers.  Mostly freezing of my screen and my browser 'hanging.'

---

### Post by russkyca on 2017-08-09
Is there a way to compare the drivers?

---

### Post by vocx on 2017-08-09
> **russkyca said:**
> Is there a way to compare the drivers?
No. Why do you want to do this?

It's like saying, how to compare two processors? Well, you use both, run the same set of tests, and see, measure, and empirically feel which is better. Not very reliable.

You may run "glxgears" and "glxinfo", and test online and local videos, and games, and figure out if there is any difference. But I wouldn't bother.
```

glxgears
glxinfo

```

---

