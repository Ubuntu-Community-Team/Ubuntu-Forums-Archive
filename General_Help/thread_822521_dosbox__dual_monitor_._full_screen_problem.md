---
title: "dosbox / dual monitor . full screen problem"
date: 2008-06-08
forum: General Help
---

### Post by F W Adams on 2008-06-08
I'm completely new to dosbox but with some Ubuntu experience, using 7.10.

Dosbox works fine except when switched to full screen mode. When in full screen mode the program still seems to run but the display is placed half way across the right hand screen, the text size doubling as expected, with half of it lost. Coming out of full screen mode the program displays correctly again. When in full screen mode I only need to use one screen, nothing more needed.

By modifying xorg.conf to boot up with only one display the full screen mode is fine so it seems definitely related to using two screens.

I enclose my xorg.conf, it has been working for at least 6 months without any other problems.

---

### Post by F W Adams on 2008-06-11
Just some additional info. Taking the two screens as 2560 x 1024 with 0,0 at the top left. When moving to full screen mode:

1.  The top left of the DOS screen appears to be at 1920,~594.
2.  What was on the left hand screen moves about 320 pixals to the left.
3.  All else is black

---

### Post by eotakos on 2008-06-15
hello there, i'm having fullscreen problem with dosbox too -

actually when i <alt+enter> while still on dosbox console my monitor reads that it can't display that kind of input.

your knowledge of ubuntu seems to be more adequate than mine since i haven't reached the point of editing xorg.conf - so why don't you give me some advice - i'm running on nvidia drivers - geforce 7600gs which has exits for two monitors but i can't see how this affects things.

---

### Post by PedroRQ on 2008-08-06
> **F W Adams said:**
> I'm completely new to dosbox but with some Ubuntu experience, using 7.10.

Dosbox works fine except when switched to full screen mode. When in full screen mode the program still seems to run but the display is placed half way across the right hand screen, the text size doubling as expected, with half of it lost. Coming out of full screen mode the program displays correctly again. When in full screen mode I only need to use one screen, nothing more needed.

By modifying xorg.conf to boot up with only one display the full screen mode is fine so it seems definitely related to using two screens.

I enclose my xorg.conf, it has been working for at least 6 months without any other problems.

DOSBox doesn't seem to like it when your main monitor is on the right of your secondary monitor. Was that the case?

---

### Post by F W Adams on 2008-08-07
Yes, you're right. My main monitor ( the one the system boots from ) is on the right of the secondary.

Just for interest I changed them round this morning putting the main monitor on the left. It changed the symptoms slightly but still doesn't work. Now in full screen mode I get a display in the middle of the two screens, split between the two, but with small text, half the size it should be.

---

### Post by bouncingmolar on 2008-08-10
The best I could manage was to edit the windowed resolution to match my monitors by editing the .dosboxrc file in my home directory


*how to create the .dosboxrc file*
1 Open dosbox
2 - From within, type the following to generate the rc file:
config -writeconf .dosboxrc

---

