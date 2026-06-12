---
title: "Adobe Flash Player is not getting installed"
date: 2012-12-24
forum: General Help
---

### Post by deb44 on 2012-12-24
Hi I am new to ubantu. I am trying to install adobe flash player. But I am getting "  [COLOR=black][FONT=&quot]Failed to fetch [http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_11.2.202.251ubuntu0.12.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_11.2.202.251ubuntu0.12.10.1_i386.deb) 404  Not Found". Please help me to install adobe player pulgin. I am using ubantu 12.10
[/FONT][/COLOR]

---

### Post by Karlchen on 2012-12-24
Hello, deb44.
 
 
I tend to assume that you are new to Ub**_u_**ntu and that you are using Ub**_u_**ntu 12.10, not Ub_a_ntu.
The error message which you receive that the file flashplugin-installer_11.2.202.251ubuntu0.12.10.1_i386.deb cannot be fetched suggests that you have to run ```
sudo apt-get update
``` first. I.e. you have to refresh the local list of available software first. The list is outdated and no longer valid.
The current Flash version for Ubuntu is 11.2.202.258.
This may be the reason why trying to download the previous version fails.
 
 
Kind regards,
Karl

---

### Post by rnerwein on 2012-12-24
> **deb44 said:**
> Hi I am new to ubantu. I am trying to install adobe flash player. But I am getting "  [COLOR=black][FONT=&quot]Failed to fetch [http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_11.2.202.251ubuntu0.12.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_11.2.202.251ubuntu0.12.10.1_i386.deb) 404  Not Found". Please help me to install adobe player pulgin. I am using ubantu 12.10
[/FONT][/COLOR]
hi
try: [www.adobe.com](www.adobe.com)  
cheers

---

