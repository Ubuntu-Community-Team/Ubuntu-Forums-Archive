---
title: "Blinking Cursor of Death after 6.06 Server Install"
date: 2006-07-12
forum: General Help
---

### Post by HedonismBot on 2006-07-12
Greetings all,


I'd say I'm a mid-level linux/ubuntu user (I work in development, but I can handle a *nix command line and editing .config stuff just fine) and over the past few weeks have happily and sucessfuly installed 6.06 on a variety of older Rack-Servers (Compaq). **BUT**


We've just purchased a generic SuperMicro based rack server to use as an iScsi / File box and after 6.06 Installs (it does detect the Adapec RAID card and partitions) it reboots and hangs on a blinking cursor forever. **What is going on???** ](*,) 

It sees the hardware on install, installs, then hangs. I've tried re-installing, force mounting the drive with the repair mode, but still nothing. What am I missing, and what the 'eff is wrong with my install? I know I'm missing something obvious, so treat me like a dummy and help me out...PLEASE! ] :)

---

### Post by cptnapalm on 2006-07-12
While I know nothing about rack mounted servers, I think that the SuperMicro model number would be helpful to know as searches could be made using it and it would enable looking up particular pieces which may be problematic.

What filesystem did you install?  ext3, I presume?

---

### Post by HedonismBot on 2006-07-12
I'm getting the hardware specs sent over to me now...thanks! :D 

Install was textbook standard, no configs set (we do them manually later). It installs fine, but then nothing...blink blink blink....:-k

---

### Post by HedonismBot on 2006-07-12
Okay, it's a Supermicro E7230

[http://www.supermicro.com/products/motherboard/PD/E7230/PDSMi.cfm]("http://www.supermicro.com/products/motherboard/PD/E7230/PDSMi.cfm")

In one of these: [http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=1903221&CatId=0]("http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=1903221&CatId=0")

As all our other 6-06 installs went flawlessly, I'm at a lost to trace what hardware or software settings are fubar'd to let this happen.

Any help from the forum squad is most appreciated!!!

---

### Post by iduriduridur on 2006-07-12
Well since the install went fine, I assume hardware is not faulty.
check in the SATA ICH7R Controller/adaptec ROM boot thing to see what is setup.

---

