---
title: "Citrix problem 7.10"
date: 2007-11-12
forum: General Help
---

### Post by infurnus on 2007-11-12
"The Citrix ICA client version installed from this workstation does not meet  minimum requirements for security and support. Please report this non-compliancy to your local technical support to upgrade your system with ICA client 10.0 or later"

I have just installed the ICAClient to /usr/lib/ICAClient if i echo $ICAROOT i get /usr/lib/ICAClient. Steps i took: logged via web interface it runs all the scripts and at the end it fails with the error above i have installed the patch and followed the directions here [http://misconfig.blogspot.com/2007/05/installing-citrix-on-linux-ubuntu.html](http://misconfig.blogspot.com/2007/05/installing-citrix-on-linux-ubuntu.html)
I have also looked through citrix's knowledge base and cannot find an answer i did download all the certs off their website and put them under  /usr/lib/ICAClient/keystore/cacerts to make sure that wasnt a problem and i still receive the same error above. Can anyone shed light on my problem? 

I am running Ubuntu 7.10 and i have got the latest version of Citrix client from their website.
EDIT: This was working with dapper before some update was done. This happened in dapper so it has to be with the recent release.

---

