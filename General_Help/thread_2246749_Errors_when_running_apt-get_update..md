---
title: "Errors when running apt-get update."
date: 2014-10-03
forum: General Help
---

### Post by vermox on 2014-10-03
When I run apt-get update with Ubuntu 13.04 I get the following output and errors. Can anyone help me with what I can do to rectify this situation?

```
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring Release.gpg
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates Release.gpg                    
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports Release.gpg                  
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring Release                                
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates Release                        
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports Release                      
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/main Sources/DiffIndex                 
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/restricted Sources/DiffIndex           
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/universe Sources/DiffIndex        
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/multiverse Sources/DiffIndex      
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/main amd64 Packages/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/restricted amd64 Packages/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/universe amd64 Packages/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/multiverse amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release.gpg
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/main i386 Packages/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/restricted i386 Packages/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/universe i386 Packages/DiffIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/multiverse i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release    
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/main Sources/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/restricted Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Sources/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/universe Sources/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/multiverse Sources/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/main amd64 Packages/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/restricted amd64 Packages/DiffIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Sources/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/universe amd64 Packages/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/multiverse amd64 Packages/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/main i386 Packages/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/restricted i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Sources/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/universe i386 Packages/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/multiverse i386 Packages/DiffIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Sources/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/main Sources/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/restricted Sources/DiffIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/universe Sources/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/multiverse Sources/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/main amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Sources/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/restricted amd64 Packages/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/universe amd64 Packages/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/multiverse amd64 Packages/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/main i386 Packages/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/restricted i386 Packages/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/universe i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main amd64 Packages/DiffIndex
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/multiverse i386 Packages/DiffIndex
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release.gpg             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted amd64 Packages/DiffIndex
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe amd64 Packages/DiffIndex
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main amd64 Packages     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse amd64 Packages/DiffIndex
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main i386 Packages      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse i386 Packages/DiffIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en_NZ                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en                        
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Sources                              
  404  Not Found
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main amd64 Packages              
  404  Not Found
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages               
  404  Not Found
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/main Translation-en_NZ       
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/main Translation-en
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/multiverse Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/multiverse Translation-en
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/restricted Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/restricted Translation-en
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/universe Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/universe Translation-en
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/main Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/main Translation-en
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/multiverse Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/multiverse Translation-en
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/restricted Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/restricted Translation-en
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/universe Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/universe Translation-en
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/main Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/main Translation-en
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/multiverse Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/multiverse Translation-en
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/restricted Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/restricted Translation-en
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/universe Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/universe Translation-en
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/main Sources
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/restricted Sources
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/universe Sources
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/multiverse Sources
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/main amd64 Packages
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/restricted amd64 Packages
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/universe amd64 Packages
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/multiverse amd64 Packages
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/main i386 Packages
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/restricted i386 Packages
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/universe i386 Packages
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring/multiverse i386 Packages
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/main Sources
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/restricted Sources
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/universe Sources
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/multiverse Sources
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/main amd64 Packages
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/restricted amd64 Packages
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/universe amd64 Packages
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/multiverse amd64 Packages
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/main i386 Packages
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/restricted i386 Packages
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/universe i386 Packages
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-updates/multiverse i386 Packages
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/main Sources
  404  Not Found
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en_NZ
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/restricted Sources
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/universe Sources
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/multiverse Sources
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/main amd64 Packages
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/restricted amd64 Packages
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/universe amd64 Packages
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/multiverse amd64 Packages
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/main i386 Packages
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/restricted i386 Packages
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/universe i386 Packages
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) raring-backports/multiverse i386 Packages
  404  Not Found
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en_NZ
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en_NZ
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en_NZ
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en_NZ
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Sources
  404  Not Found [IP: 91.189.88.153 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Sources
  404  Not Found [IP: 91.189.88.153 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Sources
  404  Not Found [IP: 91.189.88.153 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Sources
  404  Not Found [IP: 91.189.88.153 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main amd64 Packages
  404  Not Found [IP: 91.189.88.153 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted amd64 Packages
  404  Not Found [IP: 91.189.88.153 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe amd64 Packages
  404  Not Found [IP: 91.189.88.153 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse amd64 Packages
  404  Not Found [IP: 91.189.88.153 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main i386 Packages
  404  Not Found [IP: 91.189.88.153 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted i386 Packages
  404  Not Found [IP: 91.189.88.153 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe i386 Packages
  404  Not Found [IP: 91.189.88.153 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.88.153 80]
W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring/main/source/Sources](http://nz.archive.ubuntu.com/ubuntu/dists/raring/main/source/Sources)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring/restricted/source/Sources](http://nz.archive.ubuntu.com/ubuntu/dists/raring/restricted/source/Sources)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring/universe/source/Sources](http://nz.archive.ubuntu.com/ubuntu/dists/raring/universe/source/Sources)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring/multiverse/source/Sources](http://nz.archive.ubuntu.com/ubuntu/dists/raring/multiverse/source/Sources)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-amd64/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring/universe/binary-amd64/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/raring/universe/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-amd64/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-i386/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring/universe/binary-i386/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/raring/universe/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-i386/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring-updates/main/source/Sources](http://nz.archive.ubuntu.com/ubuntu/dists/raring-updates/main/source/Sources)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/source/Sources](http://nz.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/source/Sources)  404  Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/raring-security/main/source/Sources)  404  Not Found [IP: 91.189.88.153 80]

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/source/Sources](http://nz.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/source/Sources)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/source/Sources](http://nz.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/source/Sources)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-amd64/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-amd64/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/raring/main/source/Sources)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-amd64/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-amd64/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-i386/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-i386/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/source/Sources)  404  Not Found [IP: 91.189.88.153 80]

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-i386/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-i386/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages](http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/raring-security/universe/source/Sources)  404  Not Found [IP: 91.189.88.153 80]

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring-backports/main/source/Sources](http://nz.archive.ubuntu.com/ubuntu/dists/raring-backports/main/source/Sources)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/source/Sources](http://nz.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/source/Sources)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/source/Sources](http://nz.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/source/Sources)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/source/Sources](http://nz.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/source/Sources)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-amd64/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/raring-security/multiverse/source/Sources)  404  Not Found [IP: 91.189.88.153 80]

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-amd64/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-amd64/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-amd64/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-i386/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-i386/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-i386/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/main/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/raring-security/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.88.153 80]

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-i386/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.88.153 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/universe/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/raring-security/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.88.153 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/multiverse/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/raring-security/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.88.153 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/raring-security/main/binary-i386/Packages)  404  Not Found [IP: 91.189.88.153 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.88.153 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/raring-security/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.88.153 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/raring-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.88.153 80]
```

---

### Post by QIII on 2014-10-03
Hello!

13.04 has passed its EOL and is no longer supported.  The repositories have been moved.  

The staff recommends a fresh installation of one of the currently supported releases:  12.04 or 14.04.

---

### Post by vermox on 2014-10-03
Thank you very much for your reply. I am doing a fresh install now.

---

