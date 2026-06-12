---
title: "Root apps don't work..."
date: 2007-09-21
forum: General Help
---

### Post by BinaryBrother on 2007-09-21
Various programs have simply quit working, and I have tied it in relation to root privileges... Nothing in my 'administrative' menu panel works, it loads part of the GUI an appears locked up, I can't edit individual files as root either, when individual files are attempted to be edited, it appears as if everything is working, asks for a password, etc... but then just hangs, and nothing ever happens... Please help... I've asked a wireless question like 2 days ago, and haven't had one reply... Hopefully someone will help on this issue... :(

---

### Post by BinaryBrother on 2007-09-24
Come on guys... I ask a wireless question, 2 days later I've finally figured it out by myself... Where is the support here? Ubuntu FF is my primary OS with NO alternative... I made this jump when my Windows died, I need some help... PLEASE.

---

### Post by BinaryBrother on 2007-09-24
(gedit:8598): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

a simple "gksudo gedit" produced the above error... Or better yet, 'warning'... :P

[EDIT] Is it possible my password (28 characters) is too long? [/EDIT]

---

### Post by bapoumba on 2007-09-24
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/gksu/+bug/23917](https://launchpad.net/ubuntu/+source/gksu/+bug/23917) [br].[/br] ---------------------------- [br].[/br] [br].[/br]

The warning is a known bug.
What does **groups** return?

---

### Post by BinaryBrother on 2007-09-24
'GROUPS' read-out

"binarybrother adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin"

Thanks so much for helping!:)

---

### Post by BinaryBrother on 2007-09-26
Well... Thanks for starting to help... :(

---

### Post by bapoumba on 2007-09-26
Your groups are fine, the warning you reported is documented, so I'm not sure where the problem is.
Could you please post the complete output to:
```
gksudo -S -d gedit
sudo aptitude update
```

---

### Post by BinaryBrother on 2007-09-27
The first command retrieved... The below, and opened a text editor, which locked up after a second or so... The second command output is further down...

binarybrother@binarybrother:~$ gksudo -S -d gedit
No ask_pass set, using default!
xauth: /tmp/libgksu-cQDEAb/.Xauthority
STARTUP_ID: gksudo/gedit/6485-0-binarybrother_TIME972738
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: gedit
buffer: --
buffer: -(gedit:6486): GnomeUI-WARNING **: While connecting to session manager:-
buffer: -Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.-
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
brute force GNOME_SUDO_PASS ended...
No password prompt found; we'll assume we don't need a password.
(Terminal then failed to respond to any further commands)




binarybrother@binarybrother:~$ sudo aptitude update
Password:
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release                              
Get:2 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]     
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US   
Get:3 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release.gpg [191B]             
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US       
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US   
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                  
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US 
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Translation-en_US  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                      
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages                        
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US   
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US  
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                     
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages            
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Packages
Fetched 200B in 1s (112B/s)
Reading package lists... Done
binarybrother@binarybrother:~$

---

### Post by BinaryBrother on 2007-09-27
I figured I would try and keep on the initial topic, in fear you might quit helping if I stray too much.. :P

---

### Post by BinaryBrother on 2007-10-07
Still NO ideas?? :P

Where is the 'ksudo' package?

---

### Post by bapoumba on 2007-10-07
Sorry, I sort of forgot about the thread...

For KDE, its kdesu, for ex **kdesu kate** to open a text editor with admin privileges.

Your terminal mesages are fine, as far as I can see. Not sure where your problem is lying.

---

