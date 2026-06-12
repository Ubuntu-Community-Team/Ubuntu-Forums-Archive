---
title: "Megacli64 for LSI RAID controller"
date: 2016-09-16
forum: General Help
---

### Post by digitalquake on 2016-09-16
Hello

I've recently installed Megacli following the instruction [URL="http://artipc10.vub.ac.be/wordpress/2011/09/12/megacli-useful-commands/"]here.
[/URL]The installed version is* Mega CLI 5.5 P2  **Version: **                                                                  8.07.14 from the*[ Avago Website]("http://www.avagotech.com/support/download-search/?productFamilyName=&area2=&area3=&area4=&dnd-keyword=megacli")

The card is installed, detected with lspci and I can see the RAID by browsing it. I can access it also at boot.

Sometimes commands output

```

Controller Count: 0.
Exit Code: 0x00
 
```
and sometimes 
```

Exit Code: 0x01

```


If I run ./Megacli64 -v from the /usr/local/sbin  it print

                                     ```

      MegaCLI SAS RAID Management Tool  Ver 8.07.14 Dec 16, 2013

    (c)Copyright 2013, LSI Corporation, All Rights Reserved.

```

Is anyone in my situation? Am I missing some binary of any sort that prevent me from interrogate the card?

Thanks in advance

---

