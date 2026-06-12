---
title: "Default audio device"
date: 2018-11-26
forum: General Help
---

### Post by dcroxton on 2018-11-26
Since the upgrade to 18.10, alsa always defaults to the wrong audio device.  I have to go into alsamixer and then force-reload to get sound.

I have seen various solutions to this problem, but they are all either outdated or do not apply to Xubuntu.  It seems like I ought to be able to set the default audio device by changing /etc/asound.conf, but I updated it and it still doesn't work.  (Full asound.conf below.  I searched for my sound card and changed "type hw card 0 device 1" to "card 1 device 1," but it still goes to the same (incorrect) device every time I reboot.)

```
pcm.!default {
      type plug slave.pcm {
            type hw card 1 device 1
      }
}

```

---

### Post by CatKiller on 2018-11-27
Why mess with ALSA directly when PulseAudio makes it simple to set the default device?

---

### Post by dcroxton on 2018-11-27
> **CatKiller said:**
> Why mess with ALSA directly when PulseAudio makes it simple to set the default device?

And how would I do that?

---

### Post by CatKiller on 2018-11-27
> **dcroxton said:**
> And how would I do that?

I haven't used Xfce in quite a while, but in Gnome and KDE the volume widget on the panel interfaces with PulseAudio. I can't think of a reason why Xfce would do something different.

Otherwise, there is pavucontrol (which I suspect isn't installed by default) which will let you play with PulseAudio more directly. Disabling a device or setting the default device are just drop-down selections.

---

### Post by dcroxton on 2018-11-27
> **CatKiller said:**
> I haven't used Xfce in quite a while, but in Gnome and KDE the volume widget on the panel interfaces with PulseAudio. I can't think of a reason why Xfce would do something different.

Otherwise, there is pavucontrol (which I suspect isn't installed by default) which will let you play with PulseAudio more directly. Disabling a device or setting the default device are just drop-down selections.

Well, there's the rub.  Xfce does not have a panel volume control for some reason (I think removing it was a poor decision).  I had installed pavucontrol, but the device I want doesn't show up in the dropdown unless I select it via alsamixer first.

---

### Post by QIII on 2018-11-27
I don't use Xfce, but ...

I found [this]("https://www.youtube.com/watch?v=Q_vw0dC0Ba0") fairly recent Youtube video that might be helpful.

---

### Post by dcroxton on 2018-11-27
> **QIII said:**
> I don't use Xfce, but ...

I found [this]("https://www.youtube.com/watch?v=Q_vw0dC0Ba0") fairly recent Youtube video that might be helpful.

Thanks, that is helpful in general.  However, it still brings me to pavucontrol, which still does not have the audio device that I need (which is, oddly, the one on the motherboard itself) unless I set it in alsamixer first.

---

### Post by CatKiller on 2018-11-27
> **dcroxton said:**
> Well, there's the rub.  Xfce does not have a panel volume control for some reason (I think removing it was a poor decision).  I had installed pavucontrol, but the device I want doesn't show up in the dropdown unless I select it via alsamixer first.

OK, I can see how that could be a problem.

[This page]("https://www.alsa-project.org/main/index.php/Setting_the_default_device") suggests that rather than specifying the attributes of the device in your asound.conf, you can simply use ```

   defaults.pcm.card 1
   defaults.ctl.card 1
``` to pick the default.

Perhaps that would be more persistent for you?

(The slave in your default device also looks odd, but I don't have masses of experience of directly fiddling with ALSA. It's also possible that having any device specified in asound.conf is messing with the magic: I don't even have an /etc/asound.conf)

---

### Post by dcroxton on 2018-11-27
Well, that solved the problem -- I got rid of asound.conf, and it works.  I don't remember adding that file, but I may have done it at some point in the past (I have been using Ubuntu since Warty), probably to solve some other problem.

Thanks for your help!

---

