---
title: "Server 6.06 and Repos"
date: 2007-01-14
forum: General Help
---

### Post by mkosmo on 2007-01-14
I just installed fresh a LAMP copy of Ubuntu Dapper Server for i386.  I cannot access many repositories... notably official archives and security updates.  Any ideas?  IPv6 is disabled, for the record.  I can ping these IPs and use the same repos (but Edgy) from my laptop on the same network.  thanks!

kosmo@titan:~$ sudo apt-get update
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg
  Connection failed
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper Release.gpg                                                     
  Connection failed [IP: 88.191.35.32 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg                                              
  Connection failed
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release                                              
Err [http://mirror2.ubuntulinux.nl](http://mirror2.ubuntulinux.nl) dapper-seveas Release.gpg                                             
  Connection failed
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper Release                                                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release                                                  
Ign [http://mirror2.ubuntulinux.nl](http://mirror2.ubuntulinux.nl) dapper-seveas Release                                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages                                        
Ign [http://mirror2.ubuntulinux.nl](http://mirror2.ubuntulinux.nl) dapper-seveas/all Packages                                            
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/free Packages                                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages                                            
Err [http://mirror2.ubuntulinux.nl](http://mirror2.ubuntulinux.nl) dapper-seveas/all Packages                                            
  Connection failed
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages                                        
  Connection failed
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages                                      
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/non-free Packages                                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages                                        
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/free Packages                                                   
  Connection failed [IP: 88.191.30.43 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages                                      
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/non-free Packages                                               
  Connection failed [IP: 88.191.42.241 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages                                            
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages                           
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages                             
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages                           
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg                                          
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg
  Connection failed [IP: 146.137.96.7 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages    
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Packages
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Connection failed
Failed to fetch [http://mirror2.ubuntulinux.nl/dists/dapper-seveas/Release.gpg](http://mirror2.ubuntulinux.nl/dists/dapper-seveas/Release.gpg)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/dapper/Release.gpg](http://medibuntu.sos-sts.com/repo/dists/dapper/Release.gpg)  Connection failed [IP: 88.191.35.32 80]
Failed to fetch [http://archive.canonical.com/dists/dapper-commercial/Release.gpg](http://archive.canonical.com/dists/dapper-commercial/Release.gpg)  Connection failed
Failed to fetch [http://archive.canonical.com/dists/dapper-commercial/main/binary-i386/Packages.gz](http://archive.canonical.com/dists/dapper-commercial/main/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://mirror2.ubuntulinux.nl/dists/dapper-seveas/all/binary-i386/Packages.gz](http://mirror2.ubuntulinux.nl/dists/dapper-seveas/all/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/dapper/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/dapper/free/binary-i386/Packages.gz)  Connection failed [IP: 88.191.30.43 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/dapper/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/dapper/non-free/binary-i386/Packages.gz)  Connection failed [IP: 88.191.42.241 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz)  Connection failed [IP: 146.137.96.7 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
kosmo@titan:~$ ping 146.137.96.7
PING 146.137.96.7 (146.137.96.7) 56(84) bytes of data.
64 bytes from 146.137.96.7: icmp_seq=1 ttl=53 time=7.97 ms
64 bytes from 146.137.96.7: icmp_seq=2 ttl=53 time=7.37 ms
64 bytes from 146.137.96.7: icmp_seq=3 ttl=53 time=7.53 ms

--- 146.137.96.7 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2019ms
rtt min/avg/max/mdev = 7.374/7.626/7.971/0.271 ms

---

### Post by mkosmo on 2007-01-14
Still having this problem, so time did not fix it.  Any ideas?

---

### Post by mkosmo on 2007-01-14
Installed 6.10 server instead and all is well.  That doesnt seem right.  So much for Dapper being LTS.

---

