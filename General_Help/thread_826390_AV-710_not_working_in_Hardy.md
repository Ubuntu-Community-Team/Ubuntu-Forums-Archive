---
title: "AV-710 not working in Hardy"
date: 2008-06-11
forum: General Help
---

### Post by ed3120 on 2008-06-11
I can't get my Chaintech AV-710 to work in 8.04.  I know the card and the PCI slot it is sitting in work properly, because if I boot into Windows there is no issue and I can hear sound from the SPDIF.

Linux can see the card:```

ed@mythtv:/etc$ lspci | grep audio
01:08.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
ed@mythtv:/etc$

```

...but when I try to restart or launch ALSA...```

ed@mythtv:/etc$ sudo /etc/init.d/alsa-utils restart                              * Shutting down ALSA...                                                         * warning: 'alsactl store' failed with error message 'alsactl: save_state:1251: No soundcards found...'...                                              [fail]
 * Setting up ALSA...                                                    [ OK ]
ed@mythtv:/etc$
ed@mythtv:/etc$ alsamixer
alsamixer: function snd_ctl_open failed for default: No such file or directory
ed@mythtv:/etc$
```

My Ubuntu Settings Manager -> Sound doesn't show any sound cards.

If I reboot and re-enable my onboard sound, I can succesfully get analog sound working.  I can also restart ALSA, but I still get an error when I launch it....

```

ed@mythtv:~$ lspci | grep audio
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
01:08.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
ed@mythtv:~$
ed@mythtv:~$ sudo /etc/init.d/alsa-utils restart
 * Shutting down ALSA...                                                 [ OK ]
 * Setting up ALSA...                                                    [ OK ]
ed@mythtv:~$
ed@mythtv:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory
ed@mythtv:~$

```

....I find it odd that ALSA still errors out, but the analog onboard sound does work.

Regardless, I just can't get my AV-710 to work.  I've tried using the /etc/asound.conf recommended in this thread, but no luck:

[http://ubuntuforums.org/showthread.php?t=187920&highlight=av-710](http://ubuntuforums.org/showthread.php?t=187920&highlight=av-710)

---

### Post by iaculallad on 2008-06-11
Try to add yourself to the "plugdev" group then try restarting ALSA.

---

### Post by ed3120 on 2008-06-11
Unfortunately, I'm already in it...

```
ed@mythtv:~$ sudo useradd -G plugdev ed
[sudo] password for ed: 
useradd: user ed exists
ed@mythtv:~$
```

---

### Post by iaculallad on 2008-06-11
On your terminal:

Take note of whatever displays when you issue the command below:

```
sudo asoundconf list
```

Create a backup of this file for editing:

```
sudo cp /usr/share/alsa/user-must-execute-asoundconf-set-default-card.update-notifier /usr/share/alsa/user-must-execute-asoundconf-set-default-card.update-notifier.backup
```

Open it for editing:

```
sudo gedit /usr/share/alsa/user-must-execute-asoundconf-set-default-card.update-notifier
```

Locate the section in the user-must-execute-asoundconf-set-default-card.update-notifier file w/c reads:

> asoundconf set-default-card

And append whatever value you got when you issue the command **sudo asoundconf list**

Example:

> asoundconf set-default-card ICH5

Re-issue the command or Restart:

```
sudo /etc/init.d/alsa-utils restart 
```

---

### Post by ed3120 on 2008-06-11
What if 'sudo asoundconf list' returns only one card:

CK804

I think this is my onboard sound.  It doesn't seem to pick up my AV-710.

---

### Post by iaculallad on 2008-06-11
> **ed3120 said:**
> What if 'sudo asoundconf list' returns only one card:

CK804

I think this is my onboard sound.  It doesn't seem to pick up my AV-710.

Check if your AV-710 card is present when you issue lspci.

```
lspci
```

---

### Post by ed3120 on 2008-06-12
Oddly enough, it is...

```
ed@mythtv:~$ lspci | grep audio
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
01:08.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)

```

---

### Post by ed3120 on 2008-07-28
Is there anything else that I can check?

---

### Post by arloth on 2008-07-30
I've been having similar problems with this card.  It shows up in lspci, but I can't get any sound out of it.  A lot of other people seem to be having issues with this card judging by the forum posts, but there is a definite lack of solutions.

Help would be much appreciated.

---

### Post by cariboo on 2008-07-31
You may want to turn off your onboard sound in the bios and try agian.
Eliminate any other sources of problems and try again.

Jim

---

### Post by arloth on 2008-07-31
Yes, the onboard sound is disabled in the BIOS.

---

### Post by ed3120 on 2008-11-09
This still isn't working for me.  Are there any other things that I could try?

---

