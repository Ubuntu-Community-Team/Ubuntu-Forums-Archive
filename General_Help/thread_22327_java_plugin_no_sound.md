---
title: "java plugin no sound"
date: 2005-03-26
forum: General Help
---

### Post by wanama on 2005-03-26
Hi to all! I've a problem with java plugin (jre1.5.0_02). I've installed it  correctly on my system, i can see video and play games  but i can't get no sound on any type of  java sites with firefox. The only way i found is to kill esd. I don't think is a good solution, but the only one i've found. I've alredy done the simlink to libesd.so.1 .I can hear correctly flash sites mixed at the same time with others sound sources (such as beep media player or totem) .The problem is just about java and esd deamon. Any hint? The output of lspci about my audio device: ```
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
``` 

Finally i have to say that i've done ALL the last .deb upgrades and that i've the same installation on another machine with the same configuration and the same packages update level (but different audio hardware) and i've no problem at all there

 Thanks in advance!

---

### Post by pel on 2005-05-22
Right you are - java hogs /dev/dsp (wich is really cumbersome when applications do not release it when they've stoped playing sounds). It is really weird that it is hard to find information on how to solve, what I imagine is, a common problem such as this one.

The best info I've come across is to use the tritonus project ([http://www.tritonus.org/)](http://www.tritonus.org/)).
It, however, seems like the project is rather 'dead' when it comes to esound - and I have not managed to get it to work with java 1.5.

The alsa part seems to be a bit more alive - but I have yet to try that one out.

Anyway - this situation really sucks.  ](*,)

---

### Post by invalid on 2005-05-26
*bump*

I am having the same problems, no sound with java 1.5 + Firefox

---

### Post by G.Kirkham on 2007-08-06
I too have that issue of no sound from Java on every PC I build. The sun java test runs but no sound.
[http://java.sun.com/products/java-media/sound/samples/JavaSoundDemo/index.html](http://java.sun.com/products/java-media/sound/samples/JavaSoundDemo/index.html)
java -jar JavaSoundDemo.jar

Animated coffee beans, with a soundtrack and per-frame sound effects.
file:///usr/lib/jvm/java-1.5.0-sun-1.5.0.10/demo/applets/Animator/example1.html

/usr/lib/jvm/java-1.5.0-sun-1.5.0.10/demo/applets/Animator

/home/user1/.java/deployment/log/plugin150_10.trace is not showing any errors.


I have installed sun-java 1.5.

Flash plugin (non-free does have sound).

The only web site I can test sound on is Runescape logon screen.

I wonder what the following means ([http://java.sun.com/j2se/1.5.0/docs/guide/sound/programmer_guide/appendix2.html](http://java.sun.com/j2se/1.5.0/docs/guide/sound/programmer_guide/appendix2.html)) ?

To use MyDeviceProvider as the default for SourceDataLine lines, set the following key:

    javax.sound.sampled.SourceDataLine=com.xyz.MyDeviceProvider

To specify the default Synthesizer by its name InternalSynth, set the following key:

    javax.sound.midi.Synthesizer=#InternalSynth

To specify the default Receiver by provider and name, set the following key:

    javax.sound.midi.Receiver=com.sun.media.sound.MidiProvider#SunMIDI1


My file has 
#
# Example 1:
# Use MyDeviceProvider as default for SourceDataLines:
# javax.sound.sampled.SourceDataLine=com.xyz.MyDeviceProvider
#
# Example 2:
# Specify the default Synthesizer by its name "InternalSynth".
# javax.sound.midi.Synthesizer=#InternalSynth
#
# Example 3:
# Specify the default Receiver by provider and name:
# javax.sound.midi.Receiver=com.sun.media.sound.MidiProvider#SunMIDI1
#

should these be un-commented ?

This was an interesting site but still did not help me, [http://www.vsj.co.uk/java/display.asp?id=370](http://www.vsj.co.uk/java/display.asp?id=370)

I found this comment but what does it mean ?
[http://forum.java.sun.com/thread.jspa?messageID=9450488&tstart=0#9450488](http://forum.java.sun.com/thread.jspa?messageID=9450488&tstart=0#9450488)
JavaSound supports ALSA on Linux since Java 1.5.
You can select the "plughw" devices of ALSA.

[http://72.14.253.104/search?q=cache:KFYuyA4l5oIJ:www.jsresources.org/apps/3196_InternetPhone.pdf+java+linux+ALSA+%22plughw%22&hl=en&ct=clnk&cd=10&gl=au&lr=lang_en](http://72.14.253.104/search?q=cache:KFYuyA4l5oIJ:www.jsresources.org/apps/3196_InternetPhone.pdf+java+linux+ALSA+%22plughw%22&hl=en&ct=clnk&cd=10&gl=au&lr=lang_en)
jre/lib/sound/properties

# Use MyDeviceProvider as default for SourceDataLines:
javax.sound.sampled.SourceDataLine=#AudioPCI [plughw:1,0]

I even tried:
/dev/dsp
chmod 666 /dev/audio /dev/dsp /dev/mixer


Well, after trying the above, still no sound from a java applet.

If anyone out there knows what is stopping so many of us from getting sound out of sun java under linux, please let us know.

Thanks,

George.

---

