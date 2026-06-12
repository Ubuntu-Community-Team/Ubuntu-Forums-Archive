---
title: "Printer won't print!"
date: 2019-10-19
forum: General Help
---

### Post by Old Jimma on 2019-10-19
Hi Ubuntu Community!

I've got an HP Laser Jet Pro MFP M281cdw .... and cannot get it to print.

The printer is connected wirelessly to my home network and has IP address 192.254.113.86

How can I fix this???

Thanks!
Old Jimma From the Old Country

---

### Post by yancek on 2019-10-19
Does your OS recognize the printer at all?  How did you configure it?  What happens if it is recognized and you try to print something?  You might take a look at CUPS by opening a browser and entering the following:  localhost:631  You should see a number of options including CUPS for Administrators and under that using network printers.

---

### Post by Old Jimma on 2019-10-20
Hello yancek:

I found out why I could not configure my printer: I had configured it to be on another network. Once I put it on the same network as all of my computers, Ubuntu had no problem finding it and downloading the drivers.

What a rookie mistake!

Thanks you for your reply, yancek. 

Take care,
Old Jimma

---

