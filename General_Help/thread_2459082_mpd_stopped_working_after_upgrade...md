---
title: "mpd stopped working after upgrade.."
date: 2021-03-10
forum: General Help
---

### Post by Furycd001 on 2021-03-10
HI guys.. I have mpd installed on xubuntu 20.04.2. My music library gets picked up no problem with ncmpcpp, but I cannot play any songs. I simply get no audio. [Here's my mpd.conf]("https://termbin.com/7zg0") & [here's my ncmpcpp config]("https://termbin.com/uf00"). Whenever I run *"mpc" *I get the following error..

```
ERROR: Failed to enable output "esd" (pulse); pa_context_connect() has failed: Connection refused
```

While getting audio to work again, I'm also trying to set mpd to work over my network so I can access my music from my android devices. Any help appreciated & many thanks in advanced....

---

### Post by TheFu on 2021-03-10
I use** ncmpc** to control my mpd servers from Linux.  Never looked at ncmpcpp, sorry.
On android, I use f-droid with an app .... **M.A.L.P.**  or something like that.  I have 3 mpd servers around the house, so being able to switch to a different server to control is handy. MALP works on my phones and tablets.

```
$ more ~/.ncmpc/config
host = istar
# port = 
crossfade-time = 2
list-format = "[%artist%|(n/a)]-[%album%|(n/a)] - [%track%-| ][%title%|(title n/a)]"

```

istar is the mpd server. I'm using mostly defaults for everything else.
On istar, the only changes I made to the mpd.conf file was:
```
bind_to_address         "any"
audio_output {
        type            "alsa"
        name            "My ALSA Device"
#       device          "hw:0,0"        # optional
        mixer_type      "software"      # optional
#       mixer_device    "default"       # optional
#       mixer_control   "PCM"           # optional
#       mixer_index     "0"             # optional
}
```
The software mixer was very important.  I use that on the raspberry pi mpd servers too. Everything else is default. I don't have passwords. It is just music and the access to the music is through read-only mounts, so these systems can't delete anything.

It would be nice if I had correctly learned to use 1 mpd server that would output the audio to the other systems over the network. PulseAudio networking is beyond my skill. I spent about 30 minutes trying to get that working, but gave up.

---

### Post by Furycd001 on 2021-03-10
Thanks for the reply :) I believe my problem is more mpd or ubuntu rather than ncmpcpp. Before I upgraded from 18.04 to 20.04 everything was working fine. Setting mpd up to work over my network shouldn't be that hard. I've already been looking at apps on f-droid. First just want to get audio working again....

---

### Post by TheFu on 2021-03-10
> **Furycd001 said:**
> Thanks for the reply :) I believe my problem is more mpd or ubuntu rather than ncmpcpp. Before I upgraded from 18.04 to 20.04 everything was working fine. Setting mpd up to work over my network shouldn't be that hard. I've already been looking at apps on f-droid. First just want to get audio working again....

20.04 scares me.  I just moved to 18.04 in the last 2 months.  I did my bleeding edge time in the 1990s.
Good luck.

---

### Post by Furycd001 on 2021-03-10
Until recently I was still on 16.04,  but one day woke up and just felt like upgrading. Didn't stay on 18.04 long before I randomly decided to upgrade again. Anyway thanks for replying. Hopefully I'll get sound working once again soon enough....

---

### Post by TheFu on 2021-03-10
Did you see my mpd.conf changes?

---

### Post by Furycd001 on 2021-03-11
Nope.. It looks exactly the same as it has for a while now. I just compared it to a backup that I know for sure worked & there's no differences. I haven't changed my mpd.conf in quite a while because it's been working just fine. Problems only appeared after upgrading to 20.04. I've check over how I set up mpd (as user not service) & that all my users permissions are correct (in audio group etc), but still nothing. Maybe a complete reinstalled of mpd would help ??

---

### Post by Furycd001 on 2021-03-11
Ok so don't know what the problem was, but uninstalling mpd & then reinstalling solved my problem. Copied over my config & I have audio again.. YAAYYY. Going to mark this as solved now....

---

