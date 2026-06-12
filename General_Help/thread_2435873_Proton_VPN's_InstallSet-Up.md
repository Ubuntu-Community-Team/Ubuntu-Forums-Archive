---
title: "Proton VPN's Install/Set-Up"
date: 2020-01-27
forum: General Help
---

### Post by mawil10132 on 2020-01-27
Trying to set up Ubuntu19 with Proton VPN using this [https://protonvpn.com/support/linux-ikev2-protonvpn/](https://protonvpn.com/support/linux-ikev2-protonvpn/)
Below is the point where it breaks down. What am I doing wrong? I tried typing again a different way in case I used zero instead of O, and changed spacing too.

```
michael@michael-Inspiron-5575:~$ sudo apt-get install libstrongswan-extra-plugins sudo apt-get install libcharon-extra-plugins
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package apt-get
E: Unable to locate package install
michael@michael-Inspiron-5575:~$ wget [https://protonvpn.com/download/ProtonVPN_ike_root.der](https://protonvpn.com/download/ProtonVPN_ike_root.der) -0 /tmp/protonvpn.der sudo mv /tmp/protonvpn.der /etc/ispec.d/cacerts/
wget: invalid option -- '0'
Usage: wget [OPTION]... [URL]...

Try `wget --help' for more options.
michael@michael-Inspiron-5575:~$ weget https://protonvpn.com/download/ProtonVPN_ike_root.der -O/tmp/protonvpn.der sudo mv /tmp/protonvpn.der /etc/ipsec.d/cacerts/

Command 'weget' not found, did you mean:

  command 'wget' from deb wget (1.20.1-1ubuntu4)
  command 'wmget' from deb wmget (0.6.1-1build1)

Try: sudo apt install <deb name>
```

---

### Post by kevdog on 2020-01-28
Its an O like Octopus which basically specifies the output directory.  The second command you typed wrong.

---

### Post by CelticWarrior on 2020-01-28
And you mixed to different commands in the first one.

---

