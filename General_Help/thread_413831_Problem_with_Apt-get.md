---
title: "Problem with Apt-get"
date: 2007-04-19
forum: General Help
---

### Post by trevor.stuart on 2007-04-19
Whenever I try to run apt-get update I get the following:
tstuart@C1031:~/Desktop$ sudo apt-get update
Ign [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg
Ign [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Ign [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
  403 Forbidden
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release
Err [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
  403 Forbidden
Err [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages
  403 Forbidden
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
  403 Forbidden
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper Release.gpg
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages

Eventually it will just fail... Anyone know what could be causing this, or how I could fix it?

Regards,

Trevor

---

### Post by ajgreeny on 2007-04-19
I see you have mainly dapper repos you're trying to access, but then in amongst them suddenly you have  [http://www.getautomatix.com]("http://www.getautomatix.com/") feisty Release.

I don't know if this is anything to do with your problem, but it seemed worth mentioning.  Did the difficulty appear after trying to use automatix or al least after downloading automatix to your machine?  Are you running dapper (6.06) or a more updated version of ubuntu?

---

### Post by trevor.stuart on 2007-04-19
I have this problem with all package managers... I'm running Kubuntu 6.06. Apt-get does this, Adept, Automatix, etc... I first noticed the problem when trying to run the attached file to update my thunderbird, but that doesn't mean that's when the problem started, it's just when I first noticed it... I tried going into adept and removing the automatix feisty link you noticed... I then tried a fetch updates in adept and it gets to 28% and slows down, I think it's actually stopping...

Regards,

Trevor

---

### Post by ajgreeny on 2007-04-19
Just out of interest, have you tried synaptic as well as adept.  Although I use kubuntu, I prefer synaptic to adept myself and don't use adept other than the adept-notifier, which tells me updates are ready.  Then I use synaptic to get them.  Just my preference!

---

### Post by trevor.stuart on 2007-04-19
I did try synaptic... Out of curiosity I brought my laptop home tonight and tried it... Everything is working fine. This makes me thing the firewall at work, or DNS server is blocking what I need access to. As I'm the admin unblocking the necessary ports isn't an issue, but I have no idea what needs to be unblocked. I know that port 80 and port 21 are wide open in both directions. Obviously something else needs to be open, but I don't know what. I'd appreciate any help you can give!

Regards,


Trevor

---

### Post by eentonig on 2007-04-19
traffic jams. Wait untill the hype is over before doing the upgrade. If you do it now, you'll be waiting forever before everything is downloaded.

---

### Post by trevor.stuart on 2007-04-19
that would explain why I'm finding it so slow to download now from home. But would that have caused the 404 errors I got above? 
I guess it would if the servers were overloaded... I'll try again tomorrow from work and see if I get connected...

---

