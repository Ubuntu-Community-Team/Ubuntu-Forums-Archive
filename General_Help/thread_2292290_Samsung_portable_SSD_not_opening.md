---
title: "Samsung portable SSD not opening"
date: 2015-08-26
forum: General Help
---

### Post by jagannath on 2015-08-26
My Samsung portable SSD ( Model: MU-PS250B) is not opening with Wine Program Loader. I'm
 using Ubuntu 14.4  The SSD was set up with password protection on an ASUS X200M laptop running Windows 10.
A Screenshot of the file folder is attached. Please help.[ATTACH=CONFIG]264066[/ATTACH]

---

### Post by sandyd on 2015-08-26
It is possible that the password protection may work for Windows/Mac only. WINE does not support all programs, and the encryption method used may not work through WINE as it may need direct access to the device.

If you want it to work, you can mount it directly to a virtual machine, unlock/decypt it there, and share the folder.

---

### Post by jagannath on 2015-08-26
Thank you .I'll try that and post the results.

---

### Post by jagannath on 2015-08-27
I found the ram capacity on my notebook is too low (2 GB only ) to use a virtual machine. Thanks, though.

---

