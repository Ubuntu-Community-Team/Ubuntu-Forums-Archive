---
title: "Please advise on how to edit conf file in Ubuntu 22.04"
date: 2022-05-26
forum: General Help
---

### Post by eddugo on 2022-05-26
Touch screen is making cursor jump all over screen.  i can turn it off with xinput, and it works great but comes back after reboot.  I am trying to edit the config file in the attachment to keep it off.   I open the file with: sudo nano /usr/share/X11/xorg.conf.d/40-libinput.confv  but I am not sure where to go from there.  The attachment shows the file area I need to modify to shut off the touch screen.

Thank you in advance for your help

Ed

---

### Post by TheFu on 2022-05-27
Use **sudoedit** to edit system files.

Please don't post images of text. Post the text so people can point out mistakes more easily.  Please make it easy to help.

You can always ssh in from another system.

---

