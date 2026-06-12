---
title: "Can't play restricted DVDs"
date: 2021-07-02
forum: General Help
---

### Post by forteller2 on 2021-07-02
Hi. I'm on a laptop with Ubuntu 21.04, and I've done everything I can  think of to get DRM'd DVDs to work. Nothing's working, and now I hope I  can get help here. 

I've turned on multiverse and installed libdvd-pkg by  following this guide: [https://itsfoss.com/play-dvd-ubuntu-1310/](https://itsfoss.com/play-dvd-ubuntu-1310/).  I've installed libdvdcss and libdvdread8. I've installed  ubuntu-restricted-extras and VLC, and tried playing through Videos and  through VLC after rebooting. I've also checked that the DVD drive is region locked to the same region as the DVDs.

Videos gives me an error message: "DVD source is required  to play the file, but is not installed", but when I click on "Find in  Ubuntu Software" Ubuntu Software just shows up and gives me another  error about "DVD source you're looking for could not be found". 

DVDs  without DRM are playing just fine, but as you know most DVDs are "copy  protected". Please, does anyone know what's going on and can help me?  Thanks!

---

### Post by Frogs Hair on 2021-07-02
I would try installing vlc media player which is supposed to include codecs for DRM.

---

### Post by forteller2 on 2021-07-02
Thanks, but I've already tried that.

---

### Post by ActionParsnip on 2021-07-02
```

sudo apt install gstreamer1.0-plugins-bad

```
Source:
[https://bugs.launchpad.net/ubuntu/+source/gstreamer1.0/+bug/1809044](https://bugs.launchpad.net/ubuntu/+source/gstreamer1.0/+bug/1809044)

---

### Post by forteller2 on 2021-07-02
> **ActionParsnip said:**
> ```

sudo apt install gstreamer1.0-plugins-bad

```
Source:
[https://bugs.launchpad.net/ubuntu/+source/gstreamer1.0/+bug/1809044](https://bugs.launchpad.net/ubuntu/+source/gstreamer1.0/+bug/1809044)

Thanks, but that didn't help either.

But I figured out that I had misread the output of regionset. I thought it was set to the correct region (the PC has been used to play DVDs with Windows previously), but in fact it was not set to any region at all.

I set it to the correct region, and now:
- Videos still give me the same error message as before
- VLC plays some DRM'd DVDs fine, while others fail spectacularly:

The failing DVDs works fine in the menu part, but when I try to play the movie, one DVD:
- goes black, but plays the sound, won't let me go into full screen
While another DVD:
- Shows some of the video, but with a lot of green and gray boxes and lines, and it's extremely jittery. I can take it full screen, but it crashes the PC.

I'm trying this in Xorg.

Here's the output from the DVD that goes black on the movie:

```
avcodec decoder: Using Intel i965 driver for Intel(R) Ivybridge Mobile - 2.4.1 for hardware decoding
[mpeg2video @ 0x7fa2c8003d80] get_buffer() failed
[mpeg2video @ 0x7fa2c8003d80] thread_get_buffer() failed
[mpeg2video @ 0x7fa2c8003d80] get_buffer() failed (-12 (nil))
[00007fa2841fb7c0] main decoder error: buffer deadlock prevented
[000055da82ea1f30] main audio output error: too low audio sample frequency (0)
[00007fa2840795e0] main decoder error: failed to create audio output
[000055da82ea1f30] vlcpulse audio output error: digital pass-through stream connection failure: Not supported
[000055da82ea1f30] main audio output error: module not functional
[00007fa2840795e0] main decoder error: failed to create audio output
[000055da82ea1f30] main audio output error: too low audio sample frequency (0)
[00007fa2841fb7c0] main decoder error: failed to create audio output
[00007fa2840795e0] main decoder error: buffer deadlock prevented
[000055da82ea1f30] vlcpulse audio output error: digital pass-through stream connection failure: Not supported
[000055da82ea1f30] main audio output error: module not functional
[00007fa2841fb7c0] main decoder error: failed to create audio output
[ac3 @ 0x7fa290007b40] expacc 125 is out-of-range
[ac3 @ 0x7fa290007b40] error decoding the audio block
[ac3 @ 0x7fa290007b40] invalid coupling range (13 >= 13)
[ac3 @ 0x7fa290007b40] error decoding the audio block
```

Is there any way of fixing this? :/

---

