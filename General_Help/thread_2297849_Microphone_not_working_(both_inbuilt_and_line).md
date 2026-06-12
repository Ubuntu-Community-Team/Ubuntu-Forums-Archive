---
title: "Microphone not working (both inbuilt and line)"
date: 2015-10-07
forum: General Help
---

### Post by thddev on 2015-10-07
Hello everyone !
I just installed Ubuntu 14.04 on my Dell Optiplex 780 machine. I am unable to use Skype/Hangouts because mic does not work. I tried the inbuilt mic, and tried a line mic in both front and rear panels.
When I go to  System Settings -> Sound, I can see inbuilt and line mics in the input section. When I speak, the meter indicates the amplitude too (although the inbuilt mic is showing very low intensity)
When I run
 ```
arecord -vv -fdat recording.wav
```
I see the meter feedback, but on playing back the recorded sound, I only hear noise of low intensity. There is no problem in the speakers as I can listen to other system sounds and music.
I have run the alsamixer command and set everything to 100%, including boost. But no luck.

I talked to Dell support and was told Dell does not support Ubuntu. I am sharing all the info related to my machine, please help.  The three configurations are ( text file size is exceeding forum limits, so added links to pastebin) :
 (a)[without external/line mic, only inbuilt mic]("http://pastebin.com/8daEvDAE")
(b)[with line mic in front panel ]("http://pastebin.com/zE6Xycpb")
(c)[with line mic in rear panel]("http://pastebin.com/E1vrHRRE")

Thank you !

---

