---
title: "LUBUNTU Closing Windows and after restarting Lubuntu hour is changed to less 2:30"
date: 2020-07-31
forum: General Help
---

### Post by aug7744 on 2020-07-31
Closing Windows 10 and restarting the machine and starting Lubuntu the hour allways changed to less 2 hour and 30 minutes and when restarting to Windows the hour is back to correct hour. I had installed Lubuntu with machine date 12-07-2019 and 17:20 and finishing the installation the date was changed to 04-01-2020 and the hour also, but I not remember the hour value changed. How to fix it ? Thanks for reply.

---

### Post by guiverc on 2020-07-31
Ubuntu (including Lubuntu) by default sets the system clock at UTC/UST/GMT/zulu/internet time, regardless of where you are in the world (as it's the same everywhere in the world).  This is the time used for all internet traffic/dating, and is also used by all android phones, apple phones &  computers, unix computers, and more.

Windows however doesn't use that by default, modern windows uses the local time set during installation, with the internal system clock requiring change when you move timezones (rather than the OS just calculating differently what is shown on the screen as you change timezones).  

Both OSes can use each format, but they have different defaults.  My guess is your timezone is 2.5 different to UTC; if it's not that, my assumption maybe invalid.

You need to make them both use the same system clock setting, for Lubuntu please refer to the manual on changing it , [https://manual.lubuntu.me/stable/3/3.2/3.2.4/date_and_time.html?highlight=setting%20clock](https://manual.lubuntu.me/stable/3/3.2/3.2.4/date_and_time.html?highlight=setting%20clock)

(I have no idea how to change that in windows, but all OSes need to use the same default or you'll have issues whenever you switch... Windows differs to others)

---

### Post by aug7744 on 2020-07-31
I had knowledge about Linux using UTC. I will try change settings. In my beginner experience Linux is much better than windows. Have less components to configure, but unhappily some components is more work to configure than windows that for me had that have an alternative for thus help novice computer users to switch to Linux. Is how Linux developers love challeging users with commands and in other side I understand that is for user have control about the system, but had that be more simple.

---

### Post by CatKiller on 2020-07-31
> **aug7744 said:**
> Is how Linux developers love challeging users with commands and in other side I understand that is for user have control about the system, but had that be more simple.

This forum is a text-based communication method, and we're all using different desktop environments, different versions, different themes. **Of course** we're going to provide commands that users can copy-and-paste, and whose results users can copy-and-paste for more information, when people request help. That doesn't mean that it's the **only** way to achieve something.

---

### Post by guiverc on 2020-07-31
> **aug7744 said:**
> but unhappily some components is more work to configure than windows that for me had that have an alternative for thus help novice computer users to switch to Linux. Is how Linux developers love challeging users with commands and in other side I understand that is for user have control about the system, but had that be more simple.

When I first learnt computers, it was with cards, which you just hoped you never dropped (the deck was worse than useless in the wrong order).

To later get to commands was a HUGE step forward, though fighting to get terminal time became the issue (and hope you could get your work done in the time you had allotted the teleprinter/terminal).  GUIs (graphical user interfaces, which appeared in the late 1970s, though weren't affordable & thus commonplace till long after that) just allowed more people to use the machines, but didn't improve efficiency in my opinion anyway.  GUI also generally misses the power *technical* commands provide.

Commands are how I think, because I find them far  more efficient. When I'm fixing problems on windows computers, I usually drop to *powershell* there too (and wonder if microsoft let * powershell* be named by a marketing person..). 

The link I provided was for GUI operation, and was written by someone how writes much better than I do. How I write, sorry that's just me.

---

### Post by aug7744 on 2020-08-13
Configured correctly now.
Thanks for all replies :)

---

