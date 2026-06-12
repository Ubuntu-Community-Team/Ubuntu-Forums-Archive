---
title: "Microphone does not work. [Screenshots added]"
date: 2007-06-30
forum: General Help
---

### Post by Dean92 on 2007-06-30
The titel says it all,
My microphone doesn't work in Skype nor does it work in other recording apps like Sound Recorder.

It used to work, but after a reboot it stopped doing so.

It started when Skype started nagging about a Playback error,
which I fixed but which then produced a recording error.

Here are some screenshots

[img]http://i8.tinypic.com/6ag8ryd.png[/img]

[img]http://i10.tinypic.com/6f4nwar.png[/img]

[img]http://i11.tinypic.com/4uokwfa.png[/img]

[img]http://i10.tinypic.com/5zp487a.png[/img]

[img]http://i13.tinypic.com/632dq8n.png[/img]

Maybe I have to reset the volume panel?, if so, how?

Thanks in advance,

Dean.

P.S. I'm using V 7.04

---

### Post by eggdeng on 2007-06-30
Can you post the output of ```
aplay -l
```

---

### Post by Dean92 on 2007-07-01
```
dean@dean-linux:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
dean@dean-linux:~$
```

Somehow Skype (and other sound apps) now works to an extend, it records my MUSIC when this is playing, but not my voice.

So for some reason it's recording the system's internal sound, error sounds/music/notification sounds etc.

Also: I can't even call someone if the music isn't on because it would give me a Playback error.

EDIT:: These are the settings:

[IMG]http://i7.tinypic.com/525aq9d.png[/IMG]

[IMG]http://i9.tinypic.com/5zej0c7.png[/IMG]
For some reason, it keeps deselecting "Mic Capture".

Dean.

---

### Post by eggdeng on 2007-07-01
Looks like a lot of people are having problems with VIA 8293  but quite a few seem to have solved it by tweaking settings. You might get some ideas from [http://ubuntuforums.org/showthread.php?t=291992&highlight=VIA+8235+Skype&page=4](http://ubuntuforums.org/showthread.php?t=291992&highlight=VIA+8235+Skype&page=4) or [https://bugs.launchpad.net/ubuntu/+bug/80531](https://bugs.launchpad.net/ubuntu/+bug/80531). First thing might be to change Mic1 to Mic2  in Volume Control -> Options. Sorry not to be of more help.

---

### Post by Dean92 on 2007-07-01
Eggdeng, you sir,
Are AWESOME! :D

It works like a charm now!

Here are the settings which make my mic work:

[IMG]http://i9.tinypic.com/4kezx5c.png[/IMG]

[IMG]http://i17.tinypic.com/53ov9qs.png[/IMG]

[IMG]http://i14.tinypic.com/4ukwscp.png[/IMG]

[IMG]http://i18.tinypic.com/52kl0m9.png[/IMG]

[IMG]http://i17.tinypic.com/66cugkw.png[/IMG]

[IMG]http://i13.tinypic.com/4uopbpf.png[/IMG]

[IMG]http://i19.tinypic.com/680cb9w.png[/IMG]

See next post for the rest

---

### Post by Dean92 on 2007-07-01
Part 2/3:

[IMG]http://i7.tinypic.com/4zdc3fq.png[/IMG]

[IMG]http://i15.tinypic.com/4l720ef.png[/IMG]

[IMG]http://i8.tinypic.com/4u2ekb6.png[/IMG]

[IMG]http://i17.tinypic.com/67s59tw.png[/IMG]

[IMG]http://i17.tinypic.com/67s59tw.png[/IMG]

[IMG]http://i19.tinypic.com/4ue2lud.png[/IMG]

[IMG]http://i14.tinypic.com/63n15sn.png[/IMG]


See next post for the rest.

---

### Post by Dean92 on 2007-07-01
Part 3/3:

[IMG]http://i14.tinypic.com/6bamwix.png[/IMG]

[IMG]http://i8.tinypic.com/68hkx9j.png[/IMG]

[IMG]http://i15.tinypic.com/6ceptnd.png[/IMG]

And I applied this trick:

> **cccc said:**
> yep, **I've got recording working under dapper drake**:

according to:

[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

I've also done the following:

```
gedit ~.asoundrc
```

add the following text:```

pcm.skype {
   type asym
   playback.pcm "skypeout"
   capture.pcm "skypein"
}

pcm.skypein {
   # Convert from 8-bit unsigned mono (default format set by aoss when
   # /dev/dsp is opened) to 16-bit signed stereo (expected by dsnoop)
   #
   # We can't just use a "plug" plugin because although the open will
   # succeed, the buffer sizes will be wrong and we'll hear no sound at
   # all.
   type route
   slave {
      pcm "skypedsnoop"
      format S16_LE
   }
   ttable {
      0 {0 0.5}
      1 {0 0.5}
   }
}

pcm.skypeout {
   # Just pass this on to the system dmix
   type plug
   slave {
      pcm "dmix"
   }
}

pcm.skypedsnoop {
   type dsnoop
   ipc_key 1133
   slave {
      # "Magic" buffer values to get skype audio to work
      # If these are not set, opening /dev/dsp succeeds but no sound
      # will be heard. According to the alsa developers this is due
      # to skype abusing the OSS API.
      pcm "hw:0,0"
      period_size 256
      periods 16
      buffer_size 16384
   }
   bindings {
      0 0
   }
}
```
and changed in the skype settings from ALSA to **OSS**

**now the recording works great !**

Thanks for a million helping eggdeng!:)

Dean.

---

### Post by eggdeng on 2007-07-01
To be fair, you did most of the work yourself. Well done!

---

