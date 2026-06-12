---
title: "Some kind of sound problem"
date: 2006-12-25
forum: General Help
---

### Post by callaw on 2006-12-25
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open resource for writing. 
I think my sound card is not installed properly, what shall i do?

---

### Post by bcdeck on 2006-12-29
I am getting a similar issue, but my error message is

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Resource busy or not available.

this error is intermittent -- sometimes I have sound and sometimes not, and I change no settings between the times that sound does or does not work.   ](*,)

---

### Post by dgompert on 2007-01-07
I have the same error:
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Resource busy or not available.

If you change the permissions on the /dev/dsp and /dev/audio devices to 666 it seams to fix the problem.  My problem started after I used EasyUbuntu.

---

### Post by jryer on 2007-01-23
I get the same error message:
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Resource busy or not available

The problem seemed to be intermittent for me as well but now I have no sound at all, ever! I tried changing permissions for those two files but the problem continues.

Any help?

---

### Post by cowmix on 2007-02-03
I have the same issue too.. Again I have EasyUbuntu installed too..

After a reboot.. sound is fine.. then after a while at screws up again..

---

### Post by Zogg on 2007-02-07
Has this been resolved?

---

### Post by mmoalem on 2007-02-20
having the same problem... any solutions yet?
one thing is that on the sound checking app i have few options to choose from:
1. AUtodetect
2. HDA generic
3. ALSA
4. ESD
5. OSS
when i press test on autodetect it plays but no sound coming up. same on ESD. on the others i get the error 'audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Resource busy or not available'
on reboot sound is usually back...
hardware - gateway laptop, core2duo intel chipset 82801G (ICH7 Family)
hope it might help with figuring it out

---

### Post by savohead on 2007-02-27
same problem here ...
i have an usb card, when i plug it sound works from that card, trying to switch back to my inside card, sound still comes out from the usb card ... amazing!! eheh ... it's a bit annoying but i think that i fixed the same problem in dapper touching something in alsa-base ... but now i don't remember the fix ...
hope someone will help us soon ...

---

