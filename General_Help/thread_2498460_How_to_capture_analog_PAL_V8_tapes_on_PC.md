---
title: "How to capture analog PAL V8 tapes on PC"
date: 2024-06-14
forum: General Help
---

### Post by satimis on 2024-06-14
Hi all,

I have old analog Sony PAL V8 tapes and expect to rip them on PC as mp4 files.

My Sony handy camera has been broken.  I'm now searching a Hi8 digital camcorder, which can play back analog Sony PAL V8 tapes, to do the job.

Please advise, addition to Hi8 digital camcorder, what other devices I need?  Digitizer?

What software I need to run for this job.

Please advise.  Thanks in advance.

Regards

---

### Post by TheFu on 2024-06-14
Any $20 USB2 recorder can be used that will connect to a device that can playback the Hi8 tapes.  The recorder will likely record to mpeg2 format, so you can transcode that to whatever the mp4 container will hold.  That is typically h.264/aac/mp4.  Use handbrake to do that, though you can use ffmpeg, using handbrake will usually be easier and make better results.

I have a Haupauge 950Q which can handle either the yellow cable or s-video inputs along with stereo audio. It is plug-in-use under linux. I haven't tried it in a very long time, since nearly everything I've recorded since 2015 uses HDMI video and audio.  That's a different device.

I doubt there's any need to pay the premium for a Haupauge device.  Just look through the V4L2 hardware lists for supported chips and find any device that uses one of those chips. [https://www.linuxtv.org/wiki/index.php/V4L_capturing](https://www.linuxtv.org/wiki/index.php/V4L_capturing) explains.  Note that this domain is from the early 2000s when this format was more common.

BTW, it seems you ask the same question about every 12 months hoping for a different answer. What's up with that?

---

### Post by ne29914 on 2024-06-14
Wrong!
The ubiquitous "video encoders" are nothing but A/D converters delivering a raw data stream to the PC. Immense post-processing is needed to convert that data stream into something useful, like MPEG-2. Practically all the driver/post-processing/formatting software is only available for Windows, and if you're lucky for Mac.
I've yet to see a product that has good Linux support (I may be wrong here, but...).

The right (and universal) way of doing PAL/NTSC capture is to use a device that provides a direct MPEG-2 stream at its USB output. This can be recorded/processed directly by VLC or whatever video software you use.

Several professional units are available, but expensive.

The only consumer devices I've ever seen doing direct PAL/NTSC -> MPEG-2 conversion are the Grabster AV400 and AV450 from Terratec. Plug in, open VLC and select the stream: Bam! Video is on your screen.

No longer available, but they come up often on Ebay. Grab one if you see one.

---

### Post by TheFu on 2024-06-14
Well, every video recorder I've owned, which is about 5 has 
a) supported Linux
b) provided at least mpeg2 as an output format.  

Seems like you've just been unlucky in hardware choices.  I had a Plextor ConvertX [https://www.amazon.com/Plextor-ConvertX-Digital-Converter-PX-M402U/dp/B0001CJF3A](https://www.amazon.com/Plextor-ConvertX-Digital-Converter-PX-M402U/dp/B0001CJF3A) that would output either mpeg2 or DivX (the original mp4 video format).  It supported Linux with both codecs and V4L.

A link to an overly expensive Haupauge 950: [https://www.amazon.com/Hauppauge-1120CN-WinTV-HVR-950-Hybrid-Recorder/dp/B000J1CCGA/](https://www.amazon.com/Hauppauge-1120CN-WinTV-HVR-950-Hybrid-Recorder/dp/B000J1CCGA/) There are cheaper, approx $20 versions of this now, just without the Haupauge name.

I've never had luck using vlc to capture anything.  OTOH, I have used ffmpeg and a few other V4L and V4L2 compatible free software on Linux to capture the output from those devices.  It wasn't anything difficult.

The only time I was stuck using MS-Windows to capture video was with Haupauge 1212 and 1515.

Here's an example $13 version that says Linux works with it: [https://www.amazon.com/Converter-Digital-Capture-Support-Windows/dp/B087TDN2FL](https://www.amazon.com/Converter-Digital-Capture-Support-Windows/dp/B087TDN2FL)  I'd try that to start.

---

### Post by satimis on 2024-06-15
Hi all,

Lot of thanks for your advice and your time spent to help me.

Is it the right hardware which I need ?
[COLOR="#FF0000"]**[B]USB Capture Card Digital Video Recorder Av Display**[/B][/COLOR]
[https://www.ebay.com.hk/itm/387056582503?mkevt=1&mkpid=0&emsid=e11403.m43.l1123&mkcid=7&ch=osgood&euid=b61106699a5f47f18cdd5b5d313dda62&bu=45055992826&exe=0&ext=0&osub=-1%7E1&crd=20240614101054&segname=11403](https://www.ebay.com.hk/itm/387056582503?mkevt=1&mkpid=0&emsid=e11403.m43.l1123&mkcid=7&ch=osgood&euid=b61106699a5f47f18cdd5b5d313dda62&bu=45055992826&exe=0&ext=0&osub=-1%7E1&crd=20240614101054&segname=11403)

Please advise.  Thanks

So VLC will be the software for this processing ?

Regards

---

### Post by TheFu on 2024-06-15
Does the listing say it works under Linux?

---

### Post by satimis on 2024-06-15
> **TheFu said:**
> Does the listing say it works under Linux?
Hi TheFu,

Could you please explain in more details

Thanks

Regards

---

### Post by TheFu on 2024-06-15
No.  It is a simple question.  Does the listing on ebay say it works under Linux or not?  It is an easy question.  If it doesn't specifically say that it will work under Linux, I wouldn't buy it.  I provided a link to a device that DOES say it works under linux.  The chips inside the plastic matter.  You should also check that it supports the inputs you need - S-Video.  

Of course, you will need some sort of playback device too connect this recorder to. Nothing will replace that.  That requirement should be obvious.

---

### Post by satimis on 2024-06-15
> **TheFu said:**
> No.  It is a simple question.  Does the listing on ebay say it works under Linux or not?  It is an easy question.  If it doesn't specifically say that it will work under Linux, I wouldn't buy it.  I provided a link to a device that DOES say it works under linux.  The chips inside the plastic matter.  You should also check that it supports the inputs you need - S-Video.  

Of course, you will need some sort of playback device too connect this recorder to. Nothing will replace that.  That requirement should be obvious.
Nothing has been mentioned either for Linux or for Windows

Whether you meant following device;
Video Capture Card USB 2.0 Audio Device Old VHS Mini DV Hi8 DVD VCR to Digital Converter for Mac, PC Support Windows 2000/10 / 8/7 / Vista/XP/Android
[https://www.amazon.com/Converter-Digital-Capture-Support-Windows/dp/B087TDN2FL](https://www.amazon.com/Converter-Digital-Capture-Support-Windows/dp/B087TDN2FL)

Regards

---

### Post by TheFu on 2024-06-15
> &#12304;Plug and Play&#12305;Our USB 2.0 Video Capture Adapter provides a link between a PC and a video device with RCA connector or S-Video connector, such VHS, VCR, DVD,Hi8, Camcorder. Automatically install the driver once you hook up this RCA to USB Converter to a PC. No external power is needed.Support Win 2000/Win Xp/ Win Vista /Win 7/Win 8/ Win 10/_**[COLOR="#008000"]Linux[/COLOR]**_ Mac/Android. 

&#12304;Support All Video Formats&#12305; The Video Capture Card Support Brightness, Contrast, Hue, and Saturation Control. Capture audio without the sound card. Support DVD+/ -R/RW, DVD+/-VR, and DVD-Video. Applying to internet conference / net meeting. Support NTSC, PAL Video format. NTSC: 720 x 480 @ 30fps,PAL: 720x576 @ 25fps. Win 2000/Win Xp/ Win Vista /Win 7/Win 8/ Win 10 _**[COLOR="#008000"]Linux[/COLOR]**_ Mac/Android 

is in the item description for the Amz link. Not hidden.

---

### Post by ne29914 on 2024-06-15
> **TheFu said:**
> Well, every video recorder I've owned, which is about 5 has 
a) supported Linux
b) provided at least mpeg2 as an output format.  

Seems like you've just been unlucky in hardware choices.  I had a Plextor ConvertX [https://www.amazon.com/Plextor-ConvertX-Digital-Converter-PX-M402U/dp/B0001CJF3A](https://www.amazon.com/Plextor-ConvertX-Digital-Converter-PX-M402U/dp/B0001CJF3A) that would output either mpeg2 or DivX (the original mp4 video format).  It supported Linux with both codecs and V4L.
.

First, I don't want get into a p*ssing contest here, but believe me, I've been through the whole thing and seen so much cr*p for this functionality.

What you did not understand in my post was, that the Grabster AV400/450 requires NO software installation at all!
It's compatible with everything. I mentioned VLC, but any program that can open an MPEG-2 stream over USB will work with it with no exception. The question of Linux compatibility doesn't even come up.

All other consumer products I've seen are A/D converters (some more advanced than others), but they still only deliver raw A/D samples over USB that will then have to be converted to MPEG-2, DivX or whatever in the PC.

@satimis: doon't buy that cheap stuff. Spend 20 dollars more and be happy.
**Here's an offer you shouldn't refuse (if it's still there):**
[https://www.ebay.com/itm/176395273468](https://www.ebay.com/itm/176395273468)

EDIT: researching a bit more, it seems the mentioned Plextor also delivers MPEG-2/DivX directly, but needs control software on the PC. It's not 100% clear, though.

---

### Post by satimis on 2024-06-15
> **ne29914 said:**
>  - snip -

@satimis: doon't buy that cheap stuff. Spend 20 dollars more and be happy.
**Here's an offer you shouldn't refuse (if it's still there):**
[https://www.ebay.com/itm/176395273468](https://www.ebay.com/itm/176395273468)
....

Hi@ne29914,

Thanks for your advice.  The item suggested by you won't be shipped to my location.

It is very strange to me all digitizes, sold on eBay, without indication for Windows use or for Linux use.

Just found following YouTube video:-
How To Convert Your 8mm Tape To Digital Using A PC (OBS)
[https://www.youtube.com/watch?v=TLmfZo93TkE](https://www.youtube.com/watch?v=TLmfZo93TkE)

I-O Data (GV-USB2) digitizer is used
IO DATA USB DVD connection video capture Cable GV-USB2 JAPAN Import F/S
[https://www.ebay.com.hk/itm/266597171937](https://www.ebay.com.hk/itm/266597171937)

also not mentioning for Windows use or for Linux use ???

Regards

---

### Post by satimis on 2024-06-16
Hi all,

About connecting "I-O DATA DEVICE INC. I-o USB connection video capture GV-USB2"  (Digitizer) to PAL Hi8 Camcorder ?

I-O DATA DEVICE INC. I-o USB connection video capture GV-USB2  (Digitizer) 
[https://www.ebay.com.hk/itm/266597171937](https://www.ebay.com.hk/itm/266597171937)

I'm going to purchase
Sony ccd trv47e Camcorder
User manual
[https://www.sony.com/electronics/support/res/manuals/3868/38683251M.pdf](https://www.sony.com/electronics/support/res/manuals/3868/38683251M.pdf)
page 38
There are only 2 ports on the Camcorder for connecting TV set, Video Out and Audio Out.  But there are 4 pins on the digitizer, black, green, white and red,

Please  advise.  Thanks

Regards

---

### Post by ne29914 on 2024-06-16
Everything has been explained. I don't want to repeat myself. And as your location is secret, I can't comment on shipping.

Cheers.

---

