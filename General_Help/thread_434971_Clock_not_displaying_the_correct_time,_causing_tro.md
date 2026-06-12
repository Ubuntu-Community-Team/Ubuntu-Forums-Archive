---
title: "Clock not displaying the correct time, causing trouble"
date: 2007-05-06
forum: General Help
---

### Post by EmperorSquirrels on 2007-05-06
Hi, my clock is displaying an hour behind and I can't seem to fix it. When I go to "adjust date and time" a blank window appears that takes several minutes to load, and then I can't even really fix anything on it. I had it set to the correct time previously, but it seemed everything thought I had my clock set an hour ahead, rather than having it set to the actual time (Like Last.fm was reporting that I would be listening to songs 'in 54 minutes' and so forth).

Whenever I type date into the terminal it reports this:
```
Sun May  6 12:15:56 MDT 2007
```

Whereas it is actually 1:16pm CDT or whatever the code is for American Central time.

Any help?

---

### Post by benn333 on 2007-05-06
I'm guessing that blank window that's taking forever to load is the prompt to type your password for sudo access. I couldn't tell you why that's happening, but here's how to change the time from the command line:

sudo date MMDDhhmmYY

For example, May 6, 2007 8:24pm would be:

sudo date 0506202405

If it continues to jump back, check the time setting in your BIOS, including any daylight savings time settings. If possible that's were Ubuntu is getting the incorrect time from.

---

### Post by kerry_s on 2007-05-06
I think it was the tzdata update that screwed it up.
run> sudo tzconfig
and ntpdate should keep it set from there.

---

### Post by EmperorSquirrels on 2007-05-06
Well the system time was on hour 19 when it should have been on 14. I used the date command and changed the time, and it looks like everything is working. Got the right time, Last.fm is getting the correct time of play reported.... thanks :)
I'd have never through to check the BIOS.

---

### Post by EmperorSquirrels on 2007-05-06
Okay never mind it's not working. I think it's the time zone problem. How do I change the time zone from MDT to CDT? I have it set on America/Denver right now because I thought that was -6:00 like it is where I live.

---

### Post by EmperorSquirrels on 2007-05-06
Never mind. Fixed it right this time :)

---

### Post by kerry_s on 2007-05-06
Read my post!

---

