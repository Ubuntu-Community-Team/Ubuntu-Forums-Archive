---
title: "[SOLVED] GCompris broke Gnome (with my help)"
date: 2007-08-29
forum: General Help
---

### Post by Neilor on 2007-08-29
Long story ... short:

I installed GCompris from the package manager last night, everything looked okay... went to the applications menu and found the Education / GCompris Config option... went in, set up my daughter's name and selected some apps... went to log out and see how things looked under here account... and *bang* problem..

Gnome looked like it was logging in but I didn't see the usual Nautilus splash graphic/progress icons. After a couple of minutes the top left quadrant of the screen turned into something looking like a terminal screen (mouse changed to text cursor when I moved over it)... but completely unresponsive to input. I left this screen run for about 10 minutes in case it was doing some setup/mods of Gnome menus... but nothing happened.

Okay not so bad I thought, so I tried my own account, and yes you guessed it same thing... all accounts on the system logging into Gnome give me this semi-terminal screen and hang there.

I then proceeded with the following steps from a terminal login (none of which made a difference):
1. Gnome safe mode (no scripts) login.
2. Uninstalled GCompris
3. Complete remove of GCompris
4. Install edubunutu-desktop (thinking GCompris was missing some dependencies)... removed it again.
5. Moved .gnome*, .nautilus directories from HOME$
6. Reinstalled gnome-desktop

Eventually I installed the kubuntu-desktop and managed to get into KDE, but I would really like to get back to a working Gnome, and clean out the K applications that I don't use or need.

Any ideas folks? I had a quick look through the /var/logs but nothing jumped out at me... is there a particular log that can tell me what Gnome is trying to do during the boot up?

---

### Post by Neilor on 2007-08-29
Correction to original steps... I re-installed GCompris prior to edubuntu-desktop.

Any help appreciated.

---

### Post by Neilor on 2007-08-30
Turns out the problem was related to me configuring the network settings in Gnome to use OpenDNS  a couple of days earlier.... found an obscure reference to the White Quarter Screen I was seeing being caused by network problems in another forum post.

---

