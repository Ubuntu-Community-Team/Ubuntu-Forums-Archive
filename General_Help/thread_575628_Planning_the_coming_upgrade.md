---
title: "Planning the coming upgrade"
date: 2007-10-14
forum: General Help
---

### Post by thelugnut on 2007-10-14
I am presently running Ubuntu Fiesty 7.04.

Gutsy Gibbon, 7.10, is to be released in the next few days, around the 18th of October.

Can some kind soul provide me with a method to update. I would like to see the steps involved in a dist upgrade and the steps involved in a clean install.

I am, very obviously,  new to Ubuntu and I would like to get it right.

Thanks

The Lugnut

---

### Post by kshane on 2007-10-14
When Gutsy is released, Synaptic should have the option to upgrade your Feisty to Gutsy.  

Alternatively, there will be the Live CD and Alternate CD available for download from the Ubuntu web site, just as Feisty was.  You can then reformat your drive/partition and do a "clean install".


Kevin

---

### Post by FredB on 2007-10-14
Yes, the clean install is maybe the better option. Save your data, grab final or even rc ISO, install it.

You'll be quiet this way.

---

### Post by thelugnut on 2007-10-15
Thanks for the responses.

I understand that many prefer to do a clean install, but since I am so new at this, I think one way for me to get up on the power curve is to attempt a distribution upgrade.

But I do appreciate your advice and I am sure that in the future I  will attempt the clean-install method.;)

---

### Post by old_geekster on 2007-10-15
Here is how I upgraded from Feisty to Gutsy:

sudo update-manager -c -d

This thread will give you some help on upgrading:

[http://ubuntuforums.org/showthread.php?t=575632&highlight=gutsy+gibbon](http://ubuntuforums.org/showthread.php?t=575632&highlight=gutsy+gibbon)

Good luck!

---

### Post by reza81 on 2007-10-15
try
```

sudo apt-get dist-upgrade

```

---

