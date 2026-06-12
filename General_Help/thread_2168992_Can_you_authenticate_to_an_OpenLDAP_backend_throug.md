---
title: "Can you authenticate to an OpenLDAP backend through a AD Domain Controller?"
date: 2013-08-20
forum: General Help
---

### Post by michael25 on 2013-08-20
Hi Guys

First post and a a bit of strange question.

Ive has a OpenLDAP server running for years at work which holds users and home directories. I then have a suite of Apple Macs that authenticate against the OpenLADAP server. Its a nice little setup to maintain with very little issue. However i have now been tasked with integrating a suite of PC's into this environment with a AD Domain Controller. The objective set is to have all the PC's bound to the Windows domain for group policy etc but have it authenticating down to the OpenLDAP directory. This in theory would allow seamless usage between the PC and Mac environments in regards to single sign on and user folders.

The forums post several suggestions on authenticating OpenLDAP against AD but its the other way around I'm looking into.

Ive kept this sort to firstly get an indication if this would be possible?

Any pointers would be much appreciated.

Michael

---

### Post by TheFu on 2013-08-20
Sure you can. There is a PAM module just for this.  Google found this: [https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)
I've not bothered to set this up for most client machines, but I have done it for CIFS shares and 3rd party tools (mostly web-based) for the enterprise.

---

### Post by michael25 on 2013-08-20
Hi


Thank for for the response and link, ill have a read through and give it a try.

Just to confirm though we are looking for Active Directory to query OpenLDAP for the user database but all PC clients will be connected to Active Directory only.

Cheers

Michael

---

### Post by TheFu on 2013-08-20
> **michael25 said:**
> Thank for for the response and link, ill have a read through and give it a try.

Just to confirm though we are looking for Active Directory to query OpenLDAP for the user database but all PC clients will be connected to Active Directory only.

Never heard anyone going that direction, but my Windows connections are slowly dying off.

I've read about companies that have dumped AD completely (long time ago) and use OpenLDAP for Windows client auth and I know other companies that use AD for all authentication - which almost every Linux app/system can connect - lots of examples to connect almost any webapp to AD for users and auth.

Sorry, can't help with your specific need. I suck. ;(

---

