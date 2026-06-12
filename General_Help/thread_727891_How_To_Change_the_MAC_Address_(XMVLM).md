---
title: "How To Change the MAC Address?? (XM/VLM)?"
date: 2008-03-18
forum: General Help
---

### Post by matey3 on 2008-03-18
Does anyone know what is the exact command to change a virtual NIC's HW Addr (xenbr0) in my case- ?

What happened (I think) was that the server running xen crashed and now ifconfig reports one of the virtual nics mac address as  FE:FF:FF:FF:FF:FF ..well they all have FF as their addr (except for the last 2 digit i think)  and I got here in the middle of this mess and need to change the MAC address back to what XEN is expecting (00:16:3E:37:A1:1C)

any ways I thought if I could change that hw addr instead of looking for xen files to edit , my chances would be better?

thanks for any help...
''man ifconfig'' was no help as usual.. i donno why these man files cause ppl to come to these forums? lol ;) they mix codes with abbreviated english and all those damm brackets etc..make a big mess where i - a beginner- will be confused as hell ...and as to what is the command and what is for me to read? and no example of any kind in them help files either.. eekh..  none of their example works?! (and why do they use CAPs? if the OS is case sensitive?
lol.. ;-)


thanks a lot anyways....

---

### Post by bimmerd00d on 2008-03-18
I might be horribly wrong, so someone please correct me if i am.

```
sudo ifconfig eth0 ether 00:00:00:00:00:00
```

Obviously replacing eth0 with whatever you're using.  If it works, you'll need to make a script that does this upon every boot.

---

### Post by matey3 on 2008-03-18
thank you for reply.
i still get unknown host ether?
I used xenbr0 instead and also moved the commands around to no avail?

I'll try some more stuff later thanks a lot.. and thanks for the script idea, i think that will work great once i get this down..
:)

---

### Post by bimmerd00d on 2008-03-18
> **matey3 said:**
> thank you for reply.
i still get unknown host ether?
I used xenbr0 instead and also moved the commands around to no avail?

I'll try some more stuff later thanks a lot.. and thanks for the script idea, i think that will work great once i get this down..
:)

I've got a test box at work i'll play with when i get there in a few hours and reply with what I find.  This worked on my osx86 box to get it working, and i figured osx=unix=linux lol.  Please nobody flame me for that :)

---

### Post by matey3 on 2008-03-19
thanks...I think the problem is with the hardware type as u put it "ether" ..well this one is virtual so when i looked at the possible types of nics xen or vir was not mentioned in the list (--help file).
I got a new error though saying 
SIOCSIFHWADDR: No such device

:o 
any ways it is interesting and I hope I can find a solution.
thanks for taking the time...
:)

---

