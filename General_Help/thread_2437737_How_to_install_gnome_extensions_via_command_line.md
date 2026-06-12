---
title: "How to install gnome extensions via command line"
date: 2020-02-28
forum: General Help
---

### Post by yaminb on 2020-02-28
Is there a way to install gnome extensions via the command line?

Background:
I'm trying to create a shell script to setup a new system with the programs I need. Also good for tracking the applications I use.

Specific Case:
I use this extension a lot "Sound Input & Output Device Chooser"
[https://github.com/kgshank/gse-sound-output-device-chooser](https://github.com/kgshank/gse-sound-output-device-chooser)

I couldn't find this in apt-cache search or anything like that. 
I downloaded an extension manually, and I see a manifest file with a UUID ("uuid": "sound-output-device-chooser@kgshank.net")
Is there anything like 
```

gnome-extension-install "Sound Input & Output Device Chooser"
gnome-extension-install "sound-output-device-chooser@kgshank.net"

```

I do see this page 
[https://medium.com/@ankurloriya/install-gnome-extension-using-command-line-736199be1cda](https://medium.com/@ankurloriya/install-gnome-extension-using-command-line-736199be1cda)

I could do that, but I'm thinking there must be a way to execute the Ubuntu Store behavior via the command line. Something like apt or snap?
Otherwise, I'll just make note of the extension and install it manually each time.

---

