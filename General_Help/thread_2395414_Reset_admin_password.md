---
title: "Reset admin password"
date: 2018-07-01
forum: General Help
---

### Post by rkarun on 2018-07-01
I have a machine running Ubuntu 16.04 as the only OS on it. I forgot my admin password. I've looked at the online forums/videos/articles on how to reset a password, and almost all of them suggest to hold the shift key to get to the recovery menu and then reset it by running some commands. But unfortunately, in my case, for some reason, I am not able to get to that screen even after holding the shift key. I tried using escape key/enter key but nothing got me there. All I can see is a minimal Bash screen and I am not sure how to use this to reset my password.

Is there anything I can do that will help me using my computer?

---

### Post by ajgreeny on 2018-07-02
If your computer uses UEFI firmware it is sometimes difficult to get the grub-menu to appear and you may need to try many times, as the timing of the Esc press is paramount.

Try again by continuous repeat pressing the Esc key, not using a single long hold of it; that may help.

Once you have managed to get into Recovery mode and reset the password you may wish, as I have, to edit the /etc/default/grub file (as root I'm afraid so you can't do this just yet) to make the grub menu appear for a couple of seconds at each boot.

I'm not on a Ubuntu machine at the moment so will have to find that info later as get back to you but basically it needs changes of the config lines in that file to something like the following, though there are other minor things you can change.

```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=5
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR="Lubuntu 18.04 Bionic"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

---

### Post by ajgreeny on 2018-07-09
Here is the required full edit as promised of **/etc/default/grub** to ensure that the grub menu always appears at boot even if you have a single OS system where grub would not normally show by default.

```
GRUB_DEFAULT=0
#Next line will make the countdown time show menu by default
GRUB_TIMEOUT_STYLE=menu
#Next line changed from 0 to x for x second delay
GRUB_HIDDEN_TIMEOUT=2
#Next line changed from true to false to allow delay countdown to show
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR="Xubuntu-14.04"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

Note the line **GRUB_DISTRIBUTOR="Xubuntu-14.04"** which I always edit to show the proper name of the OS rather than the normal unhelpful description showing in the menu.

The "" around your edited OS name are needed for this to work.

---

