---
title: "S to skip mounting External drive"
date: 2012-12-15
forum: General Help
---

### Post by muddinyoreye on 2012-12-15
hello, all 

    got a little problem , I can"t figure out , for some reason ubuntu 12.04.1 is trying to mount a external hard drive. I no longer have available or attached, it asks me to wait for it to mount or S to skip mounting or M for manual recorvery. My question is how to make it forget about mounting this device, and do a normal boot with no user input every time?  ](*,).         Thank you.

---

### Post by jim_deadlock on 2012-12-15
```
sudo blkid
```

... to find out the UUID of the errant drive.

```
sudo nano /etc/fstab
```

... to edit the auto-mount file (CTRL-X to exit/save). Remove the line containing the offending UUID and next time you boot it won't look for it.

---

### Post by muddinyoreye on 2012-12-15
heres the output from blkid 

/dev/sda1: UUID="34870789-1ebe-4dcd-bffc-f3e6af133b2f" TYPE="ext4" 
/dev/sda5: UUID="86894edb-c2ad-4334-bec4-58ac4a285e1b" TYPE="swap"  


I dont see the id of the errant drive.
 


 thank you

---

### Post by Mark Phelps on 2012-12-15
That command only lists the devices connected when it is run.

You have to connect the external drive and THEN run the command.

---

### Post by dcstar on 2012-12-15
> **muddinyoreye said:**
> 
I dont see the id of the errant drive.


Remove the entry from the /etc/fstab file that is NOT in that list.

---

### Post by muddinyoreye on 2012-12-19
sudo nano /etc/fstab

found the errant drive entry and after a little deleteing the problem was solved
thank you [jim_deadlock]("http://ubuntuforums.org/member.php?u=1108068") 
:KS

---

