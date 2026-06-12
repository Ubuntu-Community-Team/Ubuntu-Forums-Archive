---
title: "ubuntu software center problem in laptop."
date: 2013-02-10
forum: General Help
---

### Post by sbshaikh on 2013-02-10
[SIZE="3"][COLOR="DarkRed"][COLOR="rgb(139, 0, 0)"][FONT="Arial Black"]I have using ubuntu 12.04 LTS operating system, on my laptop ubuntu software center opened and immediately it closed, i do not find the reason behind it.  I have taken efforts to solve the problem by using following command in open terminal[/FONT][/COLOR][/COLOR][/SIZE] :-

sudo apt-get remove software-center
sudo apt-get install software-center


  [FONT="Arial Black"][COLOR="DarkRed"]Eventhough it is not opening or working properly. So please help me to solve the said problem. Furthermore my open terminal window shown output as follws [/COLOR][/FONT]

ubuntu@ubuntu-linux:~/Desktop$ sudo apt-get update
[sudo] password for ubuntu: 
E: Malformed line 1 in source list /etc/apt/sources.list.d/google.list (dist)
E: The list of sources could not be read.
ubuntu@ubuntu-linux:~/Desktop$

---

### Post by claracc on 2013-02-10
> **sbshaikh said:**
> [SIZE="3"][COLOR="DarkRed"]






ubuntu@ubuntu-linux:~/Desktop$ sudo apt-get update
[sudo] password for ubuntu: 
E: Malformed line 1 in source list /etc/apt/sources.list.d/google.list (dist)
E: The list of sources could not be read.
ubuntu@ubuntu-linux:~/Desktop$

Could you please to post your sources.list file?, as it is addressed it has to have a malformation in line 1.

---

### Post by plucky on 2013-02-10
> E: Malformed line 1 in source list /etc/apt/sources.list.d/google.list (dist)


It is not the sources.list,but it is in sources.list.d directory

Use

```
cat /etc/apt/sources.list.d/google.list
```

to see what is wrong.Please post the output.

Good Luck

---

### Post by sbshaikh on 2013-02-10
Sir, as u asked the sourcelist name, I have provided the information as follows. 

I used following four steps to install the google chrome but didn't succeed and face the another problem that is [COLOR="DarkRed"][FONT="Arial Black"]" my ubuntu software center not working properly"[/FONT][/COLOR]-


Step 1 » Setup key .

krizna@leela:~$ wget -q -O - [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | sudo apt-key add -

Step 2 » Type this command exactly to add chrome repositories .


krizna@leela:~$ sudo sh -c 'echo "deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main" >> /etc/apt/sources.list.d/google.list'

Step 3 » Now Update the package list .

krizna@leela:~$ sudo apt-get update

Step 4 » Finally install google chrome

krizna@leela:~$ sudo apt-get install google-chrome-stable

---

### Post by sbshaikh on 2013-02-10
Sir, when i used the command you provided in this message then my terminal window gave following output:-

ubuntu@ubuntu-linux:~$ cat /etc/apt/sources.list.d/google.list
deb [http://dl.google.com/linux/chrome/deb/stable/main](http://dl.google.com/linux/chrome/deb/stable/main)
ubuntu@ubuntu-linux:~$

---

### Post by sbshaikh on 2013-02-10
> **sbshaikh said:**
> Sir, when i used the command you provided in this message then my terminal window gave following output:-

ubuntu@ubuntu-linux:~$ cat /etc/apt/sources.list.d/google.list
deb [http://dl.google.com/linux/chrome/deb/stable/main](http://dl.google.com/linux/chrome/deb/stable/main)
ubuntu@ubuntu-linux:~$ 



Thereafter I used the methods which used for manual installation of google chrome i.e.

Step 1 » Type apt-get update on terminal as a sudo user.

krizna@leela:~$ sudo apt-get update

This command will update the packages list index.
Step 2 » Now we need to install libnss3-1d and libxss1

krizna@leela:~$ sudo apt-get install libnss3-1d
libxss1

Step 3 » Finally install the downloaded package.

krizna@leela:~$sudo dpkg -i google-chrome-stable_current_i386.deb

---

### Post by plucky on 2013-02-11
> **sbshaikh said:**
> Sir, when i used the command you provided in this message then my terminal window gave following output:-

ubuntu@ubuntu-linux:~$ cat /etc/apt/sources.list.d/google.list
deb [http://dl.google.com/linux/chrome/deb/stable/main](http://dl.google.com/linux/chrome/deb/stable/main)
ubuntu@ubuntu-linux:~$


Just installed the google-chrome repository and it looks like ```
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
**deb http://dl.google.com/linux/chrome/deb/ stable main**
```
 and it is from ```
cat /etc/apt/sources.list.d/google-chrome.list
```

Also if your downloaded the .deb file from Google,it automatically installs the google repository.

Good Luck

---

### Post by sbshaikh on 2013-02-13
Sir, when i tried to download the google chrome from the http address provided by you that is [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

but it show - 404 page cannot found.
However i had downloaded the 'google chrome' from website that is [http://www.noobslab.com/2012/02/install-latest-google-chrome-on-ubuntu.html](http://www.noobslab.com/2012/02/install-latest-google-chrome-on-ubuntu.html) 
 then type the coomands provided there as given below in open terminal window-

This installation is problem for me, but my another important problem is that in my laptop "ubuntu software center" not properly opening. Because it opened and immediately shut down or closed. How I should correct it or get in state of proper working. 

Thanking you Plucky for your valuable information. Please also give suggestion for aforesaid problem.

---

### Post by plucky on 2013-02-13
> This installation is problem for me, but my another important problem is that in my laptop "ubuntu software center" not properly opening. Because it opened and immediately shut down or closed. How I should correct it or get in state of proper working. 

Remove the incorrect line in the .list file for google chrome or you will keep on getting the problem in the Software Centre.


Good Luck

---

### Post by schragge on 2013-02-13
Ok, try this
```

sudo sed -i 's:stable/: stable :' /etc/apt/sources.list.d/google.list

```

---

### Post by Johnread on 2013-02-13
I have several times attempted to install from the Software Centre photo printing programmes but each time I have been prevented, apparently by the need to use unapproved packages.  I am surprised for I expected downloads from the Software Centre to be free of all contact with any unapproved material.  The programmes tried are:-    Photoprint,  Gnomeprint, and flPhoto.

Can any one offer suggestions as to how such programmes can be installed.

I am running Xubuntu 12.04.1

Thank you John Read.

---

### Post by Johnread on 2013-02-13
I have several times attempted to install from the Software Centre photo printing programmes but each time I have been prevented, apparently by the need to use unapproved packages.  I am surprised for I expected downloads from the Software Centre to be free of all contact with any unapproved material.  The programmes tried are:-    Photoprint,  Gnomeprint, and flPhoto.

Can any one offer suggestions as to how such programmes can be installed.

I am running Xubuntu 12.04.1

Thank you John Read.

---

### Post by sbshaikh on 2013-02-14
> **schragge said:**
> Ok, try this
```

sudo sed -i 's:stable/: stable :' /etc/apt/sources.list.d/google.list

```

Helloo schragge Sir,

 First of all Thanks to you from the bottom of my heart for your help to resolve the problem..Sir by using the command provided by you my ubuntu software center opening properly as it previously working.. Again Thanks a lot to you.. Please help me future also if face any problem..Ok. bye sir..:D

---

