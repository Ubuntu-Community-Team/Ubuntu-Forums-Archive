---
title: "thunderbird does not start"
date: 2008-05-03
forum: General Help
---

### Post by enuckon on 2008-05-03
Installed Thunderbird 2 on Ubuntu 7.10 (see sudo app-get install thunderbird output below).  When I try to start it, nothing happens, 
no messages either.     

Is this the right thing to install? 
Or there is something wrong with installation? 


> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libpth20 libksba8
Use 'apt-get autoremove' to remove them.
Suggested packages:
  thunderbird-gnome-support latex-xft-fonts
The following NEW packages will be installed:
  thunderbird
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/11.0MB of archives.
After unpacking 32.7MB of additional disk space will be used.
Selecting previously deselected package thunderbird.
(Reading database ... 99538 files and directories currently installed.)
Unpacking thunderbird (from .../thunderbird_2.0.0.6+nobinonly-0ubuntu1_i386.deb) ...
Setting up thunderbird (2.0.0.6+nobinonly-0ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
> 



Thanks,
e.


P.S.  When I type 'thunderbird' from the terminal, this is what I get:
"
/opt/thunderbird/thunderbird-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
"
and nothing opens

---

### Post by tamoneya on 2008-05-03
seems to have installed fine to me.  What is outputted in terminal when you run:```
thunderbird
```

---

### Post by enuckon on 2008-05-03
Please see the P.S. in the original message.  Entire output is quoted.  Thanks, e.

---

### Post by tamoneya on 2008-05-03
```
sudo apt-get install libstdc++
```Then try thunderbird in terminal again and post the output.

---

### Post by enuckon on 2008-05-04
Thanks!  I have done this and below is the output of installation of libstdc++ and running 'thunderbird':


```

~$ sudo apt-get install libstdc++

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libstdc

~$ thunderbird

/opt/thunderbird/thunderbird-bin: error while loading shared 
libraries: libstdc++.so.5: cannot open shared object file: 
No such file or directory 
```

Thunderbird does not start and gives the same error message.  
I do not understand this as the system has libstdc++6 installed already.  
What do you think?

Thanks again, e.

---

### Post by enuckon on 2008-05-06
What is not clear is whether libstdc++6 should be reinstalled?

---

