---
title: "openssh-server askes me for the passphrase"
date: 2022-06-11
forum: General Help
---

### Post by NotionCommotion on 2022-06-11
Hi.  Making the move from Centos to Ubuntu! Just did a new desktop install this morning, and even though I used the desktop install, will be using it more as a server and will need to access remotely via ssh.  It appears that a ssh server doesn't come by default so I install openssh-server.

I then generated rsa public/private keys on windows using puTTYgen and used a passkey, have puTTY use the private key and put the public key in Ubuntu's ~/.ssh/authorized_keys.  When logging on, however, I am being asked for the passkey, and when entering it, I am authenticated.

What am I doing wrong?  Thank you!

```
login as: michael
Authenticating with public key "rsa-key-20220611"
Passphrase for key "rsa-key-20220611":
Welcome to Ubuntu 22.04 LTS (GNU/Linux 5.15.0-37-generic x86_64)


 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage


0 updates can be applied immediately.


Last login: Sat Jun 11 09:24:28 2022 from 10.120.11.102
michael@michael-HP-EliteBook-830-G5:~$

```

```
Jun 11 09:42:44 michael-HP-EliteBook-830-G5 sshd[4357]: Accepted publickey for michael from 10.120.11.102 port 51158 ssh2: RSA SHA256:Tfb9eUbEiYJySKgFeDoPQlcp2vsKbcKX1fXLVLvXkEA
Jun 11 09:42:44 michael-HP-EliteBook-830-G5 sshd[4357]: pam_unix(sshd:session): session opened for user michael(uid=1000) by (uid=0)
Jun 11 09:42:44 michael-HP-EliteBook-830-G5 systemd-logind[656]: New session 9 of user michael.

```
```

michael@michael-HP-EliteBook-830-G5:~$ cat .ssh/authorized_keys
ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEAlTd6XcdF/2H7HGag/l3aG8BtZL9fh2JlT51MmpZCFc3Yd0/Z11UF4sBPvQQxCp4jLDHaZXTfBPdmM/QsuuGyvVJcInL42fMvitO//G6Gr2LEkcsWnoduie2f3oJPO7ejBJENTHbIzLWHU/OHfv0r5XIrIjtbe6lLKy0PRDMTikImstHLMWGpv5lzKYFtqFuvAsQauZ5h54Xf2TuIXm8rtZ3e7TFZ6ymYJHpR7TXUS+VhInWvT9PuS+oR55xj3xT2ElM5sTauLONn9A1VTf7rmmsM85Zow/9
michael@michael-HP-EliteBook-830-G5:~$

```

```
---- BEGIN SSH2 PUBLIC KEY ----
Comment: "rsa-key-20220611"
AAAAB3NzaC1yc2EAAAABJQAAAQEAlTd6XcdF/2H7HGag/l3aG8BtZL9fh2JlT51M
mpZCFc3Yd0/Z11UF4sBPvQQxCp4jLDHaZXTfBPdmM/QsuuGyvVJcInL42fMvitO/
/G6Gr2LEkcsWnoduie2f3oJPO7ejBJENTHbIzLWHU/OHfv0r5XIrIjtbe6lLKy0P
RDMTikImstHLMWGpv5lzKYFtqFuvAsQauZ5h54Xf2TuIXm8rtZ3e7TFZ6ymYJHpR
7TXUS+VhInWvT9PuS+oR55xj3xT2ElM5sTauLONn9A1VTf7rmmsM85Zow/9L3JDP
vYfebgDEX2A8w987bCsFKGXrHIyecUXXJ9kwG/KIYyYXLPzxAw==
---- END SSH2 PUBLIC KEY ----

```



```
PuTTY-User-Key-File-2: ssh-rsa
Encryption: aes256-cbc
Comment: rsa-key-20220611
Public-Lines: 6
AAAAB3NzaC1yc2EAAAABJQAAAQEAlTd6XcdF/2H7HGag/l3aG8BtZL9fh2JlT51M
mpZCFc3Yd0/Z11UF4sBPvQQxCp4jLDHaZXTfBPdmM/QsuuGyvVJcInL42fMvitO/
/G6Gr2LEkcsWnoduie2f3oJPO7ejBJENTHbIzLWHU/OHfv0r5XIrIjtbe6lLKy0P
RDMTikImstHLMWGpv5lzKYFtqFuvAsQauZ5h54Xf2TuIXm8rtZ3e7TFZ6ymYJHpR
7TXUS+VhInWvT9PuS+oR55xj3xT2ElM5sTauLONn9A1VTf7rmmsM85Zow/9L3JDP
vYfebgDEX2A8w987bCsFKGXrHIyecUXXJ9kwG/KIYyYXLPzxAw==
Private-Lines: 14
CWUP2FOuoJYQgTQrErBXOIfWqy3WPOIgw/tS7311LsTiJCFd16Ug6g+lpu5vJLN0
MmET1l6d+VdHhyCPYzKXyoshk8Fd5bIrmsc+CVh9avQjjiWHsYG5MW3hJx30fqJu
5t8JrkLnSYLrnXS7/4UMukbi27T1hKqAtnrDe8nAQN0l4tcVckVxo+cX/qvSiXUM
LbA1652F7frRns1YEeovxqOKhNpdo5n/J0sHXZKu2wghZ5vajAWXSsvkRG483gBK
Pr1aoGfIKOrMcI7Hgpzbv3W5CgFm7zJkgHcZwlRKKRg6f4lgHDE/9EXpYC7vWJv/
vknAi0ZTWnTjlvp3c7eO5h1/V5ozF7fU7dcXddRUK2cp7lQ/R67UVz0FMCMeNeEX
4TzvV1GLI8IGKa3cfgLSJDOg2FlyiKXvDwc+PbmOdJUyTULs9++Sgga84kp6wJmA
uNH9K/S17FNsUlS6u5j7YN04itaxZh22C186FlQI3kSQv6KsvXpNRX4vJ6eTwn7g
zJGWtVmFno5qQYttVsCZe+qJfBfIqiwUMoCkc/vc6mGUdlLCuQzWIg+qoKD5Xy0t
BeNlR43UYXSvetA/xdfmMVTNkMA5J2uT3RDkEF8g0v/S5f5loI9vBLFEc5p/Ylpa
xyMTaY3x+E1duEfuaWNonPuFMe01xfR9DHeWenx/DrzzVCMkxWmx0g87kLqFPcj4
KKeyagcbwVFspYmo5Skvi9Lgn+EPmMptsyr26bvIN4vWT0c7UnjRSR4o2EEqKbfk
MTBo9RJEoz6E/fi7rHuuLVqq4d42wJhDS9P3T40JvLFDhUV85atNdnxJEP9mtQkH
UPN234Q9Z9pL0Xi+XxnEVJM5iz+DuY34jKyEQ0TZ3gJ4pQgBA2K0h4i3F93B7iyE
Private-MAC: 1a2f2d8e41956104e1bd4145238c8709f6e6315a

```
Obviously, shouldn't be showing my private key and will be creating new ones.

---

### Post by MAFoElffen on 2022-06-11
When you create the RSA Key, the passphrase is optional. If you create the passphrase, it's going to ask for it. If not, it's not going to ask for it...

Reference #5 for additional instructions relating to Putty: [https://ubuntu.com/tutorials/ssh-keygen-on-windows#1-overview](https://ubuntu.com/tutorials/ssh-keygen-on-windows#1-overview)

---

### Post by NotionCommotion on 2022-06-11
Thanks MAFoElffen,  Incorrectly thought that the passphrase only pertained to the private side.  On a positive note, much setup has been much easier on Ubuntu than on Centos.

---

### Post by mIk3_08 on 2022-06-12
> **NotionCommotion said:**
> Hi.  Making the move from Centos to Ubuntu! Just did a new desktop install this morning, and even though I used the desktop install, will be using it more as a server and will need to access remotely via ssh.  It appears that a ssh server doesn't come by default so I install openssh-server.

I then generated rsa public/private keys on windows using puTTYgen and used a passkey, have puTTY use the private key and put the public key in Ubuntu's ~/.ssh/authorized_keys.  When logging on, however, I am being asked for the passkey, and when entering it, I am authenticated.

What am I doing wrong?  Thank you!

```
login as: michael
Authenticating with public key "rsa-key-20220611"
Passphrase for key "rsa-key-20220611":
Welcome to Ubuntu 22.04 LTS (GNU/Linux 5.15.0-37-generic x86_64)


 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage


0 updates can be applied immediately.


Last login: Sat Jun 11 09:24:28 2022 from 10.120.11.102
michael@michael-HP-EliteBook-830-G5:~$

```

```
Jun 11 09:42:44 michael-HP-EliteBook-830-G5 sshd[4357]: Accepted publickey for michael from 10.120.11.102 port 51158 ssh2: RSA SHA256:Tfb9eUbEiYJySKgFeDoPQlcp2vsKbcKX1fXLVLvXkEA
Jun 11 09:42:44 michael-HP-EliteBook-830-G5 sshd[4357]: pam_unix(sshd:session): session opened for user michael(uid=1000) by (uid=0)
Jun 11 09:42:44 michael-HP-EliteBook-830-G5 systemd-logind[656]: New session 9 of user michael.

```
```

michael@michael-HP-EliteBook-830-G5:~$ cat .ssh/authorized_keys
ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEAlTd6XcdF/2H7HGag/l3aG8BtZL9fh2JlT51MmpZCFc3Yd0/Z11UF4sBPvQQxCp4jLDHaZXTfBPdmM/QsuuGyvVJcInL42fMvitO//G6Gr2LEkcsWnoduie2f3oJPO7ejBJENTHbIzLWHU/OHfv0r5XIrIjtbe6lLKy0PRDMTikImstHLMWGpv5lzKYFtqFuvAsQauZ5h54Xf2TuIXm8rtZ3e7TFZ6ymYJHpR7TXUS+VhInWvT9PuS+oR55xj3xT2ElM5sTauLONn9A1VTf7rmmsM85Zow/9
michael@michael-HP-EliteBook-830-G5:~$

```

```
---- BEGIN SSH2 PUBLIC KEY ----
Comment: "rsa-key-20220611"
AAAAB3NzaC1yc2EAAAABJQAAAQEAlTd6XcdF/2H7HGag/l3aG8BtZL9fh2JlT51M
mpZCFc3Yd0/Z11UF4sBPvQQxCp4jLDHaZXTfBPdmM/QsuuGyvVJcInL42fMvitO/
/G6Gr2LEkcsWnoduie2f3oJPO7ejBJENTHbIzLWHU/OHfv0r5XIrIjtbe6lLKy0P
RDMTikImstHLMWGpv5lzKYFtqFuvAsQauZ5h54Xf2TuIXm8rtZ3e7TFZ6ymYJHpR
7TXUS+VhInWvT9PuS+oR55xj3xT2ElM5sTauLONn9A1VTf7rmmsM85Zow/9L3JDP
vYfebgDEX2A8w987bCsFKGXrHIyecUXXJ9kwG/KIYyYXLPzxAw==
---- END SSH2 PUBLIC KEY ----

```



```
PuTTY-User-Key-File-2: ssh-rsa
Encryption: aes256-cbc
Comment: rsa-key-20220611
Public-Lines: 6
AAAAB3NzaC1yc2EAAAABJQAAAQEAlTd6XcdF/2H7HGag/l3aG8BtZL9fh2JlT51M
mpZCFc3Yd0/Z11UF4sBPvQQxCp4jLDHaZXTfBPdmM/QsuuGyvVJcInL42fMvitO/
/G6Gr2LEkcsWnoduie2f3oJPO7ejBJENTHbIzLWHU/OHfv0r5XIrIjtbe6lLKy0P
RDMTikImstHLMWGpv5lzKYFtqFuvAsQauZ5h54Xf2TuIXm8rtZ3e7TFZ6ymYJHpR
7TXUS+VhInWvT9PuS+oR55xj3xT2ElM5sTauLONn9A1VTf7rmmsM85Zow/9L3JDP
vYfebgDEX2A8w987bCsFKGXrHIyecUXXJ9kwG/KIYyYXLPzxAw==
Private-Lines: 14
CWUP2FOuoJYQgTQrErBXOIfWqy3WPOIgw/tS7311LsTiJCFd16Ug6g+lpu5vJLN0
MmET1l6d+VdHhyCPYzKXyoshk8Fd5bIrmsc+CVh9avQjjiWHsYG5MW3hJx30fqJu
5t8JrkLnSYLrnXS7/4UMukbi27T1hKqAtnrDe8nAQN0l4tcVckVxo+cX/qvSiXUM
LbA1652F7frRns1YEeovxqOKhNpdo5n/J0sHXZKu2wghZ5vajAWXSsvkRG483gBK
Pr1aoGfIKOrMcI7Hgpzbv3W5CgFm7zJkgHcZwlRKKRg6f4lgHDE/9EXpYC7vWJv/
vknAi0ZTWnTjlvp3c7eO5h1/V5ozF7fU7dcXddRUK2cp7lQ/R67UVz0FMCMeNeEX
4TzvV1GLI8IGKa3cfgLSJDOg2FlyiKXvDwc+PbmOdJUyTULs9++Sgga84kp6wJmA
uNH9K/S17FNsUlS6u5j7YN04itaxZh22C186FlQI3kSQv6KsvXpNRX4vJ6eTwn7g
zJGWtVmFno5qQYttVsCZe+qJfBfIqiwUMoCkc/vc6mGUdlLCuQzWIg+qoKD5Xy0t
BeNlR43UYXSvetA/xdfmMVTNkMA5J2uT3RDkEF8g0v/S5f5loI9vBLFEc5p/Ylpa
xyMTaY3x+E1duEfuaWNonPuFMe01xfR9DHeWenx/DrzzVCMkxWmx0g87kLqFPcj4
KKeyagcbwVFspYmo5Skvi9Lgn+EPmMptsyr26bvIN4vWT0c7UnjRSR4o2EEqKbfk
MTBo9RJEoz6E/fi7rHuuLVqq4d42wJhDS9P3T40JvLFDhUV85atNdnxJEP9mtQkH
UPN234Q9Z9pL0Xi+XxnEVJM5iz+DuY34jKyEQ0TZ3gJ4pQgBA2K0h4i3F93B7iyE
Private-MAC: 1a2f2d8e41956104e1bd4145238c8709f6e6315a

```
Obviously, shouldn't be showing my private key and will be creating new ones.
Oh no.... Please protect your keys... Its like you are giving your house key to the strangers. Maybe you need to change it. Make a new another key for safety purposes. Good Luck! Regards and cheers.

---

### Post by TheFu on 2022-06-12
Never share your private key. Never.  Public keys shouldn't be shared much, but it isn't the end of the world, thanks to "math."

BTW, Win10 has ssh built-in, so there isn't any need for putty anymore.

The Win10 **ssh-keygen** works just like the Unix one, so you can use better keys than RSA. Go with an elliptical key.

You can also setup the timeout for unlocking an ssh key.  On Unix, I think it is once per login, but this might be due to ssh-agent running here which handles re-authentication of keys on multiple systems, unless the ssh-key is different.  I'd have to read the manpage for how to do this.  The settings are the same on Win10 as Unix for the same version of ssh.  Too bad that Windows didn't port the **ssh-copy-id** program which has been used on Unix systems for trivial key exchange setup 20+ yrs.  Everyone should complain to MSFT.

There's an entire O'Reilly book on ssh. Most people have very little idea how much this core Unix tool can accomplish.

And if you want a remote desktop, x2go, or any other NX based remote desktop tool uses ssh for remote authentication.

---

