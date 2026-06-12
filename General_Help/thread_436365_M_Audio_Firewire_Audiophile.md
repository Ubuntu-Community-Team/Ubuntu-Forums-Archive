---
title: "M Audio Firewire Audiophile"
date: 2007-05-07
forum: General Help
---

### Post by bbreakz on 2007-05-07
Hi... super new to Ubuntu... like 2 days...

I have a Firewire Audiophile soundcard... Has anyone been able to get it to work yet.. Would love to be able to use it.... Would be a shame if i couldn't...

---

### Post by damo21 on 2007-07-17
I would love to know if anyone has got this to work successfully with freebob... I would buy one.
I noticed on the FFADO site that some dude got it to capture, but not playback yet....
Should have support soon i think...

From [www.ffado.org](www.ffado.org) :

>  Submitted by ppalmers on Fri, 04/13/2007 - 19:14.
Manufacturer:
M-Audio
Device Info on Vendor Site:
[http://www.m-audio.com/products/en_us/FirewireAudiophile-main.html](http://www.m-audio.com/products/en_us/FirewireAudiophile-main.html)
Support Status:
Experimental

Needs firmware upload after being switched on.
»

    * Add new comment

capture works, playback doesn't
Submitted by ppalmers on Thu, 04/26/2007 - 17:33.

(Note: From the FreeBoB-devel mailing list, referring to the experimental FreeBoB-1.4 release.)

I have tested again the freebob (or FFADO), on my MAudio Audiophile.
And this time I have tried to capture audio and it works. (I was able
to record with my microphone, and a preamp.)
I started it just after an firmware upload with the command
"jackd -d freebob -C" only for capture it works without any bad or
error output. But I still don't hear anything, and jack option
Duplex, or Playback, doesn't change anything. In fact, just after
an firmware upload jackd doesn't output bad errors or too much warnings
it just warn :

libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.

I tried the test-volume and test-mixer but I don't know very well
how it work, but I think that if I can modify volumes or some
audiophile parameter like on OSX, I will hear sounds. Has I said
on the previous mail I always modify the mixer of Audiophile (by increasing,
or decreasing software output or by linking it on Line ouput 1
or 2) to have sound. I don't yet try on Windows but I think that
this is caused by the firmware or by the Audiophile.

---------------------------------------------------------------------------------
Some additionnal information :

My version of freebob is from the svn site, where I change the directory
"libfreebob-1.4/src/maudio" by adding the file fwap.xml,
and in the file maudio_avdevice.cpp by adding in
supportedDeviceList at the line 78, the line
{0x000d6c, 0x00010060, "fwap.xml"},        // M-Audio, FW Audiophile
(to be verified);
and changing the function AvDevice::setSamplingFrequency for return true.

Consider this device experimental.
»

    * reply

M-Audio FireWire Audiophile? What's that firmware? Best distro?
Submitted by dutch77 on Fri, 06/01/2007 - 09:36.

Hi, I'm a total Linux noob after being fed up with the huge toll XP lays on my cpu. Can't play mediaplayer and surf the net together, the processor loads go through the roof. Even Mackie Tracktion doesn't run smoothly on my P4 2.4 GHz laptop. I would also love to use my FireWire Audiophile for some home recording with Ardour. But my laptop doesn't even have a line-in...

Anyway, for now Ubuntu looks very promising, but I'm probably way over my head with this:
What firmware upgrade are you talking about? Can't find any on M-Audio's site.

My Firewire Audiophile works in XP although it emits a high frequency whine through my speakers, but I have no idea how to get freebob into Ubuntu. Actually, according to Synaptic, all freebob thingies, jack and QtJackctl are all installed. QTjACKctl starts and works, but no Audiophile to be seen and the lights keep blinking. it does see the built-in audio.

The install istructions are probably very clear for Linux programmers, but me total noob it confuses completely. What means: run as root? If I just type the commands in a terminal I get no reply. Do I need to remove the # in front of the line? Then it says it doesn't know what I'm on about. What do I have to do if Synaptic has already installed the packages?

Would I do better to get an audiospecialist distro like UbuntuStudioa( :(, ugly grey), 64 studio? Dynebolic? Elive (:P)? Would that help any?
»

    * reply

The Audiophile is not a
Submitted by ppalmers on Sun, 06/24/2007 - 14:49.

The Audiophile is not a device that works out of the box. That's something for the next release I'm afraid.
»

    * reply



---

### Post by LinuxSoundMan on 2007-11-17
anyone have any updates on this. does the "firmware" mean the driver download from the maudio site? I have this device and it would complete my system if i were able to use it in my ubuntu studio set up. if anyone has any info on this please post it here. the audiophile is by far on of the best firewire soundcards for the price. if i could only get it to work with ubuntu. thanks a lot.

---

