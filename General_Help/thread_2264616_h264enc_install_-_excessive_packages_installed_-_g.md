---
title: "h264enc install - excessive packages installed - general weirdness"
date: 2015-02-08
forum: General Help
---

### Post by JamButty on 2015-02-08
Just need a reality check. On advice from this page
/askubuntu.com/questions/384650/how-to-install-h-264-decoder
 in order just to add a codec for playing/converting mp4 files I entered
sudo apt-get install h264enc
and it installed 22 packages, which seemed excessive, then popped up a scary BIOS-looking menu, asking me for option on configuring my mail server. Wha?? Chose "leave unchanged" and continued.

Is this normal?  How can media codecs be related to mail handers? I have the full install output, if needed.

---

### Post by mc4man on 2015-02-08
Well based on the ask u. question then that was rather poor advice. h264enc has nothing to do with enabling h264 decoding support for anything.
partial package description - 
> A shell script which makes it easy to encode DVDs or video files to the
H.264/AVC/MPEG-4 Part 10 video format using MEncoder from the MPlayer
project.


The number of packages installed was probably reasonable & I guess you could make some use of it for some types of encoding. If installing it managed to enable decoding support in some player then consider that an incidental benefit to your time reading & installing.

---

### Post by grahammechanical on 2015-02-08
I found this home site for h264enc and among its miscellaneous features is this:

> 
[LIST]
[*]Email notifications when encoding finishes.
[/LIST]


[http://h264enc.sourceforge.net/faq.html](http://h264enc.sourceforge.net/faq.html)

Not so sinister after all. And the user is given the opportunity to decline use of the feature.

Regards.

---

### Post by JamButty on 2015-02-08
Thanks for the quick replies! I will dig around some more.

---

### Post by andrew.46 on 2015-05-16
h264enc and its twin xvidenc produce surprisingly good results when you consider that MEncoder development ceased quite some time ago...

---

