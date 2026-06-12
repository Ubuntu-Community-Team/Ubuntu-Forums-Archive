---
title: "Af9015 dvb-t"
date: 2012-11-07
forum: General Help
---

### Post by eslavko on 2012-11-07
Hello.

I try to connect my USB DVB receiver but can't make it run.

In lsusb that is line for my receiver

Bus 001 Device 009: ID 15a4:9016 Afatech Technologies, Inc. AF9015 DVB-T USB2.0

When I 1'st time attached card to usb the message popup as some external driver was neddded. So I just click Yes to do that, and after installing reboot was required. 

But still no tv can be seen in tvtime.

The OS is Ubuntu 12.04

Any help?  (I already search the net but no succesful solution was found)

thanks in advice.

---

### Post by Hugh Mulqueen on 2012-11-07
Have you tried using a dvb program?

Because according to this site it should have been automatically detected and running so all you need I'd say is a program.
[http://linuxtv.org/wiki/index.php/Afatech_AF9015]("http://linuxtv.org/wiki/index.php/Afatech_AF9015")

MeTV for gnome would be a good try. 
[B]
sudo apt-get install me-tv[/B]

That should work out for you.

---

### Post by eslavko on 2012-11-07
I try TVTime and just before reading this post also install MeTV.

Now in the MeTV when scanning channels actualy got all channels available here (and signal strength) but can't see any video.

When I search channels the LED on receiver blinked when channels are found but when I wan't to watch there are no video (read timeout) in statusbar and LED on receiver doesn't lit (as it does in windows)

so seems that something is still wrong

Bad driver? (how/where to obtain last one?)

---

### Post by eslavko on 2012-11-07
Hmm maybe that is the problem

 dmesg | grep dvb
[   19.986801] dvb-usb: found a 'Afatech AF9015 DVB-T USB2.0 stick' in warm state.
[   19.986840] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   20.104533] dvb-usb: schedule remote query interval to 500 msecs.
[   20.104535] dvb-usb: Afatech AF9015 DVB-T USB2.0 stick successfully initialized and connected.
[   20.110792] usbcore: registered new interface driver dvb_usb_af9015


We have MPEG4 transmission here! But MPEG2 is listed above. What solution?

---

### Post by Hugh Mulqueen on 2012-11-07
A bit like myself so. Ya we have MPEG4 aswell. I don't know if your yoke supports MPEG4 you'll have to figure out that yourself. If you have the box. or else look up the web and see...

I don't know. From the look of things it might not support MPEG4 only support MPEG2. You might be able to get sattilite streams (i.e. DVB-S) on it but not DVB-T...

---

### Post by eslavko on 2012-11-07
Under windows works perfect.
And there we have only MPEG4 streams... So can't test if MPEG2 works.

---

### Post by eslavko on 2012-11-08
Hello..
I realize that this thread should be on multimedia-video forum. so I make question there.

---

