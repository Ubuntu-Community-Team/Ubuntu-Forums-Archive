---
title: "run script at startup"
date: 2006-10-29
forum: General Help
---

### Post by metricben on 2006-10-29
hi all,
i use bluetooth to transfer files to and from my phone, using a bluetooth dongle, and use 3 scripts in my nautilus context menu:

- Bluetooth Setup
- Bluetooth Recieve File
- Bluetooth Send File

This works fine, but to further help, i would like the setup script to be loaded at startup, because it asks for root priveleges (to modprobe).  i think this would need to be done system-wide, to get the required priveledges. here is the script:
```
#!/bin/bash
modprobe l2cap
gksudo modprobe rfcomm
gksudo mknod /dev/rfcomm0 c 216 0
sdptool add --channel=10 OPUSH
gksudo rfcomm bind /dev/rfcomm0 00:18:A4:E0:04:B4 10
done

```
where do i put this for it to be run at startup

thank you
ben

ps
how would i encorporate the function of transfering all jpg's from the tmp directory (where files are transfered) into another one in my home folder.  this would be part of the recieve file script:
```
#!/bin/bash
obexserver
done

```

---

