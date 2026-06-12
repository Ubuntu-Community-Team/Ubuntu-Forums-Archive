---
title: "Constant Crackling/Popping Sound on Ubuntu 13.10"
date: 2013-11-17
forum: General Help
---

### Post by childintime on 2013-11-17
Hello, I just installed 13.10 and got a problem with crackling/popping sound coming out of my Asus laptop speakers.
It's like little crackling sound which appears every ~5-15 seconds even if I am not listening to audio. It's like the sound when you would listen to very old record, but this happens all the time even if I don't listen to anything. Even if I just booted ubuntu, didn't even press anything, it's still here. But when I listen to audio, it happens more frequently.

**EDIT (2014 Aug 14), some important things:**

1. Noise is coming only from one of the two speakers.
2. Noise was in Ubuntu 13.10 and is currently on 14.04.
3. I think it have nothing to do with applications running because it appears even before login screen of Ubuntu. Also same noise is, if I boot from Live USB.
2. Muting sound will remove noise, but lowing volume has no effect.
3. Inserting headphones, removes the noise.
4. If I disconnect power cable while there is noise, noise will always disappear, but only if there is no music playing. If I start playing music, noise again appears even with power cable disconnected.
5. Sometimes that noise disappears for 1-4 weeks, and then again appears for no reason and lasts from several days to weeks.




Now I tried some solutions, like:

1. echo 0 | sudo tee /sys/module/snd_hda_intel/parameters/power_save
2. Intel Audio Powersave Fix:  [http://www.foxswap.com/computers-and-technology/ubuntu-12-04-clicking-sound-from-speakers/](http://www.foxswap.com/computers-and-technology/ubuntu-12-04-clicking-sound-from-speakers/)
3. Adding tsched=0 to /etc/pulse/default.pa

But nothing seem work, and as you can imagine it is very annoying.

---

### Post by childintime on 2013-11-18
I also noticed, that if I am watching video long enough, it seems to kind of disappear, but as soon as I start typing something it reappears again.

---

### Post by childintime on 2013-12-17
And there is constant little noise when sound is not muted. Any solutions how to fix this noise coming from speakers?

---

### Post by phoyce2 on 2013-12-17
There are two things I would try to fix this:

1.  Try and find an updated audio driver for your flavor of Linux.
2.  Try a Live CD of Linux or a dual-booted Windows OS.  If the sound happens in either of those I would guess it's a hardware issue.  If it does not happen then I would *really* suspect the drivers for the flavor Linux you are using.

Try those and get back to us.

---

### Post by childintime on 2014-02-04
> **phoyce2 said:**
> There are two things I would try to fix this:

1.  Try and find an updated audio driver for your flavor of Linux.
2.  Try a Live CD of Linux or a dual-booted Windows OS.  If the sound happens in either of those I would guess it's a hardware issue.  If it does not happen then I would *really* suspect the drivers for the flavor Linux you are using.

Try those and get back to us.

I tried removing both pulse audio and alsa and cracking sound still remains. It never stops, it elevant if I listen to audio or not. That sound is also in live ubuntu usb, but not on the Windows 8 so I would think it's unbuntu problem. 

The only way to remove it, is to mute audio.

---

### Post by childintime on 2014-02-15
Bump ...

---

### Post by sam_baker2 on 2014-02-15
I use to get a crackling sound every time my neighbor ( common wall ) used his
cell phone.
Also, I get a intermittent popping noise through my speakers. It lasts for 2 or 3 seconds
then stops for 2 or 3 seconds, but it is not loud, almost unnoticeable. I could fix it, but
I would have to move my speakers to far away from my modem & wifi router.

---

### Post by childintime on 2014-02-15
Interesting that you say that.. But I just tested it with someone calling me and noise didn't show up, so not sure if it's related.

---

### Post by Drew_Matamales on 2014-03-31
Okay, the damn crackling was driving me nuts and I searched *forever*.  I found a thread on Ask Ubuntu which might be of help to those of you who still have an issue with this problem.  For what it's worth, the PulseAudio tsched=0 thing worked like a charm for me.   
[http://askubuntu.com/questions/157891/skype-and-vlc-sounds-sizzle-distorted-bad](http://askubuntu.com/questions/157891/skype-and-vlc-sounds-sizzle-distorted-bad)

---

### Post by childintime on 2014-04-21
My problem is not related to VLC or Skype, I got that noise most of the time without those programs even installed on my ubuntu. 

I just made fresh install of 14.04 LTS and same problem. Sound is like when you have old radio and searching for stations, that buzzing sound. If I restart my computer, the buzzing sound starts as soon as moving ubuntu logo appears, long before I even login.

Now yesterday for example buzzing was gone, and today appeared again even though I didn't even restart the computer.

I am so extremely frustrated because of this issue, it's just driving me nuts. The only way to stop it is to mute sound. Would be very appreciated if someone can give me some advice on how to possibly solve it.

---

### Post by childintime on 2014-04-22
Bump, please any ideas?

---

### Post by childintime on 2014-04-27
Bump...

---

### Post by childintime on 2014-04-27
Now it literally goes every other day. Like yesterday it was alright, and today it again that buzzing sound.. Just drives me nuts. Is there anything I can try? :(

I made a recording so you can hear how it sounds: [http://vocaroo.com/i/s0Tpv83IMDqy](http://vocaroo.com/i/s0Tpv83IMDqy)
Another one (with increased mic, so you can hear better): [http://vocaroo.com/i/s0bvVqBMoNJC](http://vocaroo.com/i/s0bvVqBMoNJC) (volume warning)

As you notice, there are several different buzzing sounds going on.

---

### Post by childintime on 2014-05-03
2 days it was okay, now again started and whole day cracking sound, now little bit different. Is it possible that it's a hardware issue? But it makes no sound in Windows 8.1.

---

### Post by davea42 on 2014-05-03
See the following for details on tsched. tsched=0 helped me (intel sound) 
and I too had the sound suddenly get scratchy and intermittent on installing
a new release (not that I recall exactly when this first affected me).


[URL="http://askubuntu.com/questions/371595/for-pulseaudio-what-does-tsched-do-and-what-are-the-defaults"]http://askubuntu.com/questions/371595/for-pulseaudio-what-does-tsched-do-and-what-are-the-defaults




[/URL]

---

### Post by childintime on 2014-05-03
> **davea42 said:**
> See the following for details on tsched. tsched=0 helped me (intel sound) 
and I too had the sound suddenly get scratchy and intermittent on installing
a new release (not that I recall exactly when this first affected me).


[URL="http://askubuntu.com/questions/371595/for-pulseaudio-what-does-tsched-do-and-what-are-the-defaults"]http://askubuntu.com/questions/371595/for-pulseaudio-what-does-tsched-do-and-what-are-the-defaults
[/URL]

Thanks for trying to help, but as I mentioned in the OP, I've done that and it has no effect on that sound.

---

### Post by childintime on 2014-05-08
Bump......

---

### Post by childintime on 2014-05-11
Bump

---

### Post by davea42 on 2014-05-12
Sorry if this sounds silly..., but that recording is very much like the sound my speakers make as I unplug the audio (or replug).
(going from speakers to headphones and back, of course...).  So  ... put in earplugs (to mute the noise a bit) and
carefully manipulate all the audio wires and audio plugs to see if it's really just a bad connection or broken wire? Ok.
You probably did that.  Try it again?    Desperate measures :-)    I guess it makes no sense given Windows does
not make the noise.  Oh. And try this command (no need to be root)
      ```
lsmod | grep snd
```
and post the output.  Should be under 15 lines or so.

---

### Post by childintime on 2014-05-12
> **davea42 said:**
> Sorry if this sounds silly..., but that recording is very much like the sound my speakers make as I unplug the audio (or replug).
(going from speakers to headphones and back, of course...).  So  ... put in earplugs (to mute the noise a bit) and
carefully manipulate all the audio wires and audio plugs to see if it's really just a bad connection or broken wire? Ok.
You probably did that.  Try it again?    Desperate measures :-)    I guess it makes no sense given Windows does
not make the noise.  Oh. And try this command (no need to be root)
      ```
lsmod | grep snd
```
and post the output.  Should be under 15 lines or so.

I don't have any wires, it comes from laptop speakers.

```
mosquito@mosquito-K56CB:~$ lsmod | grep sndsnd_hda_codec_hdmi     46207  1 
snd_hda_codec_realtek    61438  1 
snd_hda_intel          52355  6 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  3 snd_pcm,snd_seq
snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd



```

---

### Post by davea42 on 2014-05-13
try
```
cat /etc/pulse/daemon.conf
```
but for 13.10 I don't find any reports that strike me as relevant, some archlinux
folks saw other daemon.conf output that they were able to use to fix a similar problem.

Does the speaker-test produce text about your system sound *and* 
speak, a voice  saying 'left front' etc etc?

Can you  post the text here from the following commands?
```
head -n 1 /proc/asound/card0/codec*
lspci -v | grep -i audio
aplay --list-devices
speaker-test -Dplug:front -c2 -l5 -twav
```

Warning: you'd be in better shape if I actually knew much about sound on Linux (sorry).
On the other hand I'm rather used to having to struggle to get sound to work after
every new release (Ubuntu is pretty good, rarely breaks sound... a few years ago
Fedora Core would break sound with every new release, forcing me to scrounge around for hours).

---

### Post by childintime on 2014-05-13
I am not on 14.04 LTS. I had same problem on 13.10, for a week or so but then it disappeared. I tried many different things, so not sure what helped. Also it was same on 12.04 LTS as far as I remember. And when using Live USB, on all those versions also the same problem.

```
mosquito@mosquito-K56CB:~$ cat /etc/pulse/daemon.conf# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.


## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values are commented out.  Use either ; or # for
## commenting.


; daemonize = no
; fail = yes
; allow-module-loading = yes
; allow-exit = yes
; use-pid-file = yes
; system-instance = no
; local-server-type = user
; enable-shm = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB
; lock-memory = no
; cpu-limit = no


; high-priority = yes
; nice-level = -11


; realtime-scheduling = yes
; realtime-priority = 5


; exit-idle-time = 20
; scache-idle-time = 20


; dl-search-path = (depends on architecture)


; load-default-script-file = yes
; default-script-file = /etc/pulse/default.pa


; log-target = auto
; log-level = notice
; log-meta = no
; log-time = no
; log-backtrace = 0


resample-method = speex-float-1
; enable-remixing = yes
; enable-lfe-remixing = no


flat-volumes = no


; rlimit-fsize = -1
; rlimit-data = -1
; rlimit-stack = -1
; rlimit-core = -1
; rlimit-as = -1
; rlimit-rss = -1
; rlimit-nproc = -1
; rlimit-nofile = 256
; rlimit-memlock = -1
; rlimit-locks = -1
; rlimit-sigpending = -1
; rlimit-msgqueue = -1
; rlimit-nice = 31
; rlimit-rtprio = 9
; rlimit-rttime = 1000000


; default-sample-format = s16le
; default-sample-rate = 44100
; alternate-sample-rate = 48000
; default-sample-channels = 2
; default-channel-map = front-left,front-right


default-fragments = 8
default-fragment-size-msec = 10


; enable-deferred-volume = yes
deferred-volume-safety-margin-usec = 1
; deferred-volume-extra-delay-usec = 0

```

```
mosquito@mosquito-K56CB:~$ head -n 1 /proc/asound/card0/codec*==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC270


==> /proc/asound/card0/codec#3 <==
Codec: Intel PantherPoint HDMI

```

```
mosquito@mosquito-K56CB:~$ lspci -v | grep -i audio
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)

```

```
mosquito@mosquito-K56CB:~$ aplay --list-devices
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC270 Analog [ALC270 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
mosquito@mosquito-K56CB:~$ speaker-test -Dplug:front -c2 -l5 -twav


speaker-test 1.0.27.2


Playback device is plug:front
Stream parameters are 48000Hz, S16_LE, 2 channels
WAV file(s)
Playback open error: -16,Device or resource busy

```

Here we go, thanks for trying to help.

---

### Post by davea42 on 2014-05-13
I reproduce your problem with speaker-test in the following way:
Start playing something (I chose KQED's radio broadcast).  Then while it is playing
I tried speaker-test and it failed with Device or resource busy.

So this suggests (not proof, but...)
that you are getting speaker noise because you have some sound generation task running. Emitting noise.

---

### Post by childintime on 2014-05-13
> **davea42 said:**
> I reproduce your problem with speaker-test in the following way:
Start playing something (I chose KQED's radio broadcast).  Then while it is playing
I tried speaker-test and it failed with Device or resource busy.

So this suggests (not proof, but...)
that you are getting speaker noise because you have some sound generation task running. Emitting noise.

How should I figure what task is that? Now, keep in mind that noise comes and goes, usually 1 day it's all the time, then next day it's all good, even though I am not really running anything particular. All I've got is Chrome, Skype, Audacious and that's pretty much it. Now, it's no noise at all, but yesterday it was horrible, and that's how it goes for weeks now.

---

### Post by davea42 on 2014-05-13
Try speaker-test when it's not making noise.  Do 
```
ps -eaf >/var/tmp/soundokps

```
Then when it is making noise, with  a similar ps to a differently named
file.

While the two instances of ps won't sort the same, by looking at the
lists of what is running try to see what is running on the 'bad'
occasion that is not running on the 'good' one.

I'm sure there are better tools, but...I cannot find one so far (-:

---

### Post by childintime on 2014-05-13
Alright gonna try this out and update! 

Cheers!

---

### Post by davea42 on 2014-05-13
Probably irrelevant, but.. be just that little bit suspicious of skype.
When you quit it, it leaves a process running.  And you might have said
you wanted it to start when you reboot.  So kill skype, by hand.

---

### Post by childintime on 2014-05-13
> **davea42 said:**
> Probably irrelevant, but.. be just that little bit suspicious of skype.
When you quit it, it leaves a process running.  And you might have said
you wanted it to start when you reboot.  So kill skype, by hand.

Sometimes it makes the noise when skype is off. As I said in the beginning, it sometimes start making the same noise even before Ubuntu boots, like as soon as I see Ubuntu logo, before loging screen. Not to mention I get noise in Live USB which has no extra programs at all.

---

### Post by davea42 on 2014-05-13
Before Ubuntu boots...Oh.
As I said though, the only way to know for sure if a skype is running is  
```
ps -eaf |grep skype
```
because, well, you might have implicitly or explicitly asked for it to start
and there may be nothing in any panel about it.
But skype won't start before you log in!

---

### Post by davea42 on 2014-05-19
Note the 
resample-method = speex-float-1
in your pulse/daemon.conf

Try -0 instead of -1.    Try -10 too.
Just guessing here, but this has helped others, apparently.

---

### Post by davea42 on 2014-05-19
The sources I notice say to do

```
sudo load-module module-udev-detect tsched=0
```

and reboot.

You said you set tsched=0, but used a different method.  
Try the one above.

---

### Post by davea42 on 2014-05-19
Of course I misunderstood and I'm a doofus.
The line
```
load-module module-udev-detect tsched=0
``` goes
in /etc/pulse/default.pa.  it's not a commandline command.

---

### Post by childintime on 2014-05-19
> **davea42 said:**
> Note the 
resample-method = speex-float-1
in your pulse/daemon.conf

Try -0 instead of -1.    Try -10 too.
Just guessing here, but this has helped others, apparently.

Tried -0 and -10 without restarting computer, didn't change anything. Btw, it was without noise for like 3 days now, and just when you posted you post, that sound came again and now it's very loud, I need to mute otherwise it's unbearable.

tsched=0 is method is done long time ago and pc was restarted. Now it is tsched=0, so nothing to change there.

Now you asked me to do ps -eaf >/var/tmp/soundokps, so there it is without noise:
```
UID        PID  PPID  C STIME TTY          TIME CMDroot         1     0  0 Mai11 ?        00:00:02 /sbin/init
root         2     0  0 Mai11 ?        00:00:00 [kthreadd]
root         3     2  0 Mai11 ?        00:00:02 [ksoftirqd/0]
root         5     2  0 Mai11 ?        00:00:00 [kworker/0:0H]
root         7     2  0 Mai11 ?        00:02:22 [rcu_sched]
root         8     2  0 Mai11 ?        00:01:03 [rcuos/0]
root         9     2  0 Mai11 ?        00:01:01 [rcuos/1]
root        10     2  0 Mai11 ?        00:00:37 [rcuos/2]
root        11     2  0 Mai11 ?        00:00:49 [rcuos/3]
root        12     2  0 Mai11 ?        00:00:00 [rcu_bh]
root        13     2  0 Mai11 ?        00:00:00 [rcuob/0]
root        14     2  0 Mai11 ?        00:00:00 [rcuob/1]
root        15     2  0 Mai11 ?        00:00:00 [rcuob/2]
root        16     2  0 Mai11 ?        00:00:00 [rcuob/3]
root        17     2  0 Mai11 ?        00:00:05 [migration/0]
root        18     2  0 Mai11 ?        00:00:00 [watchdog/0]
root        19     2  0 Mai11 ?        00:00:00 [watchdog/1]
root        20     2  0 Mai11 ?        00:00:03 [migration/1]
root        21     2  0 Mai11 ?        00:00:01 [ksoftirqd/1]
root        23     2  0 Mai11 ?        00:00:00 [kworker/1:0H]
root        24     2  0 Mai11 ?        00:00:00 [watchdog/2]
root        25     2  0 Mai11 ?        00:00:02 [migration/2]
root        26     2  0 Mai11 ?        00:00:00 [ksoftirqd/2]
root        28     2  0 Mai11 ?        00:00:00 [kworker/2:0H]
root        29     2  0 Mai11 ?        00:00:00 [watchdog/3]
root        30     2  0 Mai11 ?        00:00:02 [migration/3]
root        31     2  0 Mai11 ?        00:00:00 [ksoftirqd/3]
root        33     2  0 Mai11 ?        00:00:00 [kworker/3:0H]
root        34     2  0 Mai11 ?        00:00:00 [khelper]
root        35     2  0 Mai11 ?        00:00:00 [kdevtmpfs]
root        36     2  0 Mai11 ?        00:00:00 [netns]
root        37     2  0 Mai11 ?        00:00:00 [writeback]
root        38     2  0 Mai11 ?        00:00:00 [kintegrityd]
root        39     2  0 Mai11 ?        00:00:00 [bioset]
root        41     2  0 Mai11 ?        00:00:00 [kblockd]
root        43     2  0 Mai11 ?        00:00:00 [ata_sff]
root        44     2  0 Mai11 ?        00:00:00 [khubd]
root        45     2  0 Mai11 ?        00:00:00 [md]
root        46     2  0 Mai11 ?        00:00:00 [devfreq_wq]
root        49     2  0 Mai11 ?        00:00:00 [khungtaskd]
root        50     2  0 Mai11 ?        00:00:07 [kswapd0]
root        51     2  0 Mai11 ?        00:00:00 [ksmd]
root        52     2  0 Mai11 ?        00:00:09 [khugepaged]
root        53     2  0 Mai11 ?        00:00:00 [fsnotify_mark]
root        54     2  0 Mai11 ?        00:00:00 [ecryptfs-kthrea]
root        55     2  0 Mai11 ?        00:00:00 [crypto]
root        67     2  0 Mai11 ?        00:00:00 [kthrotld]
root        88     2  0 Mai11 ?        00:00:00 [deferwq]
root        89     2  0 Mai11 ?        00:00:00 [charger_manager]
root        90     2  0 Mai11 ?        00:01:16 [kworker/1:2]
root       143     2  0 Mai11 ?        00:00:00 [scsi_eh_0]
root       144     2  0 Mai11 ?        00:00:00 [scsi_eh_1]
root       145     2  0 Mai11 ?        00:00:00 [scsi_eh_2]
root       146     2  0 Mai11 ?        00:00:00 [scsi_eh_3]
root       147     2  0 Mai11 ?        00:00:00 [scsi_eh_4]
root       148     2  0 Mai11 ?        00:00:00 [scsi_eh_5]
root       165     2  0 Mai11 ?        00:00:09 [jbd2/sda2-8]
root       166     2  0 Mai11 ?        00:00:00 [ext4-rsv-conver]
root       314     1  0 Mai11 ?        00:00:00 upstart-udev-bridge --daemon
root       318     1  0 Mai11 ?        00:00:00 /lib/systemd/systemd-udevd --daemon
root       370     2  0 Mai11 ?        00:00:00 [kmemstick]
root       372     2  0 Mai11 ?        00:00:00 [cfg80211]
root       385     2  0 Mai11 ?        00:00:00 [kpsmoused]
root       417     2  0 Mai11 ?        00:00:00 [kvm-irqfd-clean]
root       474     1  0 Mai11 ?        00:00:00 upstart-socket-bridge --daemon
root       477     2  0 Mai11 ?        00:00:00 [led_workqueue]
root       550     2  0 Mai11 ?        00:00:00 [hd-audio0]
root       577     2  0 Mai11 ?        00:00:00 [ttm_swap]
message+   723     1  0 Mai11 ?        00:01:18 dbus-daemon --system --fork
root       757     1  0 Mai11 ?        00:00:00 /usr/sbin/ModemManager
root       759     1  0 Mai11 ?        00:00:00 /usr/sbin/bluetoothd
root       770     2  0 Mai11 ?        00:00:00 [krfcommd]
root       778     1  0 Mai11 ?        00:00:00 upstart-file-bridge --daemon
syslog     780     1  0 Mai11 ?        00:00:00 rsyslogd
avahi      846     1  0 Mai11 ?        00:00:03 avahi-daemon: running [mosquito-K56CB.local]
avahi      855   846  0 Mai11 ?        00:00:00 avahi-daemon: chroot helper
root       885     1  0 Mai11 ?        00:00:00 /lib/systemd/systemd-logind
root       911     1  0 Mai11 tty4     00:00:00 /sbin/getty -8 38400 tty4
root       915     1  0 Mai11 tty5     00:00:00 /sbin/getty -8 38400 tty5
root       921     1  0 Mai11 tty2     00:00:00 /sbin/getty -8 38400 tty2
root       923     1  0 Mai11 tty3     00:00:00 /sbin/getty -8 38400 tty3
root       931     1  0 Mai11 tty6     00:00:00 /sbin/getty -8 38400 tty6
root      1001     1  0 Mai11 ?        00:00:51 NetworkManager
root      1004     1  0 Mai11 ?        00:00:04 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      1006     1  0 Mai11 ?        00:00:13 /usr/sbin/irqbalance
root      1015     1  0 Mai11 ?        00:00:07 /usr/lib/policykit-1/polkitd --no-debug
kernoops  1023     1  0 Mai11 ?        00:00:03 /usr/sbin/kerneloops
root      1025     1  0 Mai11 ?        00:00:00 cron
root      1031     1  0 Mai11 ?        00:00:00 lightdm
root      1037     1  0 Mai11 ?        00:00:25 /sbin/wpa_supplicant -B -P /run/sendsigs.omit.d/wpasupplicant.pid -u -s -O /var/run/wpa_supplicant
root      1079  1031  3 Mai11 tty7     01:43:11 /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
root      1083     1  0 Mai11 ?        00:00:14 /usr/lib/accountsservice/accounts-daemon
whoopsie  1100     1  0 Mai11 ?        00:00:00 whoopsie
root      1130     1  0 Mai11 tty1     00:00:00 /sbin/getty -8 38400 tty1
nobody    1144  1001  0 Mai11 ?        00:00:02 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/run/sendsigs.omit.d/network-manager.dnsmasq.pid --listen-address=127.0.1.1 --conf-file=/var/run/NetworkManager/dnsmasq.conf --cache-size=0 --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq --conf-dir=/etc/NetworkManager/dnsmasq.d
root      1285     2  0 Mai11 ?        00:00:00 [kauditd]
root      1395  1031  0 Mai11 ?        00:00:00 lightdm --session-child 12 19
root      1447     1  0 Mai11 ?        00:00:10 /usr/lib/upower/upowerd
rtkit     1476     1  0 Mai11 ?        00:00:01 /usr/lib/rtkit/rtkit-daemon
root      1490     2  0 Mai11 ?        00:01:09 [kworker/2:2]
root      1530     1  0 Mai11 ?        00:02:22 /opt/teamviewer9/tv_bin/teamviewerd -f
mosquito  1787     1  0 Mai11 ?        00:00:23 /usr/bin/gnome-keyring-daemon --daemonize --login
mosquito  1791  1395  0 Mai11 ?        00:00:01 init --user
mosquito  1857  1791  0 Mai11 ?        00:00:00 ssh-agent
mosquito  1863  1791  0 Mai11 ?        00:06:08 dbus-daemon --fork --session --address=unix:abstract=/tmp/dbus-eDqznwMihK
mosquito  1871  1791  0 Mai11 ?        00:00:00 upstart-event-bridge
mosquito  1874  1791  0 Mai11 ?        00:00:00 /usr/lib/x86_64-linux-gnu/hud/window-stack-bridge
mosquito  1885  1791  0 Mai11 ?        00:00:00 upstart-file-bridge --daemon --user
mosquito  1887  1791  0 Mai11 ?        00:00:02 upstart-dbus-bridge --daemon --system --user --bus-name system
mosquito  1889  1791  0 Mai11 ?        00:02:11 upstart-dbus-bridge --daemon --session --user --bus-name session
mosquito  1891  1791  0 Mai11 ?        00:01:47 /usr/bin/ibus-daemon --daemonize --xim
mosquito  1905  1791  0 Mai11 ?        00:00:10 /usr/lib/unity-settings-daemon/unity-settings-daemon
mosquito  1909  1791  0 Mai11 ?        00:00:04 /usr/lib/x86_64-linux-gnu/hud/hud-service
mosquito  1912  1791  0 Mai11 ?        00:00:00 /usr/lib/at-spi2-core/at-spi-bus-launcher --launch-immediately
mosquito  1913  1791  0 Mai11 ?        00:00:02 gnome-session --session=ubuntu
mosquito  1915  1791  0 Mai11 ?        00:15:44 /usr/lib/unity/unity-panel-service
mosquito  1919  1912  0 Mai11 ?        00:00:00 /bin/dbus-daemon --config-file=/etc/at-spi2/accessibility.conf --nofork --print-address 3
mosquito  1922  1791  0 Mai11 ?        00:00:01 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
mosquito  1928  1791  0 Mai11 ?        00:00:00 /usr/lib/gvfs/gvfsd
mosquito  1933  1791  0 Mai11 ?        00:00:00 /usr/lib/gvfs/gvfsd-fuse /run/user/1000/gvfs -f -o big_writes
mosquito  1955  1791  0 Mai11 ?        00:02:16 /usr/lib/x86_64-linux-gnu/bamf/bamfdaemon
mosquito  1967  1791  0 Mai11 ?        00:00:00 /usr/lib/x86_64-linux-gnu/indicator-keyboard-service --use-gtk
mosquito  1969  1791  0 Mai11 ?        00:00:00 /usr/lib/x86_64-linux-gnu/indicator-messages/indicator-messages-service
mosquito  1970  1791  0 Mai11 ?        00:00:00 /usr/lib/x86_64-linux-gnu/indicator-bluetooth/indicator-bluetooth-service
mosquito  1972  1791  0 Mai11 ?        00:00:11 /usr/lib/x86_64-linux-gnu/indicator-power/indicator-power-service
mosquito  1974  1791  0 Mai11 ?        00:00:02 /usr/lib/x86_64-linux-gnu/indicator-datetime/indicator-datetime-service
mosquito  1979  1791  0 Mai11 ?        00:01:09 /usr/lib/x86_64-linux-gnu/indicator-sound/indicator-sound-service
mosquito  1980  1791  0 Mai11 ?        00:00:00 /usr/lib/x86_64-linux-gnu/indicator-printers/indicator-printers-service
mosquito  1987  1791  0 Mai11 ?        00:00:04 /usr/lib/x86_64-linux-gnu/indicator-session/indicator-session-service
mosquito  1988  1791  0 Mai11 ?        00:07:15 /usr/lib/x86_64-linux-gnu/indicator-application/indicator-application-service
mosquito  2012  1791  2 Mai11 ?        01:22:46 /usr/bin/pulseaudio --start --log-target=syslog
mosquito  2040  1791  0 Mai11 ?        00:00:00 /usr/lib/evolution/evolution-source-registry
mosquito  2042  1791  0 Mai11 ?        00:00:03 /usr/lib/x86_64-linux-gnu/notify-osd
mosquito  2046  1891  0 Mai11 ?        00:00:00 /usr/lib/ibus/ibus-dconf
mosquito  2047  1891  0 Mai11 ?        00:00:20 /usr/lib/ibus/ibus-ui-gtk3
mosquito  2049  1791  0 Mai11 ?        00:00:10 /usr/lib/ibus/ibus-x11 --kill-daemon
mosquito  2086  1891  0 Mai11 ?        00:00:28 /usr/lib/ibus/ibus-engine-simple
mosquito  2113  1913  4 Mai11 ?        02:46:04 compiz
colord    2115     1  0 Mai11 ?        00:00:00 /usr/lib/colord/colord
mosquito  2117  1791  0 Mai11 ?        00:00:00 /usr/lib/dconf/dconf-service
mosquito  2121  1905  0 Mai11 ?        00:01:06 syndaemon -i 1.0 -t -K -R
mosquito  2205  1913  0 Mai11 ?        00:01:09 nm-applet
mosquito  2207  1913  0 Mai11 ?        00:00:46 nautilus -n
mosquito  2209  1913  0 Mai11 ?        00:00:01 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
mosquito  2211  1913  0 Mai11 ?        00:00:46 /usr/bin/python3 /opt/extras.ubuntu.com/my-weather-indicator/bin/my-weather-indicator
mosquito  2212  1913  0 Mai11 ?        00:24:23 indicator-multiload
mosquito  2214  1913  0 Mai11 ?        00:00:00 /usr/lib/unity-settings-daemon/unity-fallback-mount-helper
mosquito  2231  1791  0 Mai11 ?        00:00:00 /usr/lib/gvfs/gvfs-udisks2-volume-monitor
mosquito  2235  1791  0 Mai11 ?        00:00:00 /usr/lib/x86_64-linux-gnu/gconf/gconfd-2
root      2245     1  0 Mai11 ?        00:00:13 /usr/lib/udisks2/udisksd --no-debug
mosquito  2256  1791  0 Mai11 ?        00:00:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
mosquito  2261  1791  0 Mai11 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
mosquito  2269  1791  0 Mai11 ?        00:00:01 /usr/lib/evolution/evolution-calendar-factory
mosquito  2273  1791  0 Mai11 ?        00:00:00 /usr/lib/gvfs/gvfs-mtp-volume-monitor
mosquito  2290  1791  0 Mai11 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.5 /org/gtk/gvfs/exec_spaw/0
mosquito  2320  1791  0 Mai11 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.5 /org/gtk/gvfs/exec_spaw/1
mosquito  2330  1791  0 Mai11 ?        00:00:00 /usr/lib/gvfs/gvfsd-metadata
mosquito  2336  1913  0 Mai11 ?        00:00:00 telepathy-indicator
mosquito  2344  1791  0 Mai11 ?        00:00:07 /usr/lib/telepathy/mission-control-5
mosquito  2357  1913  0 Mai11 ?        00:00:04 zeitgeist-datahub
mosquito  2362  1791  0 Mai11 ?        00:00:01 /usr/bin/zeitgeist-daemon
mosquito  2368  1791  0 Mai11 ?        00:00:03 /usr/lib/x86_64-linux-gnu/zeitgeist-fts
mosquito  2370  2368  0 Mai11 ?        00:00:00 /bin/cat
mosquito  2388  1791  5 Mai11 ?        02:57:41 /usr/bin/google-chrome-stable
mosquito  2396  2388  0 Mai11 ?        00:00:41 /usr/bin/google-chrome-stable
mosquito  2397  2388  0 Mai11 ?        00:00:00 /opt/google/chrome/chrome-sandbox /opt/google/chrome/chrome --type=zygote
mosquito  2398  2397  0 Mai11 ?        00:00:00 /opt/google/chrome/chrome --type=zygote
mosquito  2404  2398  0 Mai11 ?        00:00:00 /opt/google/chrome/nacl_helper
mosquito  2405  2398  0 Mai11 ?        00:00:00 /opt/google/chrome/chrome --type=zygote
mosquito  2448  2405  0 Mai11 ?        00:20:17 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --extension-process --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.1.1207955313
mosquito  2503  2405  0 Mai11 ?        00:04:12 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --extension-process --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.2.1833567117
mosquito  2544  2405  0 Mai11 ?        00:10:48 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.4.1433666610
mosquito  2559  2405  0 Mai11 ?        00:28:48 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.5.1969422326
mosquito  2569  1913  0 Mai11 ?        00:00:04 update-notifier
mosquito  2570  2405  0 Mai11 ?        00:28:50 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.6.217524479
mosquito  2589  2405  0 Mai11 ?        00:00:02 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.7.2103577292
mosquito  2604  2405  0 Mai11 ?        00:00:01 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.8.1194928852
mosquito  2627  2405  0 Mai11 ?        00:00:01 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.10.1323564556
mosquito  2638  2405  0 Mai11 ?        00:00:01 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.11.2098829617
mosquito  2662  2405  0 Mai11 ?        00:00:17 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.13.2089000180
mosquito  2674  2388  1 Mai11 ?        01:03:59 /opt/google/chrome/chrome --type=gpu-process --channel=2388.14.926894310 --supports-dual-gpus=false --gpu-driver-bug-workarounds=0,1,2,9,11,28 --disable-accelerated-video-decode --gpu-vendor-id=0x8086 --gpu-device-id=0x0166 --gpu-driver-vendor=Mesa --gpu-driver-version=10.1.0
mosquito  2676  2405  0 Mai11 ?        00:00:02 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.15.1921687339
mosquito  2683  2674  0 Mai11 ?        00:00:00 /opt/google/chrome/chrome --type=gpu-process --channel=2388.14.926894310 --supports-dual-gpus=false --gpu-driver-bug-workarounds=0,1,2,9,11,28 --disable-accelerated-video-decode --gpu-vendor-id=0x8086 --gpu-device-id=0x0166 --gpu-driver-vendor=Mesa --gpu-driver-version=10.1.0
mosquito  2692  2405  0 Mai11 ?        00:00:02 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.16.1247323624
mosquito  2698  2405  0 Mai11 ?        00:00:10 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.17.1031417061
mosquito  2759  2405  0 Mai11 ?        00:02:01 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.18.985101945
mosquito  2771  2405  0 Mai11 ?        00:00:55 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.19.1438004619
mosquito  2794  2405  0 Mai11 ?        00:00:02 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.21.2013413010
mosquito  2804  2405  0 Mai11 ?        00:01:58 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.22.530757719
mosquito  2814  2405  0 Mai11 ?        00:13:18 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.23.165182814
mosquito  2825  2405  3 Mai11 ?        01:42:41 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.24.1782325021
mosquito  2836  1913  0 Mai11 ?        00:00:01 /usr/lib/x86_64-linux-gnu/deja-dup/deja-dup-monitor
root      2846     1  0 Mai12 ?        00:00:00 /usr/sbin/cups-browsed
mosquito  2880  2405  0 Mai11 ?        00:25:25 /opt/google/chrome/chrome --type=ppapi --channel=2388.28.759582829 --ppapi-flash-args --lang=en-US
mosquito  3113  2405  0 Mai11 ?        00:26:19 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.39.776952905
mosquito  3395  1791  0 Mai11 ?        00:27:46 audacious
mosquito  4357  1791  0 Mai12 ?        00:00:01 /usr/lib/x86_64-linux-gnu/unity-scope-home/unity-scope-home
mosquito  4373  1791  0 Mai12 ?        00:00:02 /usr/bin/unity-scope-loader applications/applications.scope applications/scopes.scope commands.scope
mosquito  4374  1791  0 Mai12 ?        00:00:00 /usr/lib/x86_64-linux-gnu/unity-lens-files/unity-files-daemon
mosquito  4396  1791  0 Mai12 ?        00:00:01 /usr/lib/x86_64-linux-gnu/unity-lens-music/unity-music-daemon
mosquito  8827  1791  0 Mai11 ?        00:00:23 eog /home/mosquito/Power Analysis Attacks/Masking Ch9/P1020190.JPG
mosquito  8834  1791  0 Mai11 ?        00:02:27 /usr/bin/python /usr/bin/software-center
mosquito  8849  1791  0 Mai11 ?        00:00:03 /usr/lib/geoclue/geoclue-master
mosquito  8853  1791  0 Mai11 ?        00:00:04 /usr/lib/x86_64-linux-gnu/ubuntu-geoip-provider
mosquito  9499  1791  0 Mai11 ?        00:00:11 evince /home/mosquito/Downloads/AC.pdf
mosquito  9506  1791  0 Mai11 ?        00:00:00 /usr/lib/evince/evinced
mosquito  9525  1791  0 Mai11 ?        00:00:00 /usr/lib/gvfs/gvfsd-http --spawner :1.5 /org/gtk/gvfs/exec_spaw/3
mosquito 11623  2405  0 Mai12 ?        00:12:39 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.611.1603636643
mosquito 14623  2405  0 Mai12 ?        00:13:09 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.634.840293879
mosquito 14634  2405  0 Mai12 ?        00:05:40 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.635.2127459767
mosquito 14659  2405  0 Mai12 ?        00:00:06 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.637.647581167
mosquito 14901  2405  0 Mai12 ?        00:00:46 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.644.2048097570
mosquito 16752  2405  0 Mai12 ?        00:00:32 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.654.407381180
mosquito 16775  1791  0 Mai12 ?        00:07:48 transmission-gtk /home/mosquito/Downloads/[rutracker.org].t3699940.torrent
mosquito 17284  2405  0 Mai12 ?        00:00:25 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.657.1725661995
root     21196     2  0 08:29 ?        00:00:34 [kworker/3:0]
mosquito 21387  8834  0 Mai11 ?        00:00:00 [debconf-communi] <defunct>
root     22200     1  0 08:58 ?        00:00:00 /usr/sbin/cupsd -f
mosquito 22524  1791  0 Mai11 ?        00:00:00 /usr/lib/gvfs/gvfsd-recent --spawner :1.5 /org/gtk/gvfs/exec_spaw/4
mosquito 22963  2405  0 09:29 ?        00:00:11 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.710.674938340
mosquito 23624  1791  0 Mai11 ?        00:00:08 texmaker /home/mosquito/RUN/Security Seminar/AC.tex
root     26650     2  0 Mai11 ?        00:00:00 [kworker/1:1H]
root     26651     2  0 Mai11 ?        00:00:00 [kworker/2:1H]
root     26652     2  0 Mai11 ?        00:00:00 [kworker/3:1H]
root     26961     2  0 14:55 ?        00:00:00 [kworker/u9:2]
root     26967     2  0 14:56 ?        00:00:16 [kworker/0:1]
root     27273     2  0 17:34 ?        00:00:00 [irq/47-mei_me]
root     27679     2  0 17:34 ?        00:00:00 [hci0]
root     27680     2  0 17:34 ?        00:00:00 [hci0]
root     27849     2  0 17:48 ?        00:00:00 [kworker/0:0]
root     28047     2  0 18:00 ?        00:00:00 [kworker/1:1]
root     28155     2  0 18:08 ?        00:00:00 [kworker/u9:0]
mosquito 28300  2405  0 18:22 ?        00:00:23 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.746.74174406
mosquito 28783  2405  1 19:03 ?        00:03:33 /opt/google/chrome/chrome --type=renderer --disable-databases --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.752.1196423065
mosquito 28878  1791  2 19:07 ?        00:04:56 skype
mosquito 29273  2405  0 19:30 ?        00:00:17 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.762.105719447
mosquito 29506  2405  6 19:36 ?        00:10:32 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.770.113603984
mosquito 29766  2405  0 19:51 ?        00:01:05 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.775.2132784840
mosquito 29862  2405  0 20:00 ?        00:00:09 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.777.512142944
root     30982     2  0 21:29 ?        00:00:00 [kworker/3:1]
root     31018     2  0 21:29 ?        00:00:00 [kworker/2:0]
mosquito 31067  2405 10 21:31 ?        00:03:49 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.786.841967724
mosquito 31084  1791  0 21:31 ?        00:00:00 gnome-calculator
root     31093     2  0 21:33 ?        00:00:01 [kworker/u8:1]
mosquito 31106  2405  1 21:33 ?        00:00:32 /opt/google/chrome/chrome --type=renderer --disable-databases --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.788.451314027
root     31276     2  0 21:48 ?        00:00:00 [kworker/u8:2]
root     31791     2  0 22:04 ?        00:00:00 [kworker/u8:0]
root     31793     1  0 22:05 ?        00:00:00 /usr/bin/python3 /usr/sbin/aptd
mosquito 31882  1791  8 22:08 ?        00:00:00 gnome-terminal
mosquito 31928 31882  0 22:08 ?        00:00:00 gnome-pty-helper
mosquito 31929 31882  6 22:08 pts/6    00:00:00 bash
mosquito 31941 31929  0 22:08 pts/6    00:00:00 ps -eaf
```

With big noise:

```
UID        PID  PPID  C STIME TTY          TIME CMDroot         1     0  0 Mai11 ?        00:00:04 /sbin/init
root         2     0  0 Mai11 ?        00:00:00 [kthreadd]
root         3     2  0 Mai11 ?        00:00:12 [ksoftirqd/0]
root         5     2  0 Mai11 ?        00:00:00 [kworker/0:0H]
root         7     2  0 Mai11 ?        00:07:19 [rcu_sched]
root         8     2  0 Mai11 ?        00:03:31 [rcuos/0]
root         9     2  0 Mai11 ?        00:03:01 [rcuos/1]
root        10     2  0 Mai11 ?        00:01:49 [rcuos/2]
root        11     2  0 Mai11 ?        00:02:25 [rcuos/3]
root        12     2  0 Mai11 ?        00:00:00 [rcu_bh]
root        13     2  0 Mai11 ?        00:00:00 [rcuob/0]
root        14     2  0 Mai11 ?        00:00:00 [rcuob/1]
root        15     2  0 Mai11 ?        00:00:00 [rcuob/2]
root        16     2  0 Mai11 ?        00:00:00 [rcuob/3]
root        17     2  0 Mai11 ?        00:00:13 [migration/0]
root        18     2  0 Mai11 ?        00:00:02 [watchdog/0]
root        19     2  0 Mai11 ?        00:00:01 [watchdog/1]
root        20     2  0 Mai11 ?        00:00:11 [migration/1]
root        21     2  0 Mai11 ?        00:00:05 [ksoftirqd/1]
root        23     2  0 Mai11 ?        00:00:00 [kworker/1:0H]
root        24     2  0 Mai11 ?        00:00:01 [watchdog/2]
root        25     2  0 Mai11 ?        00:00:10 [migration/2]
root        26     2  0 Mai11 ?        00:00:05 [ksoftirqd/2]
root        28     2  0 Mai11 ?        00:00:00 [kworker/2:0H]
root        29     2  0 Mai11 ?        00:00:01 [watchdog/3]
root        30     2  0 Mai11 ?        00:00:11 [migration/3]
root        31     2  0 Mai11 ?        00:00:03 [ksoftirqd/3]
root        33     2  0 Mai11 ?        00:00:00 [kworker/3:0H]
root        34     2  0 Mai11 ?        00:00:00 [khelper]
root        35     2  0 Mai11 ?        00:00:00 [kdevtmpfs]
root        36     2  0 Mai11 ?        00:00:00 [netns]
root        37     2  0 Mai11 ?        00:00:00 [writeback]
root        38     2  0 Mai11 ?        00:00:00 [kintegrityd]
root        39     2  0 Mai11 ?        00:00:00 [bioset]
root        41     2  0 Mai11 ?        00:00:00 [kblockd]
root        43     2  0 Mai11 ?        00:00:00 [ata_sff]
root        44     2  0 Mai11 ?        00:00:00 [khubd]
root        45     2  0 Mai11 ?        00:00:00 [md]
root        46     2  0 Mai11 ?        00:00:00 [devfreq_wq]
root        49     2  0 Mai11 ?        00:00:00 [khungtaskd]
root        50     2  0 Mai11 ?        00:01:01 [kswapd0]
root        51     2  0 Mai11 ?        00:00:00 [ksmd]
root        52     2  0 Mai11 ?        00:00:26 [khugepaged]
root        53     2  0 Mai11 ?        00:00:00 [fsnotify_mark]
root        54     2  0 Mai11 ?        00:00:00 [ecryptfs-kthrea]
root        55     2  0 Mai11 ?        00:00:00 [crypto]
root        67     2  0 Mai11 ?        00:00:00 [kthrotld]
root        88     2  0 Mai11 ?        00:00:00 [deferwq]
root        89     2  0 Mai11 ?        00:00:00 [charger_manager]
root        90     2  0 Mai11 ?        00:04:36 [kworker/1:2]
root       143     2  0 Mai11 ?        00:00:00 [scsi_eh_0]
root       144     2  0 Mai11 ?        00:00:00 [scsi_eh_1]
root       145     2  0 Mai11 ?        00:00:00 [scsi_eh_2]
root       146     2  0 Mai11 ?        00:00:00 [scsi_eh_3]
root       147     2  0 Mai11 ?        00:00:00 [scsi_eh_4]
root       148     2  0 Mai11 ?        00:00:00 [scsi_eh_5]
root       165     2  0 Mai11 ?        00:00:28 [jbd2/sda2-8]
root       166     2  0 Mai11 ?        00:00:00 [ext4-rsv-conver]
mosquito   305  2405  0 Mai15 ?        00:00:24 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.972.1082540928
root       370     2  0 Mai11 ?        00:00:00 [kmemstick]
root       372     2  0 Mai11 ?        00:00:00 [cfg80211]
root       385     2  0 Mai11 ?        00:00:00 [kpsmoused]
root       417     2  0 Mai11 ?        00:00:00 [kvm-irqfd-clean]
root       474     1  0 Mai11 ?        00:00:00 upstart-socket-bridge --daemon
root       477     2  0 Mai11 ?        00:00:00 [led_workqueue]
root       550     2  0 Mai11 ?        00:00:00 [hd-audio0]
root       577     2  0 Mai11 ?        00:00:00 [ttm_swap]
message+   723     1  0 Mai11 ?        00:03:44 dbus-daemon --system --fork
root       757     1  0 Mai11 ?        00:00:00 /usr/sbin/ModemManager
root       759     1  0 Mai11 ?        00:00:00 /usr/sbin/bluetoothd
root       770     2  0 Mai11 ?        00:00:00 [krfcommd]
root       778     1  0 Mai11 ?        00:00:00 upstart-file-bridge --daemon
syslog     780     1  0 Mai11 ?        00:00:01 rsyslogd
avahi      846     1  0 Mai11 ?        00:00:09 avahi-daemon: running [mosquito-K56CB.local]
avahi      855   846  0 Mai11 ?        00:00:00 avahi-daemon: chroot helper
root       911     1  0 Mai11 tty4     00:00:00 /sbin/getty -8 38400 tty4
root       915     1  0 Mai11 tty5     00:00:00 /sbin/getty -8 38400 tty5
root       921     1  0 Mai11 tty2     00:00:00 /sbin/getty -8 38400 tty2
root       923     1  0 Mai11 tty3     00:00:00 /sbin/getty -8 38400 tty3
root       931     1  0 Mai11 tty6     00:00:00 /sbin/getty -8 38400 tty6
mosquito   959  2405  0 Mai16 ?        00:00:05 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.1091.2011477576
root      1001     1  0 Mai11 ?        00:02:20 NetworkManager
root      1004     1  0 Mai11 ?        00:00:13 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      1006     1  0 Mai11 ?        00:00:39 /usr/sbin/irqbalance
root      1015     1  0 Mai11 ?        00:00:35 /usr/lib/policykit-1/polkitd --no-debug
kernoops  1023     1  0 Mai11 ?        00:00:13 /usr/sbin/kerneloops
root      1025     1  0 Mai11 ?        00:00:00 cron
root      1031     1  0 Mai11 ?        00:00:04 lightdm
root      1037     1  0 Mai11 ?        00:01:10 /sbin/wpa_supplicant -B -P /run/sendsigs.omit.d/wpasupplicant.pid -u -s -O /var/run/wpa_supplicant
root      1079  1031  3 Mai11 tty7     05:58:29 /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
root      1083     1  0 Mai11 ?        00:01:16 /usr/lib/accountsservice/accounts-daemon
whoopsie  1100     1  0 Mai11 ?        00:00:02 whoopsie
root      1130     1  0 Mai11 tty1     00:00:00 /sbin/getty -8 38400 tty1
nobody    1144  1001  0 Mai11 ?        00:00:07 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/run/sendsigs.omit.d/network-manager.dnsmasq.pid --listen-address=127.0.1.1 --conf-file=/var/run/NetworkManager/dnsmasq.conf --cache-size=0 --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq --conf-dir=/etc/NetworkManager/dnsmasq.d
root      1285     2  0 Mai11 ?        00:00:00 [kauditd]
root      1395  1031  0 Mai11 ?        00:00:00 lightdm --session-child 12 19
root      1447     1  0 Mai11 ?        00:00:28 /usr/lib/upower/upowerd
rtkit     1476     1  0 Mai11 ?        00:00:04 /usr/lib/rtkit/rtkit-daemon
root      1490     2  0 Mai11 ?        00:04:34 [kworker/2:2]
root      1530     1  0 Mai11 ?        00:06:28 /opt/teamviewer9/tv_bin/teamviewerd -f
mosquito  1679 31882  0 Mai16 pts/24   00:00:00 bash
mosquito  1760  2405  0 17:01 ?        00:00:02 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.1390.1896285120
mosquito  1787     1  0 Mai11 ?        00:01:18 /usr/bin/gnome-keyring-daemon --daemonize --login
mosquito  1791  1395  0 Mai11 ?        00:00:03 init --user
mosquito  1857  1791  0 Mai11 ?        00:00:00 ssh-agent
mosquito  1863  1791  0 Mai11 ?        00:18:59 dbus-daemon --fork --session --address=unix:abstract=/tmp/dbus-eDqznwMihK
mosquito  1871  1791  0 Mai11 ?        00:00:00 upstart-event-bridge
mosquito  1874  1791  0 Mai11 ?        00:00:01 /usr/lib/x86_64-linux-gnu/hud/window-stack-bridge
mosquito  1885  1791  0 Mai11 ?        00:00:00 upstart-file-bridge --daemon --user
mosquito  1887  1791  0 Mai11 ?        00:00:06 upstart-dbus-bridge --daemon --system --user --bus-name system
mosquito  1889  1791  0 Mai11 ?        00:06:41 upstart-dbus-bridge --daemon --session --user --bus-name session
mosquito  1891  1791  0 Mai11 ?        00:06:05 /usr/bin/ibus-daemon --daemonize --xim
mosquito  1905  1791  0 Mai11 ?        00:00:35 /usr/lib/unity-settings-daemon/unity-settings-daemon
mosquito  1909  1791  0 Mai11 ?        00:00:16 /usr/lib/x86_64-linux-gnu/hud/hud-service
mosquito  1912  1791  0 Mai11 ?        00:00:00 /usr/lib/at-spi2-core/at-spi-bus-launcher --launch-immediately
mosquito  1913  1791  0 Mai11 ?        00:00:05 gnome-session --session=ubuntu
mosquito  1915  1791  0 Mai11 ?        00:44:50 /usr/lib/unity/unity-panel-service
mosquito  1919  1912  0 Mai11 ?        00:00:00 /bin/dbus-daemon --config-file=/etc/at-spi2/accessibility.conf --nofork --print-address 3
mosquito  1922  1791  0 Mai11 ?        00:00:02 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
mosquito  1928  1791  0 Mai11 ?        00:00:00 /usr/lib/gvfs/gvfsd
mosquito  1933  1791  0 Mai11 ?        00:00:00 /usr/lib/gvfs/gvfsd-fuse /run/user/1000/gvfs -f -o big_writes
mosquito  1955  1791  0 Mai11 ?        00:07:48 /usr/lib/x86_64-linux-gnu/bamf/bamfdaemon
mosquito  1967  1791  0 Mai11 ?        00:00:01 /usr/lib/x86_64-linux-gnu/indicator-keyboard-service --use-gtk
mosquito  1969  1791  0 Mai11 ?        00:00:00 /usr/lib/x86_64-linux-gnu/indicator-messages/indicator-messages-service
mosquito  1970  1791  0 Mai11 ?        00:00:00 /usr/lib/x86_64-linux-gnu/indicator-bluetooth/indicator-bluetooth-service
mosquito  1972  1791  0 Mai11 ?        00:00:32 /usr/lib/x86_64-linux-gnu/indicator-power/indicator-power-service
mosquito  1974  1791  0 Mai11 ?        00:00:07 /usr/lib/x86_64-linux-gnu/indicator-datetime/indicator-datetime-service
mosquito  1979  1791  0 Mai11 ?        00:05:37 /usr/lib/x86_64-linux-gnu/indicator-sound/indicator-sound-service
mosquito  1980  1791  0 Mai11 ?        00:00:00 /usr/lib/x86_64-linux-gnu/indicator-printers/indicator-printers-service
mosquito  1987  1791  0 Mai11 ?        00:00:15 /usr/lib/x86_64-linux-gnu/indicator-session/indicator-session-service
mosquito  1988  1791  0 Mai11 ?        00:20:20 /usr/lib/x86_64-linux-gnu/indicator-application/indicator-application-service
mosquito  2012  1791  1 Mai11 ?        03:42:04 /usr/bin/pulseaudio --start --log-target=syslog
mosquito  2040  1791  0 Mai11 ?        00:00:00 /usr/lib/evolution/evolution-source-registry
mosquito  2042  1791  0 Mai11 ?        00:00:15 /usr/lib/x86_64-linux-gnu/notify-osd
mosquito  2046  1891  0 Mai11 ?        00:00:00 /usr/lib/ibus/ibus-dconf
mosquito  2047  1891  0 Mai11 ?        00:01:05 /usr/lib/ibus/ibus-ui-gtk3
mosquito  2049  1791  0 Mai11 ?        00:00:36 /usr/lib/ibus/ibus-x11 --kill-daemon
mosquito  2086  1891  0 Mai11 ?        00:01:33 /usr/lib/ibus/ibus-engine-simple
mosquito  2113  1913  5 Mai11 ?        09:58:57 compiz
colord    2115     1  0 Mai11 ?        00:00:00 /usr/lib/colord/colord
mosquito  2116  2405  0 17:04 ?        00:00:05 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.1394.1708854783
mosquito  2117  1791  0 Mai11 ?        00:00:00 /usr/lib/dconf/dconf-service
mosquito  2121  1905  0 Mai11 ?        00:03:05 syndaemon -i 1.0 -t -K -R
mosquito  2205  1913  0 Mai11 ?        00:03:09 nm-applet
mosquito  2207  1913  0 Mai11 ?        00:03:34 nautilus -n
mosquito  2209  1913  0 Mai11 ?        00:00:02 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
mosquito  2211  1913  0 Mai11 ?        00:02:11 /usr/bin/python3 /opt/extras.ubuntu.com/my-weather-indicator/bin/my-weather-indicator
mosquito  2212  1913  0 Mai11 ?        01:13:07 indicator-multiload
mosquito  2214  1913  0 Mai11 ?        00:00:05 /usr/lib/unity-settings-daemon/unity-fallback-mount-helper
mosquito  2231  1791  0 Mai11 ?        00:00:01 /usr/lib/gvfs/gvfs-udisks2-volume-monitor
mosquito  2235  1791  0 Mai11 ?        00:00:00 /usr/lib/x86_64-linux-gnu/gconf/gconfd-2
root      2245     1  0 Mai11 ?        00:00:38 /usr/lib/udisks2/udisksd --no-debug
mosquito  2256  1791  0 Mai11 ?        00:00:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
mosquito  2261  1791  0 Mai11 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
mosquito  2269  1791  0 Mai11 ?        00:00:02 /usr/lib/evolution/evolution-calendar-factory
mosquito  2273  1791  0 Mai11 ?        00:00:00 /usr/lib/gvfs/gvfs-mtp-volume-monitor
mosquito  2290  1791  0 Mai11 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.5 /org/gtk/gvfs/exec_spaw/0
mosquito  2320  1791  0 Mai11 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.5 /org/gtk/gvfs/exec_spaw/1
mosquito  2330  1791  0 Mai11 ?        00:00:00 /usr/lib/gvfs/gvfsd-metadata
mosquito  2336  1913  0 Mai11 ?        00:00:00 telepathy-indicator
mosquito  2344  1791  0 Mai11 ?        00:00:19 /usr/lib/telepathy/mission-control-5
mosquito  2357  1913  0 Mai11 ?        00:00:14 zeitgeist-datahub
mosquito  2362  1791  0 Mai11 ?        00:00:02 /usr/bin/zeitgeist-daemon
mosquito  2368  1791  0 Mai11 ?        00:00:09 /usr/lib/x86_64-linux-gnu/zeitgeist-fts
mosquito  2370  2368  0 Mai11 ?        00:00:00 /bin/cat
mosquito  2388  1791  3 Mai11 ?        07:44:53 /usr/bin/google-chrome-stable
mosquito  2396  2388  0 Mai11 ?        00:02:01 /usr/bin/google-chrome-stable
mosquito  2397  2388  0 Mai11 ?        00:00:00 /opt/google/chrome/chrome-sandbox /opt/google/chrome/chrome --type=zygote
mosquito  2398  2397  0 Mai11 ?        00:00:00 /opt/google/chrome/chrome --type=zygote
mosquito  2404  2398  0 Mai11 ?        00:00:00 /opt/google/chrome/nacl_helper
mosquito  2405  2398  0 Mai11 ?        00:00:01 /opt/google/chrome/chrome --type=zygote
mosquito  2453  1791  1 Mai15 ?        01:31:33 audacious
mosquito  2503  2405  0 Mai11 ?        00:15:18 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --extension-process --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.2.1833567117
mosquito  2544  2405  0 Mai11 ?        00:38:35 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.4.1433666610
mosquito  2559  2405  0 Mai11 ?        01:54:30 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.5.1969422326
mosquito  2569  1913  0 Mai11 ?        00:00:09 update-notifier
mosquito  2589  2405  0 Mai11 ?        00:00:07 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.7.2103577292
mosquito  2604  2405  0 Mai11 ?        00:00:06 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.8.1194928852
mosquito  2627  2405  0 Mai11 ?        00:00:18 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.10.1323564556
mosquito  2638  2405  0 Mai11 ?        00:00:06 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.11.2098829617
mosquito  2674  2388  1 Mai11 ?        02:40:31 /opt/google/chrome/chrome --type=gpu-process --channel=2388.14.926894310 --supports-dual-gpus=false --gpu-driver-bug-workarounds=0,1,2,9,11,28 --disable-accelerated-video-decode --gpu-vendor-id=0x8086 --gpu-device-id=0x0166 --gpu-driver-vendor=Mesa --gpu-driver-version=10.1.0
mosquito  2676  2405  0 Mai11 ?        00:00:15 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.15.1921687339
mosquito  2683  2674  0 Mai11 ?        00:00:00 /opt/google/chrome/chrome --type=gpu-process --channel=2388.14.926894310 --supports-dual-gpus=false --gpu-driver-bug-workarounds=0,1,2,9,11,28 --disable-accelerated-video-decode --gpu-vendor-id=0x8086 --gpu-device-id=0x0166 --gpu-driver-vendor=Mesa --gpu-driver-version=10.1.0
mosquito  2759  2405  0 Mai11 ?        00:06:25 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.18.985101945
mosquito  2771  2405  0 Mai11 ?        00:02:36 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.19.1438004619
mosquito  2836  1913  0 Mai11 ?        00:00:02 /usr/lib/x86_64-linux-gnu/deja-dup/deja-dup-monitor
root      2846     1  0 Mai12 ?        00:00:00 /usr/sbin/cups-browsed
mosquito  2880  2405  1 Mai11 ?        02:42:04 /opt/google/chrome/chrome --type=ppapi --channel=2388.28.759582829 --ppapi-flash-args --lang=en-US
root      4006     1  0 Mai18 ?        00:00:00 /usr/sbin/cupsd -f
mosquito  4357  1791  0 Mai12 ?        00:00:03 /usr/lib/x86_64-linux-gnu/unity-scope-home/unity-scope-home
mosquito  4373  1791  0 Mai12 ?        00:00:08 /usr/bin/unity-scope-loader applications/applications.scope applications/scopes.scope commands.scope
mosquito  4374  1791  0 Mai12 ?        00:00:00 /usr/lib/x86_64-linux-gnu/unity-lens-files/unity-files-daemon
mosquito  4396  1791  0 Mai12 ?        00:00:05 /usr/lib/x86_64-linux-gnu/unity-lens-music/unity-music-daemon
mosquito  6348  2405  0 Mai18 ?        00:00:07 /opt/google/chrome/chrome --type=renderer --disable-databases --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.1267.1428266994
mosquito  6963  2405  0 17:11 ?        00:00:03 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.1402.1957247587
root      7077     2  0 17:12 ?        00:00:00 [kworker/u9:2]
root      7167     2  0 Mai17 ?        00:00:00 [kworker/1:1]
mosquito  7203  1791  0 17:15 ?        00:00:02 gedit /home/mosquito/RUN/SS/Assignment 3/ESCJava/ESCJava-2.0.5-04-11-08-binary/Bag.java
root      7788     2  0 18:07 ?        00:00:00 [irq/47-mei_me]
root      7829     2  0 18:07 ?        00:00:02 [kworker/u8:63]
root      8042  1791  0 Mai14 ?        00:00:08 hostapd -B /etc/ap-hotspot.conf -f /tmp/hostapd.log
root      8047     2  0 18:07 ?        00:00:00 [kworker/3:2]
root      8056     2  0 18:07 ?        00:00:00 [hci0]
root      8058     2  0 18:07 ?        00:00:00 [hci0]
root      8098     2  0 18:07 ?        00:00:00 [kworker/2:0]
mosquito  8249  2405  0 10:31 ?        00:05:09 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.1328.870438938
mosquito  8361  2405  0 18:09 ?        00:00:21 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.1406.1730009764
mosquito  8424  2405 13 18:10 ?        00:08:29 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.1408.2113778522
mosquito  8834  1791  0 Mai11 ?        00:04:52 /usr/bin/python /usr/bin/software-center
mosquito  8849  1791  0 Mai11 ?        00:00:11 /usr/lib/geoclue/geoclue-master
mosquito  8853  1791  0 Mai11 ?        00:00:12 /usr/lib/x86_64-linux-gnu/ubuntu-geoip-provider
mosquito  9525  1791  0 Mai11 ?        00:00:00 /usr/lib/gvfs/gvfsd-http --spawner :1.5 /org/gtk/gvfs/exec_spaw/3
mosquito 10294  2405  1 18:46 ?        00:00:22 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.1413.699002811
mosquito 10491  2405  0 18:50 ?        00:00:09 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.1415.1995325820
root     10996     2  0 19:00 ?        00:00:00 [kworker/0:2]
mosquito 11512  2405  0 Mai17 ?        00:00:51 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.1177.305524162
mosquito 11563 31882  0 19:06 pts/6    00:00:00 bash
root     11619     2  0 19:06 ?        00:00:00 [kworker/u8:0]
mosquito 11623 11563  0 19:06 pts/6    00:00:00 find / -name daemon.conf
root     11627 11563  0 19:06 pts/6    00:00:00 sudo find / -name daemon.conf
root     11631 11627  0 19:07 pts/6    00:00:00 find / -name daemon.conf
root     11686     1  0 19:08 ?        00:00:00 /usr/bin/python3 /usr/sbin/aptd
root     11868 11563  0 19:11 pts/6    00:00:00 sudo nano default.pa
root     11871 11868  0 19:11 pts/6    00:00:00 nano default.pa
mosquito 11892  2405  9 19:11 ?        00:00:15 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.1416.1296391861
mosquito 11923  2405  0 Mai16 ?        00:02:53 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.999.713560538
root     11924     2  0 19:12 ?        00:00:00 [kworker/u8:1]
mosquito 11998  2405  8 19:13 ?        00:00:02 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.1417.1726798241
root     12032 12614  0 19:14 pts/24   00:00:00 sleep 5
mosquito 12033 11563  0 19:14 pts/6    00:00:00 ps -eaf
dnsmasq  12541  1791  0 11:10 ?        00:00:00 /usr/sbin/dnsmasq -x /var/run/dnsmasq/dnsmasq.pid -u dnsmasq -r /var/run/dnsmasq/resolv.conf -7 /etc/dnsmasq.d,.dpkg-dist,.dpkg-old,.dpkg-new
root     12602  1791  0 11:10 ?        00:00:16 hostapd -B /etc/ap-hotspot.conf -f /tmp/hostapd.log
root     12614  1791  0 11:10 pts/24   00:00:05 /bin/bash /usr/bin/ap-hotspot restart
root     15113     2  0 Mai16 ?        00:01:52 [kworker/3:1]
mosquito 16707  2405  0 11:53 ?        00:00:08 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.1348.1524228089
mosquito 16849  2405  0 Mai15 ?        00:11:15 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.922.115017820
mosquito 16864  2405  0 11:54 ?        00:01:36 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.1350.351922477
mosquito 17284  2405  0 Mai12 ?        00:00:41 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.657.1725661995
mosquito 18597  2405  0 Mai16 ?        00:00:48 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.1007.1113809147
mosquito 19155  2405  0 Mai16 ?        00:25:03 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --extension-process --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.1011.1650948330
root     20029  1791  0 Mai18 ?        00:00:02 hostapd -B /etc/ap-hotspot.conf -f /tmp/hostapd.log
mosquito 20042  1791  0 Mai18 ?        00:00:00 dbus-launch --autolaunch=a1c09f78fb266a62e3994fd753503704 --binary-syntax --close-stderr
mosquito 20043  1791  0 Mai18 ?        00:00:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
mosquito 20046  1791  0 Mai18 ?        00:00:01 /usr/lib/x86_64-linux-gnu/notify-osd
mosquito 20050  1791  0 Mai18 ?        00:00:00 /usr/lib/gvfs/gvfsd
mosquito 20059  1791  0 Mai18 ?        00:00:06 /usr/bin/gnome-screensaver --no-daemon
mosquito 20418  2405  0 14:54 ?        00:00:01 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.1359.461828104
mosquito 20753  2405  0 Mai16 ?        00:38:42 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.1065.1623052803
mosquito 21387  8834  0 Mai11 ?        00:00:00 [debconf-communi] <defunct>
mosquito 21645  2405  0 Mai15 ?        00:01:27 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.929.924127122
root     22389     1  0 Mai16 ?        00:00:00 upstart-udev-bridge --daemon
root     22392     1  0 Mai16 ?        00:00:00 /lib/systemd/systemd-udevd --daemon
root     22469     1  0 Mai16 ?        00:00:00 /lib/systemd/systemd-logind
mosquito 22524  1791  0 Mai11 ?        00:00:01 /usr/lib/gvfs/gvfsd-recent --spawner :1.5 /org/gtk/gvfs/exec_spaw/4
mosquito 24001  2405  0 15:47 ?        00:00:06 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.1364.1138835251
root     24089     2  0 Mai18 ?        00:00:01 [kworker/u9:1]
mosquito 24225  2405  0 15:50 ?        00:00:03 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.1366.1354586770
mosquito 25153  2405  0 16:02 ?        00:00:07 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.1369.1061512760
mosquito 25747  2405  0 Mai18 ?        00:01:40 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.1303.619114510
mosquito 26280  2405  0 16:20 ?        00:00:42 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.1373.1102919630
root     26650     2  0 Mai11 ?        00:00:00 [kworker/1:1H]
root     26651     2  0 Mai11 ?        00:00:00 [kworker/2:1H]
root     26652     2  0 Mai11 ?        00:00:00 [kworker/3:1H]
mosquito 26698  2405  0 Mai17 ?        00:01:31 /opt/google/chrome/chrome --type=renderer --disable-databases --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.1248.726777278
mosquito 26945  2405  0 Mai17 ?        00:01:25 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.1249.1407307418
root     27045     2  0 Mai18 ?        00:00:30 [kworker/0:1]
mosquito 28878  1791  1 Mai13 ?        02:14:56 skype
mosquito 29228  2405  0 Mai18 ?        00:00:17 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.1313.1332709312
mosquito 31084  1791  0 Mai13 ?        00:00:13 gnome-calculator
mosquito 31134  2405  0 00:04 ?        00:02:35 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.1315.15502890
mosquito 31882  1791  0 Mai13 ?        00:00:37 gnome-terminal
mosquito 31927  2405  0 Mai16 ?        00:00:24 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AutocompleteDynamicTrial_2/DefaultControl_R2_Stable/ExtensionInstallVerification/None/OmniboxBundledExperimentV1/StableBookmarkValue10LaunchCandidate/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderDisabled/PrerenderLocalPredictorSpec/LocalPredictor=Disabled/QUIC/Disabled/SettingsEnforcement/no_enforcement/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Experiment/UMA-Population-Restrict/normal/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_09/UMA-Uniformity-Trial-1-Percent/group_10/UMA-Uniformity-Trial-10-Percent/group_01/UMA-Uniformity-Trial-100-Percent/group_01/UMA-Uniformity-Trial-20-Percent/group_01/UMA-Uniformity-Trial-5-Percent/group_10/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --enable-deadline-scheduling --disable-accelerated-video-decode --channel=2388.1018.1687675848
mosquito 31928 31882  0 Mai13 ?        00:00:00 gnome-pty-helper
```

---

### Post by childintime on 2014-06-06
Bump

It's just unbelievable...... i am thinking about using different OS altogether now due to this ridiculous thing. I cannot even listen music loudly cause I can still hear that noise.

---

### Post by childintime on 2014-07-20
Now issue was gone for a month, and now again appeared. Is it even possible that it's software issue considering I always use the same software?

---

### Post by childintime on 2014-08-06
If it's ok, I will keep bumping this thread once a week or two, so maybe someone who has the idea for solution can help me.

---

### Post by childintime on 2014-08-17
Do you guys think it is possible that's something apart from defective hardware issue? I would appreciate so much if someone would give me some advice on what else to check and try :)

UPDATE: Just found this: [https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)

I added ```
[COLOR=#333333]options snd-hda-intel position_fix=2[/COLOR]
```

to [COLOR=#333333][FONT=Ubuntu Beta]/etc/modprobe.d/alsa-base.conf and [/FONT][/COLOR]rebooted, and cracking is gone. I tried ..fix=1, but it made no difference. Anyways, I am not sure if it's fixed, because it often disappears, but I will update this thread after some time just to make sure :)

---

### Post by dragonfly41 on 2014-08-17
I haven't read this thread in full .. but I understand that you are experiencing annoying background noise.

A long shot .. but on occasions when I have had multiple tabs left open in firefox I would hear audio from one of the firefox tabs.  I would then have to close that tab to kill the background audio.

Is this possible in your situation?

---

### Post by childintime on 2014-08-17
> **dragonfly41 said:**
> I haven't read this thread in full .. but I understand that you are experiencing annoying background noise.

A long shot .. but on occasions when I have had multiple tabs left open in firefox I would hear audio from one of the firefox tabs.  I would then have to close that tab to kill the background audio.

Is this possible in your situation?

No, because it's not application specific, sometimes sound is on freshly booted system, or it even starts before I login (while Ubuntu loading). Also that sound is if I boot into Live USB. Not to mention I don't even use Firefox :)

---

### Post by dragonfly41 on 2014-08-17
Considering how long you have had this annoying problem .. if I had Windows available (in a dual boot configuration?) ..

> That sound is also in live ubuntu usb, but not on the Windows 8 so I would think it's unbuntu problem.

then I would ..

(a) install VirtualBox in Windows (on the problem PC)

(b) install Ubuntu as VM on Virtual Box

(c) see if I get the same problem in the Ubuntu VM on Windows.

Although a lengthy step to take this might offer more clues.

---

### Post by childintime on 2014-08-17
> **dragonfly41 said:**
> Considering how long you have had this annoying problem .. if I had Windows available (in a dual boot configuration?) ..



then I would ..

(a) install VirtualBox in Windows (on the problem PC)

(b) install Ubuntu as VM on Virtual Box

(c) see if I get the same problem in the Ubuntu VM on Windows.

Although a lengthy step to take this might offer more clues.

Yes, it's an option, but even if it works perfectly in Windows, what can I do to fix it in Ubuntu? Because I tried pretty much everything I could find. But anyways, as of now it's all good since I made that change I told above, hopefully it's fixed.

---

### Post by childintime on 2014-08-18
Update: problem still the same, those fixes didn't solve anything.

---

### Post by dragonfly41 on 2014-08-19
I have not experienced the problem you report.

But since this rogue noise occurs before you login my _best guess_ would be to explore/tweak/change your Ubuntu kernel.

[http://www.linux-magazine.com/Issues/2009/100/Multimedia-and-the-Kernel](http://www.linux-magazine.com/Issues/2009/100/Multimedia-and-the-Kernel)

What do you see when you run **uname -a** in terminal?

Have you tried a different kernel?  

System Tools > Administration > Synaptic Package Manager > search "kernel" shows kernels.

Also ...

Ubuntu Tweak in System Settings shows All Apps > Multimedia 

But these ideas are shots in the dark.

---

### Post by childintime on 2014-08-19
> **dragonfly41 said:**
> I have not experienced the problem you report.

But since this rogue noise occurs before you login my _best guess_ would be to explore/tweak/change your Ubuntu kernel.

[http://www.linux-magazine.com/Issues/2009/100/Multimedia-and-the-Kernel](http://www.linux-magazine.com/Issues/2009/100/Multimedia-and-the-Kernel)

What do you see when you run **uname -a** in terminal?

Have you tried a different kernel?  

System Tools > Administration > Synaptic Package Manager > search "kernel" shows kernels.

Also ...

Ubuntu Tweak in System Settings shows All Apps > Multimedia 

But these ideas are shots in the dark.

uname -a:

```
Linux mosquito-K56CB 3.13.0-34-generic #60-Ubuntu SMP Wed Aug 13 15:45:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```
I didn't try another kernel. I had this problem when I had Ubuntu 13.10, and now it's the same on Ubuntu 14.04.

---

### Post by dragonfly41 on 2014-08-19
Perhaps pick up some tips from here ... [http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240)

[Edit]
and see this old thread ... [URL="http://ubuntuforums.org/showthread.php?t=1271535"]http://ubuntuforums.org/showthread.php?t=1271535

[/URL][http://www.stevelarkins.freeuk.com/computer_interference.htm](http://www.stevelarkins.freeuk.com/computer_interference.htm)


[Further edit]
[U]
However[/U] .. the above does not explain why you only hear the rogue sound on Ubuntu (different versions) and not on Windows.

---

### Post by childintime on 2014-08-20
> **dragonfly41 said:**
> Perhaps pick up some tips from here ... [http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240)

[Edit]
and see this old thread ... [URL="http://ubuntuforums.org/showthread.php?t=1271535"]http://ubuntuforums.org/showthread.php?t=1271535

[/URL][http://www.stevelarkins.freeuk.com/computer_interference.htm](http://www.stevelarkins.freeuk.com/computer_interference.htm)


[Further edit]
[U]
However[/U] .. the above does not explain why you only hear the rogue sound on Ubuntu (different versions) and not on Windows.

I can't seem to find any related info on those links. Also keep in mind, that it is coming from laptop speakers, if I insert headphone jack, it disappears completely, just as if I mute the sound, so it's very weird.

---

### Post by dragonfly41 on 2014-08-20
Can you test your laptop with power lead disconnected .. i.e. running only on battery?

The last link I posted (on RFI) refers to possible pickup via power lines.

> Don't forget to feed the mains power cable to the computer speaker's  amplifier around a ferrite ring too, as it is very common for most of  the interference in these cases to emanate from the 120V or 240V mains  power supply.[LEFT][COLOR=#000000]
Read more: [http://www.stevelarkins.freeuk.com/computer_interference.htm#ixzz3AvWegiMk](http://www.stevelarkins.freeuk.com/computer_interference.htm#ixzz3AvWegiMk)
[/COLOR][/LEFT]


---

### Post by childintime on 2014-08-20
> **dragonfly41 said:**
> Can you test your laptop with power lead disconnected .. i.e. running only on battery?

The last link I posted (on RFI) refers to possible pickup via power lines.

I disconnected power cable and cracking sound disappeared after like 5 seconds. I now reconnected and that sound is gone, so I will wait until it appears once again to test it again.

Ok, tested some more. So whenever there is cracking sound, removing power cable completely removes that noise BUT only if there is not sound playing. If I start some video or music, then cracking sound appears even with removed power cable. But removing cable while no sound is playing always seems to completely remove that noise (as long as I don't start playing music). If I start playing music/video, cracking sound immediately appears.

---

### Post by dragonfly41 on 2014-08-20
> ... and cracking sound disappeared after like 5 seconds

That sounds like some capacitive effect.   Would it be possible to "earth" metal part of your laptop to some earth point such as a metal radiator pipe while running in battery mode and playing music?   A good earth might help.   Just an idea.

---

### Post by childintime on 2014-08-20
> **dragonfly41 said:**
> That sounds like some capacitive effect.   Would it be possible to "earth" metal part of your laptop to some earth point such as a metal radiator pipe while running in battery mode and playing music?   A good earth might help.   Just an idea.

I also made an edit to my previous post in case you missed. Anyways, I don't really have any metal parts on my laptop. What I tried is removing all electronic devices around laptop and disconnecting power and ethernet cables, but it's still the same if music is playing.

Also my laptop got two speakers, and that cracking sound is coming only from one of them: [http://i.imgur.com/WLKs0cf.jpg?1](http://i.imgur.com/WLKs0cf.jpg?1)

Either way, when no sound is playing, removing power cable removes that noise completely, so it's somehow related for sure. But it's very strange that it again appears when I turn music on.

---

### Post by dragonfly41 on 2014-08-20
From here ...

[http://www.tomshardware.co.uk/forum/288382-28-laptop-power-cable-causing-weird-noise-speakers](http://www.tomshardware.co.uk/forum/288382-28-laptop-power-cable-causing-weird-noise-speakers)

The last poster in this thread suggests a ground loop problem.

Also read one solution here ...

[http://forum.cockos.com/showthread.php?t=79559](http://forum.cockos.com/showthread.php?t=79559)

---

### Post by childintime on 2014-08-20
> **dragonfly41 said:**
> From here ...

[http://www.tomshardware.co.uk/forum/288382-28-laptop-power-cable-causing-weird-noise-speakers](http://www.tomshardware.co.uk/forum/288382-28-laptop-power-cable-causing-weird-noise-speakers)

The last poster in this thread suggests a ground loop problem.

Also read one solution here ...

[http://forum.cockos.com/showthread.php?t=79559](http://forum.cockos.com/showthread.php?t=79559)

Well first, I don't use and external speakers, as discussed in those threads, and second, noise still remain even if power cable is unplugged (if music is playing), so I don't think, somehow fixing cable would help with that.

Thanks anyways.

---

### Post by dragonfly41 on 2014-08-20
> Anyways, I don't really have any metal parts on my laptop

See metal socket top right in your posted jpg.  Continue to try to earth.

---

### Post by childintime on 2014-08-20
> **dragonfly41 said:**
> See metal socket top right in your posted jpg.  Continue to try to earth.

Which metal socket you are talking about exactly, and what can I do to earth it? :mad:

---

### Post by dragonfly41 on 2014-08-20
> Well first, I don't use and external speakers, as discussed in those threads, 

I don't believe that it matters whether internal or external ... any speaker (internal or external) can become an antenna for RFI.

I don't know what laptop you have but the image you posted shows a metal socket here ... see image below ...

To earth laptop just find a length of copper wire which can earth the metal socket to a bare metal pipe such as radiator. An anti static clip is good for this.

Otherwise ... can you try plugging your power adapter into a different mains socket perhaps in a different room? Perhaps on different ring main?

see also here ... more tips ...

[https://www.youtube.com/watch?v=jSA2F1AwboU](https://www.youtube.com/watch?v=jSA2F1AwboU)

---

### Post by childintime on 2014-08-20
> **dragonfly41 said:**
> I don't believe that it matters whether internal or external ... any speaker (internal or external) can become an antenna for RFI.

I don't know what laptop you have but the image you posted shows a metal socket here ... see image below ...

To earth laptop just find a length of copper wire which can earth the metal socket to a bare metal pipe such as radiator. An anti static clip is good for this.

Otherwise ... can you try plugging your power adapter into a different mains socket perhaps in a different room? Perhaps on different ring main?

see also here ... more tips ...

[https://www.youtube.com/watch?v=jSA2F1AwboU](https://www.youtube.com/watch?v=jSA2F1AwboU)

Currently I don't have access to things like copper wire, but I will get it in few days and check it out. Also is there no danger of inserting copper cable into socket (in regards to electricity)?

Oh and, in that video, he removes the cable, and cracking sound disappears unlike in my case. Anyways I will try it and update :)

---

### Post by dragonfly41 on 2014-08-20
> Currently I don't have access to things like copper wire

**Don't** insert wire **into** the socket .. only touch the **outside** metal part .. and in battery only mode .. no power connected..


[Edit]

> Oh and, in that video, he removes the cable, and cracking sound disappears unlike in my case.

Now** I'm** confused .. isn't that what you've just tested .. remove power to run in battery only mode and crackling sound disappears (until you switch on music)?

---

### Post by childintime on 2014-08-20
> **dragonfly41 said:**
> **Don't** insert wire **into** the socket .. only touch the **outside** metal part .. and in battery only mode .. no power connected..

Ahh okay, gotcha :D

---

### Post by dragonfly41 on 2014-08-20
See my late edit.

---

### Post by childintime on 2014-08-20
> **dragonfly41 said:**
> 
Now** I'm** confused .. isn't that what you've just tested .. remove power to run in battery only mode and crackling sound disappears (until you switch on music)?

No. What I said is:

1. If no music is playing and I remove power cable then cracking always stops. If I then insert the cable, cracking does not appear as long as I don't turn on music.
2. If music is playing, removing power cable makes no difference.

---

### Post by childintime on 2014-10-22
Update:

So it goes like this. Full month everything works perfectly, then for 2 weeks sound will be cracking, then again whole month it works without problems, and so on. :(

---

### Post by JazzPotato on 2014-10-22
Problems like this can be caused by interference from wireless mice and keyboards, they can interfere with speakers in headphones, laptops, etc. I hear a perceptible crackling whenever I scroll the wheel on my mouse because of the interference with my laptop's speakers. You could try using wired peripherals?

---

### Post by childintime on 2014-10-22
> **JazzPotato said:**
> Problems like this can be caused by interference from wireless mice and keyboards, they can interfere with speakers in headphones, laptops, etc. I hear a perceptible crackling whenever I scroll the wheel on my mouse because of the interference with my laptop's speakers. You could try using wired peripherals?

Well, the sound is very strong, and I don't use any non-wired peripherals. The only thing I have is router, but cracking sound was even without router. Also sound remains even if I unplug everything (even charging cable) and bring laptop to different place.

---

### Post by geemac2 on 2014-10-22
I'm not an expert at this and neither am I a Dev or Programmer, look at my other posts...;)
I'm mostly a hardware person. ](*,) [SIZE=1](*couldn't find something with a hammer, but close enough.*)[/SIZE]

This  is what I did to correct my situation with the audio via HDMI to my  TV after grappling with this for months.
I used leafpad for my editor, pick your own poison...
----------------------------
First change was **default.pa**

 *sudo leafpad /etc/pulse/default.pa*

 If you are using line numbers it is roughly line 53...

 **Original line**:
*load-module module-udev-detect*
Added to the end of this line was tsched=0
**Changed to**:
*load-module module-udev-detect tsched=0*


 So after the first change failed which has worked for others, I changed the sample rate which apparently was too low for my Visio TV.

Next was **daemon.conf**:

 *sudo leafpad /etc/pulse/daemon.conf*
 Roughly lines 81 and 82...


 **Original lines**:
*default-sample-rate = 41000*
*alternate-sample-rate = 48000*

 **Changed to**:
*default-sample-rate = 48000*
*alternate-sample-rate = 96000*


 The sample rate change was the charm that worked for my hardware situation.
No more distortion and chopping/clipping sounds during standard vocal or  incidental music while watching recordings or live streams.
 Cheers
G

P.S.  Before you edit, save and close the edit window, you may want to make a comment of what the original line of code was and rem/comment it with a # before each comment.  
example:
# Original code... 
# [I]load-module module-udev-detect
# changed due to audio distortion.
# change made 22 October 2014[/I]
In some cases if I make quite a bit of changes I date stamp and place reason for the change.

---

### Post by geemac2 on 2014-10-22
OK get your popcorn out :popcorn:

If the moderators of this forum feel that this is not appropriate for this forum since it is hardware related; please feel free to move, delete and or give me hell for posting it here.  No offence will be taken.

If all the code changes given so far in this thread do not fix your issue, can you give a breakdown of how your system hardware is set up?  But first, follow the below steps.

Let's try some processes of elimination if the changes to the code in various files did not help.

{Audio Source} *Is used to reference a computer or your Linux based media system for audio output.*
{Audio Input Device} *Is used to reference a TV's audio input, Stereo Receiver or a A/V system.*

If you have HDMI directly to a TV for your video/audio input device then it could be the HDMI cable, but... that is rare for it to only affect one channel more then the other and not both equally.
The same goes for Toslink fiber or S/PDIF coaxial cable for audio (data) out.

If you have another audio source with HDMI out try it and see if the noise is still there.
If all is well then it is your oiginal audio source.  If the distortion is still there testing with a new audio source then we have rulled out the main audio source. But now, we still have the HDMI cable and the audio input device that could be bad or have oxidized connections.
 
Try another HDMI cable and if avilable another HDMI cable from a different manufacture.
Why I state a different manufacture, it is from my experience that I have found a whole line of cables bad from a certain manufacture. Name not to be mentioned.
I only use Amphenol Premium High-Speed Certified HDMI Cable.  Not cheap, but I have learned my lesson using low grade money saving HDMI cables.  As the old saying goes... "You get what you paid for."

If the HDMI cable swap still has distortion we are now down to the *audio input device*.

Try a different input on the audio input device if available. If the original input is the cause then try to find a spray can of a **zero residue cleaner** like *[I][SIZE=1]&#57380;[/SIZE]*CRC-05103[/I] or if *CRC**[SIZE=1]&#57380;[/SIZE] *is not available then use *DeOxit*[SIZE=1]&#57380;[/SIZE] and clean the plugs and jacks. Don't flood the item you are cleaning, use sparingly. 
*DeOxit*[SIZE=1]&#57380;[/SIZE] is not my favorite in high dust areas due to it being a cleaner/lubricant.
Most conections are silver or gold plated. As you already know what happens with silver or silver plate.  Use a cleaner such as *Tarn-X*[SIZE=1]&#57380; [/SIZE]on a q-tip to remove any tarnish in or around the connection. If using a cotton swab such as a Q-Tip*[I][SIZE=1]&#57380;[/SIZE]*[/I], make sure not to leave behind any cotton fibers.

Rubbing alcohol or diluted white vinegar with filtered water are other methods for cleaning electronic connections.
 I do not always recommend using vinegar being that it is acidic and will leave a residue, and if you don't clean up the moisture after cleaning the with the vinegar, it will eat up the metal in the conections.  I only use the vinegar solution if cleaning a heavily tarnished connection and *Tarn-X*[SIZE=1]&#57380;[/SIZE] is not available.  Using rubbing alcohol for cleaning, it leaves moisture and a residue , but if these on hand at home items are all you have available at the time, then use them sparingly and immediately dry the cleaned surface.  Also be careful of alcohol and any plastics that are used in plugs and jacks, if old and some cases new, the plastic can break down from the alcohol.

All the above can be followed if using any other method of cabling between devices.
All except cleaning,  Toslink[SIZE=1]([/SIZE][SIZE=1][SIZE=1]TM[/SIZE] of Toshiba)[/SIZE] is an optical fiber link and should only be very carefully cleaned with a non abrasive dry cloth at the tips of the cable if the optics are accessible.  Usually canned air for keyboards will do.

Cheers
G

---

### Post by childintime on 2014-10-22
geemac2, first of all thank you for your insight.

Now 'tsched=0' thing I made long ago, and it makes no difference. Tried your daemon.conf changes, also no difference. Keep in mind that this noise is not just when I listen to music, but it's ALWAYS. It starts even before I get login screen on fresh reboot.

Now regarding HDMI cables.. I use ASUS laptop, the only things connected to laptop are keyboard and mouse, I can remove them and sound still remains. Sound comes directly from one out of two laptop speakers.

---

### Post by geemac2 on 2014-10-24
Some of these laptops have horrible built in sound, I know mine  does.
Looking again through this thread we are talking about two different noise situations.
One being a timing and sample rate issue with audio output, especially audio over HDMI.
The other, in your case  your noise is probably being generated by the hard drive. I  listened to your audio sample and I'm leaning towards it coming from the  hard drive servo motors while it is doing a R/W. As for hard drive noise, you're kind of out  of luck on that issue unless you replace it with a SSD or go the route of USB audio.

If you have time, take a look at some of the  USB audio interfaces.  Some have sample rates as high as 192KHz such as Creative's E-MU line. There are also some cheap USB audio interfaces coming out of China now that  are not that bad, and what I have been told some are as good as the high  end ones.  Just search for USB sound cards.  Not sure why they call them cards but apparently that is just a carry over from days of old.

Cheers
G

---

### Post by childintime on 2014-10-24
> **geemac2 said:**
> Some of these laptops have horrible built in sound, I know mine  does.
Looking again through this thread we are talking about two different noise situations.
One being a timing and sample rate issue with audio output, especially audio over HDMI.
The other, in your case  your noise is probably being generated by the hard drive. I  listened to your audio sample and I'm leaning towards it coming from the  hard drive servo motors while it is doing a R/W. As for hard drive noise, you're kind of out  of luck on that issue unless you replace it with a SSD or go the route of USB audio.

If you have time, take a look at some of the  USB audio interfaces.  Some have sample rates as high as 192KHz such as Creative's E-MU line. There are also some cheap USB audio interfaces coming out of China now that  are not that bad, and what I have been told some are as good as the high  end ones.  Just search for USB sound cards.  Not sure why they call them cards but apparently that is just a carry over from days of old.

Cheers
G

But if it's hard drive problem, then why it makes cracking sound for like 2 weeks every day, and then completely stops for a month and works perfectly, even though I didn't change anything whatsoever...

---

### Post by zierom on 2014-12-07
Hi childintime,
when I was reading your post I suffered with you. I had the same problems under 14.04 with external speakers, whereas headphones worked flawlessly. However I found a solution that worked for me:

[http://askubuntu.com/questions/160882/popping-noise-from-laptop-speakers](http://askubuntu.com/questions/160882/popping-noise-from-laptop-speakers)

The method is to disable the intel audio power save settings..

---

### Post by Bucky Ball on 2014-12-07
Rather than trawl through every post, I'll just ask: Are you still using 13.10 or have you upgraded to a supported release?

13.10 is no longer supported and updates/upgrades are no longer available. This can be problematic and leave your machine vulnerable (no security updates). 

Just thought I'd mention. ;)

---

### Post by childintime on 2014-12-08
> **zierom said:**
> Hi childintime,
when I was reading your post I suffered with you. I had the same problems under 14.04 with external speakers, whereas headphones worked flawlessly. However I found a solution that worked for me:

[http://askubuntu.com/questions/160882/popping-noise-from-laptop-speakers](http://askubuntu.com/questions/160882/popping-noise-from-laptop-speakers)

The method is to disable the intel audio power save settings..

Thanks, but I am not able to follow the guide. It say edit "[FONT=Ubuntu Mono]/sys/module/snd_hda_intel/parameters/power_save".[/FONT] But I cannot save that after editing.


> **Bucky Ball said:**
> Rather than trawl through every post, I'll just ask: Are you still using 13.10 or have you upgraded to a supported release?

13.10 is no longer supported and updates/upgrades are no longer available. This can be problematic and leave your machine vulnerable (no security updates). 

Just thought I'd mention. ;)

I am using 14.04 LTS since its release.

---

### Post by zierom on 2014-12-08
I also found that confusing. I first modified the /usr/lib/pm-utils/power.d/intel-audio-powersave
that worked without problems.

I then tried to modify the /sys/module/snd_hda_intel/parameters/power_save
and the /sys/module/snd_hda_intel/parameters/power_save_controller

I gave root-writing permission to the files but they didn't want to save any changes at all. My guess is they were being used by another process.

Then I read the guide carefully again. And it says, after you've modified the /usr/lib/pm-utils/power.d/intel-audio-powersave
you're supposed to restart your system and then modify the remaining two files. And modifying those is only necessary if you have an HDA soundcard (whatever that is).

So I restarted and out of curiosity tested the speakers and they worked! So I didn't bother about changing the remaining files.

---

### Post by childintime on 2014-12-12
> **zierom said:**
> I also found that confusing. I first modified the /usr/lib/pm-utils/power.d/intel-audio-powersave
that worked without problems.

I then tried to modify the /sys/module/snd_hda_intel/parameters/power_save
and the /sys/module/snd_hda_intel/parameters/power_save_controller

I gave root-writing permission to the files but they didn't want to save any changes at all. My guess is they were being used by another process.

Then I read the guide carefully again. And it says, after you've modified the /usr/lib/pm-utils/power.d/intel-audio-powersave
you're supposed to restart your system and then modify the remaining two files. And modifying those is only necessary if you have an HDA soundcard (whatever that is).

So I restarted and out of curiosity tested the speakers and they worked! So I didn't bother about changing the remaining files.

Well I restarted as well, but still cannot save the files. And it didn't fix anything for me unfortunately.

---

### Post by childintime on 2015-02-08
bump just in case....

---

