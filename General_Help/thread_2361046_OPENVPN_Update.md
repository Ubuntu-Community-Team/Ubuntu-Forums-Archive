---
title: "OPENVPN Update"
date: 2017-05-11
forum: General Help
---

### Post by feartheterrapin on 2017-05-11
My current OPENVPN version installed on 16.04LTS is 2.3.10.  This is the same version listed in the Ubuntu Software Center.  I see OPENVPN has been updated to 2.4.2.  Is it recommended to update my current version to  2.4.2? Will the USC soon have 2.4.2?  Are there any recommended update instructions?

---

### Post by #&amp;thj^% on 2017-05-11
```
"openvpn" versions published in Ubuntu
Zesty-updates (2.4.0-4ubuntu1.2): main/net
Zesty-security (2.4.0-4ubuntu1.2): main/net
Artful (2.4.0-4ubuntu1): main/net
Zesty (2.4.0-4ubuntu1): main/net
Yakkety (2.3.11-1ubuntu2): main/net
Xenial (2.3.10-1ubuntu2): main/net
Vivid (2.3.2-9ubuntu4): main/net
Trusty-updates (2.3.2-7ubuntu3.1): main/net 

```

 7 New bugs 

[https://bugs.launchpad.net/ubuntu/+source/openvpn/+bugs?field.status:list=NEW](https://bugs.launchpad.net/ubuntu/+source/openvpn/+bugs?field.status:list=NEW)

I'm running it now but if I were you I would just stick to the version you have now!

```
apt policy openvpn
openvpn:
  Installed: 2.4.0-4ubuntu1
  Candidate: 2.4.0-4ubuntu1
  Version table:
 *** 2.4.0-4ubuntu1 100
        100 /var/lib/dpkg/status
     2.3.10-1ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages

```

---

### Post by feartheterrapin on 2017-05-11
[**[COLOR=#000000][/COLOR]**]("https://ubuntuforums.org/member.php?u=2040855")@1fallen
Thanks.  I will hold off.

---

