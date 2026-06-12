---
title: "How do i correct this error?"
date: 2007-08-25
forum: General Help
---

### Post by empty89 on 2007-08-25
```
Get:1 http://sg.archive.ubuntu.com feisty Release.gpg [191B]                   
Ign http://sg.archive.ubuntu.com feisty/main Translation-en_SG                 
Ign http://sg.archive.ubuntu.com feisty/restricted Translation-en_SG           
Ign http://sg.archive.ubuntu.com feisty/universe Translation-en_SG             
Ign http://sg.archive.ubuntu.com feisty/multiverse Translation-en_SG           
Get:2 http://sg.archive.ubuntu.com feisty-updates Release.gpg [191B]           
Ign http://sg.archive.ubuntu.com feisty-updates/main Translation-en_SG         
Ign http://sg.archive.ubuntu.com feisty-updates/restricted Translation-en_SG   
Hit http://sg.archive.ubuntu.com feisty Release                                
Hit http://sg.archive.ubuntu.com feisty-updates Release                        
Hit http://sg.archive.ubuntu.com feisty/main Packages                          
Get:3 http://download.tuxfamily.org feisty Release.gpg [189B]                  
Hit http://sg.archive.ubuntu.com feisty/restricted Packages                    
Hit http://sg.archive.ubuntu.com feisty/main Sources                 
Hit http://sg.archive.ubuntu.com feisty/restricted Sources                     
Hit http://sg.archive.ubuntu.com feisty/universe Packages                      
Hit http://sg.archive.ubuntu.com feisty/universe Sources                       
Hit http://sg.archive.ubuntu.com feisty/multiverse Packages                    
Hit http://sg.archive.ubuntu.com feisty/multiverse Sources                     
Hit http://sg.archive.ubuntu.com feisty-updates/main Packages                  
Hit http://sg.archive.ubuntu.com feisty-updates/restricted Packages            
Hit http://sg.archive.ubuntu.com feisty-updates/main Sources         
Hit http://sg.archive.ubuntu.com feisty-updates/restricted Sources   
Get:4 http://security.ubuntu.com feisty-security Release.gpg [191B]            
Ign http://security.ubuntu.com feisty-security/main Translation-en_SG          
Ign http://download.tuxfamily.org feisty/eyecandy Translation-en_SG            
Hit http://download.tuxfamily.org feisty Release                               
Err http://download.tuxfamily.org feisty Release                               
  
Get:5 http://download.tuxfamily.org feisty Release [14.2kB]                    
Ign http://download.tuxfamily.org feisty Release                               
Hit http://download.tuxfamily.org feisty/eyecandy Packages                     
Hit http://download.tuxfamily.org feisty/eyecandy Sources                      
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_SG    
Ign http://security.ubuntu.com feisty-security/universe Translation-en_SG      
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_SG    
Hit http://security.ubuntu.com feisty-security Release                         
Hit http://security.ubuntu.com feisty-security/main Packages                   
Hit http://security.ubuntu.com feisty-security/restricted Packages             
Hit http://security.ubuntu.com feisty-security/main Sources                    
Hit http://security.ubuntu.com feisty-security/restricted Sources              
Hit http://security.ubuntu.com feisty-security/universe Packages               
Hit http://security.ubuntu.com feisty-security/universe Sources                
Hit http://security.ubuntu.com feisty-security/multiverse Packages             
Hit http://security.ubuntu.com feisty-security/multiverse Sources              
Fetched 14.9kB in 18s (826B/s)                                                 
Reading package lists... Done
[B]W: GPG error: http://download.tuxfamily.org feisty Release: The following signatures were invalid: BADSIG 2D6CFB44DD800CD9 

```
How do i correct the bold part..?

my apt-key list.
```
/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

pub   1024D/81836EBF 2006-06-26
sub   4096g/EDD1E155 2006-06-26
sub   1024D/DD800CD9 2006-10-19

```

---

### Post by bmartin on 2007-08-27
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 2D6CFB44DD800CD9
gpg --fingerprint DD800CD9
gpg --armor --export DD800CD9 | sudo apt-key add -

That should do the trick.

---

