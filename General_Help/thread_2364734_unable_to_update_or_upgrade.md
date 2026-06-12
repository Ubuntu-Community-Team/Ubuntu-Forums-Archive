---
title: "unable to update or upgrade"
date: 2017-06-27
forum: General Help
---

### Post by ranjitchavan on 2017-06-27
```
sudo apt-get upgrade
sudo: unable to resolve host ubuntu-hcl
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  libmircommon5
Use 'sudo apt autoremove' to remove it.
The following packages have been kept back:
  postgresql-client-common
The following packages will be upgraded:
  libpq5 python3-argcomplete
2 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
20 not fully installed or removed.
Need to get 0 B/156 kB of archives.
After this operation, 306 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
/usr/bin/dpkg: 1: /usr/bin/dpkg: Syntax error: word unexpected (expecting ")")
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by speartip on 2017-06-27
The problem seems to be the 20 packages that are not fully installed. Try:
```
sudo dpkg --configure -a
```
or:
```
sudo apt-get -f install
```

---

### Post by kc1di on 2017-06-27
Hello ranjitchavan and welcome to Ubuntu,

It would be helpful to know which version of Ubuntu you are using?

Here are few things you can try first:
```
sudo apt-get install -f
```
```
sudo dpkg --configure -a
```
```
sudo apt-get autoremove[CODE]

```sudo apt-get autoclean[/CODE]
```
sudo apt-get clean
```
```
sudo apt-get update
```

---

### Post by ranjitchavan on 2017-06-27
```
sudo dpkg --configure -a
sudo: unable to resolve host ubuntu-hcl
/usr/bin/dpkg: 1: /usr/bin/dpkg: Syntax error: word unexpected (expecting ")")
```


Ubuntu 16.04 lts

---

### Post by howefield on 2017-06-27
Hello ranjitchavan and welcome to the forums, please use code tags when posting terminal output for better readability, lining up and preventing some output being parsed as emoticons.

To do that, wrap the output in [noparse]```

```[/noparse] tags, eg [noparse]```
[/noparse] before the beginning of the output and [noparse]
```[/noparse] after the end.

---

### Post by speartip on 2017-06-27
OK. After Googling the problem, it seems this issue is quite varied.
Have you been trying to install things or compile programs other than those found in the official repos?
Also a look at your sources list may help.

---

### Post by ranjitchavan on 2017-06-27
i have tried to install
sudo apt-get install postgresql-client

---

### Post by speartip on 2017-06-27
When you say "tried", I take it that, that is when this issue occurred.
Also did you update everything first?
What happens when you simply run:
```
sudo apt update
```

---

### Post by kc1di on 2017-06-28
[This article]("https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-16-04") may be of help to you trying to set up postgresql-client.
Your system is looking for your local host during install and can't find it I believe you may have to define that first.

---

### Post by johndough2 on 2017-06-28
Hi

Two things.

First is the error  Unable to resolve host ubuntu-hcl needs rectifying.

And secondly try something g really simple

sudo apt install Joe

sudo apt-get install joe

Post back rests please.

---

### Post by ranjitchavan on 2017-07-05
i am giving command on ubuntu 16.04 

[FONT=monospace][COLOR=#000000]sudo apt-get -y install postgresql

 then gives  such type of error 

[/COLOR][/FONT][FONT=monospace][COLOR=#000000]/usr/bin/dpkg: 1: /usr/bin/dpkg: Syntax error: word unexpected (expecting ")")[/COLOR]
E: Sub-process /usr/bin/dpkg returned an error code (2)
[/FONT][FONT=monospace][COLOR=#000000]
[/COLOR]
[/FONT]

---

### Post by courtney2 on 2017-07-06
I was having some different issues with apt and dpkg the other day, and reinstalling dpkg solved my problem. Perhaps it could solve yours too. Run this:

sudo apt-get install --reinstall dpkg

Do what johndough2 said first though and then do a "sudo apt-get upgrade" and "sudo apt-get dist-upgrade" before you try to reinstall dpkg

---

