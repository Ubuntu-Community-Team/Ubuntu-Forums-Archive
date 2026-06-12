---
title: "Can VMWare drag and drop file between windows hosts and linux hosts?"
date: 2007-05-02
forum: General Help
---

### Post by schhaozi on 2007-05-02
I'v just install ubuntu6.06 in the vmware station 5.5.4. The host OS is windows sp2. After installing vmware tool  , everything works fine except that, I can't drag and drop between the host and guest. I'v check the option:
   ```
isolation.tools.dnd.disable = "FALSE"
```
  :confused:  Can anybody tell me the reason? Can VMWare drag and drop file between windows hosts and linux hosts?
   Thanks

---

### Post by yopnono on 2007-05-02
> **schhaozi said:**
> I'v just install ubuntu6.06 in the vmware station 5.5.4. The host OS is windows sp2. After installing vmware tool  , everything works fine except that, I can't drag and drop between the host and guest. I'v check the option:
   ```
isolation.tools.dnd.disable = "FALSE"
```
  :confused:  Can anybody tell me the reason? Can VMWare drag and drop file between windows hosts and linux hosts?
   Thanks

Have you tried to copy & paste
Also questions like this should be asked at vmware forums, since it... well have nothing to do with the ubuntu.

---

### Post by veloce on 2007-05-03
No, you can't drag and drop between host and vm.

Set up a samba share over the host only virtual network.

---

### Post by rbmorse on 2007-05-03
It works on Workstation 6 with VM tools installed...at least on a Lunux hostwith  WIndows client (and why would you want to run the other way around?....<g>)

For Workststion 5.5 with VMTools installed in the guest, you can set up shared folders with the host through VM settings. Once you have shared folders set up and defined  you can drag n' drop using a shared folder like h any other folder in the VM and the result will reflect on the host. 
. 

On a Windows host, stand by for silliness, though.  WIndows doesn't understand the file permisions or other extended features of Linux file systems, occasionally you may experience unusual or undesired results, particularly on the Linux side if permissions get hosed.

---

