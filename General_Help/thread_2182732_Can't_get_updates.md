---
title: "Can't get updates"
date: 2013-10-22
forum: General Help
---

### Post by Lloydb39 on 2013-10-22
Red triangle at the top. When I check for updates with 12.04 on homebuilt AMD 64 bit machine I get "Failed to download repository information." Not sure what that means but it doesn't sound good. Is there a fix? Thank you.

---

### Post by plucky on 2013-10-22
Do you have the Medibuntu Repository enabled?

It is now closed down and you are possibly getting a 404 error.

Open a terminal and post output for ```
sudo apt-get update
```

---

### Post by Lloydb39 on 2013-10-22
In the error details it says something about medibuntu, and also 404.
Here is the terminal output concerning medibuntu:
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free amd64 Packages                  
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free amd64 Packages              
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages                   
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages               
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en_US               
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en                  
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en_US           
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Fetched 3,548 kB in 12s (286 kB/s)
W: Failed to fetch [http://packages.medibuntu.org/dists/precise/Release.gpg](http://packages.medibuntu.org/dists/precise/Release.gpg)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/free/binary-amd64/Packages](http://packages.medibuntu.org/dists/precise/free/binary-amd64/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/binary-amd64/Packages](http://packages.medibuntu.org/dists/precise/non-free/binary-amd64/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en_US](http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en_US)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en](http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en_US](http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en_US)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en](http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by sandyd on 2013-10-22
nvm

---

### Post by howefield on 2013-10-22
The medibuntu repositories no longer exist so you have to remove them from your sources.list file.

Open up the Software Centre, and from the Edit menu, select Software Sources, you should be able to remove or uncheck anything labeled medibuntu from the Other Software tab.

---

### Post by Bashing-om on 2013-10-22
howefield; Hi !

Never mind, sandyd beat me to it !

[INDENT][INDENT]where there are solutions there are no problems
[/INDENT][/INDENT]

---

### Post by Lloydb39 on 2013-10-23
I think that did it. Thanks again.

---

### Post by kinetonat on 2013-10-26
Same problem here. Thanks for the solution!
12.04lts

---

