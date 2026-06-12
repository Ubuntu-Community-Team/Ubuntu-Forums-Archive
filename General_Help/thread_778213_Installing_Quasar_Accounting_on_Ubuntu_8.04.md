---
title: "Installing Quasar Accounting on Ubuntu 8.04"
date: 2008-05-01
forum: General Help
---

### Post by whervin on 2008-05-01
I am trying (without success) to install quasar accounting 2.0.4-1.  I have Ubuntu 8.04 "Hardy Heron".  
I've downloaded the quasar-single_2.0.4-1_i386.deb file from linuxcanada.com, and tried to install using gdebi, but keep getting the following Error:"Dependency is not satisfiable: libicu36|libicu34|icu"

Any ideas as to what I am doing wrong and how I can fix this.

Regards
Whervin

---

### Post by tamoneya on 2008-05-01
```
sudo apt-get install libicu36-dev libicu34-dev icu
```

---

### Post by whervin on 2008-05-01
Thanks Tamoneya for your quick reply.
I've done as you suggested and received the following result: *"Package libicu36-dev is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source. However the following packages replace it: libicu-dev"*

I then "sudo apt-get install libicu-dev" and again tried to install the quasar .deb file using gdebi.  I am still getting the same error.

Any more ideas?

---

### Post by MagHam on 2008-05-15
I have got the exact same problem. seems missing the icu package, but I am confused on how to get it. it is not listed in Synaptic. 
Anyone can help..that would be wonderful. I am new to Ubuntu, trying to switch from windows, but I need a program similiar to simply accounting and this is the only one that appears to fit the bill.

thanks

---

### Post by mavila on 2008-05-18
Im not sure that 2.0.4 is going to work properly on Hardy. Ive been running 8.04 since release, adn brought up a Kubuntu in a VM to be sure that this dependency wasnt isolated to Ubuntu, but its there in Kubuntu as well. The rationale was to try kubuntu as thats what the Quasar download site appears to suggest is supported.

Worst case its a Windoze VM to get this running.... If anyone has success please share.

---

### Post by caribountu on 2008-05-19
I am having the same problem.
Seems quasar is looking for icu 3.4 or 3.6 and hardy has 3.8
Last night I installed 3.6 from the icu homepage, but that didn't make any difference.

---

### Post by mavila on 2008-05-19
I reached out to Quasar directly and they are looking into the issue. THe response that I got back from them this afternoon was;

"Alright I think I understand the issue now.  Its a problem in the  
debian control file where we specify the dependencies of the package.   
It may be possible to tell the installer on Ubuntu to ignore this  
which should work since Quasar was compiled on it.  To fix it properly  
though, I'll review the dependencies in the debian control file and  
make sure its updated for the current versions."

Soon as I hear anything further back Ill post it.

---

### Post by mavila on 2008-05-20
All - sitting at the airport and checking e-maiul, the Quasar guys just dropped me a note saying that they posted a new .deb package on the site which <<should>> fix the issue. As I cant install for a couple of days till I return back, y'all might want to try the latest version. If someone would either private message me ot post back to this group wiht the results Id greatly appreciate it. That way I can let LinuxCanada know if their new packages worked.

Cheers - Matt

---

