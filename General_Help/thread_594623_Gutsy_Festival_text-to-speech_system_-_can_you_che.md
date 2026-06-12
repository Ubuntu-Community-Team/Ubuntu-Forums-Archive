---
title: "Gutsy: Festival text-to-speech system - can you check it."
date: 2007-10-28
forum: General Help
---

### Post by moma on 2007-10-28
Hello,

I have used the Festival text-to-speech-generator in Feisty where it worked out of the box but in Gutsy it just reports an error.

Before I bug report it, can you check if it works on your Ubuntu 7.10.

Install festival 
$ [COLOR="SeaGreen"]sudo aptitude install festival [/COLOR]

Test it
$ [COLOR="SeaGreen"]echo "Hello mrs Simpson. How are you?" | festival --tts[/COLOR]

In my case it reports.

[COLOR="DarkOrange"]WARNING
No default voice found in ("/usr/share/festival/voices/")
either no voices unpacked or voice-path is wrong
Scheme interpreter will work, but there is no voice to speak with.
WARNING
-=-=-=-=-=- EST Error -=-=-=-=-=-
{FND} Feature Token_Method not defined
-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-[/COLOR]

See also: [http://ubuntuforums.org/showthread.php?t=291919&highlight=TTS](http://ubuntuforums.org/showthread.php?t=291919&highlight=TTS)

---

### Post by moma on 2007-10-28
I had to install a voice (language) file for it.  I installed
festvox-don

These were in the Ubuntu's repository:
festvox-don - minimal British English male speaker for festival
festvox-ellpc11k - Castilian Spanish male speaker for Festival
festvox-rablpc16k - British English male speaker for festival, 16khz sample rate
festvox-rablpc8k - British English male speaker for festival, 8khz sample rate
----------

Anyway, it's a tiny bug.
the Festival package should have installed a default language and voice. Festival is useless without it.

---

### Post by xlinuks on 2008-02-03
A bit late, nonetheless it's still true, and I totally agree with you.

---

