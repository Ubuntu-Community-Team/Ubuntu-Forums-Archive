---
title: "Ubuntu upgraded kernel.. now my sound doesn't work.."
date: 2007-04-12
forum: General Help
---

### Post by billdotson on 2007-04-12
when I run things that require sudo in the terminal I get this message:

```

ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM default

```

it worked fine before the kernel updated.  It is weird.. I think the kernel updated to the same version that it already was.  The soundcard works in Windows and when I go to click on the sound manager in the system tray I get this message in a dialog box

```

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

```

what is going on?

---

### Post by bettlebrox on 2007-04-12
Install alsa-utils and run alsaconf (using sudo) and see if you can reconfigure your sound drivers.

---

### Post by billdotson on 2007-04-14
I have alsa-utils installed.. but it says there is no alsaconf command.  Hmmm....?

---

### Post by drpaul on 2007-04-14
If you have previously upgraded your alsa driver to fix some sound problem, then you have to go through the old procedure again with the new kernel stuff. That's what I did to revive sound after the update.

HTH

Paul

---

### Post by bettlebrox on 2007-04-15
> **billdotson said:**
> I have alsa-utils installed.. but it says there is no alsaconf command.  Hmmm....?
Maybe the Ubuntu version of the package doesn't have the command anymore? I've a Debian workstation & a Ubuntu laptop so Debian has the command, and Ubuntu doesn't? Sorry for the confusion.

---

### Post by billdotson on 2007-04-15
I installed the latest ALSA driver from source and then rebooted and I have sound back.  Problem solved!

Thanks

---

