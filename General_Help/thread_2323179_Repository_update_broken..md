---
title: "Repository update broken."
date: 2016-05-03
forum: General Help
---

### Post by nigellove2 on 2016-05-03
[COLOR=#111111][FONT=Ubuntu]This morning my system gave me a security update that I installed.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Now I cannot read or update Repositories, either from Update Manager or Terminal with $ sudo apt-get update.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I am getting the following messages:
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][I]The method driver /usr/lib/apt/methods/https could not be found. Is package apt-transport-https installed?
[/I][/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I get a similar message in Synaptic Package Manager so I tried to reinstall the package and I get the following: 

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu][I]admin@ubuntu_14:~$ sudo apt-get install apt-transport-https 
Reading package lists... Done 
Building dependency tree 
Reading state information... Done 
E: Unable to locate package apt-transport-https 
admin@ubuntu_14:~$ [/I][/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
So the package appears to be missing and I cannot update the repositories to re-load it.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Can anyone shed some light on what's happened and can I recover from this?

Thanks

Nigel[/FONT][/COLOR]

---

### Post by QDR06VV9 on 2016-05-03
This is a new one, but try this. And this is assuming that you are running Trusty(14.04)
If not which version of ubuntu are you using.
```
sudo wget http://ubuntu.mirror.atratoip.net/ubuntu/pool/main/a/apt/apt-transport-https_0.9.7.7ubuntu5_$(dpkg-architecture -qDEB_HOST_ARCH).deb && sudo dpkg -i apt-transport-https_0.9.7.7ubuntu5_$(dpkg-architecture -qDEB_HOST_ARCH).deb

```
For Zenial (16.04) the command would be:
```
sudo wget http://ubuntu.mirror.atratoip.net/ubuntu/pool/main/a/apt/apt-transport-https_1.2.10ubuntu1_$(dpkg-architecture -qDEB_HOST_ARCH).deb && sudo dpkg -i apt-transport-https_1.2.10ubuntu1_$(dpkg-architecture -qDEB_HOST_ARCH).deb

```
The dpkg-architecture command is used to determine the architecture of your system. You could also replace it with i386 or amd64.
And try again with "sudo apt update" and post back any errors.

---

### Post by mc4man on 2016-05-03
Are you still using 14.04?
What's this show
```
apt-cache policy apt
```
and 
```
apt-cache madison apt-transport-https
```

---

