---
title: "Rhythmbox ipod sync support"
date: 2005-04-29
forum: General Help
---

### Post by Klin'Targ on 2005-04-29
Am I correct in my conclusion that Rhythmbox has no ipod syncing capabilities, or have I missed something?
I installed gtkpod for syncing purposes, but it would be nice to have a unified interface for this.

---

### Post by doclivingston on 2005-04-30
Rhythmbox does support it, but I'm not sure whether the version that comes with Ubuntu has it compiled in. <goes and checks> Yep, Hoary is built with iPod support, does the iPod source show up in the sidebar?

---

### Post by Klin'Targ on 2005-05-10
Yes, the source shows up. I can read the songs from my iPod without trouble. I cannot, however, figure out how to copy songs to it through Rhythmbox.

---

### Post by JayStapleton on 2008-03-11
Use iTunes on a PC to copy one song to your ipod, after that, it should show up on the left hand side bar in Rythmbox, and you can just drag and drop.

---

### Post by wb34 on 2008-03-23
I was wondering if Rhythmbox can copy songs from an ipod onto your computer? also, does it have an actual synchronize button like itunes does or do you have to manually drag all the songs you want to put on it over to the ipod?

---

### Post by dersk on 2008-04-19
As far as I can tell, there's no actual sync capability in RhythmBox, as opposed to simple copy. Banshee does have a full sync, but the version in the repositories (11.3.1, I think?) seems to break a lot of stuff on my 60 GB video iPod (podcasts, database rebuild fails, etc.).

Just successfully copied podcasts in RhythmBox from RB to iPod and it worked fine, but the play counters didn't come over. Just trying to check now if RB will let you copy a track from the iPod to RB or the desktop, but now the iPod doesn't seem to want to mount...

OK, one iPod reset later....ok, you can copy directly from iPod to desktop, but it takes the cryptic iPod filename (four letters). You can copy from iPod to RB library, and filename and metadata seem to be preserved.

Now if I could just find a decent solution for audiobooks, I'd be able to dump Windows / iTunes...

---

### Post by orengolan on 2008-04-19
[http://retune.sourceforge.net/](http://retune.sourceforge.net/)

I use retune. 
it's a python script that you should run after you change anything in
your iPod folder.  very easy to use.

that's what you do:

[LIST=1]
[*]download the script.
[*]put all the files in your ipod's directory.
[*]add/delete audio files from the device.
[*]cd /media/your name/
[*]python retune.py
[*]python retune.py (again)
[/LIST]

done!

I created a script that I run from the 'run application' dialog, 
so I don't even need to open the command line anymore:
```
#!/bin/bash
cd "/media/OREN GOLAN"
python retune.py
```

---

### Post by orengolan on 2008-07-18
i can't find retune on the web.
any ideas where is it?

---

