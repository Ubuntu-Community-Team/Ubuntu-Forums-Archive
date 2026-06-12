---
title: "sound has stopped working"
date: 2005-10-24
forum: General Help
---

### Post by sexcopter on 2005-10-24
Hi there, when I installed Breezy, I was delighted that the sound work pretty much aok straight from installation, but there was one glitch: the spdif/headphone socket didn't work. I was trying to solve this by following howto's, forums etc to install new intel hda drivers, and it's all gone a bit pete tong; I now appear to have no sound device.
What I'd like is to either a) get some proper drivers working, which might get the spdif/headphone socket working as well, or b) just restore everything to how it was. Regarding option b), is there a way to say to Ubuntu "ok start again from fresh and set my sound up please"?

Here's some (not-so-useful) info:

james@james:~$ aplay -l
aplay: device_list:218: no soundcards found...
james@james:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory

Now, I *think* my sound card has something like alc880 in the name, but I'm not savvy enough to know what's what in codes. Just thought I'd mention it, in case it rings any bells to anyone.

Any help mucho appreciated! Cheers,

James.

*edit* I've just found this info out through device manager:
[http://users.fission.org.uk/~sexcopter/Screenshot-Device%20Manager.png](http://users.fission.org.uk/~sexcopter/Screenshot-Device%20Manager.png)
*/edit*

---

