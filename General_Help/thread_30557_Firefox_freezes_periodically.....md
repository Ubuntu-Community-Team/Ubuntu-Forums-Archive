---
title: "Firefox freezes periodically...."
date: 2005-04-29
forum: General Help
---

### Post by Turin Turambar on 2005-04-29
Firefox freezes periodically if/when pages have a flash animation.
Now, I read here that some guys experienced the same thing, although their FF was crashing, mine "just" freezes. I wonder if there is a cure for this?
I installed the flash with a click on the "missing plugin" icon.

---

### Post by nocturn on 2005-04-29
[QUOTE=Turin Turambar]Firefox freezes periodically if/when pages have a flash animation.
Now, I read here that some guys experienced the same thing, although their FF was crashing, mine "just" freezes. I wonder if there is a cure for this?
I installed the flash with a click on the "missing plugin" icon.[/QUOTE]

Do you have an Nvidia graphics card?
If so, after the crash, check dmesg for the message NVRM XID.

---

### Post by Turin Turambar on 2005-04-29
No, my card is ATI 9000PRO with Fglrx drivers working excellent and it does NOT crash! Never, just freezing....

---

### Post by nocturn on 2005-04-29
[QUOTE=Turin Turambar]No, my card is ATI 9000PRO with Fglrx drivers working excellent and it does NOT crash! Never, just freezing....[/QUOTE]

Is FireFox freezing, or the entire screen?

---

### Post by Turin Turambar on 2005-04-29
Just firefox.... this usually happens when the page (containing a flash animation) is fully loaded, I click on some link and scroll the existing page. Instead of loading another page (clicked from the link), firefox freezes and I have to force closing.
It runs normally without the flash plugin. I tried installing flash-nonfree, but the same happens. ;(

---

### Post by Turin Turambar on 2005-04-29
Well, I just found out that when I killed ESD process, I had no flash lockups!

However, I do not have sound now, anywhere. ;(
Any fix for this? Can Ubuntu use ALSA as a default source?

---

### Post by bvc on 2005-04-29
[http://www.ubuntuforums.org/showthread.php?p=152567#post152567](http://www.ubuntuforums.org/showthread.php?p=152567#post152567)
I'm not using esd, and never have, and still lock up.

---

### Post by Xerampelinae on 2005-04-29
[QUOTE=Turin Turambar]Well, I just found out that when I killed ESD process, I had no flash lockups!

However, I do not have sound now, anywhere. ;(
Any fix for this? Can Ubuntu use ALSA as a default source?[/QUOTE]
 Maybe try these directions

[http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)

---

### Post by Turin Turambar on 2005-04-29
I think I solved it with the sound settings found in a unofficial guide, HOWEVER
there's a bad line for the suggested values in asound.conf

It says:

```
pcm.!default {
type plug
slave.pcm "dmixer"
```


It should say:

```
pcm.!default {
type plug
slave.pcm "pcm.card0" 
```

If you do not change the last value, you'll get a message like "unable to open slave..." or something like that.

---

### Post by Xerampelinae on 2005-04-29
I think the settings can vary a bit depending upon your machine.   The given settings worked fine on all machines except my laptop, where I had to replace hw1,0 with hw0,0...

Glad that it's working.

---

### Post by Turin Turambar on 2005-04-29
[QUOTE=Xerampelinae]I think the settings can vary a bit depending upon your machine.   The given settings worked fine on all machines except my laptop, where I had to replace hw1,0 with hw0,0...

Glad that it's working.[/QUOTE]

Now, that's even better! I don't need to change mixer settings. Thanks! :)

---

