---
title: "Can't play midi files"
date: 2013-05-18
forum: General Help
---

### Post by MaZaMo on 2013-05-18
When I try to open a midi file on ubuntu 13.04 I get the message:

**Required plugin could not be found**
Videos requires to install plugins to play media files of the following type: audio/midi decoder

In the past when I had ubuntu 13.10 I could play them...

---

### Post by Hekabe on 2013-05-18
Those are proprietary plugins, they can't be installed with an upgrade. Use sudo apt-get in the terminal to get gstreamer-plugins-ugly and gstreamer-plugins-bad.

---

### Post by cortman on 2013-05-18
You probably didn't check the box to install third-party media plugins at installation. Depending what media player you're using it will give you the option to download the required plugin through the program itself.

---

### Post by MaZaMo on 2013-05-19
No, I did install that, and I also installed ubuntu-restricted-extras

---

### Post by MaZaMo on 2013-05-19
Can't find those packages

---

### Post by MaZaMo on 2013-05-19
> **cortman said:**
> [COLOR=#000000]Those are proprietary plugins, they can't be installed with an upgrade. Use sudo apt-get in the terminal to get gstreamer-plugins-ugly and gstreamer-plugins-bad.[/COLOR]

Can't find those packages.

---

### Post by Dennis N on 2013-05-19
> **MaZaMo said:**
> Can't find those packages.

The names should be:

gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-bad

---

### Post by Dennis N on 2013-05-19
Since I notice you installed ubuntu-restricted-extras, I think those two files should already be installed.

---

### Post by 3rdalbum on 2013-05-19
You need the Timidity package in order to play MIDIs.

---

### Post by mcduck on 2013-05-19
+1 to above.

MIDI is not a proprietary format, so ubuntu-restricted extras doesn't help. Actually it's not even an audio format, and therefore none of the gstreamer plugins (or any other codecs) help you there. Instead you need to get a program that's able to play the MIDI data into audio (usually a software synth or some similar tool). And Timidity is the most common tool when you just want to get some kind of audio conversion without knowing the exact instruments the MIDI file was made for.

---

### Post by Dennis N on 2013-05-19
Two solutions to play MIDI files:

excellent sound: timidity + fluid-soundfont-gm
fair to good sound: Audacious + AMidi Plug Plugin + fluid-soundfont-gm

Timidity is a command line tool. Play files one-at-a-time, or play an entire directory. Timidity will also direct output to audio file (could be mp3 or ogg) with the identical sound so you can use them on any player. Get rid of the MIDIs.

If you want a playlist and graphical interface and controls, try Audacious.

---

### Post by andrew.46 on 2013-05-20
vlc will do this when built against libfluidsynth and with a soundfont installed. I have not tested this package but it looks like a good choice:

[http://packages.ubuntu.com/raring/vlc-plugin-fluidsynth](http://packages.ubuntu.com/raring/vlc-plugin-fluidsynth)

---

### Post by pembertonq on 2013-10-06
But as the OP points out, this used to work. In the past I could play midi files without problems, even in the browser.

That seems no longer to be the case.

So the question is: what changed? Why? How can we fix this permanently?

---

### Post by tomwnorton on 2013-11-08
I have the same problem.  When I had 12.04 I could play midi files just fine on totem.  But now that I have 13.10, I can't.  Just like pembertonq, I chose to install the restricted extras upon installation.

---

### Post by rubo77 on 2014-05-03
> **mcduck said:**
> 
MIDI is not a proprietary format, so ubuntu-restricted extras doesn't help. 

just install

    ```
sudo apt-get install vlc-plugin-fluidsynth
```

---

