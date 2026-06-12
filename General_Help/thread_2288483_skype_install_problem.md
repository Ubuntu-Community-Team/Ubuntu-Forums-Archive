---
title: "skype install problem"
date: 2015-07-27
forum: General Help
---

### Post by andfree on 2015-07-27
Skype install problem on ubuntu 12.04.5

"libxss1 not satisfiable" error

---

### Post by QDR06VV9 on 2015-07-27
Hi andfree
See if this gets you sorted out [http://www.ubuntu4u.com/howtos/how-install-skype-ubuntu-1204-lts](http://www.ubuntu4u.com/howtos/how-install-skype-ubuntu-1204-lts)
Be sure to follow the right Arch ie [COLOR=#000000][FONT=Source Sans Pro]32bit: or [/FONT][/COLOR][COLOR=#000000][FONT=Source Sans Pro]64bit:[/FONT][/COLOR]
Regards

---

### Post by andfree on 2015-07-28
```
Package libxss1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libxss1' has no installation candidate
```

---

### Post by mastablasta on 2015-07-28
how are you installing it? enable "partners" repositories in software center, find skype and click install. see if that Works.

---

### Post by andfree on 2015-07-28
I enabled all repositories but I don't find skype in software center.

---

### Post by sudodus on 2015-07-28
Have you enabled the "Canonical Partners" repositories (as suggested by mastablasta)?

skype works for me in Ubuntu 12.04 LTS. I have still the old precise kernel (series 3.2.0-xx). I don't know if there would be problems with the trusty kernel (series 3.13-...), that you get, if you install 12.04.5 LTS from the iso file.

```
sudodus $ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.5 LTS
Release:	12.04
Codename:	precise
sudodus@ssd-grund ~ $ uname -a
Linux ssd-grund 3.2.0-88-generic-pae #126-Ubuntu SMP Mon Jul 6 21:47:47 UTC 2015 i686 i686 i386 GNU/Linux
sudodus@ssd-grund ~ $ sudo apt-cache policy [COLOR="#0000FF"]skype[/COLOR]
skype:
  Installed: 4.3.0.37-0ubuntu0.12.04.1
  Candidate: 4.3.0.37-0ubuntu0.12.04.1
  Version table:
 *** 4.3.0.37-0ubuntu0.12.04.1 0
        500 http://archive.canonical.com/ubuntu/ precise/partner i386 Packages
        100 /var/lib/dpkg/status
sudodus@ssd-grund ~ $ sudo apt-cache policy [COLOR="#0000FF"]libxss1[/COLOR]
libxss1:
  Installed: 1:1.2.1-2
  Candidate: 1:1.2.1-2
  Version table:
 *** 1:1.2.1-2 0
        500 http://se.archive.ubuntu.com/ubuntu/ precise/main i386 Packages
        100 /var/lib/dpkg/status
sudodus@ssd-grund ~ $ 
```

---

### Post by andfree on 2015-07-28
I enabled it and now I see there is skype client in software center. But it gets the error message:

```
Package dependencies cannot be resolved

This error could be caused by required additional software packages  which are missing or not installable. Furthermore there could be a  conflict between software packages which are not allowed to be installed  at the same time.
```

And in the details box:

```
The following packages have unmet dependencies: skype
```

---

### Post by andfree on 2015-07-28
Some more terminal display (unfortunally some in greek. I translate whatever I can in progress):

```
~$ sudo apt-get update
Hit http://gr.archive.ubuntu.com precise Release.gpg
Hit http://gr.archive.ubuntu.com precise-updates Release.gpg
Hit http://gr.archive.ubuntu.com precise-backports Release.gpg                                                                       
Hit http://gr.archive.ubuntu.com precise Release                                                                                     
Hit http://gr.archive.ubuntu.com precise-updates Release                                                                             
Hit http://gr.archive.ubuntu.com precise-backports Release                                                                           
&#934;&#941;&#961;&#949;:1 http://extras.ubuntu.com precise Release.gpg [72 B]                                                                           
Hit http://archive.canonical.com precise Release.gpg                                                                                 
Hit http://archive.canonical.com precise Release.gpg                                                                                 
Hit http://extras.ubuntu.com precise Release                                                                                         
Hit http://archive.canonical.com precise Release                                                                                     
Error http://extras.ubuntu.com precise Release                                                                                      
  
&#934;&#941;&#961;&#949;:2 http://gr.archive.ubuntu.com precise/main Sources [934 kB]                                                                    
&#934;&#941;&#961;&#949;:3 http://gr.archive.ubuntu.com precise/restricted Sources [5470 B]                                                              
Hit http://archive.canonical.com precise Release                                                                                     
&#934;&#941;&#961;&#949;:4 http://security.ubuntu.com precise-security Release.gpg [198 B]                                                               
Hit http://archive.canonical.com precise/partner Sources                                                                             
Hit http://archive.canonical.com precise/partner i386 Packages                                                                       
Hit http://archive.canonical.com precise/partner TranslationIndex                                                                    
&#934;&#941;&#961;&#949;:5 http://security.ubuntu.com precise-security Release [54,3 kB]                                                                 
Hit http://archive.canonical.com precise/partner Sources                                                                             
Hit http://archive.canonical.com precise/partner i386 Packages                                                                       
Hit http://archive.canonical.com precise/partner TranslationIndex                                                                    
Hit http://archive.canonical.com precise/partner Translation-en                                                                      
Hit http://archive.canonical.com precise/partner Translation-en                                                                      
&#934;&#941;&#961;&#949;:6 http://gr.archive.ubuntu.com precise/universe Sources [5019 kB]                                                               
&#934;&#941;&#961;&#949;:7 http://gr.archive.ubuntu.com precise/multiverse Sources [155 kB]                            
&#934;&#941;&#961;&#949;:8 http://gr.archive.ubuntu.com precise/main i386 Packages [1274 kB]                     
&#934;&#941;&#961;&#949;:9 http://gr.archive.ubuntu.com precise/restricted i386 Packages [8431 B]                         
&#934;&#941;&#961;&#949;:10 http://security.ubuntu.com precise-security/main Sources [131 kB]                           
&#934;&#941;&#961;&#949;:11 http://gr.archive.ubuntu.com precise/universe i386 Packages [4796 kB]                      
&#934;&#941;&#961;&#949;:12 http://gr.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]                         
Hit http://gr.archive.ubuntu.com precise/main TranslationIndex                                       
Hit http://gr.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://gr.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://gr.archive.ubuntu.com precise/universe TranslationIndex  
Hit http://gr.archive.ubuntu.com precise-updates/main Sources       
Hit http://gr.archive.ubuntu.com precise-updates/restricted Sources                   
Hit http://gr.archive.ubuntu.com precise-updates/universe Sources                     
Hit http://gr.archive.ubuntu.com precise-updates/multiverse Sources                   
Hit http://gr.archive.ubuntu.com precise-updates/main i386 Packages                                                             
Hit http://gr.archive.ubuntu.com precise-updates/restricted i386 Packages                                                       
Hit http://gr.archive.ubuntu.com precise-updates/universe i386 Packages                                                         
Hit http://gr.archive.ubuntu.com precise-updates/multiverse i386 Packages                                                       
Hit http://gr.archive.ubuntu.com precise-updates/main TranslationIndex                                                          
Hit http://gr.archive.ubuntu.com precise-updates/multiverse TranslationIndex                                                    
Hit http://gr.archive.ubuntu.com precise-updates/restricted TranslationIndex                                                    
Hit http://gr.archive.ubuntu.com precise-updates/universe TranslationIndex                                                      
Hit http://gr.archive.ubuntu.com precise-backports/main Sources                       
Hit http://gr.archive.ubuntu.com precise-backports/restricted Sources                                                           
Hit http://gr.archive.ubuntu.com precise-backports/universe Sources                                                             
Hit http://gr.archive.ubuntu.com precise-backports/multiverse Sources                                                           
Hit http://gr.archive.ubuntu.com precise-backports/main i386 Packages                                                           
Hit http://gr.archive.ubuntu.com precise-backports/restricted i386 Packages                                                     
Hit http://gr.archive.ubuntu.com precise-backports/universe i386 Packages                                                       
Hit http://gr.archive.ubuntu.com precise-backports/multiverse i386 Packages                                                     
Hit http://gr.archive.ubuntu.com precise-backports/main TranslationIndex                                                        
Hit http://gr.archive.ubuntu.com precise-backports/multiverse TranslationIndex                                                  
Hit http://gr.archive.ubuntu.com precise-backports/restricted TranslationIndex                                                  
&#934;&#941;&#961;&#949;:13 http://security.ubuntu.com precise-security/restricted Sources [3759 B]                                                 
&#934;&#941;&#961;&#949;:14 http://security.ubuntu.com precise-security/universe Sources [43,8 kB]                                                  
&#934;&#941;&#961;&#949;:15 http://security.ubuntu.com precise-security/multiverse Sources [2199 B]                                                 
&#934;&#941;&#961;&#949;:16 http://security.ubuntu.com precise-security/main i386 Packages [581 kB]                                                 
Hit http://gr.archive.ubuntu.com precise-backports/universe TranslationIndex                                                    
Hit http://gr.archive.ubuntu.com precise/main Translation-el                                                        
Hit http://gr.archive.ubuntu.com precise/main Translation-en                                                         
Hit http://gr.archive.ubuntu.com precise/multiverse Translation-el                                                   
Hit http://gr.archive.ubuntu.com precise/multiverse Translation-en                                                   
Hit http://gr.archive.ubuntu.com precise/restricted Translation-el                                                   
Hit http://gr.archive.ubuntu.com precise/restricted Translation-en                                                   
Hit http://gr.archive.ubuntu.com precise/universe Translation-el                                                     
Hit http://gr.archive.ubuntu.com precise/universe Translation-en                                                     
Hit http://gr.archive.ubuntu.com precise-updates/main Translation-el                                                 
Hit http://gr.archive.ubuntu.com precise-updates/main Translation-en                                                 
Hit http://gr.archive.ubuntu.com precise-updates/multiverse Translation-el                                           
Hit http://gr.archive.ubuntu.com precise-updates/multiverse Translation-en                                           
Hit http://gr.archive.ubuntu.com precise-updates/restricted Translation-el                                           
Hit http://gr.archive.ubuntu.com precise-updates/restricted Translation-en 
Hit http://gr.archive.ubuntu.com precise-updates/universe Translation-el                                             
Hit http://gr.archive.ubuntu.com precise-updates/universe Translation-en                                             
Hit http://gr.archive.ubuntu.com precise-backports/main Translation-en                                               
Hit http://gr.archive.ubuntu.com precise-backports/multiverse Translation-en                                         
Hit http://gr.archive.ubuntu.com precise-backports/restricted Translation-en                                         
Hit http://gr.archive.ubuntu.com precise-backports/universe Translation-en                                           
&#934;&#941;&#961;&#949;:17 http://security.ubuntu.com precise-security/restricted i386 Packages [8939 B]                                
&#934;&#941;&#961;&#949;:18 http://security.ubuntu.com precise-security/universe i386 Packages [131 kB]
&#934;&#941;&#961;&#949;:19 http://security.ubuntu.com precise-security/multiverse i386 Packages [2864 B]  
&#934;&#941;&#961;&#949;:20 http://security.ubuntu.com precise-security/main TranslationIndex [208 B]      
&#934;&#941;&#961;&#949;:21 http://security.ubuntu.com precise-security/multiverse TranslationIndex [199 B]
&#934;&#941;&#961;&#949;:22 http://security.ubuntu.com precise-security/restricted TranslationIndex [202 B]
&#934;&#941;&#961;&#949;:23 http://security.ubuntu.com precise-security/universe TranslationIndex [205 B]  
Hit http://security.ubuntu.com precise-security/main Translation-en                    
Hit http://security.ubuntu.com precise-security/multiverse Translation-en              
Hit http://security.ubuntu.com precise-security/restricted Translation-en              
Hit http://security.ubuntu.com precise-security/universe Translation-en                      
&#924;&#949;&#964;&#945;&#966;&#959;&#961;&#964;&#974;&#952;&#951;&#954;&#945;&#957; 960 kB &#963;&#949; 10s (93,2 kB/s)                                                                                             
&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#923;&#953;&#963;&#964;&#974;&#957; &#928;&#945;&#954;&#941;&#964;&#969;&#957;... &#927;&#955;&#959;&#954;&#955;&#951;&#961;&#974;&#952;&#951;&#954;&#949;
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com precise Release: *The following signatures were invalid*: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources   *MD5Sum* mismatch

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources   *MD5Sum* mismatch

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources   *MD5Sum* mismatch

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources   *MD5Sum* mismatch

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages   *MD5Sum* mismatch

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages   *MD5Sum* mismatch

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages   *MD5Sum* mismatch

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages   *MD5Sum* mismatch
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release   

W: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by Bucky Ball on 2015-07-28
Completely remove whatever you used when trying to install Skype before. Probably via a PPA. Kill the PPA and then:

```
sudo apt-get remove --purge skype
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Reboot and then try to install from Software Centre. Also, this is of some concern:

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources   MD5Sum mismatch

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources   MD5Sum mismatch

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources   MD5Sum mismatch

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources   MD5Sum mismatch

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages   MD5Sum mismatch

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages   MD5Sum mismatch

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages   MD5Sum mismatch

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages   MD5Sum mismatch
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release   

W: Some index files failed to download. They have been ignored, or old ones used instead.
```

Looks like you might have an issue with the extras PPA. Disable for the moment. You are probably going to have problems until you can run the update/upgrade commands I gave without error.

---

### Post by andfree on 2015-07-28
After disabling extras PPA:

```
~$ sudo apt-get remove --purge skype
&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#923;&#953;&#963;&#964;&#974;&#957; &#928;&#945;&#954;&#941;&#964;&#969;&#957;... &#927;&#955;&#959;&#954;&#955;&#951;&#961;&#974;&#952;&#951;&#954;&#949;
&#922;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#942; &#916;&#941;&#957;&#948;&#961;&#959;&#965; &#917;&#958;&#945;&#961;&#964;&#942;&#963;&#949;&#969;&#957;                  
&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#960;&#949;&#961;&#953;&#947;&#961;&#945;&#966;&#942;&#962; &#964;&#951;&#962; &#964;&#961;&#941;&#967;&#959;&#965;&#963;&#945;&#962; &#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951;... &#927;&#955;&#959;&#954;&#955;&#951;&#961;&#974;&#952;&#951;&#954;&#949;
&#932;&#945; &#945;&#954;&#972;&#955;&#959;&#965;&#952;&#945; &#960;&#945;&#954;&#941;&#964;&#945; &#952;&#945; &#913;&#934;&#913;&#921;&#929;&#917;&#920;&#927;&#933;&#925;:
  skype*
0 &#945;&#957;&#945;&#946;&#945;&#952;&#956;&#943;&#963;&#964;&#951;&#954;&#945;&#957;, 0 &#957;&#941;&#959; &#949;&#947;&#954;&#945;&#964;&#949;&#963;&#964;&#951;&#956;&#941;&#957;&#945;, 1 &#952;&#945; &#945;&#966;&#945;&#953;&#961;&#949;&#952;&#959;&#973;&#957; &#954;&#945;&#953; 0 &#948;&#949;&#957; &#945;&#957;&#945;&#946;&#945;&#952;&#956;&#943;&#950;&#959;&#957;&#964;&#945;&#953;.
&#924;&#949;&#964;&#940; &#945;&#960;&#972; &#945;&#965;&#964;&#942; &#964;&#951; &#955;&#949;&#953;&#964;&#959;&#965;&#961;&#947;&#943;&#945;, &#952;&#945; &#967;&#961;&#951;&#963;&#953;&#956;&#959;&#960;&#959;&#953;&#951;&#952;&#959;&#973;&#957; 0 B &#967;&#974;&#961;&#959;&#965; &#945;&#960;&#972; &#964;&#959; &#948;&#943;&#963;&#954;&#959;.
&#920;&#941;&#955;&#949;&#964;&#949; &#957;&#945; &#963;&#965;&#957;&#949;&#967;&#943;&#963;&#949;&#964;&#949; [&#925;/&#959;]; &#925;
(&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#946;&#940;&#963;&#951;&#962; &#948;&#949;&#948;&#959;&#956;&#941;&#957;&#969;&#957; ... 177245 files and directories currently installed.)
&#913;&#966;&#945;&#943;&#961;&#949;&#963;&#951; &#964;&#959;&#965; skype ...
&#916;&#953;&#945;&#947;&#961;&#945;&#966;&#942; &#964;&#969;&#957; &#945;&#961;&#967;&#949;&#943;&#969;&#957; &#961;&#965;&#952;&#956;&#943;&#963;&#949;&#969;&#957; &#964;&#959;&#965; skype ...
~$ sudo apt-get autoremove
&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#923;&#953;&#963;&#964;&#974;&#957; &#928;&#945;&#954;&#941;&#964;&#969;&#957;... &#927;&#955;&#959;&#954;&#955;&#951;&#961;&#974;&#952;&#951;&#954;&#949;
&#922;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#942; &#916;&#941;&#957;&#948;&#961;&#959;&#965; &#917;&#958;&#945;&#961;&#964;&#942;&#963;&#949;&#969;&#957;                  
&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#960;&#949;&#961;&#953;&#947;&#961;&#945;&#966;&#942;&#962; &#964;&#951;&#962; &#964;&#961;&#941;&#967;&#959;&#965;&#963;&#945;&#962; &#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951;... &#927;&#955;&#959;&#954;&#955;&#951;&#961;&#974;&#952;&#951;&#954;&#949;
0 &#945;&#957;&#945;&#946;&#945;&#952;&#956;&#943;&#963;&#964;&#951;&#954;&#945;&#957;, 0 &#957;&#941;&#959; &#949;&#947;&#954;&#945;&#964;&#949;&#963;&#964;&#951;&#956;&#941;&#957;&#945;, 0 &#952;&#945; &#945;&#966;&#945;&#953;&#961;&#949;&#952;&#959;&#973;&#957; &#954;&#945;&#953; 0 &#948;&#949;&#957; &#945;&#957;&#945;&#946;&#945;&#952;&#956;&#943;&#950;&#959;&#957;&#964;&#945;&#953;.
~$ sudo apt-get update
Hit http://archive.canonical.com precise Release.gpg
Hit http://archive.canonical.com precise Release.gpg                           
&#934;&#941;&#961;&#949;:1 http://extras.ubuntu.com precise Release.gpg [72 B]                     
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://archive.canonical.com precise Release                               
Hit http://extras.ubuntu.com precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://archive.canonical.com precise Release                               
&#931;&#966;&#940;&#955;&#956;&#945; http://extras.ubuntu.com precise Release                                
  
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://archive.canonical.com precise/partner i386 Packages                 
Hit http://archive.canonical.com precise/partner TranslationIndex              
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://archive.canonical.com precise/partner i386 Packages                 
Hit http://archive.canonical.com precise/partner TranslationIndex              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Hit http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://archive.canonical.com precise/partner Translation-en                
Hit http://ppa.launchpad.net precise/main Translation-en                       
Hit http://archive.canonical.com precise/partner Translation-en                
Hit http://archive.ubuntu.com precise Release.gpg                              
&#934;&#941;&#961;&#949;:2 http://archive.ubuntu.com precise-updates Release.gpg [198 B]
Hit http://archive.ubuntu.com precise-backports Release.gpg
&#934;&#941;&#961;&#949;:3 http://archive.ubuntu.com precise-security Release.gpg [198 B]
Hit http://archive.ubuntu.com precise Release 
&#934;&#941;&#961;&#949;:4 http://archive.ubuntu.com precise-updates Release [196 kB]    
Hit http://archive.ubuntu.com precise-backports Release              
&#934;&#941;&#961;&#949;:5 http://archive.ubuntu.com precise-security Release [54,3 kB]
Hit http://archive.ubuntu.com precise/main Sources                     
Hit http://archive.ubuntu.com precise/restricted Sources                       
Hit http://archive.ubuntu.com precise/universe Sources                         
Hit http://archive.ubuntu.com precise/multiverse Sources                       
Hit http://archive.ubuntu.com precise/main i386 Packages                       
Hit http://archive.ubuntu.com precise/restricted i386 Packages                 
Hit http://archive.ubuntu.com precise/universe i386 Packages                   
Hit http://archive.ubuntu.com precise/multiverse i386 Packages                 
Hit http://archive.ubuntu.com precise/main TranslationIndex     
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise/restricted TranslationIndex
Hit http://archive.ubuntu.com precise/universe TranslationIndex 
&#934;&#941;&#961;&#949;:6 http://archive.ubuntu.com precise-updates/main Sources [491 kB]
&#934;&#941;&#961;&#949;:7 http://archive.ubuntu.com precise-updates/restricted Sources [7981 B]   
&#934;&#941;&#961;&#949;:8 http://archive.ubuntu.com precise-updates/universe Sources [122 kB]     
&#934;&#941;&#961;&#949;:9 http://archive.ubuntu.com precise-updates/multiverse Sources [9714 B]   
&#934;&#941;&#961;&#949;:10 http://archive.ubuntu.com precise-updates/main i386 Packages [975 kB]  
&#934;&#941;&#961;&#949;:11 http://archive.ubuntu.com precise-updates/restricted i386 Packages [13,6 kB]
&#934;&#941;&#961;&#949;:12 http://archive.ubuntu.com precise-updates/universe i386 Packages [278 kB]
&#934;&#941;&#961;&#949;:13 http://archive.ubuntu.com precise-updates/multiverse i386 Packages [16,7 kB]
Hit http://archive.ubuntu.com precise-updates/main TranslationIndex            
Hit http://archive.ubuntu.com precise-updates/multiverse TranslationIndex      
Hit http://archive.ubuntu.com precise-updates/restricted TranslationIndex      
Hit http://archive.ubuntu.com precise-updates/universe TranslationIndex        
Hit http://archive.ubuntu.com precise-backports/main Sources                   
Hit http://archive.ubuntu.com precise-backports/restricted Sources             
Hit http://archive.ubuntu.com precise-backports/universe Sources               
Hit http://archive.ubuntu.com precise-backports/multiverse Sources             
Hit http://archive.ubuntu.com precise-backports/main i386 Packages    
Hit http://archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://archive.ubuntu.com precise-backports/universe i386 Packages         
Hit http://archive.ubuntu.com precise-backports/multiverse i386 Packages       
Hit http://archive.ubuntu.com precise-backports/main TranslationIndex          
Hit http://archive.ubuntu.com precise-backports/multiverse TranslationIndex    
Hit http://archive.ubuntu.com precise-backports/restricted TranslationIndex    
Hit http://archive.ubuntu.com precise-backports/universe TranslationIndex      
&#934;&#941;&#961;&#949;:14 http://archive.ubuntu.com precise-security/main Sources [131 kB]       
&#934;&#941;&#961;&#949;:15 http://archive.ubuntu.com precise-security/restricted Sources [3759 B] 
&#934;&#941;&#961;&#949;:16 http://archive.ubuntu.com precise-security/universe Sources [43,8 kB]  
&#934;&#941;&#961;&#949;:17 http://archive.ubuntu.com precise-security/multiverse Sources [2199 B] 
&#934;&#941;&#961;&#949;:18 http://archive.ubuntu.com precise-security/main i386 Packages [581 kB] 
&#934;&#941;&#961;&#949;:19 http://archive.ubuntu.com precise-security/restricted i386 Packages [8939 B]
&#934;&#941;&#961;&#949;:20 http://archive.ubuntu.com precise-security/universe i386 Packages [131 kB]
&#934;&#941;&#961;&#949;:21 http://archive.ubuntu.com precise-security/multiverse i386 Packages [2864 B]
Hit http://archive.ubuntu.com precise-security/main TranslationIndex           
Hit http://archive.ubuntu.com precise-security/multiverse TranslationIndex     
Hit http://archive.ubuntu.com precise-security/restricted TranslationIndex     
Hit http://archive.ubuntu.com precise-security/universe TranslationIndex       
Hit http://archive.ubuntu.com precise/main Translation-el                      
Hit http://archive.ubuntu.com precise/main Translation-en                      
Hit http://archive.ubuntu.com precise/multiverse Translation-el                
Hit http://archive.ubuntu.com precise/multiverse Translation-en                
Hit http://archive.ubuntu.com precise/restricted Translation-el       
Hit http://archive.ubuntu.com precise/restricted Translation-en                
Hit http://archive.ubuntu.com precise/universe Translation-el                  
Hit http://archive.ubuntu.com precise/universe Translation-en                  
Hit http://archive.ubuntu.com precise-updates/main Translation-el              
Hit http://archive.ubuntu.com precise-updates/main Translation-en              
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-el
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://archive.ubuntu.com precise-updates/restricted Translation-el
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en        
Hit http://archive.ubuntu.com precise-updates/universe Translation-el          
Hit http://archive.ubuntu.com precise-updates/universe Translation-en          
Hit http://archive.ubuntu.com precise-backports/main Translation-en    
Hit http://archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://archive.ubuntu.com precise-backports/universe Translation-en
Hit http://archive.ubuntu.com precise-security/main Translation-en     
Hit http://archive.ubuntu.com precise-security/multiverse Translation-en
Hit http://archive.ubuntu.com precise-security/restricted Translation-en       
Hit http://archive.ubuntu.com precise-security/universe Translation-en 
&#924;&#949;&#964;&#945;&#966;&#959;&#961;&#964;&#974;&#952;&#951;&#954;&#945;&#957; 3068 kB &#963;&#949; 17s (173 kB/s)                                       
&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#923;&#953;&#963;&#964;&#974;&#957; &#928;&#945;&#954;&#941;&#964;&#969;&#957;... &#927;&#955;&#959;&#954;&#955;&#951;&#961;&#974;&#952;&#951;&#954;&#949;
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com precise Release: *The following signatures were invalid*:BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release   

W: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by Bucky Ball on 2015-07-28
This:

```
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release
```

Seems to be your problem now. Perhaps let's have a look at the sources.list

```
nano /etc/apt/sources.list
```

I know this seems a little off-topic and may not have much to do with your issues, but if there is a conflict trying to grab Skype from two different repos or any other conflict from dysfunctional third-party repos it is not going to help. If the machine can't update/upgrade without throwing an error, there's a basic problem before moving to others. You want the latest updates for your release prior to installing anything. :)

---

### Post by andfree on 2015-07-28
```
# 

# deb cdrom:[Ubuntu 12.04.5 LTS _Precise Pangolin_ - Release i386 (20140807)]/ precise main restricted

# deb cdrom:[Ubuntu 12.04.5 LTS _Precise Pangolin_ - Release i386 (20140807)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu precise main restricted
deb-src http://archive.ubuntu.com/ubuntu precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu precise-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise universe
deb-src http://archive.ubuntu.com/ubuntu precise universe
deb http://archive.ubuntu.com/ubuntu precise-updates universe
deb-src http://archive.ubuntu.com/ubuntu precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu precise multiverse
deb-src http://archive.ubuntu.com/ubuntu precise multiverse
deb http://archive.ubuntu.com/ubuntu precise-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu precise-security main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-security main restricted
deb http://archive.ubuntu.com/ubuntu precise-security universe
deb-src http://archive.ubuntu.com/ubuntu precise-security universe
deb http://archive.ubuntu.com/ubuntu precise-security multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb http://archive.canonical.com/ precise partner
deb-src http://archive.canonical.com/ precise partner
deb-src http://extras.ubuntu.com/ubuntu precise main
```

---

### Post by Bucky Ball on 2015-07-28
```
sudo nano /etc/apt/sources.list
```

Put a # in front of the last four lines at the bottom of that file:

```
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu precise main
# deb http://archive.canonical.com/ precise partner
# deb-src http://archive.canonical.com/ precise partner
# deb-src http://extras.ubuntu.com/ubuntu precise main
```

Control+x to exit, y to save and then the update/upgrade commands I gave previously.

You can see the partners repo is enabled in the second to last section of your output. There may be a problem with that repo on your mirror and it may hopefully be temporary (which is why we comment the lines out and don't delete them for now ;))

---

### Post by andfree on 2015-07-28
[This]("http://ubuntuforums.org/showthread.php?p=11951697#post11951697") solved the update problem and after that skype was installed successfully. Should I try something more or it's better to let it as it is now?

---

### Post by sudodus on 2015-07-28
In the opening post your wrote "Skype install problem on ubuntu 12.04.5".

Are you running standard Ubuntu, some flavour of it or a community re-spin? This could make a difference concerning the content of the file ***/etc/apt/sources.list*** and other configurations.

Edit: Don't change a winning team.

---

### Post by andfree on 2015-07-28
ubuntu-12.04.5-alternate-i386.iso

Answers your question?

---

### Post by sudodus on 2015-07-28
Yes, thanks. But above all ***congratulations***, that the apt-get system works and you can install skype :KS

---

### Post by Bucky Ball on 2015-07-28
Way to go! Good work, enjoy. :)

PS: Nope, don't touch a thing. If it ain't broke, don't fix. :)

PPS: For the benefit of other users, you mean this fixed it for you?

```
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get update
```

---

### Post by andfree on 2015-07-28
> For the benefit of other users, you mean this fixed it for you?

```
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get update
```

Yes, exactly.

Thank you, because you helped me to focus on the right error message with [this post]("http://ubuntuforums.org/showthread.php?t=2288483&page=2&p=13328856#post13328856").

Thanks to all of you.

---

### Post by Bucky Ball on 2015-07-28
All good. Thanks for confirming and enjoy. :)

---

