---
title: "Signing dkms drivers with Machine Owner Key (MOK)"
date: 2016-07-31
forum: General Help
---

### Post by adempewolff on 2016-07-31
Since kernel version 4.4.0-20, EFI_SECURE_BOOT_SIG_ENFORCE has been enabled--meaning that all kernel modules must be signed by a trusted key.  Most modules are shipped already signed by a trusted key, however any modules that need to be build by the user themselves (ie. using dkms) are unsigned and will fail to load with a message similar to the one below.
```
modprobe: ERROR: could not insert 'vboxdrv': Required key not available
```
This is a problem for me because both virtualbox, and the proprietary NVIDIA drivers fall into the category of modules that need to be built by the user.

There are two possible solutions for this problem.

[LIST]
[*]**Disable secure boot**
Either in the bios or using ```
sudo mokutil --disable-validation
```
[*]**Sign the modules yourself **(originally suggested for ubuntu [here]("http://askubuntu.com/questions/760671/could-not-load-vboxdrv-after-upgrade-to-ubuntu-16-04-and-i-want-to-keep-secur/768310#768310")
> 

    [LIST=1]
[*]Create signing keys
       ```
openssl req -new -x509 -newkey rsa:2048 -keyout MOK.priv -outform DER -out MOK.der -nodes -days 36500 -subj "/CN=Descriptive name/"
```

[*]Sign the module (vboxdrv for this example)
       ```
sudo /usr/src/linux-headers-$(uname -r)/scripts/sign-file sha256 ./MOK.priv ./MOK.der $(modinfo -n vboxdrv)
```
[*]Register the keys to Secure Boot
       ```
 sudo mokutil --import MOK.der
```
       Supply a password for later use after reboot
       Reboot and follow instructions to Enroll MOK (Machine Owner Key). Here's a sample with pictures. The system will reboot one more time. After the reboot, you may also need to sudo modprobe vboxdrv to load the module.
[/LIST]



[/LIST]

The later option is more appealing because it doesn't require disabling a security feature.  Furthermore, I briefly had this option working (for virtualbox modules at least, it was still buggy for the NVIDIA modules).  However after reinstalling Ubuntu a couple times to try and fix discrete graphics problems I can't get it working anymore.

It looks like the key was enrolled correctly

```

austin@austin-ThinkPad-P50:~$ mokutil -l
[key 1]
SHA1 Fingerprint: 01:8e:5c:78:1e:8c:fe:df:5c:d4:4d:84:89:83:b0:69:16:50:e0:62
Certificate:
    Data:
        Version: 3 (0x2)
        Serial Number: 17112920472065278886 (0xed7d4e804ef603a6)
    Signature Algorithm: sha256WithRSAEncryption
        Issuer: CN=Austin Dempewolff
        Validity
            Not Before: Jul 31 10:02:30 2016 GMT
            Not After : Jul  7 10:02:30 2116 GMT
        Subject: CN=Austin Dempewolff
        Subject Public Key Info:
            Public Key Algorithm: rsaEncryption
                Public-Key: (2048 bit)
                Modulus:
                    00:e3:88:c5:c7:1a:d6:29:0f:98:e5:50:c1:33:49:
                    fb:e7:39:64:b9:95:17:6e:67:dd:b9:f2:7b:bf:55:
                    1d:63:24:30:ac:46:0a:ac:ad:81:6d:f3:7d:f8:b7:
                    4f:5c:6e:bf:19:e3:b1:1b:e6:65:ce:b7:a2:a6:48:
                    49:34:8d:14:7c:7d:59:d0:a4:62:77:48:a7:13:41:
                    b4:51:8c:ab:e7:01:50:e2:d0:aa:77:4c:cc:a8:56:
                    f0:06:27:b3:aa:22:da:fd:94:43:e3:65:81:fb:57:
                    be:4e:81:9d:41:45:0d:a9:55:3c:ae:a5:4f:b3:27:
                    c5:88:54:b9:a8:47:50:2a:11:3a:77:2f:69:a8:15:
                    c1:00:d5:9a:1e:e5:cc:ab:5f:be:32:2c:be:95:81:
                    00:17:45:11:49:7b:b5:33:35:ac:97:e0:18:5f:17:
                    74:44:07:f4:58:4d:e3:6e:0e:f2:40:63:c1:88:6e:
                    5c:d1:47:02:6a:5b:c6:a4:39:19:ed:b7:b8:29:02:
                    87:8b:b8:01:e1:10:ad:1f:e1:8f:7a:02:eb:69:1d:
                    06:a8:08:98:70:26:66:91:b7:2c:00:05:39:a0:5f:
                    91:a8:03:44:b5:19:b8:8d:72:90:40:bb:91:8d:8e:
                    a2:90:1e:d4:78:e4:3f:04:94:ff:1f:44:17:8f:ae:
                    55:ff
                Exponent: 65537 (0x10001)
        X509v3 extensions:
            X509v3 Subject Key Identifier: 
                C6:A1:79:31:1D:F5:6D:EE:6A:06:B6:96:2E:4E:9F:19:79:BB:4E:15
            X509v3 Authority Key Identifier: 
                keyid:C6:A1:79:31:1D:F5:6D:EE:6A:06:B6:96:2E:4E:9F:19:79:BB:4E:15

            X509v3 Basic Constraints: 
                CA:TRUE
    Signature Algorithm: sha256WithRSAEncryption
         c9:5d:28:12:ea:fa:df:98:f0:2d:25:d7:3d:3f:8c:94:9a:cf:
         2d:b1:2e:de:4d:63:0f:6e:48:2b:75:1b:80:f2:2e:8a:56:a1:
         eb:69:9d:f2:2f:50:3a:56:5a:28:ac:98:7c:5d:1c:fe:1f:64:
         25:ee:72:bd:35:ad:0d:e3:64:f3:b4:73:2c:07:58:26:e6:8d:
         68:da:27:b6:1d:a4:74:82:88:55:8f:5b:80:31:26:90:bb:dd:
         c2:b4:86:8d:1c:c1:e6:f3:fc:04:04:c3:18:1a:c8:9e:8d:a8:
         1a:ca:94:46:ee:b7:5d:6e:50:ec:5e:ef:22:07:00:d5:5f:9f:
         97:9b:30:cf:04:45:b0:30:8a:0d:ad:5e:55:1e:fe:42:d0:e6:
         8e:63:54:8c:7d:4c:eb:6e:4b:b9:13:dc:7d:4e:5b:50:a9:75:
         e9:91:66:30:59:4f:77:de:82:66:fd:25:d7:f5:af:2b:f8:a8:
         ce:b5:7e:5a:44:ba:bf:da:bc:5e:bc:2d:bf:27:30:5b:21:d2:
         ec:84:b4:6a:79:65:78:34:2c:8d:60:a5:8b:a7:38:6a:20:28:
         3e:67:2a:1b:3f:5d:6e:e1:77:96:18:dd:be:1e:55:7e:27:3a:
         85:25:d2:e5:fd:a4:83:78:90:a7:c9:45:56:a1:ad:0b:8f:28:
         60:a9:6f:9c

[key 2]
SHA1 Fingerprint: 76:a0:92:06:58:00:bf:37:69:01:c3:72:cd:55:a9:0e:1f:de:d2:e0
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

And I signed my modules in exactly the same manner that I used before when it worked (with no errors generated).

```
sudo /usr/src/linux-headers-$(uname -r)/scripts/sign-file sha256 ./MOK.priv ./MOK.der $(modinfo -n vboxdrv)
```

However, when I try to load a signed module it fails.

```
$ sudo modprobe vboxdrv
modprobe: ERROR: could not insert 'vboxdrv': Required key not available
```

Very frustrating as exactly the same steps worked two days ago.

Any suggestions regarding how to go about debugging this would be highly appreciated.  I'm especially interested in suggestions along the following lines:
[LIST]
[*] How to check if the modules were signed correctly.
[*] How to check if the kernel has access to the enrolled MOK.
Interestingly the following commands don't appear to show the MOK--but I'm unsure if they should or not.
```
$ sudo cat /proc/keys
01b7ab74 I------     1 perm 1f030000     0     0 asymmetri Build time autogenerated kernel key: fc7c0e9f152f32eca50ea2d9722926e5127af244: X509.RSA 127af244 []
0bbb8103 I------     1 perm 1f030000     0     0 keyring   .dns_resolver: empty
158d48b9 I--Q---     1 perm 1f3f0000     0 65534 keyring   _uid_ses.0: 1
2176005b I------     1 perm 1f0b0000     0     0 keyring   .system_keyring: 1
23ff3c12 I--Q---     2 perm 1f3f0000     0 65534 keyring   _uid.0: empty
332af305 I------     1 perm 1f0f0000     0     0 keyring   .ima: empty
$ sudo keyctl list %:.system_keyring
1 key in keyring:
 28814196: ---lswrv     0     0 asymmetric: Build time autogenerated kernel key: fc7c0e9f152f32eca50ea2d9722926e5127af244
```
[*] Other suggestions
[*] Any insights on whether or not Canonical is working on a solution for signing dkms built modules.  If a solution is around the corner, I can probably afford to just wait it out rather then dealing with trying to sort this out.
[/LIST]

---

### Post by marcoil on 2016-11-18
I'm having exactly the same problem on a Lenovo Thinkpad X250, with kernel 2.4.0-42. The key is enrolled but it doesn't appear in /proc/keys, so the module can't be loaded. Any news?

---

