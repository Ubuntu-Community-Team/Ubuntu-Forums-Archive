---
title: "No sound, except in Totem."
date: 2006-08-23
forum: General Help
---

### Post by SonicChao on 2006-08-23
I am getting no sound in any applications, including aMSN, Firefox (no sound in flash or java), and most other applications.

The amazing part of this is, I still have sound in Totem, I hear the sound that Ubuntu makes when it logs in and when it logs out. The only terminal output I'm getting is from one application, festival, which is a Text-to-Speech app for Linux. It says:

```

sonicchao@sonicchao-laptop:~$ festival
Festival Speech Synthesis System 1.4.3:release Jan 2003
Copyright (C) University of Edinburgh, 1996-2003. All rights reserved.
For details type `(festival_warranty)'
festival> (SayText "LOL")
#<Utterance 0xb71949a8>
festival> Linux: can't open /dev/dsp

```

Ok, I took a look at the folder /dev, did an 'ls', and behold, I fould dsp in there.

It's quite random, sometimes it happens and sometimes it doesn't...however I haven't been able to figure out what I do to make it not happen yet.

My sound comes from laptop speakers, Conexant AC-Link.

---

