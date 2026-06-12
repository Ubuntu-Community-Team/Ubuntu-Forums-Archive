---
title: "UEFI Secure-Boot Using MOKUtil"
date: 2015-05-27
forum: General Help
---

### Post by naroyce on 2015-05-27
[http://docs.fedoraproject.org/en-US/Fedora/21/html/System_Administrators_Guide/sect-loading-signed-kernel-module.html](http://docs.fedoraproject.org/en-US/Fedora/21/html/System_Administrators_Guide/sect-loading-signed-kernel-module.html)
Has anyone gotten self-signed keys registered using MOKUtil?

For me,
$ mokutil --list-enrolled
//shows Canonical's Magrathea

$ sudo mokutil --import
//imports my key in a queue

$ sudo mokutil --list-new
// show's the key awaiting to be added

$ sudo reboot
//MOK starts after UEFI and before Ubuntu to confirm the key should be added

$ sudo keyctl list %:.system_keyring
//key is **NOT **showing, only Magrathea


$ sudo insmod /lib/modules/3.19.7+/updates/module.ko
```
insmod: ERROR: could not insert module /lib/modules/3.19.7+/updates/module.ko: Unknown symbol in module
```

$ dmesg -e | tail -n 100
```
[May27 18:53] Request for unknown module key 'devv64Kernel: cf283e428e15d96a5c4af1cd2d06aea5999f0b3d' err -11
[  +0.000100] au0828: module verification failed: signature and/or  required key missing - tainting kernel
[  +0.000053] au0828: Unknown symbol videobuf_streamoff (err 0)

```

I think I'll try
[https://wiki.ubuntu.com/SecurityTeam/SecureBoot](https://wiki.ubuntu.com/SecurityTeam/SecureBoot)
[http://jk.ozlabs.org/docs/sbkeysync-maintaing-uefi-key-databases/](http://jk.ozlabs.org/docs/sbkeysync-maintaing-uefi-key-databases/)
but it just looks scarier since it seems to be messing with the actual firmware

---

### Post by naroyce on 2015-06-02
Another issue relates to MOK:
```
$ efi-readvar Variable PK, length 639
PK: List 0, type X509
    Signature 0, size 611, owner eea2f5d2-c835-4e8c-ae00-c1605a53bb43
        Subject:
            CN=ASOCK - PK
        Issuer:
            CN=Root Agency
Variable KEK, length 1560
KEK: List 0, type X509
    Signature 0, size 1532, owner 77fa9abd-0359-4d32-bd60-28f4e78f784b
        Subject:
            C=US, ST=Washington, L=Redmond, O=Microsoft Corporation, CN=Microsoft Corporation KEK CA 2011
        Issuer:
            C=US, ST=Washington, L=Redmond, O=Microsoft Corporation, CN=Microsoft Corporation Third Party Marketplace Root
Variable db, length 3143
db: List 0, type X509
    Signature 0, size 1515, owner 77fa9abd-0359-4d32-bd60-28f4e78f784b
        Subject:
            C=US, ST=Washington, L=Redmond, O=Microsoft Corporation, CN=Microsoft Windows Production PCA 2011
        Issuer:
            C=US, ST=Washington, L=Redmond, O=Microsoft Corporation, CN=Microsoft Root Certificate Authority 2010
db: List 1, type X509
    Signature 0, size 1572, owner 77fa9abd-0359-4d32-bd60-28f4e78f784b
        Subject:
            C=US, ST=Washington, L=Redmond, O=Microsoft Corporation, CN=Microsoft Corporation UEFI CA 2011
        Issuer:
            C=US, ST=Washington, L=Redmond, O=Microsoft Corporation, CN=Microsoft Corporation Third Party Marketplace Root
Variable dbx, length 76
dbx: List 0, type SHA256
    Signature 0, size 48, owner 26dc4851-195f-4ae1-9a19-fbf883bbb35e
        Hash:e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855
Variable MokList has no entries
```
Note the "**MokList has no entries**" even though I enrolled my MOK not to mention Canonical already had it's own MOK enrolled:
```
...
[key 2]SHA1 Fingerprint: 76:a0:92:06:58:00:bf:37:69:01:c3:72:cd:55:a9:0e:1f:de:d2:e0
Certificate:
    Data:
        Version: 3 (0x2)
        Serial Number: 13348991040521802343 (0xb94124a0182c9267)
    Signature Algorithm: sha256WithRSAEncryption
        Issuer: C=GB, ST=Isle of Man, L=Douglas, O=Canonical Ltd., CN=Canonical Ltd. Master Certificate Authority
        Validity
            Not Before: Apr 12 11:12:51 2012 GMT
            Not After : Apr 11 11:12:51 2042 GMT
        Subject: C=GB, ST=Isle of Man, L=Douglas, O=Canonical Ltd., CN=Canonical Ltd. Master Certificate Authority
        Subject Public Key Info:
            Public Key Algorithm: rsaEncryption
                Public-Key: (2048 bit)
                Modulus:
                    00:bf:5b:3a:16:74:ee:21:5d:ae:61:ed:9d:56:ac:
                    bd:de:de:72:f3:dd:7e:2d:4c:62:0f:ac:c0:6d:48:
                    08:11:cf:8d:8b:fb:61:1f:27:cc:11:6e:d9:55:3d:
                    39:54:eb:40:3b:b1:bb:e2:85:34:79:ca:f7:7b:bf:
                    ba:7a:c8:10:2d:19:7d:ad:59:cf:a6:d4:e9:4e:0f:
                    da:ae:52:ea:4c:9e:90:ce:c6:99:0d:4e:67:65:78:
                    5d:f9:d1:d5:38:4a:4a:7a:8f:93:9c:7f:1a:a3:85:
                    db:ce:fa:8b:f7:c2:a2:21:2d:9b:54:41:35:10:57:
                    13:8d:6c:bc:29:06:50:4a:7e:ea:99:a9:68:a7:3b:
                    c7:07:1b:32:9e:a0:19:87:0e:79:bb:68:99:2d:7e:
                    93:52:e5:f6:eb:c9:9b:f9:2b:ed:b8:68:49:bc:d9:
                    95:50:40:5b:c5:b2:71:aa:eb:5c:57:de:71:f9:40:
                    0a:dd:5b:ac:1e:84:2d:50:1a:52:d6:e1:f3:6b:6e:
                    90:64:4f:5b:b4:eb:20:e4:61:10:da:5a:f0:ea:e4:
                    42:d7:01:c4:fe:21:1f:d9:b9:c0:54:95:42:81:52:
                    72:1f:49:64:7a:c8:6c:24:f1:08:70:0b:4d:a5:a0:
                    32:d1:a0:1c:57:a8:4d:e3:af:a5:8e:05:05:3e:10:
                    43:a1
                Exponent: 65537 (0x10001)
        X509v3 extensions:
            X509v3 Subject Key Identifier: 
                AD:91:99:0B:C2:2A:B1:F5:17:04:8C:23:B6:65:5A:26:8E:34:5A:63
            X509v3 Authority Key Identifier: 
                keyid:AD:91:99:0B:C2:2A:B1:F5:17:04:8C:23:B6:65:5A:26:8E:34:5A:63


            X509v3 Basic Constraints: critical
                CA:TRUE
            X509v3 Key Usage: 
                Digital Signature, Certificate Sign, CRL Sign
            X509v3 CRL Distribution Points: 


                Full Name:
                  URI:http://www.canonical.com/secure-boot-master-ca.crl


    Signature Algorithm: sha256WithRSAEncryption
         3f:7d:f6:76:a5:b3:83:b4:2b:7a:d0:6d:52:1a:03:83:c4:12:
         a7:50:9c:47:92:cc:c0:94:77:82:d2:ae:57:b3:99:04:f5:32:
         3a:c6:55:1d:07:db:12:a9:56:fa:d8:d4:76:20:eb:e4:c3:51:
         db:9a:5c:9c:92:3f:18:73:da:94:6a:a1:99:38:8c:a4:88:6d:
         c1:fc:39:71:d0:74:76:16:03:3e:56:23:35:d5:55:47:5b:1a:
         1d:41:c2:d3:12:4c:dc:ff:ae:0a:92:9c:62:0a:17:01:9c:73:
         e0:5e:b1:fd:bc:d6:b5:19:11:7a:7e:cd:3e:03:7e:66:db:5b:
         a8:c9:39:48:51:ff:53:e1:9c:31:53:91:1b:3b:10:75:03:17:
         ba:e6:81:02:80:94:70:4c:46:b7:94:b0:3d:15:cd:1f:8e:02:
         e0:68:02:8f:fb:f9:47:1d:7d:a2:01:c6:07:51:c4:9a:cc:ed:
         dd:cf:a3:5d:ed:92:bb:be:d1:fd:e6:ec:1f:33:51:73:04:be:
         3c:72:b0:7d:08:f8:01:ff:98:7d:cb:9c:e0:69:39:77:25:47:
         71:88:b1:8d:27:a5:2e:a8:f7:3f:5f:80:69:97:3e:a9:f4:99:
         14:db:ce:03:0e:0b:66:c4:1c:6d:bd:b8:27:77:c1:42:94:bd:
         fc:6a:0a:bc
```
I just want my driver to be signed and run under a secure-boot environment.
Do I have to start at the top replacing the PK with my own, sign my own shim, own kernel...??

It just seems that maybe this topic is too difficult to even comment on, that nobody uses custom drivers, or they just don't run with secure-boot.

---

### Post by oldfred on 2015-06-02
I do not know about it, but have a link, than may have some info.

 Added Fedora key with MokManager to secure boot Fedora from Ubuntu
[http://ubuntuforums.org/showthread.php?t=2260361](http://ubuntuforums.org/showthread.php?t=2260361)

---

### Post by naroyce on 2015-06-02
Thanks, but nope: [http://ubuntuforums.org/showthread.php?t=2260361&p=13208172#post13208172](http://ubuntuforums.org/showthread.php?t=2260361&p=13208172#post13208172)
I had already put my key in via mokutil. I only outputted Key2 which is Canonical's to prove that even their key isn't being found via keyctl nor efi-readvar.

To add more thoroughness:
From mokutil --list-enrolled Key1:
```
X509v3 extensions:            X509v3 Basic Constraints: critical
                CA:FALSE
            X509v3 Key Usage: 
                Digital Signature
            X509v3 Subject Key Identifier: 
**                24:7A:89:AA:90:34:5C:8E:21:BD:AD:8A:2E:ED:EC:A2:09:82:4C:FB**
            X509v3 Authority Key Identifier: 
                keyid:16:87:30:FD:33:A8:F8:F9:46:49:B1:94:30:C6:C5:B7:8B:06:69:70
```
From journalctl after insmod for the module (copied from /lib..kernel...module) I signed:
```
Request for unknown module key 'devx64Signer: **247a89aa90345c8e21bdad8a2eedeca209824cfb**' err -11
```
(and yes, I know keys and names have changed from my OP as I would reinstall and start all over sometimes)

---

