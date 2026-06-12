---
title: "BETA Octoshape plug-in for Linux"
date: 2007-05-30
forum: General Help
---

### Post by Rebecca354 on 2007-05-30
I tried installing this by following the directions but mplayer never pops up when I execute the plug-in. Any help would be greatly appreciated thanks. here is the original link :[http://octoshape.com/plugin/linux.asp](http://octoshape.com/plugin/linux.asp)

> Requirements

    * Sun Java 1.5 or above
    * libstdc++.so.6 (installed on most Linux distributions by default)
    * An http-enabled media player (mplayer)

* With a 32 bit Java Runtime Environment, the Octoshape plug-in is known to run in 32 bit emulation mode.
Setup procedure

   1. Download the .bin file and make it executeable with chmod +x octosetup-linux_i386.bin
   2. Execute ./octosetup-linux_i386.bin and follow the installation instructions
   3. Enter the newly created directory "octoshape" and create a file called "setup.cfg". Enter the path of your libjvm.so file in setup.cfg, like this:

      JavaExec=/path/to/libjvm.so

      (If you don't know the path of your libjvm.so file, see this FAQ entry: Where should I look for libjvm.so?
   4. Proceed to "Using the Octoshape plug-in"

Using the Octoshape plug-in

   1. Navigate to the Linux play page
   2. Use the string from the "Play" column to play your stream. Pass the string as the -url argument to OctoshapeClient like this:
      ./OctoshapeClient -url:XYZ.xyz
   3. A media player should launch (default is mplayer) and play the file.

OctoshapeClient will fill in the setup.cfg file with default options, the first time you run it. You can modify setup.cfg afterwards, if you want to use a different media player.

It mentions at the end that when I first run the plug-in it will write to the setup.cfg file when first run but that doesn't happen.

---

### Post by reclusivemonkey on 2007-06-03
It wouldn't work for me either. It says in the instructions you have to create setup.cfg yourself which I did. It doesn't seem to make a difference. You might want to email them.

Hmm, I tried it again and it tried a little more; it tries to get some updates, but there is an error;

```

Error : An internal error was discovered. Detailed error information: Thread: mpmain-4. Stacktrace: octoshape.um: {%]BN6

```

Still a work in progress I guess.

---

### Post by jrib on 2007-09-09
It's working fine for me at the moment after following the directions at [http://www.octoshape.com/plugin/linux.asp](http://www.octoshape.com/plugin/linux.asp).

Some ubuntu-specific information:
On Feisty and Gutsy i386: 
* Install the sun-java6-bin and mplayer packages to fulfill the requirements.
* When you are creating the setup.cfg file, make the contents:
```
JavaExec=/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/client/libjvm.so
```

On Feisty amd64: 
* Install the ia32-sun-java6-bin and mplayer packages to fulfill the requirements.
* When you are creating the setup.cfg file, make the contents:
```
/usr/lib/jvm/ia32-java-6-sun-1.6.0.00/jre/lib/i386/client/libjvm.so
```

I've created a wiki page with instructions that should work on Ubuntu: [https://help.ubuntu.com/community/Octoshape](https://help.ubuntu.com/community/Octoshape)

---

### Post by Lokasvami on 2007-09-20
I followed the instructions on the wiki and it worked, except that the mplayer only shows a blue screen, but I can hear the audio. Any ideas on how to fix this ? I'm running a Toshiba R-100 ?

---

### Post by jrib on 2007-09-21
Let's make sure it's not an issue with the stream.  What stream are you trying?

I've been viewing "./OctoshapeClient -url:RTP.800" and it has been working fine.  Can you test that one and see if you have the same problem?

---

### Post by Lokasvami on 2007-09-21
What a coincidence - the RTP stream is the one I am interested in watching !  Anyway, I tried it just now and can only still hear sound. I now also get a black screen. In addition, I have to manually open MPlayer, it won't do that automatically (not sure if it is suppose to anyway). I have set it up on an IBM Thinkpad and it works fine, so I think its a R100  issue. I think there are too many little (and therefore really annoying) issues, and I might keep the R100 an XP machine and the old PIII Thinkpad brick as Ubuntu, as everything works perfectly. I would have preferred the opposite scenario, but hey, that's life.

---

### Post by jrib on 2007-09-21
mplayer opens automatically for me here.

video codec appears to be wmv3.  Have you installed the w32codecs?  If not, grab them at either [http://www.medibuntu.org](http://www.medibuntu.org) or [http://wiki.ubuntu.com/SeveasPackages](http://wiki.ubuntu.com/SeveasPackages)

By the way, how are you opening mplayer manually?

---

### Post by Lokasvami on 2007-09-21
I have the codecs. Actually, I have realized that it is opening automatically, I have just not been waiting long enough, it does eventually come up. Its just that if I open MPlayer, then the window appears to comes up quicker. Strange. I think I have a more general video problem - I just tried the Nelson Mandela ogg video in the Examples folder, and that is blank, but I can hear the sound.

---

### Post by jrib on 2007-09-21
try opening mplayer as:
```
mplayer -vo x11 /some/file
```
does that work?

---

### Post by Lokasvami on 2007-09-21
That made the Nelson video play. What does that mean ?

---

### Post by jrib on 2007-09-21
Means your card isn't doing video acceleration for some reason.  What video card do you have and what driver are you using for it?

You could also just make x11 the default in ~/.mplayer/config with "vo=x11" but then you won't get video acceleration from your video card.

---

### Post by Lokasvami on 2007-09-21
I think its a "Trident Microsystems CyberBlade XP4m32", with the a "trident" driver, but I could be way off, but I just looked in the xorg.conf file (I'm new to Linux).

---

### Post by jrib on 2007-09-21
> **Lokasvami said:**
> I think its a "Trident Microsystems CyberBlade XP4m32", with the a "trident" driver, but I could be way off, but I just looked in the xorg.conf file (I'm new to Linux).

ok, I know nothing about this card, but in your xorg.conf, is the "trident" driver being used instead of something like "vesa"?

---

