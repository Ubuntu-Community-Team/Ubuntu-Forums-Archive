---
title: "I need urgent help"
date: 2016-10-14
forum: General Help
---

### Post by dompughter on 2016-10-14
Okay so earlier I kept getting a pop up saying I was having system issues. And i decided that maybe if I went to my system settings, clicked on 'details' and then 'install updates' it would update the system and maybe fix the issue because I wasn't sure what the issue was. So I update it and it installs and ask to restart my computer so I do but then things go really weird. During the loading screen I got 5 red loading dots that appeared on my screen before I was promoted to login. After i logged in I noticed my appearance was reverted back to normal. My side panel was enlarged. My top bar was black instead of clear like I set it. My system settings are the same as I set them to be but the appearance is not as it should be. My internet, both ethernet and WiFi aren't working anymore, none of my computer ports are working. My usbs, hdmi, my touch screen(it's a 2 in 1 laptop), my multi-touch on my TouchPad. None of that is working anymore. I've been using my phone to look on the internet for solutions but I can't find anything. I'm using Ubuntu 16.04 LTS. If anyone could help me on this issue that would be great! I'm like panicking because I can't do much with my computer at the moment.

---

### Post by howefield on 2016-10-14
Might help to know which updates you applied. Open the apt history.log file in a text editor and post the information about the last update(s) that you applied.

```
/var/log/apt/history.log
```

---

### Post by ajgreeny on 2016-10-14
Use command **uname -a** to see what kernel are you using when you have that problem as it looks as if there was a new kernel in normal updates, dated 10th Oct (4.4.0-42.44) and then another one, (4.4.0-43.63) yesterday or today, so I wonder if there was a problem with the 4.4.0-42.44 kernel that arrived on the 10th as kernel updates so close together are unusual.

See if booting to a previous kernel, eg 4.4.0-38, from the grub menu and then updating again, assuming you get a network connection with that, solves your problem when the 4.4.0-43.63 version is installed.

---

### Post by dompughter on 2016-10-14
Thank you! This worked. I had to do some side searching on how to figure out how to access the grub menu, but I found out and booted from a previous update. And then while booted under the previous update, I re-downloaded the new updates, restarted and the new update worked just fine! Thanks a bunch!

---

### Post by ajgreeny on 2016-10-14
Great! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

I have no idea what went wrong with the 4.4.0-42 kernel but I note there have been a few problems over the last two or three days similar to yours and it was purely by chance that I noticed new kernel versions arriving so closely together.

---

