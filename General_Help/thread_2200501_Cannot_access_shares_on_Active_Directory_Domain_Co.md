---
title: "Cannot access shares on Active Directory Domain Controller"
date: 2014-01-19
forum: General Help
---

### Post by steve72 on 2014-01-19
Trying to access (or even see) shares on a Windows Server 2008 AD DC results in failure. I can see shares OK on other Windows 2008 servers that are on the domain, but not those on the Domain Controller. smbtree shows nothing on the DC, but sees shares on other domain PCs / servers. I am running samba and Centrify Express on Ubuntu 12.0.4.3. I can authenticate OK to the domain, the Ubuntu has joined the domain as  computer, I can see the Windows network and computers (including the DC), but cannot see the shares on the DC. 

There is no difference with the DC firewall on or off. I've confirmed that ports (136/7/8, 445) are open and reachable on the DC. Others Windows PCs can access the DC's shares. 

Anyone know why this might be the case?

---

### Post by bab1 on 2014-01-19
> **steve72 said:**
> Trying to access (or even see) shares on a Windows Server 2008 AD DC results in failure. I can see shares OK on other Windows 2008 servers that are on the domain, but not those on the Domain Controller. smbtree shows nothing on the DC, but sees shares on other domain PCs / servers. I am running samba and Centrify Express on Ubuntu 12.0.4.3. I can authenticate OK to the domain, the Ubuntu has joined the domain as  computer, I can see the Windows network and computers (including the DC), but cannot see the shares on the DC. 

There is no difference with the DC firewall on or off. I've confirmed that ports (136/7/8, 445) are open and reachable on the DC. Others Windows PCs can access the DC's shares. 

Anyone know why this might be the case?

Turn on a little more debug.  Post the output of ```
smbtree -d3
```

---

