---
title: "Sub-process bzip2 returned an error code (2)"
date: 2008-05-09
forum: General Help
---

### Post by jawana on 2008-05-09
Hi All,

Today when i tried apt-get update , i started getting the following errors Sub-process bzip2 returned an error code (2) on most of the repo links.
Any idea why i am getting this ?

Any advice will be much appreciated.

```
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy Release.gpg
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Translation-en_GB
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Translation-en_GB
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy Release
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Packages
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Packages
Err cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.gpg                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg            
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                   
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_GB
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Translation-en_GB     
Get: 3 [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_GB  
99% [1 Translation-en_GB bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_GB   
66% [2 Translation-en_GB bzip2 0] [Waiting for headers] [Waiting for headers] [bzip2: (stdin) is not a bzip2 file.
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Translation-en_GB                  
33% [3 Translation-en_GB bzip2 0] [Waiting for headers] [Waiting for headers] [bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_GB               
Get: 4 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_GB        
25% [4 Translation-en_GB bzip2 0] [Waiting for headers] [Waiting for headers] [bzip2: (stdin) is not a bzip2 file.
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_GB           
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Translation-en_GB         
20% [5 Translation-en_GB bzip2 0] [Waiting for headers] [Waiting for headers] [bzip2: (stdin) is not a bzip2 file.
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Translation-en_GB            
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Get: 6 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_GB
16% [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_GB     
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Translation-en_GB           
14% [Release gpgv 6998] [7 Translation-en_GB bzip2 0] [Waiting for headers] [Wabzip2: (stdin) is not a bzip2 file.
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Translation-en_GB              
Get: 8 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_GB    
12% [Release gpgv 6998] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get: 9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Translation-en_GB         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_GB       
11% [9 Translation-en_GB bzip2 0] [Waiting for headers] [Waiting for headers] [bzip2: (stdin) is not a bzip2 file.
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Translation-en_GB            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release.gpg          
Get: 10 [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages        
10% [Release gpgv 37041] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
  Sub-process bzip2 returned an error code (2)
Get: 11 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
18% [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get: 12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Translation-en_GB
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages    
  Sub-process bzip2 returned an error code (2)
25% [12 Translation-en_GB bzip2 0] [Waiting for headers] [Waiting for headers] bzip2: (stdin) is not a bzip2 file.
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Translation-en_GB          
Get: 13 [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                     
23% [13 Sources bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources              
  Sub-process bzip2 returned an error code (2)
Get: 14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Translation-en_GB
Get: 15 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
33% [14 Translation-en_GB bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Translation-en_GB   
26% [15 Packages bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages          
  Sub-process bzip2 returned an error code (2)
Get: 16 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
31% [16 Packages bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages    
  Sub-process bzip2 returned an error code (2)
Get: 17 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Translation-en_GB
35% [17 Translation-en_GB bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Translation-en_GB     
Get: 18 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages           
33% [18 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
  Sub-process bzip2 returned an error code (2)
Get: 19 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB
36% [19 Translation-en_GB bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports Release.gpg
Get: 20 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/main Translation-en_GB
34% [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/main Translation-en_GB
Get: 21 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/restricted Translation-en_GB
33% [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/restricted Translation-en_GB
Get: 22 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/universe Translation-en_GB
31% [22 Translation-en_GB bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/universe Translation-en_GB
Get: 23 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/multiverse Translation-en_GB
30% [23 Translation-en_GB bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed Release.gpg
Get: 24 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/restricted Translation-en_GB
29% [24 Translation-en_GB bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/restricted Translation-en_GB
Get: 25 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/main Translation-en_GB
27% [25 Translation-en_GB bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/main Translation-en_GB
Get: 26 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/multiverse Translation-en_GB
26% [26 Translation-en_GB bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/multiverse Translation-en_GB
Get: 27 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/universe Translation-en_GB
25% [27 Translation-en_GB bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed Release
Get: 28 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Packages
24% [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Packages
  Sub-process bzip2 returned an error code (2)
Get: 29 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Packages
27% [29 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Packages
  Sub-process bzip2 returned an error code (2)
Get: 30 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Sources
29% [30 Sources bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Sources
  Sub-process bzip2 returned an error code (2)
Get: 31 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Sources
32% [31 Sources bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Sources
  Sub-process bzip2 returned an error code (2)
Get: 32 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Packages
34% [32 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Packages
  Sub-process bzip2 returned an error code (2)
Get: 33 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Sources
36% [33 Sources bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Sources
  Sub-process bzip2 returned an error code (2)
Get: 34 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Packages
38% [34 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Packages
  Sub-process bzip2 returned an error code (2)
Get: 35 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Sources
39% [35 Sources bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Sources
  Sub-process bzip2 returned an error code (2)
Get: 36 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Packages
41% [36 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Packages
  Sub-process bzip2 returned an error code (2)
Get: 37 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Packages
43% [37 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Packages
  Sub-process bzip2 returned an error code (2)
Get: 38 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Sources
44% [38 Sources bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Sources
  Sub-process bzip2 returned an error code (2)
Get: 39 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Sources
45% [39 Sources bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Sources
  Sub-process bzip2 returned an error code (2)
Get: 40 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Packages
47% [40 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Packages
  Sub-process bzip2 returned an error code (2)
Get: 41 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Sources
48% [41 Sources bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Sources
  Sub-process bzip2 returned an error code (2)
Get: 42 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Packages
49% [42 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Packages
  Sub-process bzip2 returned an error code (2)
Get: 43 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Sources
51% [43 Sources bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Sources
  Sub-process bzip2 returned an error code (2)
Get: 44 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/main Packages
52% [44 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/main Packages
  Sub-process bzip2 returned an error code (2)
Get: 45 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/restricted Packages
53% [45 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/restricted Packages
  Sub-process bzip2 returned an error code (2)
Get: 46 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/universe Packages
54% [46 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/universe Packages
  Sub-process bzip2 returned an error code (2)
Get: 47 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/multiverse Packages
55% [47 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/multiverse Packages
  Sub-process bzip2 returned an error code (2)
Get: 48 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/main Sources
56% [48 Sources bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/main Sources
  Sub-process bzip2 returned an error code (2)
Get: 49 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/restricted Sources
57% [49 Sources bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/restricted Sources
  Sub-process bzip2 returned an error code (2)
Get: 50 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/universe Sources
57% [50 Sources bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/universe Sources
  Sub-process bzip2 returned an error code (2)
Get: 51 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/multiverse Sources
58% [51 Sources bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/multiverse Sources
  Sub-process bzip2 returned an error code (2)
Get: 52 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/restricted Packages
59% [52 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/restricted Packages
  Sub-process bzip2 returned an error code (2)
Get: 53 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/main Packages
60% [53 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/main Packages
  Sub-process bzip2 returned an error code (2)
Get: 54 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/multiverse Packages
61% [54 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/multiverse Packages
  Sub-process bzip2 returned an error code (2)
Get: 55 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/universe Packages
61% [55 Packages bzip2 0]bzip2: (stdin) is not a bzip2 file.
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/universe Packages
  Sub-process bzip2 returned an error code (2)
Fetched 123kB in 4s (28.3kB/s)
W: Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/hardy/partner/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/source/Sources.bz2](http://archive.canonical.com/ubuntu/dists/hardy/partner/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-backports/main/binary-i386/Packages.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-backports/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/binary-i386/Packages.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/binary-i386/Packages.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/binary-i386/Packages.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-backports/main/source/Sources.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-backports/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/source/Sources.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/source/Sources.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/source/Sources.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-proposed/restricted/binary-i386/Packages.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-proposed/restricted/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/binary-i386/Packages.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-proposed/multiverse/binary-i386/Packages.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-proposed/multiverse/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-proposed/universe/binary-i386/Packages.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-proposed/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

here is my sources.list file

```
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu hardy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://security.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe
```

---

### Post by Perfect Storm on 2008-05-09
First try change to the main server instead of (gb) and disable the CD-rom source in the repo. Thereafter run and update again and see what happens.

---

### Post by jawana on 2008-05-09
HI AI

I disabled the cd rom repo and changed the repos from gb to main , but when i tried to update again i got the following error

```
GPG error: http://archive.ubuntu.com hardy-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>Failed to fetch http://archive.canonical.com/ubuntu/dists/hardy/partner/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.canonical.com/ubuntu/dists/hardy/partner/source/Sources.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-backports/main/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-backports/main/source/Sources.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/source/Sources.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/source/Sources.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/source/Sources.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/restricted/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/multiverse/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/universe/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by Perfect Storm on 2008-05-09
ok, backup your sourcelist first.
```
sudo apt-get clean
gksudo /etc/apt/sources.list

```

Try my list;
```
[size=1]# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Beta amd64 (20080319)]/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://dk.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu/ hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://dk.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://dk.archive.ubuntu.com/ubuntu/ hardy universe
deb http://dk.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://dk.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://dk.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://dk.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://dk.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
[/size]
```

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by jawana on 2008-05-09
HI AI,
Really appreciated your quick reply, i followed your instructions but still getting same error or update.

Do you recommend i trash and reinstall the whole thing again?

```
Get: 1 http://archive.ubuntu.com hardy Release.gpg [191B]                      
Get: 2 http://archive.canonical.com hardy Release.gpg [191B]                   
Get: 3 http://archive.canonical.com hardy/partner Translation-en_GB  
99% [3 Translation-en_GB bzip2 0] [Waiting for headers] [Waiting for headers] [bzip2: (stdin) is not a bzip2 file.
Ign http://archive.canonical.com hardy/partner Translation-en_GB               
Hit http://archive.canonical.com hardy Release                                 
Ign http://archive.canonical.com hardy Release                                 
Get: 4 http://dk.archive.ubuntu.com hardy Release.gpg [191B]                   
Get: 5 http://archive.canonical.com hardy/partner Packages                     
55% [Waiting for headers] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://archive.canonical.com hardy/partner Packages                        
  Sub-process bzip2 returned an error code (2)
Get: 6 http://archive.canonical.com hardy/partner Sources                      
69% [6 Sources bzip2 0] [Waiting for headers] [Waiting for headers] [Waiting fobzip2: (stdin) is not a bzip2 file.
Err http://archive.canonical.com hardy/partner Sources                         
  Sub-process bzip2 returned an error code (2)
Get: 7 http://dk.archive.ubuntu.com hardy/main Translation-en_GB               
69% [7 Translation-en_GB bzip2 0] [Waiting for headers] [Waiting for headers] [bzip2: (stdin) is not a bzip2 file.
Ign http://dk.archive.ubuntu.com hardy/main Translation-en_GB                  
Get: 8 http://dk.archive.ubuntu.com hardy/restricted Translation-en_GB         
68% [8 Translation-en_GB bzip2 0] [Waiting for headers] [Waiting for headers] [bzip2: (stdin) is not a bzip2 file.
Ign http://dk.archive.ubuntu.com hardy/restricted Translation-en_GB            
Get: 9 http://security.ubuntu.com hardy-security Release.gpg [191B]            
Get: 10 http://security.ubuntu.com hardy-security/main Translation-en_GB
67% [Waiting for headers] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://security.ubuntu.com hardy-security/main Translation-en_GB           
Get: 11 http://security.ubuntu.com hardy-security/restricted Translation-en_GB 
66% [Waiting for headers] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_GB     
Get: 12 http://security.ubuntu.com hardy-security/universe Translation-en_GB   
64% [12 Translation-en_GB bzip2 0] [Waiting for headers] [Waiting for headers] bzip2: (stdin) is not a bzip2 file.
Ign http://security.ubuntu.com hardy-security/universe Translation-en_GB       
Get: 13 http://security.ubuntu.com hardy-security/multiverse Translation-en_GB 
63% [13 Translation-en_GB bzip2 0] [Waiting for headers] [Waiting for headers] bzip2: (stdin) is not a bzip2 file.
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_GB     
Get: 14 http://dk.archive.ubuntu.com hardy/universe Translation-en_GB          
62% [Waiting for headers] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://dk.archive.ubuntu.com hardy/universe Translation-en_GB              
Hit http://security.ubuntu.com hardy-security Release                          
Get: 15 http://dk.archive.ubuntu.com hardy/multiverse Translation-en_GB        
61% [Release gpgv 37041] [Waiting for headers] [Waiting for headers]  849B/s 3sbzip2: (stdin) is not a bzip2 file.
Ign http://security.ubuntu.com hardy-security Release                          
Ign http://dk.archive.ubuntu.com hardy/multiverse Translation-en_GB            
Get: 16 http://security.ubuntu.com hardy-security/main Packages               
67% [Waiting for headers] [Waiting for headers]                       849B/s 4sbzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com hardy-security/main Packages                    
  Sub-process bzip2 returned an error code (2)
Get: 17 http://security.ubuntu.com hardy-security/restricted Packages
73% [17 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Waiting bzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com hardy-security/restricted Packages              
  Sub-process bzip2 returned an error code (2)
Get: 18 http://security.ubuntu.com hardy-security/restricted Sources           
77% [Waiting for headers] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com hardy-security/restricted Sources               
  Sub-process bzip2 returned an error code (2)
Get: 19 http://security.ubuntu.com hardy-security/main Sources                 
79% [19 Sources bzip2 0] [Waiting for headers] [Waiting for headers] [Waiting fbzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com hardy-security/main Sources                     
  Sub-process bzip2 returned an error code (2)
Get: 20 http://security.ubuntu.com hardy-security/multiverse Sources           
82% [20 Sources bzip2 0] [Waiting for headers] [Waiting for headers] [Waiting fbzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com hardy-security/multiverse Sources               
  Sub-process bzip2 returned an error code (2)
Get: 21 http://dk.archive.ubuntu.com hardy-updates Release.gpg [191B]          
Get: 22 http://security.ubuntu.com hardy-security/universe Sources   
84% [22 Sources bzip2 0] [Waiting for headers] [Waiting for headers] [Waiting fbzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com hardy-security/universe Sources                 
  Sub-process bzip2 returned an error code (2)
Get: 23 http://security.ubuntu.com hardy-security/universe Packages            
85% [23 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Waiting bzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com hardy-security/universe Packages                
  Sub-process bzip2 returned an error code (2)
Get: 24 http://security.ubuntu.com hardy-security/multiverse Packages          
86% [24 Packages bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com hardy-security/multiverse Packages    
  Sub-process bzip2 returned an error code (2)
Get: 25 http://dk.archive.ubuntu.com hardy-updates/main Translation-en_GB      
86% [25 Translation-en_GB bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://dk.archive.ubuntu.com hardy-updates/main Translation-en_GB         
Get: 26 http://dk.archive.ubuntu.com hardy-updates/restricted Translation-en_GB
86% [Waiting for headers] [Waiting for headers]                       849B/s 4sbzip2: (stdin) is not a bzip2 file.
Ign http://dk.archive.ubuntu.com hardy-updates/restricted Translation-en_GB    
Get: 27 http://dk.archive.ubuntu.com hardy-updates/universe Translation-en_GB  
85% [27 Translation-en_GB bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://dk.archive.ubuntu.com hardy-updates/universe Translation-en_GB     
Get: 28 http://dk.archive.ubuntu.com hardy-updates/multiverse Translation-en_GB
85% [28 Translation-en_GB bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://dk.archive.ubuntu.com hardy-updates/multiverse Translation-en_GB   
Get: 29 http://dk.archive.ubuntu.com hardy Release [65.9kB]                    
Ign http://dk.archive.ubuntu.com hardy Release                                 
Get: 30 http://dk.archive.ubuntu.com hardy-updates Release [51.2kB]            
Ign http://dk.archive.ubuntu.com hardy-updates Release                         
Get: 31 http://dk.archive.ubuntu.com hardy/main Packages                       
97% [Waiting for headers] [Waiting for headers]                      2938B/s 1sbzip2: (stdin) is not a bzip2 file.
Err http://dk.archive.ubuntu.com hardy/main Packages                           
  Sub-process bzip2 returned an error code (2)
Get: 32 http://dk.archive.ubuntu.com hardy/restricted Packages                 
97% [Waiting for headers] [Waiting for headers]                      2938B/s 1sbzip2: (stdin) is not a bzip2 file.
Err http://dk.archive.ubuntu.com hardy/restricted Packages                     
  Sub-process bzip2 returned an error code (2)
Get: 33 http://dk.archive.ubuntu.com hardy/restricted Sources                  
97% [33 Sources bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://dk.archive.ubuntu.com hardy/restricted Sources           
  Sub-process bzip2 returned an error code (2)
Get: 34 http://dk.archive.ubuntu.com hardy/main Sources                        
97% [34 Sources bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://dk.archive.ubuntu.com hardy/main Sources                 
  Sub-process bzip2 returned an error code (2)
Get: 35 http://dk.archive.ubuntu.com hardy/multiverse Sources                  
97% [35 Sources bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://dk.archive.ubuntu.com hardy/multiverse Sources           
  Sub-process bzip2 returned an error code (2)
Get: 36 http://dk.archive.ubuntu.com hardy/universe Sources                    
97% [Waiting for headers] [Waiting for headers]                     18.8kB/s 0sbzip2: (stdin) is not a bzip2 file.
Err http://dk.archive.ubuntu.com hardy/universe Sources                        
  Sub-process bzip2 returned an error code (2)
Get: 37 http://dk.archive.ubuntu.com hardy/universe Packages                   
97% [Waiting for headers] [Waiting for headers]                     18.8kB/s 0sbzip2: (stdin) is not a bzip2 file.
Err http://dk.archive.ubuntu.com hardy/universe Packages                       
  Sub-process bzip2 returned an error code (2)
Get: 38 http://dk.archive.ubuntu.com hardy/multiverse Packages                 
97% [38 Packages bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://dk.archive.ubuntu.com hardy/multiverse Packages           
  Sub-process bzip2 returned an error code (2)
Get: 39 http://dk.archive.ubuntu.com hardy-updates/main Packages               
97% [39 Packages bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://dk.archive.ubuntu.com hardy-updates/main Packages         
  Sub-process bzip2 returned an error code (2)
Get: 40 http://dk.archive.ubuntu.com hardy-updates/restricted Packages         
97% [40 Packages bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://dk.archive.ubuntu.com hardy-updates/restricted Packages   
  Sub-process bzip2 returned an error code (2)
Get: 41 http://dk.archive.ubuntu.com hardy-updates/restricted Sources          
97% [41 Sources bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://dk.archive.ubuntu.com hardy-updates/restricted Sources   
  Sub-process bzip2 returned an error code (2)
Get: 42 http://dk.archive.ubuntu.com hardy-updates/main Sources                
97% [42 Sources bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://dk.archive.ubuntu.com hardy-updates/main Sources         
  Sub-process bzip2 returned an error code (2)
Get: 43 http://dk.archive.ubuntu.com hardy-updates/multiverse Sources          
97% [43 Sources bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://dk.archive.ubuntu.com hardy-updates/multiverse Sources   
  Sub-process bzip2 returned an error code (2)
Get: 44 http://dk.archive.ubuntu.com hardy-updates/universe Sources            
97% [44 Sources bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://dk.archive.ubuntu.com hardy-updates/universe Sources     
  Sub-process bzip2 returned an error code (2)
Get: 45 http://dk.archive.ubuntu.com hardy-updates/universe Packages           
97% [45 Packages bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://dk.archive.ubuntu.com hardy-updates/universe Packages     
  Sub-process bzip2 returned an error code (2)
Get: 46 http://dk.archive.ubuntu.com hardy-updates/multiverse Packages         
97% [Waiting for headers]                                            281B/s 14sbzip2: (stdin) is not a bzip2 file.
Err http://dk.archive.ubuntu.com hardy-updates/multiverse Packages             
  Sub-process bzip2 returned an error code (2)
Hit http://archive.ubuntu.com hardy Release                                    
Ign http://archive.ubuntu.com hardy Release
Get: 47 http://archive.ubuntu.com hardy/main Sources
97% [Working]bzip2: (stdin) is not a bzip2 file.
Err http://archive.ubuntu.com hardy/main Sources
  Sub-process bzip2 returned an error code (2)
Get: 48 http://archive.ubuntu.com hardy/restricted Sources                     
97% [Working]bzip2: (stdin) is not a bzip2 file.
Err http://archive.ubuntu.com hardy/restricted Sources
  Sub-process bzip2 returned an error code (2)
Fetched 154kB in 2min2s (1258B/s)
W: GPG error: http://archive.canonical.com hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://security.ubuntu.com hardy-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://dk.archive.ubuntu.com hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://dk.archive.ubuntu.com hardy-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://archive.ubuntu.com hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/hardy/partner/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/hardy/partner/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by Perfect Storm on 2008-05-10
Are you behind a firewall or router, it seems it can't connect to the servers.

---

