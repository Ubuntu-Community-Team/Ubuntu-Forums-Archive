---
title: "Lubuntu 18.04 LTS now upgraded?"
date: 2020-07-21
forum: General Help
---

### Post by anap on 2020-07-21
I use Lubuntu 18.04 LTS. Today 21st July the whole look and usage of my install changed. I have lost the task bar, the short cuts have changed.. I have tried make the shorcuts as they were; ctrl+right arrow , ctrl+left arrow for instance, they were to switch workspaces, I have manually set them for that now, but they don't work, I press those keys and they simply don't do anything, after setting them up on the settings-devices-keyboard.

I have also lost the graphic way of minimising, maximising and resizing. And the desktop. And the menu, now it is 'activities'...
Is there any way to go back to how it worked?
Thank you...

---

### Post by guiverc on 2020-07-21
My thoughts.

 I can't imagine a way of how upgrades would cause you to loose panel (what I assume you mean by task bar, a screen-picture may help; ideally with pointer).

More likely though to me is if you've logged into a different session, "Openbox" for example, as no panel will be visible then (openbox has no panel, as that's provided by pcmanfm which is part of LXDE).

The 'activities' reference makes me think of GNOME??  Have you logged into a different session? Openbox is included with a Lubuntu install, a GNOME session however requires you to add packages.

Either way (at least with where my mind has gone), I'd logout  (if it's openbox, right click of the background should make a menu appear allowing logout) and return to the greeter (or `lightdm`) Up near the top right you'll have a number of icons; (from right to left) power, accessibility*, session. It's the session I'm proposing you've somehow logged into.  Switch it back to Lubuntu (which is LXDE + Openbox on 18.04 LTS)

There are other alternatives I can think of (you've chosen themes not suited to GTK2/LXDE, which usually aren't noticed in the session of the change, but on next login). If you made changes to appearance in the prior session before this problem, providing details of that may help

*accessibility maybe the wrong term I suspect; it's a term like that

---

### Post by anap on 2020-07-22
> **guiverc said:**
> My thoughts.

Thank you

>  I can't imagine a way of how upgrades would cause you to loose panel (what I assume you mean by task bar, a screen-picture may help; ideally with pointer).

Yes, sorry. The task bar is what I meant. I am (trying to) attach a screenshot. The task bar there, I have put since I posted this; the black 'hole' is what remains of each program I hover over ... I spent a few hours trying to figure out different extensions where that wouldn't happen, I thought I had solved that but there it is.
Usually my task bar would be on the bottom of the screen. it is not there now, and as I said the faulty one I have now is an extension to gnome I installed after some research.

What needs fixing though, is, the fact that the desktop changed at all, which you seem to assume was of my own doing.

> More likely though to me is if you've logged into a different session, "Openbox" for example, as no panel will be visible then (openbox has no panel, as that's provided by pcmanfm which is part of LXDE).

The previous time I used my computer, I switched it off normally, I don't usually 'log off' sessions. I am the only person using this computer, so only one user name, one session. I switch it on, work, then switch it off. The next morning, I switch it on again, put in my password (my user name is already there) and this happened. The whole desktop changed.


>  The 'activities' reference makes me think of GNOME??  

Exactly!! I have now checked the "about" and not only am I using gnome and not Unity, as I was before this happened. In the "About" section, it tells me I am using Ubuntu! and not Lubuntu which is what I downloaded and have been using for about four years.

> Have you logged into a different session? 

As I said above, no, I don't use different sessions for the different time I switch on my computer.

>  Either way (at least with where my mind has gone), I'd logout  (if it's openbox, right click of the background should make a menu appear allowing logout) and return to the greeter (or `lightdm`) Up near the top right you'll have a number of icons; (from right to left) power, accessibility*, session. 

I'm afraid it doesn't. It only gives me the options: Cancel, Restart, Power Off

It was Lubuntu 18.04, now it is Ubuntu 18.04, I am told it may be time to wipe the whole hard drive off, and make a clean re-install, so that I should do.

Only, I was going to do it with the option that was on the main menu, "create a bootable pen drive", but now I have also lost that menu, I would be thankful for pointers there too.

But thank you very much for taking the time to think iinto this and write a possible solution

---

### Post by guiverc on 2020-07-23
> **anap said:**
> I spent a few hours trying to figure out different extensions where that wouldn't happen, I thought I had solved that but there it is.
Usually my task bar would be on the bottom of the screen. it is not there now, and as I said the faulty one I have now is an extension to gnome I installed after some research.

What needs fixing though, is, the fact that the desktop changed at all, which you seem to assume was of my own doing.

Lubuntu 18.04 uses LXDE, which uses GTK2, so your use of *extensions* has me wondering what you mean. GNOME hasn't used GTK2 in about a decade (11.04 as I recall used 2.6 in classic), so if you're talking GNOME3 extensions I would expect them to create problems.

> **anap said:**
> The previous time I used my computer, I switched it off normally, I don't usually 'log off' sessions.

I'm about the only person using this machine, and if by switch off normally you mean going through menus and selecting shutdown, or doing the same via command that's fine.


> **anap said:**
> Exactly!! I have now checked the "about" and not only am I using gnome and not Unity, as I was before this happened. In the "About" section, it tells me I am using Ubuntu! and not Lubuntu which is what I downloaded and have been using for about four years.
..
It was Lubuntu 18.04, now it is Ubuntu 18.04

If you've been adding GNOME (3) extensions to your system, I'd not expect you to be using Lubuntu/LXDE anymore, as they're not compatible, and to make them work, you'll have needed to add Ubuntu packages to your system meaning it's multi-desktop (which my own is) and you select at the greeter/DM login screen. 

 Logout and have a look at the login screen, the session option should be there, however where it appears will depend on which DM you're using (you've pulled in GNOME packages to add what sure reads like GNOME3 extensions which may have switched the DM too).

Re-read my first comment, as your last reply just confirms what I said there, except it reads now you didn't intend to add other desktops, just did so in order to use extensions built for other desktops (thus package tools complied with your comomands & did it as they needed to).

Having multiple DESKTOPS installed isn't a problem, my own desktop started as a Ubuntu install (GNOME), on which I added XFCE (Xubuntu), LXDE (Lubuntu), & MATE (Ubuntu-MATE). The LXDE changed to LXQt during upgrades, XFCE switched from GTK2 to GTK3, and I removed MATE as I was running out of disk space.  I made my system by choice, I think however you got there without realizing consequences of your decision.

Details such as what extension, how it was added (commands can be obtained from your command `history`, or packages via logs (/var/log/apt/history.log for example) would allow me to provide more facts instead of theory/belief.

---

### Post by anap on 2020-07-24
Solved this. The automatic updates did this, I guessed as much. On the first screen on switch-on, where the password is required, there are a few icons right top of the screen. The one next to the human figure is an 'unfoldable' menu for desktop 'flavours' or options. I could choose the lubuntu desktop and voilâ, now I have my old desktop and all my old shortcuts and notifications settings. Thank you so much to bita who told me exactly where to look [https://sindominio.net/bita](https://sindominio.net/bita)

---

