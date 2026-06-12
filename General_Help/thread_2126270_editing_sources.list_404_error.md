---
title: "editing sources.list 404 error"
date: 2013-03-16
forum: General Help
---

### Post by martin1991 on 2013-03-16
hi, 
i have edited the sources.list file to include a new package i require, however when i run the apt-get update command i get a 404 not found error (..... .amazonaws.com/apt/dists/precise/contrib/binary-i386/Packages 404 not found). however inspecting the index online the packages are located in a binary-amd64 library. 

I am running Ubuntu 12.04.1 64 bit on a vm ware virtual machine.

How would i be able to make Ubuntu direct to the binary-amd64 library and not binary-i386? 

Thanks, Martin

---

### Post by mcduck on 2013-03-16
Could you post the complete sources.list entry you are trying to use here? And perhaps a link to the web site (or something) about the repository?

Keep in mind that you can't add a *package* through the sources.list, and as you can see from the other entries in the file, they are not simple URLs to the directory where the files are located, but instead the entries include URL and both distribution and repository names...

---

### Post by martin1991 on 2013-03-16
hi, thanks for the reply.

The sources.list entry is: deb [http://ec2-79-125-53-176.eu-west-1.compute.amazonaws.com/apt/](http://ec2-79-125-53-176.eu-west-1.compute.amazonaws.com/apt/) precise contrib

The repository is: [http://ec2-79-125-53-176.eu-west-1.compute.amazonaws.com/apt/](http://ec2-79-125-53-176.eu-west-1.compute.amazonaws.com/apt/)

within the repository is a binary-amd64 library, however when the at-get update command is ran it searches for a binary-i388 library, i cannot work out why or how to change this.

Thanks

---

### Post by martin1991 on 2013-03-17
Any one any ideas?

---

### Post by matt_symes on 2013-03-17
Hi

Can we check something as i don't quite understand.

Copy and paste this into the terminal

```
cd && sudo apt-cache gencaches -o Debug::pkgCacheGen=true 1&> tmp.txt && grep amazon tmp.txt
```

Copy and paste the output back into your next post.

I'll be away from keyboard for a number of hours.

Kind regards

---

### Post by martin1991 on 2013-03-17
Hi, 

thanks for the reply, this is the output from the command: 

 Do we have write-access to the cache files? YES
Reading package lists...CacheFile doesn't exist
pkgcache.bin is NOT valid
Open filebased MMap
CacheFile doesn't exist
srcpkgcache.bin is NOT valid - rebuild
Remaping from 0x7fa033f99000 to 0x7fa032698000
Remaping from 0x7fa032698000 to 0x7fa030c98000
Caches are ready for shipping


Checking PkgFile [http://ec2-79-125-53-176.eu-west-1.compute.amazonaws.com/apt/](http://ec2-79-125-53-176.eu-west-1.compute.amazonaws.com/apt/) precise/contrib Sources (ec2-79-125-53-176.eu-west-1.compute.amazonaws.com_apt_dists_precise_contrib_source_Sources): Has NO packages
Checking PkgFile [http://ec2-79-125-53-176.eu-west-1.compute.amazonaws.com/apt/](http://ec2-79-125-53-176.eu-west-1.compute.amazonaws.com/apt/) precise/contrib amd64 Packages (/var/lib/apt/lists/ec2-79-125-53-176.eu-west-1.compute.amazonaws.com_apt_dists_precise_contrib_binary-amd64_Packages): with ID 58 is valid
Checking PkgFile [http://ec2-79-125-53-176.eu-west-1.compute.amazonaws.com/apt/](http://ec2-79-125-53-176.eu-west-1.compute.amazonaws.com/apt/) precise/contrib i386 Packages (/var/lib/apt/lists/ec2-79-125-53-176.eu-west-1.compute.amazonaws.com_apt_dists_precise_contrib_binary-i386_Packages): file doesn't exist
Checking PkgFile [http://ec2-79-125-53-176.eu-west-1.compute.amazonaws.com/apt/](http://ec2-79-125-53-176.eu-west-1.compute.amazonaws.com/apt/) precise/contrib Translation-en (/var/lib/apt/lists/ec2-79-125-53-176.eu-west-1.compute.amazonaws.com_apt_dists_precise_contrib_i18n_Translation-en): Has NO packages
Checking PkgFile [http://ec2-79-125-53-176.eu-west-1.compute.amazonaws.com/apt/](http://ec2-79-125-53-176.eu-west-1.compute.amazonaws.com/apt/) precise/contrib Translation-en_GB (/var/lib/apt/lists/ec2-79-125-53-176.eu-west-1.compute.amazonaws.com_apt_dists_precise_contrib_i18n_Translation-en%5fGB): Has NO packages

The output shows the amd64 library is valid? 
How would i make the apt-get update command look for that amd64 library instead of the i368 one?

Thanks, martin

---

### Post by matt_symes on 2013-03-17
Hi
> 
The output shows the amd64 library is valid? 

Yes it's valid.

> How would i make the apt-get update command look for that amd64 library instead of the i368 one?

Exactly which library are you trying to install and exactly what command are you typing ?

I am to and fro from keyboard but i will get back to you.

Kind regards

---

### Post by martin1991 on 2013-03-17
Hi, 

sorry im not very experienced with Ubuntu. I am trying to  install a package from this amazon aws server (the package name is  co3509ns2).

i have added "deb [http://ec2-79-125-53-176.eu-west-1.c...onaws.com/apt/]("http://ec2-79-125-53-176.eu-west-1.compute.amazonaws.com/apt/") precise contrib" to the sources list.

after this i am running the "sudo apt-get update" command in the terminal which gives this 404 error:

W:  Failed to fetch  [http://ec2-79-125-53-176.eu-west-1.compute.amazonaws.com/apt/dists/precise/contrib/binary-i386/Packages](http://ec2-79-125-53-176.eu-west-1.compute.amazonaws.com/apt/dists/precise/contrib/binary-i386/Packages)   404  Not Found

as you can see the 404 is coming from ubuntu looking in the i368 library and not amd64 (i think?), but i dont know how to change this. 

sorry if im not making much sense 

Thanks, Martin

---

### Post by matt_symes on 2013-03-17
Hi

I'm not sure if that's a problem as it is finding the amd64 package list.

It's not finding the i386 package file as there is none.

On my machine

```

matthew-S206:/home/matthew % uname -m
x86_64
matthew-S206:/home/matthew % 

```

i added the deb to /etc/apt/sources.list

```
matthew-S206:/home/matthew % grep amazon /etc/apt/sources.list
deb http://ec2-79-125-53-176.eu-west-1.compute.amazonaws.com/apt/ precise contrib

```

After an apt-get update it got the package files.

```

matthew-S206:/home/matthew % ls -l /var/lib/apt/lists/*amazon*
-rw-r--r-- 1 root root 2301 Mar 12 23:28 /var/lib/apt/lists/ec2-79-125-53-176.eu-west-1.compute.amazonaws.com_apt_dists_precise_contrib_binary-amd64_Packages
-rw-r--r-- 1 root root  952 Mar 12 23:28 /var/lib/apt/lists/ec2-79-125-53-176.eu-west-1.compute.amazonaws.com_apt_dists_precise_Release
```

I can then search for the packages.

```

matthew-S206:/home/matthew % apt-cache search co3509          
co3509ns2 - ns-2 packaged for using on CO3509 at UCLan
co3509nsbench - nsBench 1.3 from http://www.mnlab.cs.depaul.edu/projects/nsbench/
co3509nstrparsers - Parsers for ns-2 trace files which give throughput, jitter, delay and packet loss measurements.
co3509stats - Stats packages for network data. Including: stddev, CI, jains and NRU.
matthew-S206:/home/matthew % 
```

I should then be able to install them (but i have no real idea what they are :) ).

```

matthew-S206:/home/matthew % sudo apt-get install co3509ns2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  co3509ns2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 85.1 MB of archives.
After this operation, 0 B of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  co3509ns2
Install these packages without verification [y/N]? n
E: Some packages could not be authenticated
matthew-S206:/home/matthew % 

```

You may be missing keys to anthenticate the repo.

Can you tell me the name of the package you are trying to install ?

I think the question is how to remove search for the i386 packages ?

Kind regards

---

### Post by martin1991 on 2013-03-17
Hi, 

I have eventually managed to get them to download ... i was looking through the index and found the .deb files which allowed me to download the packages i need via the software centre, which seems to have worked ok. 

I am still completely clueless as to why im getting that 404 error though :confused:

many thanks for the help, martin

---

