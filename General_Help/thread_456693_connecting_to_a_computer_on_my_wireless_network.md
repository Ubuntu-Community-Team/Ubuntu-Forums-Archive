---
title: "connecting to a computer on my wireless network"
date: 2007-05-27
forum: General Help
---

### Post by cessna_89702 on 2007-05-27
Can I connect the windows computer thats on my wireless network if both of us are on the wireless network and how  would I do this?? 

thanks

---

### Post by bung33 on 2007-05-28
Yes you can. You will need to use samba to identify computers on the network that are running Windows. Assuming samba is installed with defaults, type this command to start the service...

```
sudo /etc/init.d/samba start
```

This will allow you to see Windows computers on the network. Getting data from shared folders on the Windows boxes is easy, however, setting up Linux to share folders with read and write permissions takes a lot more tweaking. Search the forums for more information about samba if you can't get it working...

---

