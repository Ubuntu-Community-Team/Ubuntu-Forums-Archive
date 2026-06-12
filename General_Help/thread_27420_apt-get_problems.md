---
title: "apt-get problems"
date: 2005-04-16
forum: General Help
---

### Post by Xaero on 2005-04-16
I've just installed Ubuntu onto my laptop running an AMD64 processor. I'm going through through the Starter Guide and editing my sources.list file. I've ran the keyserver commands, but every time I update, I get:

W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-amd64_Packages) - stat (2 No such file or directory)

or 

Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/stable/Release](ftp://ftp.nerim.net/debian-marillat/dists/stable/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)

It looks like I am getting 1 of every error for each ftp.nerim.net entry. I can't install any of the .deb files that are hosted on that site. (Acrobat, flash, rar, etc), giving an error: 

E: Couldn't find package flashplayer-mozilla (for example)

I've traded sources.list files with someone on IRC, and his gives the same errors.  Is there something I missed or not doing? 

Thanks

---

### Post by lukem on 2005-04-16
[QUOTE=Xaero]I've just installed Ubuntu onto my laptop running an AMD64 processor. I'm going through through the Starter Guide and editing my sources.list file. I've ran the keyserver commands, but every time I update, I get:

W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-amd64_Packages) - stat (2 No such file or directory)

or 

Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/stable/Release](ftp://ftp.nerim.net/debian-marillat/dists/stable/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)

It looks like I am getting 1 of every error for each ftp.nerim.net entry. I can't install any of the .deb files that are hosted on that site. (Acrobat, flash, rar, etc), giving an error: 

E: Couldn't find package flashplayer-mozilla (for example)

I've traded sources.list files with someone on IRC, and his gives the same errors.  Is there something I missed or not doing? 

Thanks[/QUOTE]


Not familiar with the amd64 version, but does your repository list read 
[ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main 
or does it say
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main

mine is written as the latter and seems to be ok.

good luck

---

### Post by Xaero on 2005-04-17
[QUOTE=lukem]Not familiar with the amd64 version, but does your repository list read 
[ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main 
or does it say
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main

mine is written as the latter and seems to be ok.

good luck[/QUOTE]

my sources.list has the following lines:

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

I was thinking maybe a problem with that site, but nobody else is having this problem.  ](*,)

---

### Post by acantril on 2005-04-17
[QUOTE=Xaero]my sources.list has the following lines:

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

I was thinking maybe a problem with that site, but nobody else is having this problem.  ](*,)[/QUOTE]

Im having problems with "500 connection refused" when using apt today...

---

### Post by Windsurfer on 2005-04-20
Jag har precis samma problem. Kör ubuntu på en AMD64-burk och det är inte mycket som går att installera via apt-get. Finns det någon som har en sources.list fil anpassad för 64-bitarsversionen av ubuntu?

---

### Post by klutzini on 2005-05-07
I am also having the same challange as Xaero. this is my text when I do apt-get update:

Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/stable/Release](ftp://ftp.nerim.net/debian-marillat/dists/stable/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/testing/Release](ftp://ftp.nerim.net/debian-marillat/dists/testing/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done

Also, when I try to install some packages like 'flash' etc... it cannot find the package. I assume that this is due to the above.

hope u can help...
Klutzini

---

### Post by klutzini on 2005-05-07
[QUOTE=klutzini]I am also having the same challange as Xaero. this is my text when I do apt-get update:

Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/stable/Release](ftp://ftp.nerim.net/debian-marillat/dists/stable/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/testing/Release](ftp://ftp.nerim.net/debian-marillat/dists/testing/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done

Also, when I try to install some packages like 'flash' etc... it cannot find the package. I assume that this is due to the above.

hope u can help...
Klutzini[/QUOTE]
 oh... and I forgot to say that my machine is a amd64!!

---

