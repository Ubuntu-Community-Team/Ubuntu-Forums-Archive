---
title: "VMware help"
date: 2007-04-01
forum: General Help
---

### Post by neogenesis213 on 2007-04-01
I was trying to get seamless virtualisaiton working following the instruciton [here]("https://help.ubuntu.com/community/SeamlessVirtualization").

There is a problem when I execute the command below, with releveant, IP username, password offcourse-

rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Internet Explorer\iexplore.exe" <IP of VM>:3389 -u administrator -p password

I recieve the following error "ERROR: expected CC, got 0x0" and nothing happens.

i'm using host-only networking on VMware.
the IP being 192.168.53.1 for my XP guest. 

I can ping XP from the Host-feisty but I can't ping from XP. I can't access shared folders or use the internet.



Not sure if its related, but I had to disable the ath0 bridge device in my VMware configuration as it kept saying failed at the end of the configuration. 
Then the only way I could finish the configuratin succesfully and hence run VMserver was if i disabled it. 

Is there a way out of this mess?

---

