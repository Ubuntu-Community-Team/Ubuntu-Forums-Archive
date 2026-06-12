---
title: "Pinnacle USB capture device"
date: 2019-04-03
forum: General Help
---

### Post by BigD77 on 2019-04-03
Hello,

   I have a Pinnacle USB capture device for recording video from VCR's and satellite feeds.   I tried VLC to record, to no avail.  I went Media-Open Capture Device - TV Digital - DVB-T - /dev/dvb/adapter1 - and all I got was a line darting across the bottom as if it were searching for something.  Nothing to come up.  

What am I doing wrong?

---

### Post by Autodave on 2019-04-03
I don't think that I can help, but lets get some info for someone that may be able to help.

What version Pinnacle?  Model #?
What version of Buntu are you running?
Make and model of computer?
How is the Pinnacle connected to the PC: RCA, USB, ??

---

### Post by BigD77 on 2019-04-04
> **Autodave said:**
> I don't think that I can help, but lets get some info for someone that may be able to help.

What version Pinnacle?  Model #?
What version of Buntu are you running?
Make and model of computer?
How is the Pinnacle connected to the PC: RCA, USB, ??

Pinacle 801e 1101
Ubuntu 18.04.2 LTS
Dell Lattitude  E6420
Connected via USB

---

### Post by tea for one on 2019-04-04
> **BigD77 said:**
> Hello,

   I have a Pinnacle USB capture device for recording video from VCR's and satellite feeds.   I tried VLC to record, to no avail.  I went Media-Open Capture Device - TV Digital - DVB-T - /dev/dvb/adapter1 - and all I got was a line darting across the bottom as if it were searching for something.  Nothing to come up.  

What am I doing wrong?

Have you installed the firmware for this device?

Here is some info:- [https://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Pro_Stick_%28801e%29](https://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Pro_Stick_%28801e%29)

---

### Post by BigD77 on 2019-04-06
No, not that I know of.  The device works fine as a TV tuner for Me Tv, but I cannot get it to work using the USB input on the side for video and audio.

---

### Post by tea for one on 2019-04-07
Can you add a bit more detail because I'm not sure what you are trying to do?

The fact that your TV Tuner works as a TV Tuner is clearly a good sign.

What does this mean "using the USB input on the side"?

Can you describe which devices are attached to both ends of your Tuner?

Have you streamed live TV with this tuner via VLC?

I have used VLC for recording TV and radio via a DVB-T2 tuner and, generally, the first hurdle is to get VLC to play the stream and then solve the recording problem.

---

### Post by BigD77 on 2019-04-07
The Pinnacle device has a small usb connection on the side for attaching audio and video inputs for recording vcr or satellite inputs.  I tried to connect the satellite receiver to the usb inputs, then plug the Pinacle into the laptop.

I have never got the Pinacle device to work with VLC, only as a TV receiver with Me TV.  I am trying to stream and record off the satellite receiver with VLC.  I have never streamed live TV with VLC.

I have tried using DVB-T and all I get is a line darting back and forth on the bottom of the screen as if VLC was looking for something.

---

### Post by dennisn77-ameritech on 2019-04-07
[ATTACH=CONFIG]282988[/ATTACH][ATTACH=CONFIG]282989[/ATTACH]

---

### Post by tea for one on 2019-04-08
> **BigD77 said:**
> I have never streamed live TV with VLC.

I have tried using DVB-T and all I get is a line darting back and forth on the bottom of the screen as if VLC was looking for something.

I think that VLC is looking for a channel list.

In order to stream live TV via VLC, you must have a channel list. 

As me-tv works for you, there must be a channel list somewhere. Try a search with Nautilus for **channel**.

I used me-tv a few years ago and I think it uses a channel.conf file. (VLC will open a **.conf** file)

Alternatively, there are other ways of generating a channel scan such as [http://manpages.ubuntu.com/manpages/bionic/man1/w_scan.1.html](http://manpages.ubuntu.com/manpages/bionic/man1/w_scan.1.html) or using [https://tvheadend.org/](https://tvheadend.org/).

Anyway, attach your Pinnacle device as if you were going to use me-tv.

Navigate to your channels file > right click > open with VLC > select channel.

**or** Open VLC > Open Media > Open File (i.e. channel list) > select channel.

Once VLC is playing your channel, you can record by opening the menu and click on Record (with the red circle)

Ensure that you have set the recording path via Interface > Peferences > Input/Codecs

I do not have a satellite dish so I'm hoping the procedure is similar to the reception of terrestrial DVB TV.

Best wishes

---

### Post by BigD77 on 2019-04-08
What I want to do is to use the composite feed, not the over the air TV feed.

---

### Post by tea for one on 2019-04-08
> **BigD77 said:**
> What I want to do is to use the composite feed, not the over the air TV feed.

Ah, apologies, I misunderstood your requirement.

I'm not au fait with composite feed to VLC so I am unable to offer further suggestions.

Good luck with your search

---

### Post by BigD77 on 2019-04-09
The over the air TV feed I can do fine with Me TV.  What I want to do is record off the old VCR tapes and satellite feeds which you can't do with Me TV.  I have tried to use the Pinnacle 801e device, a Roxio HU3192-E USB video capture device, as well as a Tevion USB capture device with VLC, all to no avail.  I didn't want to spend more money on a Easy Cap if I didn't have to.

---

### Post by BigD77 on 2019-04-24
Update on issue:

   I once again tried the Tevion 8738 device.  WORKED with OBS.  I had to play with the adjustments, like the audio.  Only video comes out of the USB, as it has a separate stereo plug for audio that goes into the microphone input.  Then I had to go into Pulse audio control to set it to a "line in" instead of "Mocrophone in" so the audio is not overloading the front end of the audio input, causing distortion.  I then had to make video adjustments in recording (using .flv instead of mp4) so that I wouldn't cause too much CPU usage, resulting in dropped frames and choppy video.
:popcorn::D

---

