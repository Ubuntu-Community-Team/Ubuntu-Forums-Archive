---
title: "Groundworks Console"
date: 2015-08-24
forum: General Help
---

### Post by aaron27 on 2015-08-24
I am currently having an issue with access to our Groundworks console. I  have a Ubuntu 12.04 machine running on VMware Player, we can login to  the GWOS console but all the tabs display the following error message

>  This portlet encountered an error and could not be displayed 

There  is no error code or any other indication of where the issue is stemming  from, and being inexperienced with Linux I am not sure where to  begin  looking. 

Any advice would be gratefully received.

---

### Post by aaron27 on 2015-08-28
Just as a note I have been advised to check the following:
> 
1)  A properly formatted entry in the /etc/hosts file for self resolution. As an example:
```
 192.168.5.50   [groundwork-server.domain.com]("http://groundwork-server.domain.com")   groundwork-server
```
 
Note that is you did not have this prior to install, you may need to re-install after you add the entry.
 
2)  Make sure there are not capitol letters in the hostname
 
3)  Check the credentials for the web services account in /usr/local/groundwork/config/ws_client.properties.  If you have local authentication configured, this account needs to match what is in the local database.  If you configured groundwork for LDAP integration, they need to match the credentials in LDAP.  Additionally, the web services account needs to be a member of  Authenticated and GWWsuser ldap groups.
[https://kb.groundworkopensource.com/display/DOC70/How+to+AD+and+LDAP+configuration](https://kb.groundworkopensource.com/display/DOC70/How+to+AD+and+LDAP+configuration)
 
4)  Make sure you have either a host A record in DNS or an entry for the groundwork server in the workstation you are accessing groundwork on - similar to the entry in #1

1 - was properly formatted and correct
2 - there are no capitals
3 - We had a seperate issue which we had to do these instructions to fix
4 - DNS has been setup and we are trying to access this on the local linux machine.

Is anyone able to offer advice on this?

---

