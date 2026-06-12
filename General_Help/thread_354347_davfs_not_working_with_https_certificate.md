---
title: "davfs not working with https certificate"
date: 2007-02-05
forum: General Help
---

### Post by tag on 2007-02-05
I am trying to automate the mount/umount cycle for a script that does some backup work for me. My local mail provider (gmx) offers WebDAV based storage, so I mounted the WebDAV drive as suggested here:

[http://de.gentoo-wiki.com/GMX_mediacenter_mounten](http://de.gentoo-wiki.com/GMX_mediacenter_mounten)
[http://www.zerties.org/tiki-index.php?page=WebdavHowto](http://www.zerties.org/tiki-index.php?page=WebdavHowto)

Now my problem is, that every time I run the mount command I am being asked whether the https certificate can be trusted of not. Of course it can be trusted, but this way it's impossible for me to automate. Is there some way to add this key to "known_hosts" or something similar, so that it stops bothering me? Here is what it does:

```
root@ubuntu60664m:~/.ssh# mount /home/tag/gmxstorage/
Server cerifticate could not be verified.
  presented for `mediacenter.gmx.net':
  Issuer:  Certification Services Division, Thawte Consulting cc, Cape Town, Western Cape, ZA
  Subject: GMX GmbH, Munich, Bayern, DE
  Fingerprint: 15:0d:5f:bd:db:fc:3c:4f:26:12:d7:04:73:bc:d1:2c:83:c9:1a:c5
If you can't verify the fingerprint the server may be faked
or there may be a man-in-the-middle-attack!
I am not a coward and accept the certificate anyway [y,N]?
```

---

### Post by tag on 2007-02-07
I tried to extract the ssl certificate and add it to know hosts with openssl, but failed. Can anybody tell me a valid parameter configuration for this?

---

### Post by ecor6633 on 2007-09-26
Reading that davfs2 man page online : [http://linux.die.net/man/8/mount.davfs]("http://linux.die.net/man/8/mount.davfs")
I tried to place a $HOME/.davfs2/certs file containing the server certificate but it didn't work

The strange thing is that when on ubuntu you try man mount.davfs or man davfs2.conf you will nerver read about those certificate files... 

Is there a "ubuntu" reason ?

*tag, in the code you display here, you're in .ssh folder which is not ssl. Known hosts is for ssh and i don't think there's the same thing in openssl.*

---

### Post by ecor6633 on 2007-12-03
On my laptop, after gusty update the problem is solved.

---

### Post by usingruby on 2008-02-24
Hi,

may you post all you did to make the mediacenter stuff working with davfs2? I did the following:
[LIST=1]
[*] I dumped the server certificate with "echo|openssl s_client -connect mediacenter.gmx..net:443 |openssl x509 -out gmxmediacenter.pem"
[*]copied file to /etc/davfs2/certs/gmxmediacenter.pem
[*] edited davfs.conf: changed #servercerts line to  "servercerts gmxmediacenter.pem"
[/LIST]

Certificate is still untrusted. davfs2 reads the certificate file. If I rename the file mounting is not possible error: missing servercert file.

What am I missing? Ubuntu is 7.10 with all updates installed.

Regards
Klaas

---

### Post by ecor6633 on 2008-02-25
Ok here is my folder tree :

~/.davfs2/
...|-- certs/
......|-- private/
......|-- trusted.pem
...|-- davfs2.conf
...|-- secrets


the ~/.davfs2/davfs2.conf contains this line (all the other lines are commented):
 servercert ~/.davfs2/certs/trusted.pem

secrets has chmod 0600 and contains my password for the server i wish to connect to.

trusted.pem file contains the Certificate Authority public key and the server public key but only the key not the textual informations. So it should contain :
-----BEGIN CERTIFICATE-----
<unreadable text>
-----END CERTIFICATE-----
-----BEGIN CERTIFICATE-----
<unreadable text>
-----END CERTIFICATE-----
and nothing else.

With that configuration, it works perfectly well for me. Maybe the difference is in the Certificate Authority.

---

