---
title: "SkypeIn Ringing Problem"
date: 2005-04-23
forum: General Help
---

### Post by dqsis on 2005-04-23
Hello Ubuntu Friends! 

Recently I bought a SkypeIn number (IP telephony provided by Skype). 

When I call the number, my computer doesn't ring at all and I even don't get any screen notification. 

Do you have similar problems?  :???: Any solutions?

ps. I tried playing around with settings but nothing changed! All the right ones seem to be ticked!

ps. I should mention, that everything else works perfect with Skype!

Thanks in advance!

---

### Post by mduduzi on 2005-04-28
[QUOTE=dqsis]Hello Ubuntu Friends! 

... 

When I call the number, my computer doesn't ring at all and I even don't get any screen notification. 

Do you have similar problems?  :???: Any solutions?
....

Thanks in advance![/QUOTE]


Yes, I had a similar problem when I was using Novell/SuSE 9.2 Professional AMD64. What is strange is that it worked well at first. But after my CUPS was messed up and having resorted to using the install CD's automatic repair functionality, I had the problem like you've discribed.
Now I'm not even getting to install Skype -despite following the guideline suggested on:  [http://ubuntuforums.org/showthread.php?t=16143](http://ubuntuforums.org/showthread.php?t=16143) .
MMK.

---

### Post by stevenyu on 2005-04-28
anyone having issues with sound delay and static noise when using skype in ubuntu?  is there a setting like buffer for the sound? ](*,)

---

### Post by davegahan on 2005-04-29
Try ALSA sound system, you select that in system - preferences - multimedia systems selector. Changing to ALSA solved my skype problems (huge latency, infinite loops, etc....). Took me weeks to find one out. Now Skype works without a glitch.

---

### Post by ozorba on 2005-04-30
[QUOTE=davegahan]Try ALSA sound system, you select that in system - preferences - multimedia systems selector. Changing to ALSA solved my skype problems (huge latency, infinite loops, etc....). Took me weeks to find one out. Now Skype works without a glitch.[/QUOTE]

I have tried ALSA with my computer and I lost sound. The only way I can get my one working is vias ESD. It's a pity that Skype does not work on my system. I woud have removed Windows on my system if I did not have problem with Skype.

---

### Post by davegahan on 2005-05-01
Check the following site if your sound card is supported by ALSA 

[http://www.alsa-project.org/alsa-doc/index.php?vendor=All#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=All#matrix)

ALSA works fine on my notebook......

---

