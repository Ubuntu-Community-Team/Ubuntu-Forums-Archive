---
title: "Ecryptfs,cryptsetup p/w prompt enter key failures"
date: 2013-12-07
forum: General Help
---

### Post by helloworld1215 on 2013-12-07
[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1258900](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1258900)

Reported as bug, however if you have any idea why boot input prompts are behaving as such, please specify how to resolve. 

1. With ecryptsfs:

 /etc/fstab:
/root/ecfs_data /root/ecfs ecryptfs rw,exec,suid 0 0
 a) Pressing the enter key quickly with no other input returns that some input is required.
b) Pressing the enter key the first time subsequent to some input  appears to append a return character to the password string. Pressing  the enter subsequent to that submits the now incorrect password  resulting in failure.
c) If you hold the enter key, it sends multiple return characters, some  times some of them appear to be appended to the password string, until  eventually they start being sent to subsequent prompts.  It would appear  that sometimes multiple return characters are added to the password  string because the signatures change on various attempts.
 c) may be relevant in the sense that the holding the enter key in #2 facilitates a workaround.
 2. The password prompt created by cryptsetup exhibits similar behavior but can be worked around by holding the enter key.
 /etc/fstab:
/root/e_data /root/e crypto_LUKS defaults 0 0
 b) Pressing the enter key without any input specifies that the password was incorrect.
a) Pressing the enter key the first time subsequent to some input  appears to append a return character to the password string. A  subsequent press of the enter key submits the now incorrect password.
c) Holding the enter key subsequent to entering the password facilitates  mounting. However, there are no further messages specifying success.  Boot continues.
 In both instances of #1 and #2, the data from previous boot instructions appears past the `Password:` semicolon, ie:
 Password: /dev/sda1: 333 files, 13026/126976 clusters
 This does not appear to affect the success of 2.c.
 3. The following may look like it is unrelated but consider the fact  that the password prompt is not halted and the fact that this should in  fact work.
 The reason why I think the following is related is because I think  that it's possible that it is returning from the password prompt and  failing the crypttab execution asynchronously if that is perhaps how the  relevant executables (upstart?) operate.
 /etc/crypttab:
swap_e /dev/sda8 /dev/urandom swap
 /etc/fstab:
/dev/mapper/swap_e none swap sw 0 0 #<-- if this is before the next  line, it specifies that /dev/mapper/swape does not exist, and auto  returns from the ecryptfs password prompt
/root/ecfs_data /root/ecfs ecryptfs rw,exec,suid 0 0
 As specified, when the ecryptfs mount entry in fstab is after the  swap mount, it specifies that the /dev/mapper/swape disk does not exist  and auto skips the ecryptfs mount, auto returning from the password  prompt and said mount failure in /var/log/boot.log.
 System:
 Ubuntu 12.04.3 LTS
ecryptfs-utils 96-0ubuntu3
cryptsetup-luks 2:1.6.1-1ubuntu1
libpam-mount 2.14-1

---

