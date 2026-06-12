---
title: "Photorec. E: you don't have enough free space in /var/cache/apt/archives/"
date: 2020-02-01
forum: General Help
---

### Post by visualdrome on 2020-02-01
Hello to everyone
 I installed Lubuntu 18.04.3 LTS on an Intel Atom N270
 

 I had a problem with an external HD so I used Photorec to recover some files
 The external HD is 4TB
 I haven't connected another 4TB HD to recover files so...now the computer is blocked and it didn't boot (LogIn loop).
 

 I tried different solutions founded on the net:
 
[LIST]
[*]recovery to free up space but nothing happens
[*]sudo apt-get     clean/autoclean/autoremove/upgrade (nothing happens) 
[*]remove and install     the DM: I successfully deinstalled it (sudo     apt-get purge lightdm) but I can't reinstall it (sudo     apt-get install lightdm) because there's no free space and I     get the error message E: you don't have enough free space in     /var/cache/apt/archives/ 
[/LIST]
 

 If i check the computer space (df -h) I get
 
[LIST]
[*]/dev/sda1 100% Use     and 0% Avail 
[/LIST]
 

 I think my disk it's full.
 

 What can I do?
 Thanks

---

### Post by TheFu on 2020-02-03
Boot from the install media and delete non-OS files on the internal storage.  Probably just easiest to delete all the files under /home/xxxxxxx/* on the same partition as the installed OS.  Don't bother deleting /home/ stuff on the install/Try Ubuntu media.

I had an N270 based Asus Eee in 2010. Ouch.

---

### Post by rsteinmetz70112 on 2020-02-03
Boot from live media and see if you can't find some files to delete.

You might try clearing old logs in /var/log and see if that opens up enough space.
You might try sudo apt autoclean.

These won't get you much but it might be enough.

---

### Post by CelticWarrior on 2020-02-03
If I remember correctly those small notebooks used to come with a 160GB HDD.

There's no way you can cram 4TB on that, really. It was doomed to fail from the start.

---

### Post by visualdrome on 2020-02-03
> **TheFu said:**
> Boot from the install media and delete non-OS files on the internal storage.  Probably just easiest to delete all the files under /home/xxxxxxx/* on the same partition as the installed OS.  Don't bother deleting /home/ stuff on the install/Try Ubuntu media.

I had an N270 based Asus Eee in 2010. Ouch.

> **rsteinmetz70112 said:**
> Boot from live media and see if you can't find some files to delete.

You might try clearing old logs in /var/log and see if that opens up enough space.
You might try sudo apt autoclean.

These won't get you much but it might be enough.
I alredy tried autoclean and other simialr commands but without success.
At the end I reformatted and reinstalled lubuntu!

> **CelticWarrior said:**
> If I remember correctly those small notebooks used to come with a 160GB HDD.

There's no way you can cram 4TB on that, really. It was doomed to fail from the start. 

Yes, it was a superbig mistake.
Now I bout another 4Tb HardDisk, NTFS formatted, where I want to save the recovered files.
It's the right procedure?

Thanks

---

### Post by CelticWarrior on 2020-02-03
> **visualdrome said:**
> 
Yes, it was a superbig mistake.
Now I bout another 4Tb HardDisk, NTFS formatted, where I want to save the recovered files.
It's the right procedure?


As long as the destination drive works with the computer then yes, it's doable, but it'll take an awful long time with two drives in that flaky USB2.0 controller with a recovery software running with a CPU with a computing power similar or worse than a 20 years old desktop and capped at what? 1GB of RAM? Good luck with that and lots of patience.

---

### Post by visualdrome on 2020-02-03
> **CelticWarrior said:**
> As long as the destination drive works with the computer then yes
What do you mean? What can happen?

> **CelticWarrior said:**
> ... and lots of patience.
It says 60/70 hours (3 days); It's a computer used only for download and streaming

---

### Post by TheFu on 2020-02-03
> **visualdrome said:**
>  
Now I bout another 4Tb HardDisk, NTFS formatted, where I want to save the recovered files.
It's the right procedure?

NTFS should be avoided, unless the source file system is also NTFS.  NTFS is not suitable for Linux files, which must have owner, group, permissions and ACLs to be useful.

---

### Post by CelticWarrior on 2020-02-03
> **TheFu said:**
> NTFS should be avoided, unless the source file system is also NTFS.  NTFS is not suitable for Linux files, which must have owner, group, permissions and ACLs to be useful.

True, but the original drive is also external and probably NTFS as well and used as simple storage so, I suppose ownership/permissions, etc. isn't relevant in this case?

---

