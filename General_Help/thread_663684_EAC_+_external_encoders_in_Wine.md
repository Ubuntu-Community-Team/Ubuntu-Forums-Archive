---
title: "EAC + external encoders in Wine"
date: 2008-01-10
forum: General Help
---

### Post by ThumbBumpkins on 2008-01-10
I have EAC running in wine, and it works, no problem. However, when I try to use an external program (i.e. lame.exe), nothing happens. Is there some setup I need to do to make the external compressor work under wine? Any help would be very much appreciated.

---

### Post by logos34 on 2008-01-10
Are you dual booting and maybe the .exe's are on the windows partition?

---

### Post by ThumbBumpkins on 2008-01-10
No, I am not dual booting and don't have any actual windows files anywhere. The external compressor's files are in my /.wine/drive_c directory, and should definitely be accessible to EAC. It just simply does not launch the exe like it should.

---

### Post by logos34 on 2008-01-10
try copying them outside the .wine dir, in home somewhere

i.e. mine are in ~/eac_codecs

my path in eac  j:\<codec>.exe

---

### Post by doug1212 on 2008-01-10
Hi,
Possibly permissions, is the file executable bit set?
I know EAC via wine mostly works i have used it.
Doug.

---

### Post by ThumbBumpkins on 2008-01-10
Nope, same problem.  It gets to the "Compress by external program" step and after a few seconds stops, and the original .wav file is still there. Do I need an actual windows partition for some crucial system files or something?

---

### Post by logos34 on 2008-01-10
Mine's installed on my windows partition, and I have the  .wav only problem too unless the .exe's are on my linux partition

---

### Post by ThumbBumpkins on 2008-01-10
Doug,
I'm not sure what you mean, could you explain more?

---

### Post by doug1212 on 2008-01-10
Right click on the .exe and click permissions tab and ensure that the execute box is ticked.

---

### Post by ThumbBumpkins on 2008-01-10
I changed the permissions and it still didn't work. I'm at a total loss now.

---

### Post by doug1212 on 2008-01-10
Here is a thread on EAC:

[HTML]http://ubuntuforums.org/showthread.php?t=142784&highlight=eac+wine[/HTML]

Also double check the path to lame.exe encoder is correct in the setup pages.

I am not actually using eac at present, I am quite happy with grip or abcde. I may put it on and try, maybe it's a wine problem has been known :(

Doug.

---

### Post by doug1212 on 2008-01-10
OK, just installed eac-0.95b4 and dropped lame into the directory ensuring that it is executable, got the command line options from hydrogen audio wiki and ripped a few tracks just fine, mp3 created and wav deleted.
Doug.

---

### Post by ThumbBumpkins on 2008-01-10
I followed that thread exactly, and EAC itself works with no problem. I have turned on the "check external program return code," and now after every track it tells me lame.exe returned an error with no more details than that. I have just checked to make sure I am running the latest wine and LAME 3.97b2 and EAC 0.95b4, and I have tried running lame.exe from within my wine c drive and my home folder, and made sure that it has permission to run as a program. However, it's still not working. Any other ideas?

---

### Post by doug1212 on 2008-01-11
Double check that the cmd line options are correct, I used this:
```
-V 2 --vbr-new --id3v2-only --pad-id3v2 --ta "%a" --tt "%t" --tg "%m" --tl "%g" --ty "%y" --tn "%n" %s %d
```
Doug.

---

### Post by Glamdring on 2008-02-24
Hi!

I'm new and this is my first post (so have mercy). I started to play around with EAC in Ubuntu, and everything run fine til I got to the part of using LAME as external encoder. Tried EVERYTHING, but it ended always in some error message (as also mentioned before). Then, I tried this:

1. Copy all the contents of LAME folder into the EAC folder (it sounds stupid, but hang on)
2. Make the lame.exe executable through properties and permissions.
3. Open EAC, go Compressions Options, and BINGO in the Waveform tab, scroll down and you'll find LAME MPEG MP3 encoding as internal encoder. I used Preset:Extreme in Sample Format.
4. Check Do not write WAV header to file
5. File extension: .mp3
6. Check the new Tab which has been formed: LAME DLL for more tunning. :-)

Then rip in peace. There'll be no wav files, only straight to mp3.

It seems to work for me. Anybody confirm...

---

