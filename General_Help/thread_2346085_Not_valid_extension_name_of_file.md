---
title: "Not valid extension name of file"
date: 2016-12-11
forum: General Help
---

### Post by claracc on 2016-12-11
Hello, 

Ubuntu-gnome 16.04.1 in hp 6720s laptop.

Any time I  install updates or run ```
sudo apt-get update
``` command, I obtain the following error:

```
sudo apt-get update
[sudo] password for clara: 
Obj:1 http://ubuntu.cica.es/ubuntu xenial InRelease
Obj:2 http://archive.canonical.com/ubuntu xenial InRelease
Obj:3 http://ppa.launchpad.net/audio-recorder/ppa/ubuntu xenial InRelease      
Des:4 http://ubuntu.cica.es/ubuntu xenial-updates InRelease [102 kB]           
Des:5 http://ubuntu.cica.es/ubuntu xenial-security InRelease [102 kB]
Des:6 http://ubuntu.cica.es/ubuntu xenial-updates/main i386 DEP-11 Metadata [293 kB]
Des:7 http://ubuntu.cica.es/ubuntu xenial-updates/main DEP-11 64x64 Icons [180 kB]
Des:8 http://ubuntu.cica.es/ubuntu xenial-updates/universe i386 DEP-11 Metadata [121 kB]
Des:9 http://ubuntu.cica.es/ubuntu xenial-updates/universe DEP-11 64x64 Icons [145 kB]
Des:10 http://ubuntu.cica.es/ubuntu xenial-updates/multiverse i386 DEP-11 Metadata [2.520 B]
Des:11 http://ubuntu.cica.es/ubuntu xenial-security/main i386 DEP-11 Metadata [68,1 kB]
Des:12 http://ubuntu.cica.es/ubuntu xenial-security/main DEP-11 64x64 Icons [43,1 kB]
Des:13 http://ubuntu.cica.es/ubuntu xenial-security/universe i386 DEP-11 Metadata [19,4 kB]
Des:14 http://ubuntu.cica.es/ubuntu xenial-security/universe DEP-11 64x64 Icons [25,6 kB]
Des:15 http://ubuntu.cica.es/ubuntu xenial-security/multiverse i386 DEP-11 Metadata [212 B]
Descargados 1.101 kB en 1s (643 kB/s)                              
AppStream cache update completed, but some metadata was ignored due to errors.
Leyendo lista de paquetes... Hecho
N: Omitiendo el fichero «20auto-upgrades.ucf-dist» del directorio «/etc/apt/apt.conf.d/», ya que tiene una extensión de nombre de fichero no válida

```

Note last line error: Ommiting file «20auto-upgrades.ucf-dist» from directory «/etc/apt/apt.conf.d/» since It has a not valid extension of name of file.

What can I do to get rid of this error?

Thank you in advance.

---

### Post by vasa1 on 2016-12-11
Could you please post the output of```
LANG=C sudo apt-get update
``` so that "N: Omitiendo el fichero «20auto-upgrades.ucf-dist» del directorio «/etc/apt/apt.conf.d/», ya que tiene una extensión de nombre de fichero no válida" will be in English?

---

### Post by claracc on 2016-12-11
Hello Vasa1, I have just translated the error (it is in the bottom part of my question), any case, the translated into English error is:

"N: Omitting file «20auto-upgrades.ucf-dist» from directory «/etc/apt/apt.conf.d/» since It has a not valid extension of name of file."

Regards

---

### Post by vasa1 on 2016-12-11
> **claracc said:**
> Hello Vasa1, I have just translated the error (it is in the bottom part of my question), any case, the translated into English error is:

"N: Omitting file «20auto-upgrades.ucf-dist» from directory «/etc/apt/apt.conf.d/» since It has a not valid extension of name of file."

Regards

I purposely asked you to run with LANG=C so that we get the exact wording, not an approximate translation. Searching the internet for the phrase will then be easier.

---

### Post by claracc on 2016-12-11
Ok, I understand.

Here you are the output of the " sudo apt-get update" in english:

```
clara@clara-HP-Compaq-6720s:~$ LANG=C sudo apt-get update
[sudo] password for clara: 
Hit:1 http://ubuntu.cica.es/ubuntu xenial InRelease
Hit:2 http://ppa.launchpad.net/audio-recorder/ppa/ubuntu xenial InRelease
Hit:3 http://archive.canonical.com/ubuntu xenial InRelease                                       
Get:4 http://ubuntu.cica.es/ubuntu xenial-updates InRelease [102 kB]                             
Get:5 http://ubuntu.cica.es/ubuntu xenial-security InRelease [102 kB]      
Get:6 http://ubuntu.cica.es/ubuntu xenial-updates/main i386 DEP-11 Metadata [293 kB]
Get:7 http://ubuntu.cica.es/ubuntu xenial-updates/main DEP-11 64x64 Icons [182 kB]
Get:8 http://ubuntu.cica.es/ubuntu xenial-updates/universe i386 DEP-11 Metadata [121 kB]
Get:9 http://ubuntu.cica.es/ubuntu xenial-updates/universe DEP-11 64x64 Icons [145 kB]
Get:10 http://ubuntu.cica.es/ubuntu xenial-updates/multiverse i386 DEP-11 Metadata [2520 B]
Get:11 http://ubuntu.cica.es/ubuntu xenial-security/main i386 DEP-11 Metadata [68.1 kB]
Get:12 http://ubuntu.cica.es/ubuntu xenial-security/main DEP-11 64x64 Icons [43.1 kB]
Get:13 http://ubuntu.cica.es/ubuntu xenial-security/universe i386 DEP-11 Metadata [19.4 kB]
Get:14 http://ubuntu.cica.es/ubuntu xenial-security/universe DEP-11 64x64 Icons [25.6 kB]
Get:15 http://ubuntu.cica.es/ubuntu xenial-security/multiverse i386 DEP-11 Metadata [208 B]
Fetched 1104 kB in 1s (797 kB/s)                                   
AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Done
N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension

```

Thankyou

---

### Post by claracc on 2016-12-11
I have been looking for information about this error in the forum and I have found this thread: [https://ubuntuforums.org/showthread.php?t=2344563](https://ubuntuforums.org/showthread.php?t=2344563), where the problem is solved running the following command:

```
sudo mv  /etc/apt/apt.conf.d/20auto-upgrades.ucf-dist  /etc/apt/apt.conf.d/20auto-upgrades
```

I have run it and now, the error has disappeared and the result of running ```
sudo apt-get update
``` is:

```
Hit:1 http://ppa.launchpad.net/audio-recorder/ppa/ubuntu xenial InRelease
Hit:2 http://ubuntu.cica.es/ubuntu xenial InRelease
Hit:3 http://archive.canonical.com/ubuntu xenial InRelease                                        
Hit:4 http://ubuntu.cica.es/ubuntu xenial-updates InRelease                                       
Hit:5 http://ubuntu.cica.es/ubuntu xenial-security InRelease                
Reading package lists... Done                     

```

So , I am going to mark the thread as solved.

Thankyou

---

