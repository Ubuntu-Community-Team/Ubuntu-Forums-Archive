---
title: "startup session help"
date: 2007-08-30
forum: General Help
---

### Post by dondad on 2007-08-30
I am dual booting fiesty and gutsy. I made a change to the session startup (in the gutsy install)  that apparently does not work and after the normal boot, I end up with a black screen and a pointer. I guess, two questions:

1. What could I try to get a desktop
2. Where are the startup parameters stored so that I can get rid of the command that is messing up the system.

I can access all of the gutsy files from my fiesty install.

---

### Post by -X- on 2007-08-31
I have the same issue - I think it might be one of the updates. Editing the xorg.conf doesn't really seem to help.

Actually, what usually happens to me is that the screen dims to 1% (can only see some shapes) when I log in, and in order to get the screen to its normal 90% brightness or so I need to change sessions (hit CTRL-ALT-F1) and then go back to the GUI (CTRL-ALT-F7). Now when I go back to the GUI I get the 100% black screen and pointer.

After being struck by the 100% black screen and pointer "bug" I can't even kill X or switch sessions.

---

### Post by dondad on 2007-09-02
Whatever it was, it was associated with the home directory. I finally reinstalled Gutsy, and had the same problem. (My /home is on a separate partition and I did not format that one) Since I had no real data in my /home directory, I reinstalled again and formatted /home also. That fixed the problem, and when I downloaded all of the updates, everything still works.

One thing that would be usefull to me, and probably a lot of others, is the file locations for all of the various settings. For instance, where does the session manager save its settings? It would be useful to know the answer for all of the programs in administration and preferences. (at least for the default and maybe a few of the common extras.) I am pretty sure that had I been able to find some of them, I could have fixed the problem without doing the reload.

---

