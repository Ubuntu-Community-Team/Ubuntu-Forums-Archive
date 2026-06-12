---
title: "Music Composition in Linux?"
date: 2007-03-05
forum: General Help
---

### Post by valkarin on 2007-03-05
I have not composed music for nearly ten years.  Back then I used an apple setup with lots of synthesizers (mostly Roland).  I would like to get into again, but have no real understanding of the technology anymore.  Can someone help me with this?  I would like to read some good guides on setting up a Linux studio using as little hardware as I can get away with.  Nothing but my computer would be ideal.
:guitar:

---

### Post by 23meg on 2007-03-05
The following may be a good start:

[https://wiki.ubuntu.com/UbuntuStudio](https://wiki.ubuntu.com/UbuntuStudio)
[http://www.linux-sound.org/](http://www.linux-sound.org/)

---

### Post by tubasoldier on 2007-03-05
RoseGarden is an option. But frankly it blows. And the lilypond export is horrible.
NoteEdit is another option. It is decent. Not too great but not too bad. It does simple things but does not do anything really well.

I personally run NoteWorthy Composer under wine. I have a soundcard that can load soundfonts so midi playback for me is a snap. I would assume for midi playback that you would need to use timidity + fluidsynth.

---

### Post by stmiller on 2007-03-23
Rosegarden is an excellent program. The newest version does midi and audio multitracking. There is no 'bounce' feature, however. You'd have to play and then record your work in Audacity in realtime.

The problem with Linux and audio is that there are no professional firewire audio devices with good Linux drivers. The freebob project has had luck with a few devices. You can have lots of great analog synths setting in your studio, but with no way to hook them up to the sequencer program, you are out of luck.

So unfortunately, you'll have to find a good I/O box that is Linux driver friendly.

Edit: And check out Ardour2. It's pretty cool.

---

### Post by Bat on 2007-04-11
KDE NoteEdit seems similar to NoteWorthy Composer, though I haven't got the midi driver working on my kubuntu so I don't know how good it is at playback.  I tried GNU Denemo but it's very flakey - a number of features don't work, and others are intermittent, which suggests it's alpha software written without terribly much care and attention, so I'd give it a miss.  Rosegarden doesn't have the ability to enter musical notation ("the dots", as music fiends like to call sheet music) so it's no use to me, but if it's what you're used to then maybe you can figure out how the hell it works.  I haven't found anything to compare to the ease of use of NoteWorthy, which is really the king of free/cheap software for this purpose.

---

### Post by djaquay on 2007-04-12
> **Bat said:**
> Rosegarden doesn't have the ability to enter musical notation ("the dots", as music fiends like to call sheet music)

Actually, entering musical notation is about all I've done with Rosegarden thus far.  I just opened the notation window and clicked in a few measures, saved it to a MIDI file (.mid), and used aplaymidi to play it out to my keyboard.

Bear in mind I'm very new to this, so that might not be what you meant, and it might not be what you want, but RG does do notation.

Dave

---

### Post by damu on 2007-04-12
Until Ubuntustudio is released for Ubuntu feisty, forget about doing music on Ubuntu. You will spend more time tweaking the system, eventually breaking things than making music. 


I have been using linux for audio recording and musical workshops for about 2 years now. 

My distro of choice was [studio-to-go]("http://www.ferventsoftware.com/"). 
It just works out of the box, as a live-cd. No need to install really. the coming version STG 2.0 is much more user friendly and comes with loads of synths and everything you need to have fun.
It has VST support out of the box , which is really nice ( there are a lot of free VST synthetisers and effects to play with... just google it)but very limited too : some just don't work, doesn't integrate well in a music project (no way to save the parameters of your vsts with your project, no automation, etc)...if you really need VTSs go back to WinXP or MAc...
It is not free : £80. It supports some of the developpers of some main open source audio apps (Rosegarden, dssi, Sonic Visualiser, etc)... 
In any case, you can give a go to their  free demo version and have fun with it.


[64Studio]("http://64studio.com/") offers now the same quality of audio platform than Studio-to-go and its free!!! very nice  distro, without VST support (who cares they don't really work on linux anyway),  but you will have to install it on your computer as it doesn't come as a live cd (make sure you get the 32bits version if your processor is 32 bits....). Like Studio-to-go it supports multicore processors with jackdmp.
[URL="http://ubuntustudio.org/"]

Ubuntustudio[/URL] is not yet at the level of both the previous option but is not far. It doesn't support multicore processors for audio, and I didn't find a way to get post synchro video with xjadeo/qjadeo. The real time kernel seems to still be at beta stage compared to the 2 other distros...I hope it will grow fast though, as it obviously has the enormous advantage of  being based on the rock solid and efficient Ubuntu system! It doesn't come either as a live cd but as an install DVD. A live DVD would be just great...



Musix is another free option. Less polished but comes as a live-cd. That's what I offer to my students to begin with.

Jacklab has an alpha release of their audio distro. It looks promising, but again you need to install on HD + it comes as a DVD (be patient for download and install...) + you need to install the real-time kernel to have something working...so not as straightforward as the other options.

There are other multimedia distros which offer few audio apps (dynebolic, artistx ), but they are not audio centered.

So to start with, I would suggest to go for a live-cd option. Download the demo of studio-to-go, burn the iso, and restart your computer from the cd...that's it, you have a working sound studio.

I use Rosegarden all the time. Simple, user friendly and efficient midi/audio sequencer.
Check the great Hydrogen rhythm box.
Have fun with the amazing Zynaddsubfx synth.
If you really want to do a pro audio recording and mix with full automation, then Ardour is your friend. You will see that you can have Rosegarden+ Hydrogen+Ardour synchronised through Jack...

You can also decide to go more with a loop approach. Then LMMS is the one you are looking for.

Have fun

---

### Post by Gongchime on 2008-02-27
Some of my tunes have been forwarded to a music library. Potential for someone looking for tunes to put them in TV or movies. 

Need a lot more than that to make a living, but it does show that it IS possible to do this.

Greg

---

### Post by Gongchime on 2008-04-29
I've been studying how Expert Systems mimic pro composers. I'd really like to see some music composition software which isn't only  music sequencing software or music notation/graphing software. 

I'd specifically like to see a program that will take a melody I input, perhaps only scanned in, that the computer then runs through all of the traditional music composition transformational devices without making me write them all out and test them on my instrument before I input them into the so called music composition software. 

If and when it can instantly create, inversions, retrogrades, retrograde-inversions, permutations, augmentations, diminutions, diatonic transpositions, putting the original melodic series together with the rhythmic retrograde, or putting the melodic series' retrograde inversion with the original melodic rhythm or taking the melodic series from one tune and combining it with the melodic rhythm from another tune, automatically make a diatonic melody pentatonic or automatically change the mode, then and ONLY then will there be any real music composition software in the universe.

---

### Post by goodmanbrown on 2008-04-29
I basically second damu's suggestions.  Instead of Rosegarden, I use seq24 for midi sequencing.  It is much, much simpler, which suits me 'cause I hardly do any midi sequencing.

The combination of zynaddsubfx, seq24, hydrogen, and ardour, all hooked together with jack, will allow you to compose on your computer, with no external midi controllers or synths.

Here are a couple tutorials I found helpful in getting up and running.  They are getting dated, but it's still a decent place to start.

[Drum loops in hydrogen, recorded in ardour via jack]("http://quicktoots.linuxaudio.org/toots/ardour-osx/page2.php").
[Using seq24 to control zynaddsubfx]("https://help.ubuntu.com/community/HowToSeq24Introduction").
Last, there's a guy who started blogging his [experiences with Ubuntu Studio]("http://briansbedroom.blogspot.com/").  It's not so helpful for getting off the ground, but it us good for the occasional tip or trick.

---

