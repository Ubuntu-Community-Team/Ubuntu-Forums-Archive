---
title: "beast using timidity and midi"
date: 2006-08-23
forum: General Help
---

### Post by disector88 on 2006-08-23
Hi,

I am trying to get a working midi composing software - beast, but am a little confused by the terms and capabilities available. Here is my setup:
Ubuntu Dapper w/ gnome(kernel/packages up to date as of 8/21)
Creative Sound Blaster Audigy SE (the dreaded ca0106 - [http://alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy+SE.&chip=CA0106&module=ca0106](http://alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy+SE.&chip=CA0106&module=ca0106))

The sound card works fine - playing movies, mp3s, etc. but not midi.
Since the ALSA page does not say anything about MIDI supported for this card and monkeying around with it didnt help either, I installed timidity from synaptic. After much effort, i was able to get midi playback by using aplaymidi. "aplaymidi -l" lists 4 timidity ports and I can hear it when i play a file through that port using timidity. I cannot play it using amarok/rhythmbox/totem, but I'm not really bothered. 

The problem is when using beast. When I click the play button, I cannot hear anything. Is there a way to verify whether timidity is set up as the default MIDI device? Or is there a way to tell beast to use timidity? Also, I was a little alarmed/confused by the statement on [http://beast.gtk.org/wiki:HelpDesk](http://beast.gtk.org/wiki:HelpDesk) : 
	> I would like to know if it is possible to use Beast with a virtual synthesizer like timidity since my sound card do not have a hardware synthesizer. 		Thanks, Sawyer 

	Up to and including version 0.6.6, beast does not support MIDI output, regardless of hardware support. We do support loading the GUS patches used 	by timidity for some time now but pure MIDI sequencing has yet to be implemented. --RamboKid
Does this mean that beast does not output the sound of the sequence it creates?

Alternatively, can someone suggest  a music composition tool where you can see and hear a piano keyboard; and write music notes which can be played back (either via midi or PCM).

Your help is much appreciated as usual.

---

### Post by SteveF on 2006-08-23
> **disector88 said:**
> Hi,

I am trying to get a working midi composing software - beast, but am a little confused by the terms and capabilities available. Here is my setup:
Ubuntu Dapper w/ gnome(kernel/packages up to date as of 8/21)
Creative Sound Blaster Audigy SE (the dreaded ca0106 - [http://alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy+SE.&chip=CA0106&module=ca0106](http://alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy+SE.&chip=CA0106&module=ca0106))

The sound card works fine - playing movies, mp3s, etc. but not midi.
Since the ALSA page does not say anything about MIDI supported for this card and monkeying around with it didnt help either, I installed timidity from synaptic. After much effort, i was able to get midi playback by using aplaymidi. "aplaymidi -l" lists 4 timidity ports and I can hear it when i play a file through that port using timidity. I cannot play it using amarok/rhythmbox/totem, but I'm not really bothered. 

The problem is when using beast. When I click the play button, I cannot hear anything. Is there a way to verify whether timidity is set up as the default MIDI device? Or is there a way to tell beast to use timidity? Also, I was a little alarmed/confused by the statement on [http://beast.gtk.org/wiki:HelpDesk](http://beast.gtk.org/wiki:HelpDesk) : 
	
Does this mean that timidity does not output the sound of the sequence it creates?

Alternatively, can someone suggest  a music composition tool where you can see and hear a piano keyboard; and write music notes which can be played back (either via midi or PCM).

Your help is much appreciated as usual.


This doesn't answer your question in any way, but if you find that you can't solve the beast issue, you might want to take a look at RoseGarden.  It is a KDE app if that bothers you.  I have it running under gnome along with midi playback.  So it might be an alternative for you.

Steve

---

### Post by peabody on 2006-08-23
> **disector88 said:**
> 
Does this mean that timidity does not output the sound of the sequence it creates?


No, no, timidity can definitely play midi.  I use it all the time.  I'm assuming the post you quote is out of context.

I don't know off hand if the Sound Blaster Audigy supports loading Sound Fonts, but I believe it should (I have an older sound blaster live that does).  You may want to look into sound fonts as this offloads the generation of sound to the actual sound card.  Timidity does everything in software and as a consequence absolutely gobbles up CPU cycles.

Sound fonts are done transparently with the windows drivers, but not so in the Linux world because most sound fonts are copyrighted and not legal to distribute.  There are some free ones on offer over the Internet I believe.

---

### Post by disector88 on 2006-08-23
> Quote:
Originally Posted by disector88  
Does this mean that timidity does not output the sound of the sequence it creates? 

Sorry, what I meant to say was: 
Does this mean that beast does not output the sound of the sequence it creates? This is corrected in my original post.

Again, timidity and aplaymidi can play the midi file correctly. I copied a soundfont file from the creative driver CD which came with the card to /etc/soundfonts and configured timidity to use it. I think this is working fine since aplaymidi can play the midi files.

The problem is making timidity visible to beast.

---

### Post by disector88 on 2006-08-24
Thanks steveF !

Rosegarden works great. Works well with timidity. Is there a way to get high quality midi sounds? I'm guessing this means gettinga  new soundfont. Is thera  place to get good quality soundfonts?

---

### Post by SteveF on 2006-08-27
> **disector88 said:**
> Thanks steveF !

Rosegarden works great. Works well with timidity. Is there a way to get high quality midi sounds? I'm guessing this means gettinga  new soundfont. Is thera  place to get good quality soundfonts?

The soundfont I'm trying I found at:
[www.personalcopy.com](www.personalcopy.com)

I'm using the one called PC51f.sf2.  I think on the site it is gzipped to about 53mb.

Also, you should install awesfx package in order to load asfxload on the sequencer settings.

Steve

---

