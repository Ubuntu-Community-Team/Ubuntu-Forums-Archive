---
title: "Java: Sound in Blackdown, No Sound in Sun.  Blackdown Freezes."
date: 2007-07-10
forum: General Help
---

### Post by mig5 on 2007-07-10
[SIZE="4"][CENTER]THIS PROBLEM IS STILL NOT PROPERLY SOLVED.  ANY HELP IS APPRECIATED[/CENTER][/SIZE]
[COLOR="Gray"][B][COLOR="Black"](Scroll Down For Updated Description)[/COLOR]
Original And Now Obsolete Description Of The Problem:
[/B]With Blackdown java (j2re1.4) I get sound when I play runescape (runescape.com), but java freezes after a while of playing (30 mins - 1.5 hours).  I understand that blackdown is based on an older version of java and that it is no longer developed.  I even tried a debian package which was 1.4.2.03 (the Blackdown in the repos is 1.4.2.02), but it freezes all the same.
With Sun java (jre1.6) the game doesn't crash, but I don't get any ingame sounds.  I've tried the javas in both Opera and Firefox with the same results.  In both Opera and Firefox the sound is fine with other plugins, such as flash and vlc plugin.

I'm looking for a way to either get Blackdown to stop crashing or to get Sun java to make some noise.  I'm wondering whether there is some configuration file that I can just copy from one installation to the other.
As a side note I'd like to add that I first installed Sun java manually, following the instructions on the Sun website.  Subsequently, I tried installing it from the repos, but still didn't get any sound so I uninstalled the one from the repos, leaving the manually installed one intact.  I also tried Sun jre1.5 (from the repos), but there was no sound with that either.  The first Blackdown java I got was from the repos (j2re1.4.2.02), and the second was from [http://www.blackdown.org/](http://www.blackdown.org/) .  Both of the Blackdown java's had sound, both froze.

I'm running 32 bit Xubuntu feisty.[/COLOR]


**Updated Description of the Problem (After Attempted Fixes And Lots Of User Input):**
I don't get sound in the newer Sun java JREs (1.5 and 1.6).  I have discovered that the cause of the problem is not the web browsers, but the fact that Sun and other versions of java are not properly automatically detecting my sound devices.  After some very useful help from techburt , I managed to get sampled sound working in Sun JRE 1.5 and 1.6 .  However, it appears that techburt has stopped visiting these forums and I am still in need of help to sort out the java MIDI sound.  I know that I need to add some information to the /etc/Java/sound.properties file (like I did to make the sampled sound work), but I can't find any information that I can understand about how to do so.  So what I'm looking for is someone to explain to me how to get this information and add it to /etc/Java/sound.properties .  Help I was given concerning the /etc/Java/sound.properties file starts on page 3, post #29, so you can skip along to there if you want to help me configure it to make MIDI sound work.
[B]
[COLOR="Red"][CENTER]For a summary of everything that I have tried look at post 2.[/CENTER][/COLOR]
I currently have a sort of temporary fix, I'm using a Windows K-Meleon browser in wine and the java works with sound and it doesn't crash.  More details on post 6.  I am still trying to get a linux jre working properly though, as running java and K-Meleon in wine uses 85% of my processor (AMD 2500, core 1.8ghz).  So far I have managed to get the runescape music to play in Sun Java, but not the midi sound effects.  I really need help with setting up the /etc/Java/sound.properties file for my sound card.[/B]

---

### Post by mig5 on 2007-07-10
[SIZE="4"][CENTER]**Summary of Attempted Fixes**[/CENTER][/SIZE]
Here is a summary of what I have tried so far (what was originally posted here has been merged with the post underneath):


[INDENT]-**Configuring the /etc/java/sound.properties file (Sun JREs 1.5 and 1.6).**  I have managed to configure this file successfully for sampled sound playback.  However, I need someone with more knowledge about configuring this file to explain to me how to get the MIDI sounds working.

-**Various browsers and JREs under wine**, my current (and best) temporal fix is running K-meleon (lightweight Gecko based browser) with Sun JRE 1.4.2_14 for Windows.  This obviously presents some security risk and a lot more processing power/memory is needed than a native browser with a native JRE.
[INDENT]**Browsers:**
[LIST][*]Firefox 2.0.0.4
[*]Internet Explorer (IEs4Linux)
[*]Safari Public Beta 3 - *Failed to install*
[*]K-meleon
[/LIST]

**JREs:**
[LIST][*]Microsoft Java - *Failed to install*
[*]Sun Java JRE 1.5 - *Failed to install*
[*]Sun Java JRE 1.4.2_14 - *Installs, only works if running in NT 4 emulation mode*[/LIST][/INDENT]



-**Lots of linux native JREs**, all of which have been tested in Firefox or Opera.  I have sorted them into 3 sections:

[INDENT]**JREs that play sounds but crash after ~1.5 hours of play:**
[LIST][*]Blackdown Java (JRE 1.4.x)
[*]Sun Java JRE 1.4.1_x
[*]Sun Java JRE 1.4.2_x[/LIST]

**JREs that don't crash, but don't play sounds:**
[LIST][*]Sun Java JRE 1.5
[*]Sun Java JRE 1.6
[*]IBM Java JRE 1.5[/LIST]

**JREs that won't run Runescape at all:**
[LIST][*]GCJ Java
[*]IBM Java JRE 1.4[/LIST][/INDENT]



-**Adding maximum heap option (-Xmx256x)** in the Sun JRE 1.4.2 control panel.  This made no difference, as the applet still froze after an hour.



-**Installing timidity midi emulation software.**  This installed correctly, but did not make any difference to later Sun Javas' abilities to play midi sounds, as was hoped.[/INDENT]


Note: due to the fact that this was posted after the posts that follow, some things may not make chronological sense.

---

### Post by mig5 on 2007-07-10
I've just tried IBM java (jre1.5) for which I found a howto for here: [http://ubuntuforums.org/showthread.php?t=6320](http://ubuntuforums.org/showthread.php?t=6320) . However it has no sound, like Sun java.
Edit: I've just tried IBM java jre 1.4.2 aswell.  No sound with that either.

---

### Post by mig5 on 2007-07-10
I also tried the gcj java in the repos, but that just says error loading applet when I try to start runescape.  However it loaded runescape classic, so I'm guessing that normal runescape is too complex for it.  Still don't know whether the sound worked with that java anyway, so I've ditched that one too.

After that I got Sun java jre1.4.2-14 for linux from the Sun website, thinking that if Blackdown is based on that then maybe the sound would work.  Sure enough it did, but it also crashed just like Blackdown =( .

---

### Post by mig5 on 2007-07-11
I'd also like to add that Sun java gives me sound on my Windows XP OS on the same computer.

---

### Post by mig5 on 2007-07-12
> **mig5 said:**
> I'd also like to add that Sun java gives me sound on my Windows XP OS on the same computer.

This got me thinking, if Sun java works OK on Windows and with sound, then maybe it would work under wine.  After a while of searching I found out how to install Windows Firefox in wine and how to get java working with it.  The java that was recommended was jre1.4.2 (any surprises).  Sure enough it installed OK and I now have a working java with sound.  It hasn't frozen yet...

I only want this as a temporary fix until someone can tell me how to get sound with the newer Sun javas.  I don't really want to have to use wine all the time.

---

### Post by mig5 on 2007-07-12
[COLOR="Gray"]Bump.[/COLOR]

---

### Post by mig5 on 2007-07-13
[COLOR="Gray"]Bump.[/COLOR]

---

### Post by mig5 on 2007-07-14
[COLOR="Gray"]Bump.[/COLOR]

---

### Post by Tur Third on 2007-07-14
mig 5, I still haven't worked out why sound sometimes works. However connected with this is that sometimes it runs very slowly when logging in, and has also hung. I think how busy the runescape servers are maybe a factor. I'll let you know if I make any progress..

---

### Post by mig5 on 2007-07-14
I think we have slightly different problems, seeing as I always get sound in jre1.4.x-x and never get sound in jre 1.5 or 1.6, whereas you sometimes get sound and sometimes don't.   Anyway, please keep me informed on any progress that you make, there are so few people who can help with this sort of problem that it's good if we can help each other to help ourselves.


> **Tur Third said:**
> sometimes it runs very slowly when logging in, and has also hung. I think how busy the runescape servers are maybe a factor.
I nearly always use full servers, which I can't avoid due to the stuff that I'm currently doing ingame.  Maybe this is a factor that causes jre 1.4 and Blackdown (which is based on 1.4) to hang, although I'm not getting the hangs on login, it's after about 30 minutes of playing.  The thing is I'm using the exact same version of Sun java in wine, but the Windows version, and it's as solid as a rock.  And seeing as Blackdown java is supposed to be a port of the windows version of Sun java that was made before Sun supported linux, it doesn't make sense that the ported should crash and the unported shouldn't.  (However, looking at the dates, it may well be that by the time they were making 1.4, Sun had started supporting linux, so therefore Blackdown could be a cross of half native and half ported code.  This is a gray area, seeing as Blackdown is no longer developed and they have little info on their website).  I'm not even sure when sound was actually implemented into java applets, maybe I could go back even more versions and find one that was completely ported from Windows code.  However runescape probably won't work on the oldest of the old, or if it does I doubt it will do so reasonably.  And to be honest I don't really like using jre 1.4 because there is probably a security risk, older is even worse.

---

### Post by mig5 on 2007-07-15
[COLOR="Gray"]bump[/COLOR]

---

### Post by Tur Third on 2007-07-15
Not really tested playing it, but it has been ok the last few times ie, music at the login screen. I think you are right they are different problems but I think your best bet maybe to try to get sound working in 1.6, as it will then hopefully work in future versions.

I am a bit out of my depth now, but this is the output from lsmod for anything sound related. Don't know whether it will help or not. 

The last thing I did that seems to have fixed it (I say that with caution) is that I unplugged a webcam that was getting confused with my sound card and installed 'alsamixergui' looked at the settings and closed it again.

```
lsmod |grep snd
snd_rtctimer            5016  1
snd_seq_dummy           5508  0
snd_seq_oss            38372  0
snd_seq_midi           11456  0
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
snd_seq                64088  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_m idi_event
snd_via82xx            32936  1
gameport               19216  1 snd_via82xx
snd_ac97_codec        110396  1 snd_via82xx
snd_ac97_bus            4096  1 snd_ac97_codec
snd_pcm_oss            59424  0
snd_mixer_oss          20608  1 snd_pcm_oss
snd_pcm               104584  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              29064  3 snd_rtctimer,snd_seq,snd_pcm
snd_page_alloc         13968  2 snd_via82xx,snd_pcm
snd_mpu401_uart        10368  1 snd_via82xx
snd_rawmidi            31648  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device         11280  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,s nd_rawmidi
snd                    68576  14 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec, snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_ device
soundcore              13216  1 snd

```

The version of java run time is Java Plug-in 1.6.0_01
Using JRE version 1.6.0_01 Java HotSpot(TM) Client VM

---

### Post by mig5 on 2007-07-15
I ran that command and this is what I get:

[PHP]
michael@mikeubunt:~$ lsmod |grep snd
snd_rtctimer            4384  1 
snd_ens1371            27552  2 
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            29208  0 
snd_via82xx_modem      16008  0 
snd_ac97_codec         98464  3 snd_ens1371,snd_via82xx,snd_via82xx_modem
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
ac97_bus                3200  1 snd_ac97_codec
snd_mpu401_uart         9472  1 snd_via82xx
snd_rawmidi            25472  3 snd_ens1371,snd_seq_midi,snd_mpu401_uart
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
gameport               16520  3 snd_ens1371,analog,snd_via82xx
snd_pcm                79876  5 snd_ens1371,snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
snd_timer              23684  3 snd_rtctimer,snd_seq,snd_pcm
snd                    54020  18 snd_ens1371,snd_seq_oss,snd_seq,snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_pcm,snd_timer
soundcore               8672  1 snd
snd_page_alloc         10888  3 snd_via82xx,snd_via82xx_modem,snd_pcm[/PHP]

I have 2 sound cards in my computer, but the via one is blacklisted.  I wonder if java is somehow still trying to use it.  I've never had that sort of problem before, everything else uses the esoniq card.
I'll look more carefully, and compare the outputs later.  I might try that gui thing that you suggested.

---

### Post by mig5 on 2007-07-18
After comparing them it seems that all the numbers are different anyway, probably because we are using different sound cards.

---

### Post by mig5 on 2007-07-20
[COLOR="Gray"]bump[/COLOR]

---

### Post by mig5 on 2007-07-21
[COLOR="Gray"]bump[/COLOR]

---

### Post by mig5 on 2007-07-24
[COLOR="Gray"]bump[/COLOR]

---

### Post by mig5 on 2007-07-29
[COLOR="Gray"]Bump. By the way I did what you suggested with 'alsamixergui', but still no joy.[/COLOR]

---

### Post by MakotoTheKnight on 2007-07-31
RuneScape has had a history of not doing things right with Sun Java, ever since its days when it was on MSJVM.  I believe that the problem lies with handling MIDI files improperly, but the only hotfix I can think of off the top of my head would be what you've already done - Firefox in Wine.

If I find more information or if I get it to work I will let you know immediately.

---

### Post by mig5 on 2007-08-02
Thanks for the response.  I know that the runescape people seem the favour Microsoft Java over others.  But the thing is, in wine I'm using Sun Java and the sound is working.  But it is version 1.4, the version that also gave me sound in the linux version (but in the linux version it crashed, wheras the Windows version doesn't seem to).  I'm still thinking that maybe it's to do with the the gecko based browsers that the java 1.4 crashed, but 1.5 and 1.6 don't crash.  I guess I could try konqueror which isn't based on gecko, but I don't want half of KDE =P.

---

### Post by Tur Third on 2007-08-03
Just noticed this thread 

[http://ubuntuforums.org/showthread.php?t=108479&highlight=runescape]("http://ubuntuforums.org/showthread.php?t=108479&highlight=runescape")

This talks about a setting in control panel to prevent a memory leak, that stops Firefox from crashing. It looks old, but maybe something worth trying.

---

### Post by mig5 on 2007-08-03
Thanks for the link.  I think I've read that thread before, but I never tried adding that maximum heap option.  I'll try it when I get home.  I'm not sure whether they are having the same problem as me, seeing as when I use jre 1.4 it's only the applet that freezes, I can still use firefox after it has frozen for normal browsing.
I really chose the wrong derivative for this, seeing as with XFCE I can't really try ephiphany or konqueror without getting half of gnome or KDE.

---

### Post by mig5 on 2007-08-05
I added the maximum heap option on jre 1.4 and it still froze as usual, after about 1 hour and 30 minutes of playing.

---

### Post by mig5 on 2007-08-08
Bump.  I have now modified the first page of this thread to make it easier to see all of the fixes that have been tried in one post, instead of having to trawl through the whole thing.

---

### Post by jamesstansell on 2007-08-08
I just checked and my sound works fine in runescape with sun-java6-plugin on my feisty laptop from zareason.  They installed feisty before shipping, so I've only added packages (including the java plugin) so far.  I'm hoping to re-install sometime in the next few weeks so I'll let you know how it works after that.

As far as I know the exact same setup versions also work on my Dell machine at home.

Are you relatively sure that no other firefox plugins are interfering with Java?

Regards,

-james.

---

### Post by jamesstansell on 2007-08-08
Yes, sound in Runescape using firefox with Sun Java is working on my feisty box at home.

Tell us more about your setup and how you installed or upgraded to it.

Also, what if you create a brand-new user on your system and use it to try things out.  Any differences?

Regards,

-james.

---

### Post by mig5 on 2007-08-09
I don't think that other plugins are conflicting with the java, seeing as I tried the javas in both Firefox and Opera.  My Opera install only has flash and real player plugins, and I still didn't get java sound on it.  And only the flash player plugin would be loaded for the adverts on runescape.com , the real player one shouldn't start unless I watch a video or something.

**My Setup**
2500 AMD processor (1.8ghz core), 512mb memory, onboard sound plus PCI sound card (the onboard sound is disabled in the BIOS and has been blacklisted, but maybe java is still trying to use it), a TV tuner card, a Satellite tuner card (no drivers are installed for this) and an external USB TV tuner (the one inside the box is broken, I should really take it out).
I installed Xubuntu 7.04 from the live CD.  The only hardware change that I have made since the install is changing the monitor, and I changed that after I knew that Sun Java didn't give me any sound.

I'll try the new user idea when I get home from work tonight. I'll post the results here once I've done it.

---

### Post by techbert on 2007-08-16
I was having a problem with Puzzle Pirates and stumbled onto your post looking for the answer.  I eventually got it working on Sun's 1.5 Java and wanted to share.  My computer has an Audigy 2 in it and a dialup modem that looks like a sound card.  I found a piece of software here:

[http://www.developer.com/java/other/article.php/1579071](http://www.developer.com/java/other/article.php/1579071)

I didn't care about it much except that it listed the available sound mixers on my computer.  I had to install Sun's JDK from Synaptic to use that because the site doesn't just give a jar file.  I copied the source there into a AudioCapture02.java file, typed javac AudioCapture02.java and then finally typed java AudioCapture02.  After pressing the Capture button on the applet, my terminal spewed this:

V8237 [plughw:0,0]
V8237 [plughw:0,1]
CX8801 [plughw:1,0]
Audigy2 [plughw:2,0]
Audigy2 [plughw:2,1]
Audigy2 [plughw:2,2]
Audigy2 [plughw:2,3]
Audigy2 [plughw:2,4]
Java Sound Audio Engine
Port V8237 [hw:0]
Port CX8801 [hw:1]
Port Audigy2 [hw:2]

I'm assuming that Java was using the first device listed (not my real sound card).  I edited my /etc/java-1.5.0-sun/sound.properties file to add these lines:

javax.sound.sampled.Clip=#Audigy2 [plughw:2,0]
javax.sound.sampled.Port=#Port Audigy2 [hw:2]
javax.sound.sampled.SourceDataLine=#Audigy2 [plughw:2,0]
javax.sound.sampled.TargetDataLine=#Audigy2 [plughw:2,0]

And it started working!  Pumping sound to a fake card doesn't help much when my speakers are plugged into the real one :)

Hope that helps!

---

### Post by mig5 on 2007-08-20
I'm trying what you suggested, but I've fallen at the first hurdle.  I'm no sure how to get the program from the website that you linked me to.  Do i need to copy the contents of 'listing 12' into a plan text file and then rename it AudioCapture02.java?

EDIT: you don't need to answer this question, carry on to the next post.

---

### Post by mig5 on 2007-08-20
OK, i did have to copy and paste the contents of 'listing 12' to a plain text document.  I followed your steps and AudioCapture02 gave this in the terminal when I tried to record:
```

Available mixers:
AudioPCI [plughw:0,0]
AudioPCI [plughw:0,1]
V8237 [plughw:1,0]
V8237 [plughw:1,1]
Java Sound Audio Engine
Port AudioPCI [hw:0]
Port V8237 [hw:1]

```

My sound card is an esoniq, and I know that the on board sound is the V8237.  So i edited /etc/java-1.5.0-sun/sound.properties , and added this:
```

javax.sound.sampled.Clip=#AudioPCI [plughw:0,0]
javax.sound.sampled.Port=#Port AudioPCI [hw:0]
javax.sound.sampled.SourceDataLine=#AudioPCI [plughw:0,0]
javax.sound.sampled.TargetDataLine=#AudioPCI [plughw:0,0]

```

I now get the music in RuneScape (which I am very happy about) with Sun Java 1.5 .  However, the game sound effects still do not work, as they are midi sounds.  I tried adding this to /etc/java-1.5.0-sun/sound.properties :

```

javax.sound.midi.Receiver=#AudioPCI [plughw:0,0]
javax.sound.midi.Sequencer=#AudioPCI [plughw:0,0]
javax.sound.midi.Synthesizer=#AudioPCI [plughw:0,0]
javax.sound.midi.Transmitter=#AudioPCI [plughw:0,0]

```
but it did not fix the problem.  I think I am no writing the javax.sound.midi stuff in correctly.  Do you know how to do it?

---

### Post by mig5 on 2007-08-20
After doing some research I have found these pages that give some info about the sound.properties file and the MidiSytem setup:
[http://java.sun.com/j2se/1.5.0/docs/guide/sound/programmer_guide/appendix2.html](http://java.sun.com/j2se/1.5.0/docs/guide/sound/programmer_guide/appendix2.html)
[http://java.sun.com/j2se/1.5.0/docs/api/javax/sound/midi/MidiSystem.html](http://java.sun.com/j2se/1.5.0/docs/api/javax/sound/midi/MidiSystem.html)

They explain how to write the provider and name of the sound card, but I don't know what information to put in :(.

---

### Post by techbert on 2007-08-20
Hey,

I poked around and I have an idea.  The sound devices listed are from the "getMixerInfo()" java method in that program I pointed you to.  The "Mididevices" are called different things.  I snagged the important bit out of the code I pointed you to earlier and edited it to list Midi devices instead of AudioSystem devices.  Try copying and pasting this into a file called "midilist.java"

```



import java.io.*;
import javax.sound.midi.*;

public class midilist{


  public static void main(String args[]){

    //Get and display a list of
    // available mixers.
    MidiDevice.Info[] mixerInfo = 
                  MidiSystem.getMidiDeviceInfo();
    System.out.println("Available mixers:");
    for(int cnt = 0; cnt < mixerInfo.length;
                                          cnt++){
        System.out.println(mixerInfo[cnt].
      	                              getName());
      }//end for loop
  }

}


```

You should be able to compile it and run it.  Puzzle Pirates doesn't seem to use Midi, so I didn't catch this one.  I believe your intuition about the properties was right, though.  I've got something like 20 different entries for my card when I run it on my machine.

Hope that helps!

---

### Post by mig5 on 2007-08-22
I did what you said, and the output I got was this:
```

Available mixers:
AudioPCI [hw:0,0]
AudioPCI [hw:0,0]
Real Time Sequencer
Java Sound Synthesizer

```

I'm still not sure how to put this into the sound.properties file to make midi work.

---

### Post by ktur on 2007-08-26
Hi
the sound wasn't working under java on my computer, i found the solution here
[http://java.sun.com/javase/6/webnotes/trouble/TSG-Desktop/html/sound.html](http://java.sun.com/javase/6/webnotes/trouble/TSG-Desktop/html/sound.html)
in my case was the esd daemon, i killed it and the sound worked!

---

### Post by mig5 on 2007-09-06
I don't think that something is stopping the sound, rather the sound devices aren't automatically detected by java.

Bump

---

### Post by mig5 on 2007-10-12
I've re-vamped the first post of this thread with a better description of what is actually the problem, in the hope that someone will come forward with help.
I'm also going to grey-out some of my posts, so that new people to the thread don't have to read useless stuff.

---

### Post by Colsta on 2007-10-25
I've followed your various threads for the same reason - sounds when playing Runescape.  My situation differs from yours slightly but I've come to the same conclusions - it's Java at the root of the problem.

With Gutsy, I started with the benefit of a clean install rather than updating a previous build, so I've no legacy packages to mess things up.  I was fortunate enough to get sounds from RS straight after install (using Firefox with SUN Java 1.6.0_03 from repos).  However, I can confirm that Java hogs the dsp, as nothing else can play sounds concurrently (i.e. I have missed IM alerts and Skype calls etc).  Kill the Java session and everything works together and multiplexes as you'd hope - even youtube/flash based sound in firefox with other sound sources.  So I know that my problem is aligned to yours in as much as it's Java oriented rather than firefox oriented (there's many other threads discussing the shortcomings of firefox and sound).  Unfortunately, the fix for me is still the same at present - start firefox with an aoss wrapper and play RS in that.  I know Java *should* use ALSA (from v.1.5), and so it *should* multiplex - but it doesn't.

However, your situation (if I read it right) differs from mine insofar as you weren't getting *any* sounds out of Java when playing RS in FF (other than under wine).  Your Java setup needed to be tweaked to use the right soundcard and now you're stuck with a partial solution i.e. you got some sounds coming out the card, but no midi.


Well in the course of twiddling myself, I got to wondering why I had sound with Java (albeit sub-optimal) and you didn't.  Could it be that with all the Java installs you made you have lost the library linking along the way or something?

I'm in the UK at present, and it's getting very late as I type this, so I'll get to the random suggestions.
How many JRE types and versions do you have? What do you see when you type this in the console:
>  sudo update-alternatives --config java Is your preferred version selected by default?

Have you got a symlink to the correct version of java in /usr/lib/jvm? e.g. similar to (on mine) java-6-sun -> java-6-sun-1.6.0.03?

Sorry must go sleep now.  I just wanted you to know that someone out there sympathises with your situation :)  I'll be checking back.

---

### Post by mig5 on 2007-11-02
> **Colsta said:**
> How many JRE types and versions do you have? What do you see when you type this in the console:
Is your preferred version selected by default?

Have you got a symlink to the correct version of java in /usr/lib/jvm? e.g. similar to (on mine) java-6-sun -> java-6-sun-1.6.0.03?

Sorry must go sleep now.  I just wanted you to know that someone out there sympathises with your situation :)  I'll be checking back.

At the moment I have 2 versions of java installed, Sun 1.5 (JRE+JDK) and Sun 1.6 (JRE).  I had the problem when I only had Sun 1.6 installed, I installed 1.5 to compile something that helped me fix the sampled sound, because I couldn't get 1.6 JDK to compile it.

```
michael@mikeubunt:~$ sudo update-alternatives --config java
[sudo] password for michael:

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/jamvm
*+        2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 
michael@mikeubunt:~$ 

```


> Have you got a symlink to the correct version of java in /usr/lib/jvm? e.g. similar to (on mine) java-6-sun -> java-6-sun-1.6.0.03?  I have /usr/lib/jvm/java-6-sun-1.6.0.03 and /usr/lib/jvm/java-6-sun , the second one being a symbolic link to the first.

Here is a link to the second thread that I made about this problem, [http://ubuntuforums.org/showthread.php?t=574157](http://ubuntuforums.org/showthread.php?t=574157) .  It is a lot more specific, seeing as when I wrote it I knew what the problem was.

---

