---
title: "Authenticate to network printer"
date: 2007-06-18
forum: General Help
---

### Post by datube on 2007-06-18
Hi,

I work at a company which is completely W.nd.ws based. There are several OCE 3145 printers in the building at which users can print when they supply their company credentials at printer setup. I have no experience with setting up printers in Ubuntu/Debian and do not know how to translate the W.nd.ws configuration to Linux printing system. I also have no idea which protocol or 'stuff' like that is used to access those printers at this point.

What I do for the W.nd.ws-clients is: 1) Add a network printer 2) specify the URL like: *[http://location.url/printer/longnumber/.printer](http://location.url/printer/longnumber/.printer)*. 3) Add company user credentials at security options.

After that I can print and the documents are listed at the printer with the supplied username. 

How do I configure those printers in Ubuntu? Thanks for any help/guides on this.

---

### Post by timcredible on 2007-06-18
when you go through the 'add printer' wizard, there's options for providing windows username/password to a print server.  i've done it with AD, it works ok.  never tried your setup, but give it a try.

---

### Post by datube on 2007-06-27
That didn't work.. Still no luck...

---

