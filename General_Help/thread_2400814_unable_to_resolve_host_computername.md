---
title: "unable to resolve host computername"
date: 2018-09-10
forum: General Help
---

### Post by mystmaiden on 2018-09-10
I've looked this up several places but not found the exact problem. I haven't changed the computer name that I am aware of but now I can't seem to dl things via command line. I get 'unable to resolve host computername.  I found one recommendation to add it to the host list but it did not give specific instructions. Another site said it was \not recommended to change it directly because you could break sudo. I'm running Ubuntu Trusty.

Thanks in advance, 

mystmaiden

---

### Post by TheFu on 2018-09-10
Support for 12.04 ends soon (5 yrs for Unity and Server). Time to plan the migration.  Some 12.04 desktops are already out of support over a year, like Lubuntu, Xubuntu, Kubuntu ... 

What does the hostname and DNS have to do with each other?

Normal network troubleshooting should be followed:
* ping the router using the IP
* ping 8.8.8.8 
* ping google.com
* ping the other computer using the IP
* ping the other computer using the DNS name.  

This will only work if you have setup IP name resolution.  That would be using a DNS server or NIS or NIS+ or /etc/hosts file updates.  If you haven't done those things, I have no idea how one computer on a LAN would be able to resolve the hostname for another computer on the same LAN on a 12.04 system.  Later releases have a solution for this called Avahi, but for 12.04 I think avahi didn't work well, if at all.   With avahi, you'd use the "hostname.local" and both systems need to run avahi or some other ZeroConf compatible service.

---

