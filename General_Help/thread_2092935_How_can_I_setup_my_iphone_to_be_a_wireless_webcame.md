---
title: "How can I setup my iphone to be a wireless webcamera (wifi)"
date: 2012-12-09
forum: General Help
---

### Post by pittbbh on 2012-12-09
Does anyone know a way to use the video camera on my iphone 4s as a wireless webcam? Tried tinkering with iwebcamera but it really did not work out well with Ubuntu 12.04.1 LTS.

---

### Post by taidoka on 2013-05-12
Hi there,

I had the same problem. But I figured it out. 
First, read this post: [http://www.kudanai.com/2010/11/howto-use-your-iphone-as-webcam-in.html](http://www.kudanai.com/2010/11/howto-use-your-iphone-as-webcam-in.html)

Install all dependencies:
```
sudo apt-get install build-essential libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libtool autoconf mercurial gstreamer-tools git
```

Then install v4l2loopback from the native repositories:
```
sudo apt-get install v4l2loopback-dkms
```

Load the module:
```
sudo modprobe v4l2loopback
```

Get the gstreamer sink:
```
git clone http://github.com/umlaeute/gst-v4l2loopback.git
cd gst-v4l2loopback && ./autogen.sh
make && sudo make install
```

To get the stream working start the app (iWebcamera) on the iPhone and run the following command (you'll probably have to change wildcards/ip-address):
```
gst-launch souphttpsrc location=http://192.168.???.??:8080/strm ! jpegdec ! ffmpegcolorspace ! v4l2loopback device=/dev/video0
```

Each time the computer is restarted you have to reload the module and each time the app is restarted you have to launch above command as well.

I've written two little scripts which you can place in your ~/bin folder to start the stream and the application in question directly from commandline.
Make them executable:
```
mv skype.txt runskype && chmod +x runskype
mv runvlc.txt runvlc && chmod +x runvlc
```

Have fun
taidoka

NB. I'm not running maverick any more but LM 13 (Precise Pangolin).

---

