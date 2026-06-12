---
title: "KMid not working"
date: 2004-11-28
forum: General Help
---

### Post by Quest-Master on 2004-11-28
Just a quick note to those who develop Ubuntu, you've done a fabulous job in creating one of the most wonderful and user-friendly Linux distributions ever ;)

Now, I installed some KDE stuff, notably KMid so I could listen to MIDIs. The program loads up perfectly fine, and I can open up MIDIs fine too, but when I try to play them, I get this error:

Couldn't open /dev/sequencer.
Probably there is another program using it.

I have tried opening KMid as su, as well as letting it be the first and only program running just in case there WAS another program using it or if I couldn't get priveleges. None of these seem to be the problem and KMid was working fine on SUSE.. so, could anyone tell me how to fix this?

---

### Post by jdodson on 2004-11-29
this might help.

[http://www.google.com/search?q=Couldn%27t+open+%2Fdev%2Fsequencer.&sourceid=mozilla-search&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox-a&rls=org.mozilla:en-US:official](http://www.google.com/search?q=Couldn%27t+open+%2Fdev%2Fsequencer.&sourceid=mozilla-search&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox-a&rls=org.mozilla:en-US:official)

---

### Post by Quest-Master on 2004-11-29
Wonderful, thanks a bunch.

Hm.. It seems /dev/sequencer does not exist :o!!! I suppose I'll make it and see if it works.

---

### Post by Quest-Master on 2004-11-30
After a bit of work I installed the missing ALSA MIDI plugin, and apparently, it is fully working, but no output is being produced by KMid.

I'm going to see if Rhythmbox will work.

---

### Post by CowPie on 2004-12-17
[QUOTE=Quest-Master]After a bit of work I installed the missing ALSA MIDI plugin, and apparently, it is fully working, but no output is being produced by KMid.

I'm going to see if Rhythmbox will work.[/QUOTE]
 Hi, how does one installs missing ALSA MIDI plugin?

---

### Post by captainboog on 2005-05-03
[QUOTE=CowPie]Hi, how does one installs missing ALSA MIDI plugin?[/QUOTE]

edit /etc/modules
add  the line:
"snd-seq-midi"

note: i'm new to this so i may be missing the easy or more thorough way

---

