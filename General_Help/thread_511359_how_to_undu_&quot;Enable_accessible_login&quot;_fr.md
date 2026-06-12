---
title: "how to undu &quot;Enable accessible login&quot; from terminal"
date: 2007-07-27
forum: General Help
---

### Post by lcolson on 2007-07-27
I was trying to get the option of choosing between picking kde and gdm at start Linux start-up, like I've heard some people mentioning, so I looked for check boxes that seemed that they might do the trick and checked the "Enable Accessible Login" box under the "Accessibility" tab in the "Login Window Preferences", which is accessible under the "Administration" tab under the "System" tab on the desktop.  

Well, as many of you probably know, this was not what I wanted to do.  When I start up my computer now, I get to grub, pick to use Ubuntu, and then it never loads.  

So, my question is, how do I uncheck " the "Enable Accessible Login" box from the "command prompt" start-up option (yes, I know Linux has another word for it but I don't recall it)?

P.S.  I'm going out for the weekend and will check back on Sunday, so I won't be responding immediately to anything posted here.

---

### Post by rockey3 on 2007-07-27
> **lcolson said:**
> I was trying to get the option of choosing between picking kde and gdm at start Linux start-up, like I've heard some people mentioning, so I looked for check boxes that seemed that they might do the trick and checked the "Enable Accessible Login" box under the "Accessibility" tab in the "Login Window Preferences", which is accessible under the "Administration" tab under the "System" tab on the desktop.  

Well, as many of you probably know, this was not what I wanted to do.  When I start up my computer now, I get to grub, pick to use Ubuntu, and then it never loads.  

So, my question is, how do I uncheck " the "Enable Accessible Login" box from the "command prompt" start-up option (yes, I know Linux has another word for it but I don't recall it)?

P.S.  I'm going out for the weekend and will check back on Sunday, so I won't be responding immediately to anything posted here.

Hey folks I think I have the same problem. 
I was customizing and I think I hit that tab by accident.  When I shutdown and tried to restart ubuntu does not load completely.  I just get that circular loading mouse pointer and it goes nowhere.  I hit a bunch of random buttons on the keyboard and it asks for my username and pw.  After I enter that I get a command prompt/terminal.  I want it back to normal and have no clue what to do. I need help!! Contact me here or even better over the phone RJ 3017920590

---

### Post by dcstar on 2007-07-28
> **lcolson said:**
> I was trying to get the option of choosing between picking kde and gdm at start Linux start-up, like I've heard some people mentioning, so I looked for check boxes that seemed that they might do the trick and checked the "Enable Accessible Login" box under the "Accessibility" tab in the "Login Window Preferences", which is accessible under the "Administration" tab under the "System" tab on the desktop.  

Well, as many of you probably know, this was not what I wanted to do.  When I start up my computer now, I get to grub, pick to use Ubuntu, and then it never loads.  

So, my question is, how do I uncheck " the "Enable Accessible Login" box from the "command prompt" start-up option (yes, I know Linux has another word for it but I don't recall it)?

P.S.  I'm going out for the weekend and will check back on Sunday, so I won't be responding immediately to anything posted here.

Looking at the Help file, any changes are stored in /etc/gdm/gdm.conf-custom, so log in to a terminal and do:
```
sudo nano /etc/gdm/gdm.conf-custom
```
to have a look around in that file.

When I select that "Enable Accessible Login", the following seem to be added in that file:
```
GtkModulesList=gail:atk-bridge:/usr/lib/gtk-2.0/modules/libkeymouselistener:/usr/lib/gtk-2.0/modules/libdwellmouselistener
AddGtkModules=true
```
so deleting them (or commenting them out) should fix it.

---

### Post by lcolson on 2007-07-29
Thanks dcstar, that solved the problem.:)

---

### Post by rockey3 on 2007-07-30
dude thank you sooo sooo much it worked

---

