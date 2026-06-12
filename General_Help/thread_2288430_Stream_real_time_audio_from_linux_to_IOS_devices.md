---
title: "Stream real time audio from linux to IOS devices"
date: 2015-07-27
forum: General Help
---

### Post by pirpi on 2015-07-27
Hi all,

I want to stream pactl ( pulseaudio ) recorded audio to ios devices. I am using following command at the linux side to start the real time audio stream

[COLOR=#333333][FONT=Consolas]pactl load-module module-simple-protocol-tcp rate=48000 format=s16le channels=2 record=true port=1234[/FONT][/COLOR] 

but, I am not able to play this stream on the ios devices.

Could you tell me the way to play this stream on ios devices?

Could you please help me with this?

Thanks

---

### Post by howefield on 2015-07-27
Are you streaming from an Ubuntu machine, what version ?

---

### Post by pirpi on 2015-07-27
Thanks for your reply.

I am using lubuntu 12.04.

Thanks

---

### Post by HermanAB on 2015-07-27
This works with pretty much anything on the client side:

[http://edna.sourceforge.net/](http://edna.sourceforge.net/)

[http://ubuntuforums.org/showthread.php?t=1941242](http://ubuntuforums.org/showthread.php?t=1941242)

---

### Post by pirpi on 2015-07-27
Thanks for your reply.

But I want to stream real time audio over tcp from linux system to ios device.

please help me with this.

Thanks

---

### Post by SeijiSensei on 2015-07-27
You could try a DLNA-based solution.  [Install]("http://ubuntuforums.org/showthread.php?t=1866520") **minidlna** on the Linux box, then read this: [http://techpp.com/2012/03/24/dlna-streaming-apps-iphone/](http://techpp.com/2012/03/24/dlna-streaming-apps-iphone/)

Apple devices are designed to work in the closed, proprietary world that Apple created.  That's why I would never own one.

---

### Post by pirpi on 2015-07-29
No I don't want to use dlna service. I want to use the pulseaudio (pactl) only. 

Could you please help me with this?

Thanks
pirpi

---

