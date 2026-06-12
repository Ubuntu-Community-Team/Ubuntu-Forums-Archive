---
title: "digest-md5 auth with postfix in ubuntu server 12.04 lts"
date: 2014-05-27
forum: General Help
---

### Post by aaron44 on 2014-05-27
Hi all, first time poster and somewhat noobish to Linux, please be gentle :)


I set up an ubuntu 12.04lts server, and then attempted to set up a Postfix mail server with ssl support using the following document: [https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto).  I stopped before the clamstp section, as I don't need to use that.

After following the document, I was able to authenticate with cram-md5 to my server using Mulberry as an email client.  Here's the issue: I am setting this up as a test server for recreating customer defects, and they want a server that supports Digest-md5 as the only authentication method.  I had hoped all I needed to do was change to digest-md5 in the /etc/dovecot/dovecot.conf (auth_mechanisms section) and /etc/postfix/sasl/smtpd.conf (mech_list) files.  However this did not work either with Mulberry or using the Imtest program.  My suspicion is that the adddovecotusers script in the setup guide creates passwords based on cram-md5 and the hashes won't work for digest-md5.  I've messed around with more settings than I can even describe (thank god for snapshots on vmware) and am clueless at how to proceed.  Even Google doesn't give me much help looking for properly configuring digest-md5 with postfix instead of cram.  Is there anyone that could help me out?  Thanks a ton.

Aaron

---

### Post by aaron44 on 2014-05-28
anybody? a decent number of views, but no replies :(

---

