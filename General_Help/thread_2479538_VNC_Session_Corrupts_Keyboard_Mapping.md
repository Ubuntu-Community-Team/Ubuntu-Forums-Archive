---
title: "VNC Session Corrupts Keyboard Mapping"
date: 2022-09-28
forum: General Help
---

### Post by texanrunner on 2022-09-28
Just installed 22.04 LTS on hardware that was previously running Mac OS. Installed and configured OpenSSH server and enabled Sharing (including Legacy VNC protocol).

I can connect to the machine remotely by entering vnc://<ip_address> in Finder on my Macbook. However it seems that the VNC session somehow corrupts the keyboard mapping on the remote machine as suddenly I am unable to type a "-". No matter what depressing the "-" on either the Macbook keyboard or the remote keyboard results in an underscore "_" on the screen.

Rebooting the remote machine returns the keyboard to normal. My assumption is that the VNC session is somehow corrupting the keyboard mapping on the remote machine but I have no idea on where to begin on fixing this issue. Can anyone offer some insight and advice as to how I might proceed?

---

