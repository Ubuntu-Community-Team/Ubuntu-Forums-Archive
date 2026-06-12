---
title: "Confused about live cd"
date: 2006-07-27
forum: General Help
---

### Post by njzillest on 2006-07-27
I have ubuntu installed on the hard drive. I have an intel 2200b/g and the driver installed pefectly.

I'm having problems for booting on too a live cd (Knoppix STD) and using the wireless card. I boot up fine, but i dont know how to enable the wireless card. 



Should i modeprobe, should i use ndiswrapper.

Please help me, im really confused... N00b needs help lol.

Thank you soo much for your help.

If you have anyquestions about the problem, please just post or PM me.


Thanks again and have a nice morning (its 12:20 am) :-D

---

### Post by Paerez on 2006-07-27
i too have a 2200. You may have to do:
```
sudo modprobe ipw2200
sudo modprobe ipw2200-firmware
```
then you can type:
```
dmesg | tail
lsmod | grep ipw2200
```
the first command shows how well the module inserted, and the second will show the modules that are currently loaded (to see if it worked). Then run:
```
iwconfig
``` to see if it shows up.

---

### Post by njzillest on 2006-07-27
This is how i can get the Live CD to work (Knoppix)..

So.. all i have to do is modprobe (what does that mean) i think it means to search for the module, and load it?

Correct me if im wrong, but im still a little confused.


Thanks for your help

---

### Post by Paerez on 2006-07-27
Modprobe = find the module, and attempt to load it by seeing if there is any hardware that is compatible with it.

In knoppix, you have to open a terminal, then type in what I posted. Just the first part with the modprobes. Then to see if it's working, type iwconfig to see the status of your devices.

---

### Post by njzillest on 2006-08-05
Knoppix STD desont work with it, When i type in modprobe ipw2200 it says:

```
modprobe: can't locate module ipw2200
```


5s there any workaround to get the wireless adaptor working?

Thanks for the help

---

### Post by Paerez on 2006-08-05
what does iwconfig say?

This worked for me with knoppix 4, I haven't tried knoppix 5 though. Whats Knoppix STD?

---

### Post by njzillest on 2006-08-05
it says no wireless extensions 
(all for eth0, eth1, and something else) 


STD is the security version of KNoppix. It isnt as updated as Knoppix. Hmm 

i guess i'll check out backtrack. IM a little confused though, whats better backtrack or auditor? i read somewhere backtrack is auditor and and whax. lets see what supports the IPW2200.

Thanks for your help :-D

---

### Post by Paerez on 2006-08-05
Back|Track is the new auditor. I have an ipw2200 and a lot of the stuff doesn't work because the ipw2200 is not a prism card and has trouble with some of the packet manipulation.

Let me know if it works.

---

### Post by njzillest on 2006-08-05
I was reading that Auditor fully supports the IPW2200.

I was wondering if they carried it on to Backtrack

---

### Post by Paerez on 2006-08-05
it does support it, but I could never fully crack my own wep because some of the tools didn't work with it.

---

