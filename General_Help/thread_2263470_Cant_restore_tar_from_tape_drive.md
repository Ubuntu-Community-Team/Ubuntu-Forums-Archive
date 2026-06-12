---
title: "Cant restore tar from tape drive"
date: 2015-02-01
forum: General Help
---

### Post by vangend.robert on 2015-02-01
I have written about 135GB of data to a tape drive (Dell LTO2).

I can list all the archive members (sudo tar tvf /dev/nst0), but when I try to restore an individual file or a complete directory, tar reports errors:

administrator@VMDataServ:~$ sudmt -f /dev/nst0 rewind
administrator@VMDataServ:~$ sudo tar -xvf /dev/nst0 -C ./tartest/ srv/VMData/pub/2008/Embizweni/Embizweni/Catia files/40.00.SLDPRT.CATPart
tar: srv/VMData/pub/2008/Embizweni/Embizweni/Catia: Not found in archive
tar: files/40.00.SLDPRT.CATPart: Not found in archive
tar: Exiting with failure status due to previous errors

Is there a problem with the tar command I am using for extraction, ot is there another hardware issue I need to consider?

Ubuntu 12.04 Server

---

### Post by Holger_Gehrke on 2015-02-01
> **vangend.robert said:**
> 
administrator@VMDataServ:~$ sudo tar -xvf /dev/nst0 -C ./tartest/ srv/VMData/pub/2008/Embizweni/Embizweni/Catia files/40.00.SLDPRT.CATPart
tar: srv/VMData/pub/2008/Embizweni/Embizweni/Catia: Not found in archive
tar: files/40.00.SLDPRT.CATPart: Not found in archive


You forgot to escape the space in "Catia files", the command should read:
```

sudo tar -xvf /dev/nst0 -C ./tartest/ srv/VMData/pub/2008/Embizweni/Embizweni/Catia**\** files/40.00.SLDPRT.CATPart

```

---

