---
title: "Need video recording apt"
date: 2012-10-22
forum: General Help
---

### Post by Silvernail on 2012-10-22
I am looking for an apt that will record video through my video camera or my webcam and sound through an professional external USB microphone. I want something very simple, no blitz or bling bling. Just record and save to external terabite size hard drive.

I want this to use on my laptop so I can be mobile. It can even be a script if necessary.

After 2  weeks of scouring the web, I have not found anything.

I'm running Ubuntu 12.04, gnome3.

Any help would be appreciated.
Thanks
Dave

---

### Post by HermanAB on 2012-10-22
vlc
mplayer
ffmpeg
kinelerra

no, it is not easy.

---

### Post by mag1strate on 2012-10-22
How about this? 

[http://www.nixiepixel.com/webcam-recording-in-linux/](http://www.nixiepixel.com/webcam-recording-in-linux/)

---

### Post by FakeOutdoorsman on 2012-10-22
Also see:

[list]
[*][How to capture a webcam input](https://ffmpeg.org/trac/ffmpeg/wiki/How%20to%20capture%20a%20webcam%20input)
[*][Capturing audio with FFmpeg and ALSA](https://ffmpeg.org/trac/ffmpeg/wiki/Capturing%20audio%20with%20FFmpeg%20and%20ALSA) 
[/list]

Note: These guides refer to ffmpeg from FFmpeg; not avconv from libav.

---

### Post by Silvernail on 2012-10-22
Using:
```
ffmpeg -f v4l2 -r 25 -s 640x480 -i /dev/video0 out.avi

```

How do I get it to recongnize the external microphone?

lsusb:
> 
Bus 005 Device 002: ID 0d8c:0139 C-Media Electronics, Inc.

usb-devices:
> 
T:  Bus=05 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0d8c ProdID=0139 Rev=01.00
S:  Manufacturer=C-Media Electronics Inc.      
S:  Product=USB PnP Sound Device
C:  #Ifs= 4 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=snd-usb-audio
I:  If#= 1 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
I:  If#= 2 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
I:  If#= 3 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid


Digging deeply, I find this link in /dev.
> 
lrwxrwxrwx 1 root root 12 Oct 22 19:46 usb-C-Media_Electronics_Inc._USB_PnP_Sound_Device-00 -> ../controlC2

Thus constructing my command line:
```
ffmpeg -f v4l2 -r 25 -s 640x480 -i /dev/video0 -i /dev/snd/controlC2 out.avi
```
I get this abort message.
> /dev/snd/controlC2: File descriptor in bad state

I'm at a loss as to where to go from here and back to one of my original problems.
"How do I get it to recongnize the external microphone?"

---

### Post by Silvernail on 2012-10-22
Basically disregard the response above. I posted before I saw all the links 'FakeOutdoorsman' gave me.

[https://ffmpeg.org/trac/ffmpeg/wiki/Capturing%20audio%20with%20FFmpeg%20and%20ALSACapturing](https://ffmpeg.org/trac/ffmpeg/wiki/Capturing%20audio%20with%20FFmpeg%20and%20ALSACapturing) audio with FFmpeg and ALSA

This will keep me busy for a while. Will mark solved and open a new thread if needed.

Thanks to everyone.
Dave

---

