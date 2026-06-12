---
title: "2 soundcards ... different programs to different cards?"
date: 2007-09-17
forum: General Help
---

### Post by gschoppe on 2007-09-17
ok, here's the deal.  I want everything to run from one sound card, unless specifically set to the other.

More specifically, I want Azureus (and only Azureus) to notify through my secondary sound card.

Is this possible, and, how?


Here's my setup (in case its important):
Feisty 64bit box
onboard sound runs to a KVM with my windows box
USB sound card runs off an internal header to powered speakers built into the case
I need Azureus to Audibly notify download completion, even when the windows box is in use.
I don't want to use a splitter off the main card, because I want the PC to be quiet when KVMed unless Azureus has a notification (also, it would mess with music playback)

Is this related to alta-oss ?  what is alta-oss? can it do the job?

---

### Post by gschoppe on 2007-09-18
here's how I think the process works... this is a guess and may be way off the bat.  I'll test it tomorrow, and hope for the best, but if anyone can point out issues, let me know

DISCLAIMER: this is lifted right from my working notes file... please excuse any formatting or general incorrectness... please correct me if you spot where i'm making errors

```

	DEVICE NAMES: CK804 (ONBOARD) , U0xd8c0x0c (USB)
	
	FIRST:
		sudo nano /etc/modprobe.d/alsa-base
	ADD TO THE END:
		options CK804      index=0
		options U0xd8c0x0c index=1 
	TO FORCE DEFAULT SOUNDCARD TO BE ONBOARD
	SECOND:
		gedit ~/.asoundrc
	ADD TO THE END:
		ALSA_OSS_PCM_DEVICE { type plug
		slave.pcm "hw:1,0"
		}
	OR MAYBE
		pcm.dsp0 { type plug
		slave.pcm "hw:1,0"
		}
	CHANGE ALL AZUREUS SHORTCUTS TO
		aoss azureus

```

Is this anywhere near the mark?:confused:

can non OSS programs be forced to use a certain card with this technique? ... what would happen, for example, if I ran "aoss vlc"? (yes, I know vlc has a gui and cli method to set sound device, this is a hypothetical question)

---

### Post by gschoppe on 2007-09-19
haven't yet completed testing, but it seems to work

---

