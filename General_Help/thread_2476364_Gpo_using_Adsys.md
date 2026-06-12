---
title: "Gpo using Adsys"
date: 2022-06-23
forum: General Help
---

### Post by jorgehenriques-2022 on 2022-06-23
Hi!

I have this scenario in Microsoft Azure:

- Windows Server 2019 with Active Directory
- Windows 10 Pro
- Ubuntu Desktop 22.04 LTS

I'm trying to create group policy objects for the Ubuntu virtual machine using adsys tool but it isn't working. I enabled the "client administrators" policy and added one user to make it "sudo"  (at Windows Server) and the i typed this command to update this policy into Ubuntu's terminal ( "adsysctl policy update -av" ) and then i got theses error messages:

"INFO No configuration file: Config File "adsys" Not Found in "[/home/username/etc].We will only use the defaults, env variables or flags. 
INFO Apply policy for linux-test (machine: true)  
INFO Apply policy for username@domain (machine: false) "

I don't know what to do... does anyone have a clue?

Thanks!

---

