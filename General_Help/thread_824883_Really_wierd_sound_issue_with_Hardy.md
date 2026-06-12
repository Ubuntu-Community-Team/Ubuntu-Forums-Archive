---
title: "Really wierd sound issue with Hardy"
date: 2008-06-10
forum: General Help
---

### Post by d_in_Conduct on 2008-06-10
I process probably 500 short (3-20 seconds).wav files daily.  I use the sound you get when resting the cursor over the file icon most of the time, which is really handy.  Often I need to open the file and transcribe the contents, applying EQ or looping short sections, etc.  I installed Baudline ([www.baudline.com](www.baudline.com)) to see if there was anything to offer there that might make it easier.  Opening the file directly in Baudline didn't work too well, but I thought I could patch Audacity to Baudline using Jack.  In my experience, Audacity support of Jack has been near useless, but this looked like a situation it could handle.  Didn't work.  Left me with the common problem of not being to use Audacity because of some mismatch with Alsa.  

Against my own better judgement, I tried Gnusound, which has never worked for me very well.  While setting Gnusound up my whole system crashed and after about 5 seconds went back to the login screen.

After logging back in I found that it took Audacity 15-20 seconds to start and it showed  a flat line for the waveform.  I realize that the waveform doesn't necessarily mean there is no sound there.  But, the problem with Audacity persisted, taking an equally long time to open the Preferences page, which did no good.  Audacity claims the file is a 9600khz file.  They are all 44100 recorded with ecasound.  I reinstalled Audacity several times and alsa-base with synaptic.  No change.  Ecawave would display a correct waveform for files that Audacity wouldn't touch (for awhile) and play them.  Now all the files show flatlines and no sound.  They don't even play on another machine.

Thanks for reading this far.  I'm stumped.  Anyone have any ideas?

---

