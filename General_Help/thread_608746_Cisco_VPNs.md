---
title: "Cisco VPNs"
date: 2007-11-10
forum: General Help
---

### Post by mark on 2007-11-10
I currently multi-boot into Ubuntu 7,10 and WinXP Pro, beacuse I need to access the Cisco VPN client software to connect to a number of my company's customer sites (as well as our own).  I've installed *vpnc* and it almost works - but it keeps choking on the group_password.  The Cisco .pcf files I was given are blank for the group_password line, but include a long string of gibberish characters for the enc_group_password line - which I take to mean "encrypted group password".

vpnc asks for the following (and I'm trying to map it from the .pcf file):

Enter IPSec gateway address: xx.xxx.xxx.xx
Enter IPSec ID for xx.xxx.xxx.xx: 
Enter IPSec secret for @xx.xxx.xxx.xx: 
Enter username for xx.xxx.xxx.xx: mtomlinson
Enter password for [email]mtomlinson@xx.xxx.xxx.xx[/email]: 

Does anybody know how to translate a .pcf file into a successful vpnc connection under Linux?

Thanks,

Mark

---

### Post by mark on 2007-11-10
No matter what I've tried, I keep getting:

vpnc: hash comparison failed: (ISAKMP_N_AUTHENTICATION_FAILED)(24)
check group password!

Help!

---

### Post by SeanBlader on 2007-11-13
Mark check out this thread:
[http://ubuntuforums.org/showthread.php?t=500504](http://ubuntuforums.org/showthread.php?t=500504) 

That's what I used successfully in Feisty. It's been a little less reliable in Gusty unfortunately.

---

