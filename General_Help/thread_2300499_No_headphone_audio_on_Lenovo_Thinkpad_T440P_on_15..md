---
title: "No headphone audio on Lenovo Thinkpad T440P on 15.10 (Fresh Install)"
date: 2015-10-26
forum: General Help
---

### Post by Peter_Warwick-Maho on 2015-10-26
Thanks in advance for any suggestions you might have.

I've been an avid Ubuntu user for a decade and very rarely had any issues. But this one I have been unable to solve!

Since installing a fresh 15.10 Desktop on my Lenovo Thinkpad T440P I have not had audio from my Headphone jack.

I can confirm that:
[LIST]
[*]the speaker/jack switch works fine, when my headphones are plugged in it mutes the speaker
[*]I have tried a variety of lines added to my alsa-base.conf file, but am open to suggestions
[*]It did work once after I turned it on, but just that once and I could not see that as part of a pattern
[*]I have removed pulseaudio to test it directly via alsa (with no success) and have since reinstalled pulseaudio
[*]I have disabled auto-mute in alsamixer
[*]I have played around a good deal with levels in alsamixer
[/LIST]

One thing that is unexpected, is the alsamixer shows two headphones, labelled "headphone" and "headphone 1". The second one is always on 00, and I have been unable to change that.

The speaker/headphones mute switch that happens when plugging or unplugging the headphones affects "headphone". I suspect the issue might be the sound is trying to come out of the permanently set to 00 "headphone 1", but I cannot be sure.

Any help would be greatly appreciated!

Peter

[IMG]http://i.imgur.com/UyGbJn9.png[/IMG]

---

### Post by Peter_Warwick-Maho on 2015-10-26
Further information:
I have noted if I turn the laptop on with the speaker jack removed, and then plug them in after the laptop is logged in it works fine. (Even with the "Headphone"+"Headphone 1" issue--so I don't thin that's the issue).

---

### Post by al6x on 2015-10-28
I also have a T440P that I just upgraded to 15.10, and I am having the same problem. However when I try to work around you mentioned above I have no luck.
EDIT:
I am dual booting Windows 10 with Ubuntu 15.10, and I am experiencing the same problem in Windows 10 too.

---

### Post by djpate on 2015-10-29
Same here on T440s.

I did an upgrade from 15.04.
Worked fine the first day.
Speaker is muted when headphones is plugged in but no audio in headphones.

Waiting for full boot before plugin in does not work for me.

I hope we can fix this. This laptop is supposed to be certified for Ubuntu.

---

### Post by djpate on 2015-10-29
Fixed it by following this comment.

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1508826/comments/15](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1508826/comments/15)

---

### Post by blm-ubunet on 2015-10-29
redundant info

---

### Post by BHSPitMonkey on 2015-11-03
The same thing happened to me after upgrading to 15.10 on a T540p, but I use the machine with a dock (Lenovo Ultra Dock). The audio jack on the side of the laptop has stopped working, and the one on the back of the dock has taken its place and works as expected when something is plugged into it.

Fortunately this is convenient for me since my headphones stay where the dock lives. Still, it would be nice if the jack on the laptop body took precedence, or if the audio settings UI exposed a way of choosing which one to make active.

---

