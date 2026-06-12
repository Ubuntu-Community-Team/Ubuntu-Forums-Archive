---
title: "Make File or Folder immutable/unchangeable"
date: 2021-12-06
forum: General Help
---

### Post by rathorecdn on 2021-12-06
Hello, all the knowledgeable person here...
I'm a newbie and I recently changed my system from bloody/monitoring monster windows 10 to ubuntu LTS.

I am perfectly alright with ubuntu as it works with all of my peripherals and it does everything i needed, but one thing is very serious that my son is watching pornography on my system, i have somehow blocked all the pornography sites using energized porn ultimate list using hosts file, but he is more knowledgeable than me he mutated the hosts file and continue to pornography.

I want to know that is there any way to completely block pornograhical material using hosts file by making hosts file immutable even by root user? And by freezing dns resolving file to opendns family shield dns because opendns also blocks proxy servers by default so there will be no way to go to adult sites.

Please help me to resolve my issue.

Thanks in advance ..

---

### Post by TheFu on 2021-12-06
Completely?  No.  /etc/hosts files are a 20% solution, at best.  Same for DNS. Anyone with any technical skill can get around those.

Why can he modify the /etc/hosts file at all?  Don't give his account sudo and if you see he modifies it, ever, block his access to the system. You'll need to physically do this, since it is trivial for someone to bring their own OS on a flash drive and boot from that to do whatever they want.

If you like, you can do like enterprises do to control internet access, but if you have to ask how, then it is likely beyond your current skill and gaining the required skill would be months to years of knowledge .... which could just be gotten around with a flash drive if you allow him physically access to the router system.

I suspect the most practical answer is to switch all network connectivity over to a wifi dongle that you take with you when you leave daily - or give to your wife for control.

I'm unsure of your situation, but parental control needs to work and if disobeyed, all computer access needs to be removed.

If you want to do some research about this, first you'll need another computer that is physically unavailable to everyone in the house except you.  Only that system should have internet access as setup in the modem/router/AP.  Then setup a proxy server with whatever filters you like on that other system. All other computing devices in the house MUST use the proxy to get on the internet, period.  Without it, they don't get anywhere.  If you cannot physically secure the router and this other computer running the proxy, give up. Inside corporations, this is why there are locked network equipment closets and floors that normal employees cannot access.  Plus the threat of being fired if anyone violates corporate policy.  I doubt you can fire your son and suspect the other parent in the house may not back you up.

---

