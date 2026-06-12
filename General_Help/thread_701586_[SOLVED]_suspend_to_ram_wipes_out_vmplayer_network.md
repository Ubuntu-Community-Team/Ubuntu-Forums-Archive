---
title: "[SOLVED] suspend to ram wipes out vmplayer network settings"
date: 2008-02-19
forum: General Help
---

### Post by dixonstalbert on 2008-02-19
hello 

If I suspend to ram my computer with vmplayer closed, the next time I go to use vmplayer my network settings are gone and ifconfig no longer reports presence of vmnet1 and vmnet8

 If I run ```
sudo /usr/lib/vmware/net-services.sh restart
```

then my vmware net services are restored and LAN networking works again inside my Windows guest OS 


Does anyone know where I could add this command in the scripts running computer wakeup so it restores vmware network settings?


thanks dcstar (post below) for solution

I added the line above to the bottom of /etc/acpi/resume.d/69-services.sh and that fixed it.


I recently did an upgrade from Feisty to Gutsy and vmplayer would not work after the upgrade. I noticed after I re-installed vmplayer I have an active link in rc.d for vmware and quite a few broken ones for vmplayer. I think that is why it is not being woken up after the network is up- but this solution will fix things until I get that sorted out. thanks again.

---

### Post by dcstar on 2008-02-19
> **dixonstalbert said:**
> hello 

If I suspend to ram my computer with vmplayer closed, the next time I go to use vmplayer my network settings are gone and ifconfig no longer reports presence of vmnet1 and vmnet8

 If I run ```
sudo /usr/lib/vmware/net-services.sh restart
```

then my vmware net services are restored and LAN networking works again inside my Windows guest OS 


Does anyone know where I could add this command in the scripts running computer wakeup so it restores vmware network settings?

thanks
Dixon

Possibly /etc/acpi/resume.d

---

