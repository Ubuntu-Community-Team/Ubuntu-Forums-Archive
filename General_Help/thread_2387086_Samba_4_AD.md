---
title: "Samba 4 AD"
date: 2018-03-14
forum: General Help
---

### Post by semperfi1775 on 2018-03-14
Hello,  I was looking at implementing Samba 4 Active Directory.   I have a user base of about 10 employees.  However,  typically no more than 5 users are active at any given time. 
Many of these users share systems, so roaming profiles seems to be a viable solution.   

The current solution is a single Win2012 Essentials AD\File server, with 5 old desktops running win10.

I bought 5 new laptops (win10).   I've migrated email & file storage to GSuite.   However, I still have some local services, such as; printing, an on-prem app that require authentication and authorization. 

I took two older laptops (decent laptops Dell e6430's - 4gb memory, 250 storage), and created two Ubuntu 16.04 OpenLDAP systems.  Then used pGina on the win10 systems, to authenticate into the LDAPservers.
This was fine, until the "learning curve",  many users are use to the roaming profile solution that was implemented when 2012 Essentials was introduced.

We are a non-profit with a limited budget.
[LIST=1|INDENT=2]
[*]What are the System\Hardware Samba 4 Active Directory requirements ?
[LIST=1]
[*]could the e6430's meet the requirement as a (PDC, BDC)?
[LIST=1]
[*]I know using laptops, maybe not ideal. but, its what we have, and our user base is small.
[*]the old 2012 Essentials box will more than likely be repurposed for something else.
[/LIST]
[/LIST]

[*]Can the roaming profiles, be placed on a different Samba share ? So, the profiles could be backed up.
[LIST=1|INDENT=1]
[*]if the e6430's meet the requirement; It seems lot for a PDC and BDC, to have AD, DNS, DHCP, Profile Sharing roles. Then again, we talking about 5 active users.
[/LIST]

[*]OpenLDAP works very well. I do manage it with JXplorer, pwm & syncs with GSuite fine.
[LIST=1]
[*]I'm not sure how difficult it would be to configure LDAP roaming profiles. Would a Samba share, work ? if so, how ?
[/LIST]
[/LIST]

Thank you for your help & time

---

