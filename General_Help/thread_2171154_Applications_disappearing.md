---
title: "Applications disappearing?"
date: 2013-08-29
forum: General Help
---

### Post by acebone on 2013-08-29
Hi, 

Ubuntu 13.04 on a Dell XPS 13 (with SSD-Drive)

Yesterday while installing a downloaded .deb package I closed firefox while installing. Software center immediately complained and aborted the installation. I may have been trying to install the not completely downloaded package.

Now it gets weird: I restart firefox, and it opens over Software Center, when trying to alt-tab to software center i realize it must have crashed because it's gone. So I try to restart it .... the program is no longer there!

I search for it, and there are lots of traces of it - but no binary. 

I then proceed to reinstall it  with sudo apt-get install software-center. Apt-get makes no protests that it is already installed and continues to fetch and install it.

I've now got a fully functional software-center - but that was a strange event. 

Today however ...

I hit CTRL+ENTER to bring up synapse ... but nothing happens. There is no binary any longer!! I try "locate synapse" and locate shows me that the binary is supposed to be in /usr/bin/synapse ... but there is NO file in /usr/bin called synapse.

I reinstall it with apt-get ... and apt-get does not complain that it is already installed but continues to fetch and install (I think it fetches from a local cached copy - but that's irrelevant) synapse.

Ie. 

use software-center - an error happens - software-center is no longer installed
use synapse - reboot - synapse is no longer installed.

WHAT ON EARTH IS THIS???

Maybe I should mention that I installed Kubuntu-desktop on the ubuntu installation, and that I've had some problems with char-encoding. I still sometimes get "illegal space-char" in filenames from KDE ... Not sure that this is related, just mentioning it.

---

### Post by rai_shu2 on 2013-08-29
Let's see. You downloaded some mystery deb using Firefox and then used Software Center to install it, and suddenly Software Center disappears...

This just raises the question: what the heck did you download? You do realize that Software Center does your downloading for you, right?

---

