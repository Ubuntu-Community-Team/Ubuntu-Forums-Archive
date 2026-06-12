---
title: "[SOLVED] Virus scan for windows files in Ubuntu"
date: 2008-02-18
forum: General Help
---

### Post by geo909 on 2008-02-18
Hello everybody,

does anyone knows a good anti-virus or/and anti-spyware program in Ubuntu that is able to scan for viruses in .exe files etc? It would also be great if I could scan my XP partition with it!

    Thanks in advance!

---

### Post by honeydew on 2008-02-18
Clamav should do the trick 

[http://www.clamav.net/](http://www.clamav.net/)

clamav is in the repositories

```
austin@underling:~$ aptitude search clamav
p   clamav                                         - anti-virus utility for Unix - command-line interface    
c   clamav-base                                    - anti-virus utility for Unix - base package              
p   clamav-daemon                                  - anti-virus utility for Unix - scanner daemon            
p   clamav-data                                    - clamav data files                                       
p   clamav-dbg                                     - debug symbols for ClamAV                                
p   clamav-docs                                    - anti-virus utility for Unix - documentation             
c   clamav-freshclam                               - anti-virus utility for Unix - virus database update util
p   clamav-getfiles                                - Update script for clamav                                
p   clamav-milter                                  - anti-virus utility for Unix - sendmail integration      
p   clamav-testfiles                               - anti-virus utility for Unix - test files                
p   claws-mail-clamav                              - Clam AntiVirus plugin for Claws Mail                    
p   libclamav-client-perl                          - A client for the ClamAV virus scanner daemon            
p   libclamav-dev                                  - anti-virus utility for Unix - development files         
c   libclamav3                                     - anti-virus utility for Unix - library                   
p   php5-clamavlib                                 - PHP ClamAV Lib - ClamAV Interface for PHP5 Scripts      
p   python-clamav                                  - Python bindings to ClamAV                               
v   python2.4-clamav                               -                                                         
v   python2.5-clamav                               -                                                         
p   sylpheed-claws-gtk2-clamav                     - Transition package for Claws Mail renaming           

```

sorry though I dont have much experience setting it up.  Though I know we use it to scan files before they hit our windows users.

---

### Post by sb12 on 2008-02-18
> **geo909 said:**
> Hello everybody,

does anyone knows a good anti-virus or/and anti-spyware program in Ubuntu that is able to scan for viruses in .exe files etc? It would also be great if I could scan my XP partition with it!

    Thanks in advance!

clamav maybe

---

### Post by frankos44 on 2008-02-18
Try this 

[http://www.grisoft.com/doc/31/us/crp/0?prd=avl](http://www.grisoft.com/doc/31/us/crp/0?prd=avl)

---

### Post by geo909 on 2008-02-20
Thanks everybody! I'll have a look at them!

---

### Post by frankos44 on 2008-02-21
If you decide to use AVG you will need to add yourself the AVG group in order to perform updates.

System->Administration->Users and Groups

Click manage groups and locate AVG

Add yourself to that group.

Not sure if you need to  re-login, I cant remember.

---

### Post by geo909 on 2008-02-21
Thanks for the advice! Yes, I think I'm going to check AVG, too

---

