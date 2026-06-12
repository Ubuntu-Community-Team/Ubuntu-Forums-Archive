---
title: "In the Terminal 13.04"
date: 2013-05-15
forum: General Help
---

### Post by Frankiewizard on 2013-05-15
Why do I get this every time I do an update in the terminal ?

[HTML]Errors were encountered while processing:
 libbonoboui2-0:amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)
frankiewizard@frankiewizard-Presario-CQ62-Notebook-PC:~$ [/HTML]

I start of with [HTML]sudo apt-get update
[/HTML]

then

[HTML]sudo apt-get upgrade[/HTML]

Is this a really bad thing ?

Cheers Frankie.

---

### Post by slickymaster on 2013-05-15
Please try, one at a time the follwoing commands:
```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Frankiewizard on 2013-05-15
Well did try but got this > After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing libbonoboui2-0:amd64 (--configure):
 package libbonoboui2-0:amd64 is not ready for configuration
 cannot configure (current status `half-installed')
Errors were encountered while processing:
 libbonoboui2-0:amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)
frankiewizard@frankiewizard-Presario-CQ62-Notebook-PC:~$ ^C
frankiewizard@frankiewizard-Presario-CQ62-Notebook-PC:~$ sudo apt-get autoremoveReading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/189 kB of archives.
After this operation, 0 B of additional disk space will be used.
dpkg: error processing libbonoboui2-0:amd64 (--configure):
 package libbonoboui2-0:amd64 is not ready for configuration
 cannot configure (current status `half-installed')
Errors were encountered while processing:
 libbonoboui2-0:amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)

Does it lôôk bad doctor ?
frankiewizard@frankiewizard-Presario-CQ62-Notebook-PC:~$ 

---

### Post by ibjsb4 on 2013-05-15
Try

```
sudo dpkg --configure -a
sudo apt-get -f install
```

Get errors?

---

### Post by Frankiewizard on 2013-05-15
Tis done & this is the result folks.
[HTML]frankiewizard@frankiewizard-Presario-CQ62-Notebook-PC:~$ sudo apt-get -f installReading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/189 kB of archives.
After this operation, 0 B of additional disk space will be used.
dpkg: error processing libbonoboui2-0:amd64 (--configure):
 package libbonoboui2-0:amd64 is not ready for configuration
 cannot configure (current status `half-installed')
Errors were encountered while processing:
 libbonoboui2-0:amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)
frankiewizard@frankiewizard-Presario-CQ62-Notebook-PC:~$ [/HTML]

---

### Post by Frankiewizard on 2013-05-15
Should I do a fresh install of 13.04 ?

---

### Post by slickymaster on 2013-05-15
Can you please try one more thing? Run the following:
```
sudo apt-get update
sudo apt-get dist-upgrade
```and post the output, please.

---

### Post by Frankiewizard on 2013-05-15
I have tryed it and here is the result. Cheers

[HTML]frankiewizard@frankiewizard-Presario-CQ62-Notebook-PC:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/189 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing libbonoboui2-0:amd64 (--configure):
 package libbonoboui2-0:amd64 is not ready for configuration
 cannot configure (current status `half-installed')
Errors were encountered while processing:
 libbonoboui2-0:amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)
frankiewizard@frankiewizard-Presario-CQ62-Notebook-PC:~$[/HTML]

---

### Post by slickymaster on 2013-05-15
Please run the following and post back the ouput:
```
sudo dpkg --audit | more
```If it finds anything, it should also give us instructions on how to fix it.

---

### Post by Frankiewizard on 2013-05-15
This is what it found
[HTML]The following packages are in a mess due to serious problems during
installation. They must be reinstalled for them (and any packages
that depend on them) to function properly:
 libbonoboui2-0:amd64 The Bonobo UI library

The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 libbonoboui2-0:amd64 The Bonobo UI library
[/HTML]

Please advise. Frankie.

---

### Post by Frogs Hair on 2013-05-15
You can try the following since the package needs to be reinstalled . I am seeing this package installed on my system.  

```
sudo apt-get install --reinstall libbonoboui2-0
```

```
sudo apt-get update 
```

---

### Post by slickymaster on 2013-05-15
Frogs Hair's advice is correct, but if somehow you run into errors again, you could purge that package and afterwards try to re-install it:
```
sudo apt-get purge libbonoboui2-0
```and then
```
sudo apt-get install libbonoboui2-0
```

---

### Post by Frankiewizard on 2013-05-22
I have done a brand new re-install "13.04" 64 bits. The "Terminal" functions there are no problems when doing up dates. But on booting "I am just on a single boot" computer hangs once out of three times. 

Memory 1,9 GiB
Processor Intel® Celeron(R) CPU 900 @ 2.20GHz 
Graph Mobile Intel® GM45 Express Chipset
QS 64-bit
Disk 312,9 GB

Cheers Frankie.

---

### Post by HiImTye on 2013-05-22
this is usually the result of mixing repositories for different versions, normally upgrading to the next release without disabling added PPAs, and can usually be remedied with some combination of ppa-purge and manually removing packages with no installation candidates. the easiest remedy isbto disable extra repos in advance of a release upgrade

---

### Post by Frankiewizard on 2013-05-23
I have done a brand new re-install "13.04" 64 bits. The "Terminal" functions there are no problems when doing up dates. But on booting "I am just on a single boot" computer hangs once out of three times. STILL !

---

