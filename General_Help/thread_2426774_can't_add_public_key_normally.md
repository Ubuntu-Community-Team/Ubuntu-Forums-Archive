---
title: "can't add public key normally"
date: 2019-09-13
forum: General Help
---

### Post by mohamed-ali-mhenni on 2019-09-13
Hello every one i have an odroid with ubuntu 16.04 on it and i have a probleme
when i walt to add the  repo with this commande
```
sudo add-apt-repository ppa:deluge-team/stable
```



it's ok but when i use 
```
sudo apt update
```
an error came out
```
Hit:2 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial InRelease
Hit:3 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates InRelease            
Hit:4 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-backports InRelease          
Get:1 [http://ppa.launchpad.net/deluge-team/stable/ubuntu](http://ppa.launchpad.net/deluge-team/stable/ubuntu) xenial InRelease [17.5 kB]
Hit:5 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-security InRelease           
Err:1 [http://ppa.launchpad.net/deluge-team/stable/ubuntu](http://ppa.launchpad.net/deluge-team/stable/ubuntu) xenial InRelease      
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C5E6A5ED249AD24C
Reading package lists... Done
N: Ignoring file 'C5E6A5ED249AD24C.key' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
W: GPG error: [http://ppa.launchpad.net/deluge-team/stable/ubuntu](http://ppa.launchpad.net/deluge-team/stable/ubuntu) xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C5E6A5ED249AD24C
E: The repository 'http://ppa.launchpad.net/deluge-team/stable/ubuntu xenial InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

i tried to add the key with apt-key add and even with the PGP PUBLIC KEY BLOCK but failed
when i type
```
sudo apt-key list
```

this error show

---

### Post by mohamed-ali-mhenni on 2019-09-13
Sorry this was the error from sudo apt-key list
> /etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   4096R/C0B21F32 2012-05-11
uid                  Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>

pub   4096R/EFE21092 2012-05-11
uid                  Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>

pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

/usr/bin/sort: 1: /usr/bin/sort: 1O&#65533;PP&#65533;&#65533;&#65533;&#65533;!KA&#65533;&#65533;&#65533;&#65533;: not found
/usr/bin/sort: 1: /usr/bin/sort: &#65533;M&#65533;Q&#65533;&#65533; &#65533;&#65533;&#65533;
                                               &#65533;&#65533;&#65533;M&#65533;&#65533;&#65533;xh&#65533;&#65533;&#65533;&#65533;&#65533;F&#65533;E&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;
                                                                         &#65533;&#65533;F&#65533;&#65533;i&#65533;#FpGBi*&#65533;&#65533;~&#65533;&#65533;B~*&#65533;&#1091;~{&#65533;*&#65533;&#65533;CS&#65533;&#65533;*&#65533;&#1104;&#65533;  *&#65533;&#65533;&#65533;~&#65533;&#65533;&#65533;&#65533;F&#65533;&#65533;&#65533;~&#65533;C~+F&#65533;Jb#
                                                                    p#Ki&#65533;B&#65533;d#pC&#65533;2+:&#65533;Sf!p&#65533;g3&#65533;,B&#65533;h3&#65533;,Ji&#65533;B&#65533;ip&#65533;3&#65533;M3&#65533;,&#65533;~&#65533;n3&#65533;,&#65533;~&#65533;R3&#65533;,&#65533;&#65533;r3&#65533;,&#65533;&#65533;: not found
/usr/bin/sort: 2: /usr/bin/sort: Syntax error: "(" unexpected

---

### Post by oldos2er on 2019-09-13
Moved to General Help. The Resolution Centre is "the place to contact a forum admin  concerning problems with your forum account, to appeal moderator action,  to request a thread be moved from the jail, or to file a complaint  about forum harrassment or abuse."

---

### Post by mohamed-ali-mhenni on 2019-09-19
Any one can help me ???

---

### Post by mohamed-ali-mhenni on 2019-09-30
Up

---

