---
title: "IP Camera Viewer"
date: 2017-07-02
forum: General Help
---

### Post by ndstate on 2017-07-02
Hello,

I am looking for software that will allow me to view my ip cameras. I am not looking for recording or anything else, just accessing the live streaming (hence I don't need Zoneminder).

I cannot find anything for Ubuntu, any ideas?

Thanks

---

### Post by mmajames on 2017-07-02
What kind of IP cameras do you have. Most IP cameras have RTSP or RTP and can be viewed in VLC. All you need to know is the url to pull the stream. For example rtsp://admin:password@192.168.1.200:10554/Streaming/Channels/102

Other then using streaming via RTSP or RTP.  You will need a browser to log into camera. IE can be run in Wine sometimes but can be tricky to setup with a camera due to ActiveX plug-ins.

---

### Post by ndstate on 2017-07-02
Thanks. I know about that method, but its not really ideal -- it would be nice to view multiple streams side-by-side without having to open multiple VLCs. I just thought maybe there was something out there like [Tinycam]("https://tinycammonitor.com").

---

### Post by HermanAB on 2017-07-03
Err... make a script that spawns VLC, ffplay, xine, mplayer, whatever - side by side.

---

