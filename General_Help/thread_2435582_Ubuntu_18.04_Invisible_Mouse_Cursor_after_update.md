---
title: "Ubuntu 18.04 Invisible Mouse Cursor after update"
date: 2020-01-22
forum: General Help
---

### Post by gameweasel1964 on 2020-01-22
Hey all
Kinda new to Ubuntu so bear with me.

I have had Ubuntu 18.04 installed and running just fine for about 3 months now. This morning I installed an update, and upon reboot my mouse cursor turned invisible.
The mouse is still working, I can highlight icons on the toolbar with it by moving it all the way to the left and when I click on them they open, but there is no visible mouse cursor.
I have tried various things I found online all to no avail.

This is installed on a Dell PowerEdge T140 server and is running the Gnome desktop with the Ubuntu video driver.

Any Ideas???

---

### Post by francogp on 2020-01-23
I have the same problem on my 2 HP servers. I update on Monday 23 (January). And now both servers have invisible mouse.

---

### Post by jon123456 on 2020-01-23
I also updated today (January 23rd, 2020), and now the cursor is invisible on all three of my Dell PowerEdge R815 servers.

---

### Post by jon123456 on 2020-01-23
I have found a solution that brings back the cursor. This is a problem that seems to affect servers like the Dell PowerEdge.

[https://www.reddit.com/r/Ubuntu/comments/dugjdv/ubuntu_v1804_1910_desktopserverstudio_mouse/f7alvgd/](https://www.reddit.com/r/Ubuntu/comments/dugjdv/ubuntu_v1804_1910_desktopserverstudio_mouse/f7alvgd/)

"[COLOR=#1A1A1B][FONT=&amp]Open terminal (Keyboard shortcut for this is CTRL+ALT+T)[/FONT][/COLOR][COLOR=#1A1A1B][FONT=&amp]Open /etc/default/grub in your preferred text editor (e.g. sudo nano /etc/default/grub)[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]Change the line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]Save the file and run sudo grub-mkconfig -o /boot/grub/grub.cfg[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]Then reboot. That should give you workable graphics until a solution is found."[/FONT][/COLOR]

---

### Post by iamjim61 on 2020-01-26
This worked for me, thank you! I've spent hours today trying different things.

---

### Post by CelticWarrior on 2020-01-27
```
[COLOR=#1A1A1B][FONT=&amp]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"[/FONT][/COLOR]
```

This is not a solution, it's a temporary workaround as any other usage of 'nomodeset' (disables graphics drivers).

---

### Post by the23flavors on 2020-02-04
I have a Poweredge R510, I got the update to 18.04.04 LTS and I also cannot see my mouse cursor. No other faults. 18.04.03 worked fine.

---

### Post by gameweasel1964 on 2020-02-10
Had to re-install 18.04 because of another issue on one for my Dell servers. Everything worked just fine, and I got the mouse cursor back. So I decided to try the update again to see if the issue had been resolved.

NOPE

Mouse cursor disappeared again. This has happened on all 3 of my Dell PowerEdge servers.
I tried the above work-around but no go on bringing the mouse cursor back.
So I re-installed again with no update.

Should I have filed a bug report???

---

### Post by mawarschool on 2020-02-15
I confirmed that after update, the mouse went invisible. I re-installed 18.04 mouse appeared, but after updating the mouse went invisible again. I have re-install the ubuntu again. I would leave the update alone, until Ubuntu has found the fix to the mouse problem.

---

### Post by GZaha on 2020-02-15
> **gameweasel1964 said:**
> Had to re-install 18.04 because of another issue on one for my Dell servers. Everything worked just fine, and I got the mouse cursor back. So I decided to try the update again to see if the issue had been resolved.

NOPE

Mouse cursor disappeared again. This has happened on all 3 of my Dell PowerEdge servers.
I tried the above work-around but no go on bringing the mouse cursor back.
So I re-installed again with no update.

Should I have filed a bug report???

I really would appreciate if you do.... Spent countless hours to try to fix this... In a PowerEdge R710. Thanks!

---

### Post by the23flavors on 2020-02-15
Since the last time my cursor disappeared, I started from scratch, reinstalled 18.04.03, and it worked on a Dell R620. I came back to the machine the next day, my cursor was gone again. I had not updated the machine manually. 

I have since then tried updating everything, and nothing has fixed the missing cursor.

edit: I submitted a bug report.

---

### Post by mörgæs on 2020-02-16
In stead of reinstalling 18.04 has anyone tried installing 19.10?

---

### Post by the23flavors on 2020-02-17
I haven't tried it yet, I was hoping to stick with LTS.

---

### Post by mörgæs on 2020-02-18
LTS is an abbreviation for 'museum for old bugs'.
Better to test a number of alternatives before deciding what to use.

---

### Post by the23flavors on 2020-02-20
Thank you for the advise. On LTS I pulled an update today, restarted the machine, and now the mouse cursor is back. So I won't have to try your fix.

---

