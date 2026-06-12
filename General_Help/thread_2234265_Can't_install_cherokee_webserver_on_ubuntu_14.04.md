---
title: "Can't install cherokee webserver on ubuntu 14.04"
date: 2014-07-13
forum: General Help
---

### Post by kernelgo on 2014-07-13
Hi, first..I'm on Linuxmint 17 Quiana 64 bit xfce(based on ubuntu 14.04 - I'm right?)
I want to instal Cherokee webserver and tryed to add repo:
```
add-apt-repository ppa:cherokee-webserver
```

and after that:
```
apt-get update
```

but i got:
```
apt-get update
Ign file: apt-build InRelease
Ign file: apt-build Release.gpg                                                
Des:1 file: apt-build Release [107 B]                                          
Err file: apt-build/main i386 Packages                                         
  Fichero no encontrado
Ign file: apt-build/main Translation-es_ES                                     
Ign file: apt-build/main Translation-es                                        
Ign file: apt-build/main Translation-en                                        
Ign http://security.ubuntu.com trusty-security InRelease                       
Ign http://archive.ubuntu.com trusty InRelease                                 
Ign http://archive.canonical.com trusty InRelease                              
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://archive.ubuntu.com trusty-updates InRelease                         
Obj http://security.ubuntu.com trusty-security Release.gpg                     
Obj http://archive.canonical.com trusty Release.gpg                            
Ign http://ppa.launchpad.net trusty Release.gpg                                
Obj http://security.ubuntu.com trusty-security Release                         
Obj http://archive.ubuntu.com trusty Release.gpg                               
Obj http://archive.canonical.com trusty Release                                
Ign http://ppa.launchpad.net trusty Release                                    
Des:2 http://archive.ubuntu.com trusty-updates Release.gpg [933 B]             
Obj http://security.ubuntu.com trusty-security/main amd64 Packages             
Obj http://archive.canonical.com trusty/partner amd64 Packages                 
Obj http://archive.ubuntu.com trusty Release                                   
Obj http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Des:3 http://archive.ubuntu.com trusty-updates Release [58,5 kB]               
Obj http://archive.canonical.com trusty/partner i386 Packages                  
Ign http://extra.linuxmint.com qiana InRelease                                 
Ign http://packages.linuxmint.com qiana InRelease                              
Obj http://security.ubuntu.com trusty-security/universe amd64 Packages         
Obj http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Obj http://archive.getdeb.net trusty-getdeb InRelease                          
Obj http://security.ubuntu.com trusty-security/main i386 Packages              
Obj http://security.ubuntu.com trusty-security/restricted i386 Packages        
Des:4 http://extra.linuxmint.com qiana Release.gpg [198 B]                     
Des:5 http://packages.linuxmint.com qiana Release.gpg [198 B]                  
Obj http://archive.ubuntu.com trusty/main amd64 Packages                       
Obj http://security.ubuntu.com trusty-security/universe i386 Packages          
Obj http://archive.ubuntu.com trusty/restricted amd64 Packages                 
Obj http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Obj http://archive.ubuntu.com trusty/universe amd64 Packages                   
Obj http://archive.ubuntu.com trusty/multiverse amd64 Packages                 
Des:6 http://extra.linuxmint.com qiana Release [3.144 B]                       
Des:7 http://packages.linuxmint.com qiana Release [18,6 kB]                    
Obj http://archive.ubuntu.com trusty/main i386 Packages                        
Obj http://security.ubuntu.com trusty-security/main Translation-en             
Obj http://archive.getdeb.net trusty-getdeb/apps amd64 Packages                
Obj http://archive.ubuntu.com trusty/restricted i386 Packages                  
Obj http://archive.ubuntu.com trusty/universe i386 Packages                    
Des:8 http://extra.linuxmint.com qiana/main amd64 Packages [7.904 B]           
Obj http://security.ubuntu.com trusty-security/multiverse Translation-en       
Obj http://archive.ubuntu.com trusty/multiverse i386 Packages                  
Obj http://archive.ubuntu.com trusty/main Translation-es                       
Ign http://archive.canonical.com trusty/partner Translation-es_ES              
Obj http://archive.getdeb.net trusty-getdeb/apps i386 Packages                 
Obj http://archive.ubuntu.com trusty/main Translation-en                       
Ign http://archive.canonical.com trusty/partner Translation-es                 
Des:9 http://extra.linuxmint.com qiana/main i386 Packages [8.421 B]            
Des:10 http://packages.linuxmint.com qiana/main amd64 Packages [30,3 kB]       
Ign http://archive.canonical.com trusty/partner Translation-en                 
Obj http://security.ubuntu.com trusty-security/restricted Translation-en       
Obj http://archive.ubuntu.com trusty/multiverse Translation-es                 
Obj http://archive.ubuntu.com trusty/multiverse Translation-en                 
Obj http://security.ubuntu.com trusty-security/universe Translation-en         
Obj http://archive.ubuntu.com trusty/restricted Translation-es                 
Obj http://archive.ubuntu.com trusty/restricted Translation-en                 
Des:11 http://packages.linuxmint.com qiana/upstream amd64 Packages [23,6 kB]   
Obj http://archive.ubuntu.com trusty/universe Translation-es                   
Obj http://archive.ubuntu.com trusty/universe Translation-en                   
Des:12 http://archive.ubuntu.com trusty-updates/main amd64 Packages [218 kB]   
Err http://ppa.launchpad.net trusty/main Sources                               
  404  Not Found
Err http://ppa.launchpad.net trusty/main amd64 Packages                        
  404  Not Found
Des:13 http://packages.linuxmint.com qiana/import amd64 Packages [31,5 kB]     
Err http://ppa.launchpad.net trusty/main i386 Packages                         
  404  Not Found
Ign http://ppa.launchpad.net trusty/main Translation-es_ES                     
Ign http://ppa.launchpad.net trusty/main Translation-es                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Des:14 http://packages.linuxmint.com qiana/main i386 Packages [29,7 kB]        
Des:15 http://archive.ubuntu.com trusty-updates/restricted amd64 Packages [14 B]
Des:16 http://archive.ubuntu.com trusty-updates/universe amd64 Packages [155 kB]
Des:17 http://packages.linuxmint.com qiana/upstream i386 Packages [23,6 kB]    
Ign http://security.ubuntu.com trusty-security/main Translation-es_ES          
Ign http://security.ubuntu.com trusty-security/main Translation-es             
Ign http://security.ubuntu.com trusty-security/multiverse Translation-es_ES    
Des:18 http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages [7.392 B]
Ign http://security.ubuntu.com trusty-security/multiverse Translation-es       
Des:19 http://archive.ubuntu.com trusty-updates/main i386 Packages [214 kB]    
Des:20 http://packages.linuxmint.com qiana/import i386 Packages [31,6 kB]      
Ign http://security.ubuntu.com trusty-security/restricted Translation-es_ES    
Ign http://security.ubuntu.com trusty-security/restricted Translation-es       
Ign http://security.ubuntu.com trusty-security/universe Translation-es_ES      
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-es_ES             
Ign http://security.ubuntu.com trusty-security/universe Translation-es         
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-es                
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en                
Des:21 http://archive.ubuntu.com trusty-updates/restricted i386 Packages [14 B]
Des:22 http://archive.ubuntu.com trusty-updates/universe i386 Packages [155 kB]
Ign http://extra.linuxmint.com qiana/main Translation-es_ES                    
Des:23 http://archive.ubuntu.com trusty-updates/multiverse i386 Packages [7.587 B]
Ign http://extra.linuxmint.com qiana/main Translation-es                       
Ign http://extra.linuxmint.com qiana/main Translation-en                       
Obj http://archive.ubuntu.com trusty-updates/main Translation-en
Obj http://archive.ubuntu.com trusty-updates/multiverse Translation-en
Obj http://archive.ubuntu.com trusty-updates/restricted Translation-en
Obj http://archive.ubuntu.com trusty-updates/universe Translation-en
Ign http://archive.ubuntu.com trusty/main Translation-es_ES                    
Ign http://archive.ubuntu.com trusty/multiverse Translation-es_ES              
Ign http://archive.ubuntu.com trusty/restricted Translation-es_ES              
Ign http://archive.ubuntu.com trusty/universe Translation-es_ES                
Ign http://archive.ubuntu.com trusty-updates/main Translation-es_ES            
Ign http://archive.ubuntu.com trusty-updates/main Translation-es               
Ign http://archive.ubuntu.com trusty-updates/multiverse Translation-es_ES      
Ign http://archive.ubuntu.com trusty-updates/multiverse Translation-es         
Ign http://archive.ubuntu.com trusty-updates/restricted Translation-es_ES      
Ign http://archive.ubuntu.com trusty-updates/restricted Translation-es         
Ign http://archive.ubuntu.com trusty-updates/universe Translation-es_ES        
Ign http://archive.ubuntu.com trusty-updates/universe Translation-es           
Ign http://packages.linuxmint.com qiana/import Translation-es_ES               
Ign http://packages.linuxmint.com qiana/import Translation-es                  
Ign http://packages.linuxmint.com qiana/import Translation-en                  
Ign http://packages.linuxmint.com qiana/main Translation-es_ES                 
Ign http://packages.linuxmint.com qiana/main Translation-es
Ign http://packages.linuxmint.com qiana/main Translation-en
Ign http://packages.linuxmint.com qiana/upstream Translation-es_ES
Ign http://packages.linuxmint.com qiana/upstream Translation-es
Ign http://packages.linuxmint.com qiana/upstream Translation-en
Descargados 1.025 kB en 14seg. (70,8 kB/s)
W: Imposible obtener file:/var/cache/apt-build/repository/dists/apt-build/main/binary-i386/Packages  Fichero no encontrado

W: Imposible obtener http://ppa.launchpad.net/cherokee-webserver/ppa/ubuntu/dists/trusty/main/source/Sources  404  Not Found

W: Imposible obtener http://ppa.launchpad.net/cherokee-webserver/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

W: Imposible obtener http://ppa.launchpad.net/cherokee-webserver/ppa/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

E: Algunos archivos de índice fallaron al descargar. Se han ignorado, o se han utilizado unos antiguos en su lugar
```

Maybe someone installed Cherokee succesfully on ubuntu 14.04 ? Any help is welcome.. thanks!!

---

### Post by uri3 on 2014-08-07
apt-get doesn't work because no one has added a version in the repository for 14.04 ("trusty").

Unfortunately I'm currently having difficulties compiling it manually, too.... autogen.sh seems to fail.

Have you managed to install cherokee on 14.04 by now?

---

### Post by Miguel_Muiz on 2014-08-11
> **uri3 said:**
> apt-get doesn't work because no one has added a version in the repository for 14.04 ("trusty").

Unfortunately I'm currently having difficulties compiling it manually, too.... autogen.sh seems to fail.

Have you managed to install cherokee on 14.04 by now?

I just used "saucy" package meanwhile like this:

add-apt-repository ppa:cherokee-webserver

cd /etc/apt/sources.list.d

vi cherokee-webserver-ppa-trusty.list

replace:

deb [http://ppa.launchpad.net/cherokee-webserver/ppa/ubuntu](http://ppa.launchpad.net/cherokee-webserver/ppa/ubuntu) trusty main

to:

deb [http://ppa.launchpad.net/cherokee-webserver/ppa/ubuntu](http://ppa.launchpad.net/cherokee-webserver/ppa/ubuntu) saucy main

apt-get update

aptitude install cherokee

---

### Post by azuer88 on 2014-09-11
> **uri3 said:**
> apt-get doesn't work because no one has added a version in the repository for 14.04 ("trusty").

Unfortunately I'm currently having difficulties compiling it manually, too.... autogen.sh seems to fail.

Have you managed to install cherokee on 14.04 by now?

i was able to compile cherokee from [https://github.com/cherokee/webserver](https://github.com/cherokee/webserver)

---

