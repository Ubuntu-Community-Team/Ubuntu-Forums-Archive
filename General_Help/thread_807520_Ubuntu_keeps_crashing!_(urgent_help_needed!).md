---
title: "Ubuntu keeps crashing! (urgent help needed!)"
date: 2008-05-25
forum: General Help
---

### Post by illbashu on 2008-05-25
Ubuntu keeps crashing after i use it for like 10 min :( this just started happening i have no clue why, because it was running pretty smooth until like yesterday :(

---

### Post by pixel :-) on 2008-05-25
hmm random crashes?Check your memory with mem test.An option at boot time.

Tel us your specs,any whay.You run Windows side buy side,does it has problems?What video drive do you use?

---

### Post by illbashu on 2008-05-25
i dont run windows, 

756.9mb of ram, 110.6gb free hard drive space 

i have a gt 5500 video card i think, 5500 or 5100 cant remember.

---

### Post by pixel :-) on 2008-05-26
If it's complitly random it could be hardware.

Have installed something since then?Upgraded your video drive?remove it.You have automatic upgrade on?You installed new hardware?

At boot time,select recovery mode,and check for the default video mode or vesa (don't remeber the exact name).This will disable you video card and hopefully stop the crashes.

Reinstal the kernel and your video driver.Can you afford complite reinstall?Something could have gotten corrupted.

---

### Post by illbashu on 2008-05-27
i booted it up again and now its runing fine! i am scared to turn the comp off now :/

---

### Post by Zip247 on 2008-05-27
I started having the random crashes yesterday after updating to the 2.6.24-17 kernel.  Re-booted to the -16 kernel and 10 min later...crash.  

I was playing a flash based game at the time of all of the crashes, but I have played the same game many many times before and did not have a crash.  

Any suggestions?  If you need info just ask and I will try and get it for you.

---

### Post by illbashu on 2008-05-27
i had to restart my comp and now its happening again :'(!! HELP!

memory test didn't find anything. :(

---

### Post by PadreSol on 2008-05-27
What do the /var/log/ logs say? Any clues?  Any common thread to when the crash occurs? Is it while playing flash games or just anytime? Is the browser running? Email? Etc., etc. Have to try to narrow it down. If you find that you can't narrow it down it might be a hardware problem. Is the CPU fan working properly?  The system is not overheating is it?

---

### Post by illbashu on 2008-05-27
sometimes when i boot up the comp it says like error ati3 or something like that..

how do i see /var/log/logs

---

### Post by illbashu on 2008-05-27
sometimes when i boot up the comp it says like "88 ati3...." or something like that and its useally when its trying to load up the hardware driver..

how do i see /var/log/logs

---

### Post by PadreSol on 2008-05-27
> **illbashu said:**
> sometimes when i boot up the comp it says like "88 ati3...." or something like that and its useally when its trying to load up the hardware driver..

how do i see /var/log/logs

Open a term window Accesories->terminal
cd /var/log
grep ati3 *

You really haven't provided enough info to allow anyone to help you.

---

### Post by illbashu on 2008-05-27
what kind of info do you need?

---

### Post by Zip247 on 2008-05-27
Mine seems to only crash when playing a flash game.  I have used my laptop for a while today with no crashes.  The odd thing is that I have played the same flash game many times for many hours with no crashes and then all of a sudden....crash, and now it seems to happen about ten minutes into playing the game.  

I hear my fans going, but my laptop does get much hotter when playing the flash game then any other time.  It may be a heat issue.  I will just have to monitor my pc and try and figure out exactly what is happening when it crashes.  Maybe its just coincidence that the crashes started happening right after I updated to 2.6.24-17 kernel.  There were some Toshiba acpi updates associated with the update.  

I will keep all informed.

---

