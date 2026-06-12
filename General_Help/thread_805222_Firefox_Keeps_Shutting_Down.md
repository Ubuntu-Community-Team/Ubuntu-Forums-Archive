---
title: "Firefox Keeps Shutting Down"
date: 2008-05-23
forum: General Help
---

### Post by RATM_Owns on 2008-05-23
Whenever I may go to a different page on YouTube, the firefox window just shuts down and I get the "Restore Tabs" thing whenever I reopen it.

Any work around? I'm using 3.0b5, so would the 2.0.0.14 browser work better?

---

### Post by Jaxilian on 2008-05-27
I have same problem. I got it both in FF2 as in FF3. No clue of why it happens. At least Internet Explorer gives an error message when a problem occurs :lolflag:

---

### Post by Majorix on 2008-05-27
Which Flash Player you use? Adobe or Gnash? Change the provider if you continue to see the same problem (don't forget to completely remove the other one).

---

### Post by ricky_bains on 2008-05-27
yes i have stucked vid same problem i tried by installing opera thinking that must be due to Firefox corruption but opera also crashed when youtube or javascript enabled feature countred

---

### Post by sizzam on 2008-05-27
I was having the same problem with Flash videos crashing Firefox.  There is an open bug ticket for this here:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888)


I corrected the problem for myself with these steps (gleaned from the bug ticket):

**Remove your current Flash plugin and libflashsupport (if installed):**
```
$ sudo apt-get remove flashplugin-nonfree libflashsupport
```

**Install Flash 10 Beta:**
Download the tar.gz from here:  [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
Untar, enter directory via command line,
```
$ sudo ./flashplayer-installer
```
When prompted for the installation path, I entered:
```
/usr/lib/firefox-3.0b5
```

That installs the beta Flash player that has a code fix that allows it to work correctly with PulseAudio.

**Then, make these config changes for PulseAudio:**

```
$ sudo gedit /etc/asound.conf
```
Enter the following into this file:
```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

```

**Finally, install the libasound2-plugins package:**
```
$ sudo apt-get install libasound2-plugins
```

I have been crash-free since performing these steps.

---

### Post by Jaxilian on 2008-06-24
I did as above,but problem still remains

---

