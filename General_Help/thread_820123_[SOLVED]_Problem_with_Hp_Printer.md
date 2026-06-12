---
title: "[SOLVED] Problem with Hp Printer"
date: 2008-06-06
forum: General Help
---

### Post by bmac on 2008-06-06
Recently my printer was removed from my system - possibly by an update, as I haven't used it for a week. When I reinstalled it using the hplip in Synaptic - still won't function. I proceeded to download the self extracting archive with installer &quot;hplip-2.8.5.run&quot; and it fails to open in terminal under the command &quot;sh hplip-2.8.5.run&quot; as defined by this site: [http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)
Hope someone has a solution.... I have searched the forum for a possible solution but couldn't locate a solution...
Thanks in advance....
Info:
Printer type - HP Officejet 5610 All In One
Hardy 8.04
Kernel linux 2.6.24-18-generic

---

### Post by PmDematagoda on 2008-06-06
Post the output of:-
```
lsusb
```

---

### Post by kaibob on 2008-06-06
Deleted post

---

### Post by bmac on 2008-06-06
bmac@bmac-desktop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 03f0:4f11 Hewlett-Packard 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

Any ideas???

---

### Post by bmac on 2008-06-06
Sorry, it must have been a defective download. I deleted the file and downloaded a second time and now it appears to be installing.
Thanks again for the help...
:smile:

---

### Post by PmDematagoda on 2008-06-06
Remove the USB printer and plug it back in, after you do that post the output of:-
```
dmesg | tail -25
```

---

