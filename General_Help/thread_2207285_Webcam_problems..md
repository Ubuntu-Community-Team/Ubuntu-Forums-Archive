---
title: "Webcam problems."
date: 2014-02-22
forum: General Help
---

### Post by ilikecolors on 2014-02-22
Okay guys, my webcam works just fine, except in online websites like omegle. I must say that in the unity dash I cannot find the Adobe Flash Player. I recently installed a new webcam, uninstalled firefox and installed chrome, and I installed the Ubuntu restricted extras. It clearly says in the Software Center that it is installed, however. The only way that I could edit accessibility was by using the online adobe website. Even configuring to "always allow" it still wont work. Help?

---

### Post by papibe on 2014-02-23
Hi ilikecolors.

Install 'Control panel for Adobe Flash player' from the 'Software Center'. I believe that's is what your're looking for.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by ilikecolors on 2014-02-23
> **papibe said:**
> Hi ilikecolors.

Install 'Control panel for Adobe Flash player' from the 'Software Center'. I believe that's is what your're looking for.

Hope it helps. Let us know how it goes.
Regards.

Theres no such thing. Im really confused because the webcam works on Cheese Booth and other software, but online it doesn't.

---

### Post by ilikecolors on 2014-02-23
Okay, I reinstalled Firefox. It works with Firefox but not with Chrome so I guess im just going to have to use Firefox for webcam things.

---

### Post by papibe on 2014-02-23
Glad to hear is working at least on Firefox. I believe Chrome does not carry flash anymore, but its own 'pepper' player from Google.

If you are referring to Chromium, check if the flash player is working first (play some videos with ads on youtube for instance).

BTW, I was talking of this package:

```
$ apt-cache search control panel adobe flash
adobe-flash-properties-gtk - GTK+ control panel for Adobe Flash Player plugin version 11
adobe-flash-properties-kde - KDE control panel Adobe Flash Player plugin version 11

$ apt-cache policy adobe-flash-properties-gtk 
adobe-flash-properties-gtk:
  Installed: (none)
  Candidate: 11.2.202.341-0precise1
  Version table:
     11.2.202.341-0precise1 0
        500 http://archive.canonical.com/ubuntu/ precise/partner amd64 Packages

```
Regards.

---

### Post by ilikecolors on 2014-02-23
Thank you. I am not using Chromium, I am using the official Chrome. It works fine to play videos and all too.

---

