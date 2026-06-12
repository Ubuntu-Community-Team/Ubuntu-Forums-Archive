---
title: "ALSAMIXER and PulseAudio"
date: 2020-05-22
forum: General Help
---

### Post by yegnal on 2020-05-22
In 18.04 I did some looking around to solve an issue with being able to leave my headphones plugged into the front of the case on a tower, and then be able to switch between headphones and speakers simply by selecting the desired output in settings. 

[https://askubuntu.com/questions/712517/how-to-switch-between-headphones-and-speakers-without-unplugging-headphones](https://askubuntu.com/questions/712517/how-to-switch-between-headphones-and-speakers-without-unplugging-headphones)

Now in 20.04, it's close but no cigar.

If I choose headphones, they come on but the line out speakers remain on.  I have to open alsamixer and turn on auto mute.  

It I then choose speakers, I have to open alsamixer and disable auto mute.

The .conf files referenced in the link I used in 18.04 above contain very similar entries to what I see in my new 20.04, but not exactly.  I can't follow the advice from that previous post, i.e. there is no entry named [front headphones] and there are many named 'phantom' and it's just not the same apparently.

Making the edits I can do, and I know it's probably a relatively easy fix, but I don't exactly understand the working enough to go it alone.....

---

