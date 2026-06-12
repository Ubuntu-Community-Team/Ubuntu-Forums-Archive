---
title: "Web pages randomally closed."
date: 2008-01-22
forum: General Help
---

### Post by stasia on 2008-01-22
Started a little over 2 months ago. No one could understand why. Now I'm coming to the forums for some advice.
I really don't know to much about Ubuntu so any tech. help I can get would be greatly appreciated. My browser is Mozilla only on random pages will it close. Sometimes yahoo, sometimes myspace. Normally when I start checking my email is when it closes the most anymore. Used to be yahoo and myspace.

---

### Post by djrobthaman on 2008-01-22
It's probably flash.  Adobe's flash player for linux is lackluster to say the least.  I have firefox crashes on a daily basis because of that thing.

---

### Post by stasia on 2008-01-22
Anyway to actually fix it if that is the problem?

---

### Post by djrobthaman on 2008-01-22
Send naughty emails to adobe???

Right now, I don't think there's anything you can really do.  That said, if you figure something out don't hesitate to pass on the knowledge

---

### Post by stasia on 2008-01-22
Thanks for the info.

---

### Post by hikaricore on 2008-01-24
Turns out that firefox was crashing with the following occasionally:

```
firefox-bin: pcm_params.c:2351: sndrv_pcm_hw_params: Assertion `err >= 0' failed.
```

The user's system is using pulseaudio (for good reasons) and a possible fix was to edit the following:

**/etc/firefox/firefoxrc**

Changing from:

> # which /dev/dsp wrapper to use
FIREFOX_DSP="none"

To:


> # which /dev/dsp wrapper to use
FIREFOX_DSP="padsp"

The user is still testing to see if this fixes it completely.

---

### Post by stasia on 2008-01-24
and any follow ups will be posted on the test. :)

---

