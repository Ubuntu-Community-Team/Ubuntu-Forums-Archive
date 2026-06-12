---
title: "Linux Printer on a windows home network?"
date: 2007-11-22
forum: General Help
---

### Post by teryowen on 2007-11-22
I currently have a small home network with 4 computers.

Now on my main computer i am Dual booting currently and also on some others. My question is weather there will be a problem with the other computers(Windows) communicating with the printer on the Linux machine?

Any one who has this set up ide like to know how its working out and if there are any problems.

Thanks in advance.

---

### Post by mpierce on 2007-11-22
There will be no problem as long as you have samba enabled to share the printer to your WIN machines. Make sure all machines are in the same WORKGROUP in your samba config file. 

Here's a good link to look at as there is tons of material on How To.

Hope this helps...

---

### Post by zippy028 on 2007-11-23
I have it setup this way the only problem I have is that CUPS seems to shutdown the printer so I have to tell CUPS to enable the printer before my print job will execute.

in a browser enter as the URL

```
localhost:631
```

That will get you the CUPS config-tool.

---

### Post by mahousaru on 2007-11-23
If your windows boxes say they can't connect to the printer after it has been successfully added then you need to add to the the [printers] section of the smb.conf

[printers]
   use client driver = Yes

---

