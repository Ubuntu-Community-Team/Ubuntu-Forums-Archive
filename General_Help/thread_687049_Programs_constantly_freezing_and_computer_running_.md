---
title: "Programs constantly freezing and computer running slow"
date: 2008-02-03
forum: General Help
---

### Post by Thyzer on 2008-02-03
I'm running Ubuntu 7.10 (gusty gibbon) on a Dell Inspiron 1521 laptop. Up until a few days ago I was not having any problems. Now I am having problems not just with specific programs, but all programs, constantly freezing. It's usually not permanent, but they will gray out, and then come back in a few seconds. It usually is happening when the computer is loading something. But for whatever reason, it seems to be constantly loading something - the little loading light next to the power light is on, and it is just about always making that loading noise (as you can probably tell, I know little about computers). So having programs freeze up when the computer was running slow, or loading a lot, would not be a problem if it didn't always seem to be busy, and thereby always running slow. It's behaving much as a old computer running Windows would: when I try to switch between applications there is a lag, drop down menus are taking a couple seconds to appear, it will take a few seconds for programs to close, text won't always appear as i type it, but rather lag, and then appear real quick a couple seconds later. Basically all the things an old slow computer would do. This started happening very suddenly, I was not having this problem a few days ago, and I've been running quite a few of the desktop effects. I turned most of them off now, and it hasn't really helped.

The only things that I've changed were installing Kopete and Limewire, though I haven't downloaded any programs, just media (audio/video etc.), and I'm under the impression there isn't really the problem with spyware that there is on windows, which was one of my reasons for switching to linux a month or so ago.

Any thoughts?

---

### Post by Thyzer on 2008-02-03
So after posting my last post a few minutes ago, I looked up how much RAM was being used, and discovered that 91% of my GB of RAM was being used (officially 1gb, the computer tells me it has something like 879). so i searched through the list of processes, and found that there was a process named trackerd taking 527mb of ram. I stopped the process, and the computer finally stopped the little loading noise, for the first time in all of today. My computer is running a bit better with that process stopped, since it seems to have some of its processing power back; with some experimenting of switching back and forth between programs, and giving quick commands, it still seems to be having the freezing problem, but that may be due to the fact that I still have very little ram left since I didn't end the trackerd process, only stop it.

My question now becomes how do I find out what this trackerd program is and what is it doing? I'm assuming its malevolent, or at least not working for me, but I want to know how to get rid of it, so I don't have to end the process every time I use the computer.

---

### Post by bran on 2008-02-27
System > preferences > Sessions and uncheck the tracker on the startup tab.

still looking for a solution to the grey out stalls on all sorts of programs after killing tracker though.  seems to be related to Xorg frome watching top in a terminal.

Bran

---

