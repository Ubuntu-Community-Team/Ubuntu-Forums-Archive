---
title: "DVD drive won't open after running script"
date: 2006-10-08
forum: General Help
---

### Post by painaxl on 2006-10-08
I ran Gnomebaker to make a disc from a DVD image and got an "input/output error" message.  I tried to eject the disc and it wouldn't come out.  The light comes on when the button is pressed, but then goes off.  Going to eject in the filesystem produces a longer light, but nothing.  I rebooted and get the same effects.

I've burned many things before and never had the error message or this problem.  I ran a script to burn .cdi (discjuggler) image but had to abort it midway through (the burning hadn't started yet).  This is probably the cause but I don't know how or what needs to be done.

Here is the script:
```
"#!/bin/sh

CDIIMG="$1"


cdirip "${CDIIMG}" -cdrecord
COUNTER="0"
MORE=true

while $MORE
do
	COUNTER=`expr $COUNTER + 1`
	NUMBER=`printf %02u $COUNTER`
	ISOFILE=tdata${NUMBER}.iso
	WAVFILE=taudio${NUMBER}.wav

	
	if [ -f $WAVFILE ]; then
		cdrecord dev=ATA:1,0,0 speed=4 -multi -audio $WAVFILE && rm $WAVFILE
	elif [ -f $ISOFILE ]; then
		cdrecord dev=ATA:1,0,0 speed=4 -multi -xa $ISOFILE && rm $ISOFILE
	else
		MORE=false
	fi
done
eject
```

Any ideas?

---

### Post by William the Conquerer on 2006-10-08
hmm, this sounds odd, can you run
```
$sudo eject
``` from a terminal?  that might give you some more clues.

---

### Post by painaxl on 2006-10-08
> **William the Conquerer said:**
> hmm, this sounds odd, can you run
```
$sudo eject
``` from a terminal?  that might give you some more clues.

Ok, the light on the drive went on for about 25 seconds, then went off and the prompt came back up.  Same thing happens when you push the button on the drive or right click the drive and click eject in the computer "places" from the desktop.

---

### Post by tommcd on 2006-10-09
Is it possible the drive is jammed? You could try to stick something small in the tiny hole to open the drive. Then reboot and try again, possibly using a different CD disc.

---

