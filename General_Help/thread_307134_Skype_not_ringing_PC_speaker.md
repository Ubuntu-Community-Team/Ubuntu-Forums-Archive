---
title: "Skype not ringing PC speaker"
date: 2006-11-26
forum: General Help
---

### Post by gary101 on 2006-11-26
Hi

Downloaded and installed Skype deb from skype.com. Works flawlessly but I cannot get it to ring the pc speaker.

In the options under 'Sound Devices', 'Audio System to Use' there are two settings in the dropdown. Alsa and OSS, both are showing 1 Device found.
Sound works great on Alsa and no sound on OSS.
The sound device listed under Alsa is: VIA 82C686A/B rev50

For audio out, audio in & ringing this device is showing as the only option.
I would like it to ring the PC Speaker (as I had it set when I used to use M$) as I use a headset and cannot hear it ringing otherwise.

Is there any setup file I can use in the back end to get the PC Speaker set as the device to ring?

Any help appreciated.

---

### Post by teataster on 2007-03-16
Any ideas? I have exactly the same issue.  The option is there in the Windows version to do this, but I cannot find it in the Linux version.  I am using the latest version of Skype for Debian 1.3.0.53_API

---

### Post by laidback on 2007-03-16
Run alsamixer in a terminal and check the input/output settings.

I too use Skype but have no problems with sound.

If I have the speakers on I can hear the ring tone, but the conversation will also come out on the speakers, it doesn't automatically turn off. I can have both headphones and speakers on.

---

### Post by teataster on 2007-03-16
My problem is that I do not have speakers, only headphones.  That's why the 'ring PC speaker' feature on the Windows version is so useful.

---

### Post by kiaran on 2007-03-19
I have this same problem.

I use SPDIF digital audio through my home theater, but I don't want my home theater to ring when somebody calls me on Skype. I would much rather use the PC speaker, but alas the option is missing.

This is a real pain because I can't incoming calls if my stereo is off (which is 90% of the time).

Where is the PC speaker option???!!

---

