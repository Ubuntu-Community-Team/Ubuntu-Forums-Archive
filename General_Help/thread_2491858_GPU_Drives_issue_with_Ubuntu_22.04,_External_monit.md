---
title: "GPU Drives issue with Ubuntu 22.04, External monitors freeze"
date: 2023-10-23
forum: General Help
---

### Post by alexhalo3115 on 2023-10-23
Hello, I am currently having an issue that if I were to connect my laptop to  a external monitors, the external monitors completely freezes. I can  still move the cursor and the monitor on my laptop works fine but it is  still pretty annoying and i have to turn off and on my laptop for this  to fix it self, unplugging and plugging it back it does not work.


 My laptop is a Lenovo legion pro 7 4070 gpu and i9 13th gen I believe I have two external monitors, one plugged in via HDMI and one via USB -C


 To be honest i am not 100% sure if this is a drivers issue, i have  gone to the software and update app to change drivers for the graphics  card and issue still persists


 I have reinstalled ubuntu twice and once completely erased the  partition to do a full restart (i am dual booting and i have 0 issues on  the Windows 11 end)


 The only reason i use ubuntu is for software development and having a  2nd and 3rd monitor is kind of important to me, so you can imagine that  the only things i have installed are VSC and Spotify basically.


 These freezes occur at any instance and this is a list of times it has happened so far:
 
[LIST]
[*]run a local server using npm start (website with phaser instance running)
[*]run a rust program with cargo run (i was running the bevy game engine)
[*]opening up a visual studio window after it has been minimized
[*]changing video on youtube (i don't remember if this is when i tried to maximize the video window)
[*]
[/LIST]
 I cant really see a pattern to be honest in what could cause this  issue. Maybe the fact that all 4 instance is where the GPU sort of gets  utilised lead me to believe is a GPU driver issue...



 There was a period where this didn't happen and then since the 19th  of October 2023 i did a system update and it started doing it again. I  have since reinstalled ubuntu but the issue persists.


 I tried to give as much info as I could, if there is something that I  missed or its needed pls ask, I would love to use my second monitor.  Coding with only one monitor is a pain in the ass :)
 Thanks in advance, I really do appreciate it.

---

### Post by #&amp;thj^% on 2023-10-23
Can we also see this:
```
prime-select query
```
Ok I just saw Windows also, so is secure boot set to off?

---

### Post by alexhalo3115 on 2023-10-24
Hey,

I tried to run that code in my terminal and is says on-demand

as for the secure boot off thing i am not 100% sure what that is but from what i could find on google something about the bios so i would say i havents touched anything in there, like i said i am dual booting so when i first start my laptop it asks me if i want ubuntu or windows

---

### Post by app20 on 2023-10-30
I have the same problem after the latest nvidia driver update
Looks like we just have to wait for them to notice and roll back the changes

---

