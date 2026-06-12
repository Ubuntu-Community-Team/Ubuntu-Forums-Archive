---
title: "no internet connection"
date: 2007-06-08
forum: General Help
---

### Post by Dai777 on 2007-06-08
Installed version 6.10 last night using VMWare server got everything up and running tidy but can't send email or connect to the net. My internet provider is NTL (Virgin Media) and my connection is cable moden using usb not ethernet. Do I need to install drivers for the usb connection.

Would it be better to have my modem connection via ethernet?

Thanks 
Dai:D

---

### Post by ArieT on 2007-06-08
> **Dai777 said:**
> 
Would it be better to have my modem connection via ethernet?

Yes! Much better. USB isn't designed for this.

---

### Post by veloce on 2007-06-08
> **Dai777 said:**
> Installed version 6.10 last night using VMWare server got everything up and running tidy but can't send email or connect to the net. My internet provider is NTL (Virgin Media) and my connection is cable moden using usb not ethernet. Do I need to install drivers for the usb connection.

Would it be better to have my modem connection via ethernet?

Thanks 
Dai:D

You're a bit unclear here, I take it that you have installed ubuntu as a vm inside a windows host?

Vmware server needs to be set up to provide internet access for the vm.  Best alternative for your setup is NAT.  Then the vm needs to have a virtual network card "connected" to the virtual network.

---

### Post by Dai777 on 2007-06-11
yes absolutely correct got ubuntu setup as virtual network on xp working ok apart from internet connection which is bridged but not working.

Followed this tute to get it working 
[http://www.tanguay.info/web/tutorial.php?idCode=installUbuntuOnVmware&sectionIdCode=installUbuntuOnTheVirtualMachine](http://www.tanguay.info/web/tutorial.php?idCode=installUbuntuOnVmware&sectionIdCode=installUbuntuOnTheVirtualMachine)

just need to sort out email and internet connections but, do't know what to do as I'm a noob at linux and VMware.

Would appreciate some help on this. 

also now using ethernet cable.

---

### Post by veloce on 2007-06-11
> **Dai777 said:**
> yes absolutely correct got ubuntu setup as virtual network on xp working ok apart from internet connection which is bridged but not working.

Followed this tute to get it working 
[http://www.tanguay.info/web/tutorial.php?idCode=installUbuntuOnVmware&sectionIdCode=installUbuntuOnTheVirtualMachine](http://www.tanguay.info/web/tutorial.php?idCode=installUbuntuOnVmware&sectionIdCode=installUbuntuOnTheVirtualMachine)

just need to sort out email and internet connections but, do't know what to do as I'm a noob at linux and VMware.

Would appreciate some help on this. 

also now using ethernet cable.

Can you post the output of:

```
ifconfig
```

From within the ubuntu vm.

---

### Post by Dai777 on 2007-06-12
switched NAT used to share the host ip and got a internet coonection.
Thanks for the offer of help

---

