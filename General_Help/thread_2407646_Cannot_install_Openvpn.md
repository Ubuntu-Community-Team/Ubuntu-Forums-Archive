---
title: "Cannot install Openvpn"
date: 2018-12-07
forum: General Help
---

### Post by Heeter on 2018-12-07
Hi all,

I have the latest openvpn repository added to my repository list and added the key and updated the list no problem. 

Now when I try to install openvpn, I keep getting this error:

```

root@tester:/home/tester# apt-get install openvpn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 openvpn : Depends: initscripts (>= 2.88dsf-13.3) but it is not installable
E: Unable to correct problems, you have held broken packages.
root@tester:/home/tester# 

```

Any assistance would be greatly apprciated

Regards

---

### Post by TheFu on 2018-12-07
The error says:
```
E: Unable to correct problems, you have held broken packages.
```
 I bet you can't install many packages. It isn't just openvpn.

```
sudo apt update
sudo apt upgrade
```

What problems are seen with those commands?  Fix them.

---

### Post by SeijiSensei on 2018-12-07
```
sudo dpkg --configure -a
```

can also solve a lot of problems.

---

### Post by Heeter on 2018-12-07
> **TheFu said:**
> The error says:
```
E: Unable to correct problems, you have held broken packages.
```
 I bet you can't install many packages. It isn't just openvpn.

```
sudo apt update
sudo apt upgrade
```

What problems are seen with those commands?  Fix them.

No problems with those 2 commands are coming up.

> **SeijiSensei said:**
> ```
sudo dpkg --configure -a
```

can also solve a lot of problems.

```

root@tester:/home/tester# sudo dpkg --configure -a
root@tester:/home/tester# 

```

It is not doing anything, 

Regards

---

### Post by SeijiSensei on 2018-12-08
Try removing that repository and install openvpn from the regular Ubuntu repos.  I've installed it on both Ubuntu and CentOS using the standard packages without a hitch.

Remember to run "sudo apt update" after you remove the repository.

---

### Post by Heeter on 2018-12-08
> **SeijiSensei said:**
> Try removing that repository and install openvpn from the regular Ubuntu repos.  I've installed it on both Ubuntu and CentOS using the standard packages without a hitch.

Remember to run "sudo apt update" after you remove the repository.

Hi Thanks for the response

The problem was that repo.  Installed just fine with default ubuntu repository, same version too 2.4.4

Thank you for your assistance

Regards

---

