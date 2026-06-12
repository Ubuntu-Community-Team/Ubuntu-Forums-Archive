---
title: "No Dash, No Window Borders, No Terminal Access???"
date: 2016-02-29
forum: General Help
---

### Post by arsenic-creed on 2016-02-29
Hello,
I was having some problems getting something to work in my Wine install so I decided to remove Wine, install it new, and try again. I uninstalled it through the terminal, ran sudo apt-get update, then just as that finished I got a notification saying I needed to restart to finish installing the updates so I did but when it came back on and I logged in, there's (as the title says) no dash and no window borders. I tried getting into a terminal via ctrl alt T and through alt F1-6 but the former does nothing and the latter switches to a black screen with an input curser blinking but never lets me log in and doesn't accept any input at all. Since this is my only operating system, I don't get a GRUB boot menu when I start the computer up either.
As much as I enjoy fiddling with a clean, new system, I'd rather not reinstall if it's at all possible but I'm not finding any alternatives. Is there a way to get into the GRUB boot menu if it doesn't come up on start up to try to get to the recovery console?

---

### Post by TheFu on 2016-03-02
Support for 15.04 ended in January.

Whenever there is an issue with any program, I find it easiest to create a new account and test with that, since often just the settings for 1 account have broken it, not the entire system.

So ... if you boot off a flash drive with 15.10, then you should be able to upgrade the 15.04 OS to a supported release and when 16.04 is released, upgrade to that before support for 15.10 ends in June.  I prefer to only install LTS releases - which get support for 5 yrs.  14.04 is the current LTS with support.  15.xx, 16.10 and 17.xx releases get 9 months of support.  April of even years are LTS releases.

---

