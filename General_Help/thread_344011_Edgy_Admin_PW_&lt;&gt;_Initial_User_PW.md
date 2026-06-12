---
title: "Edgy: Admin P/W &lt;&gt; Initial User P/W?"
date: 2007-01-22
forum: General Help
---

### Post by asdinnie on 2007-01-22
Hi

I have just installed Kubuntu 6.10 (being an exile from Mandriva).

Trying to configure my new system with no success because the Admin/root password fails.

The documentation states that the initial user password becomes the root password by default.

The initial user id is me (uid 1000) and my user password works fine to enter KDE.

However, once I try anything that requires root access (eg. Adept) using my user password, I get the error "Conversation with su failed".

The install seemed to work fine.  It was a clean install onto a newly repartioned system.

So I cannot progress much further to configure this system.

Can someone pls help.

TIA

Andy

---

### Post by taurus on 2007-01-22
Open a terminal and see what happens when you run this command?

```
sudo aptitude update
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by asdinnie on 2007-01-22
Hi Taurus.

Thx for the quick reply.

Tried "sudo aptitude update" and entered the same password that failed above when prompted by su.

Result: It kick started aptitude. 
Aptitude is now getting the security updates for Edgy it seems (not used to apt, only rpmi).

So the root password works in a terminal but not within KDE?
Got me stumped.

BTW my typing of passwords is pretty good.  I had a number of goes at it in different KDE programs plus checked my caps lock key, etc.

Cheers

Andy

PS Its way beyond bedtime here and need to work tomorrow! So I'll check out replies tomorrow night our time.

---

### Post by taurus on 2007-01-22
What's the output of this command from a terminal?

```
id
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by asdinnie on 2007-01-23
Hi Taurus

id gives:
uid=1000(asd) gid=1000(asd) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(au                                                              dio),30(dip),44(video),46(plugdev),109(lpadmin),111(scanner),113(admin),1000(asd)

Curiously the problem appears to be fixed today.
Once I installed the updates last night & restarted the PC this PM, I could run Adept.
Same password used.  All that changed was the install and system reboot.
Wierd to me.

Many thanks for your help.

Cheers

Andy

---

