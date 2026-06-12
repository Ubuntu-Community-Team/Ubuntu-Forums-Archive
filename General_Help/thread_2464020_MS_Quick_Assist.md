---
title: "MS Quick Assist"
date: 2021-06-23
forum: General Help
---

### Post by artist-wavenet on 2021-06-23
My OS is Ubuntu 18.04. I desire to remotely assist another person whose computer has Windows 10 using Windows 10's Quick Assist feature. Is there a way for me to do that from my Ubuntu computer?

---

### Post by ActionParsnip on 2021-06-23
Seems to be RDP based so tsclient or remmina maybe...

---

### Post by artist-wavenet on 2021-06-23
For me to use Remmina the person I would help would have to give away her password to her Windows 10 account. RDP using Remmina is a different thing than Quick Assist.

---

### Post by dragonfly41 on 2021-06-23
I have shared Ubuntu and Windows 10 and I use automation scripts or simply notes passed via shared dropbox account.
CherryTree is a good candidate since it runs cross platform. Place a CherryTree note in dropbox and it can be shared. Even code (Bash, Python .. whatever) can be embedded and run in any CherryTree object.
If you need to interact with the remote Windows (i.e. drive the Windows UI) you can pass automation scripts which run in Windows. Actiona is one example.

---

### Post by scorp123 on 2021-06-23
> **artist-wavenet said:**
>  Is there a way for me to do that from my Ubuntu computer?

Or you use a 3rd party application that exists for both Linux and Windows, such as one of these:

[https://www.teamviewer.com/]("https://www.teamviewer.com/")
[https://anydesk.com/]("https://anydesk.com/")

Please make sure you uninstall those apps again after you're done needing them. Keeping either of those apps running unattended 24x7 is not wise.

---

