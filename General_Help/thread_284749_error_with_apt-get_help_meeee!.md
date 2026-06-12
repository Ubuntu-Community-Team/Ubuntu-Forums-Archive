---
title: "error with apt-get help meeee!"
date: 2006-10-26
forum: General Help
---

### Post by Nevermore on 2006-10-26
Hello
i keep getting errors using apt-get update..i dunno how to fix it, please someone help me!

agostino@agostino-laptop:~$ sudo apt-get update
Password:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [189B]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-it               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-it         
Get:2 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]        
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Translation-it         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-it         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-it           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-it           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release                     
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg                                 
  Impossibile risolvere 'archive.ubuntu.com'
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                     
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                 
Err [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg                               
  Impossibile risolvere 'www.getautomatix.com'
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                 
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-it                       
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                   
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages             
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-it [62,7kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-it [14B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-it [559B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-it [46,1kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-it [46,1kB]
75% [6 Translation-it bzip2 0] [7 Translation-it 1404/46,1kB 3%]
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-it      
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-it [62,7kB]              
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-it [14B]           
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-it [46,1kB]         
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-it [559B]         
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [189B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-it                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-it           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-it           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-it             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-it                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-it           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-it             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-it           
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [189B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-it               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-it         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-it           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-it         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-it         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-it               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-it         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-it           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-it               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-it         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-it           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-it         
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release.gpg [189B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Translation-it          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Translation-it                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Translation-it          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Translation-it            
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [189B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-it                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-it          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-it            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-it          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                                     
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release [19,6kB]                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release                            
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages [940kB]                    
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages [5974B]              
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages [126kB]              
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages [3559kB]               
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages [3559kB]               
57% [20 Packages bzip2 0] [21 Packages 991/3559kB 0%]            36,0kB/s 1m40s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages                           
  Il sottoprocesso bzip2 ha ritornato un codice d'errore (2)
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages [940kB]                    
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages [5974B]              
99% [22 Packages bzip2 0] [23 Packages 894/5974B 14%]               36,0kB/s 1sbzip2: (stdin) is not a bzip2 file.
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages                               
  Il sottoprocesso bzip2 ha ritornato un codice d'errore (2)
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages [3559kB]               
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages [126kB]              
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages [14B]              
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages [14B]        
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages [14B]        
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages [14B]          
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages [14B]              
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages [14B]        
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages [14B]          
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages [14B]        
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages [14B]            
99% [30 Packages bzip2 0] [In attesa degli header]                  31,9kB/s 1s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages                       
  Impossibile aprire il file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_edgy-updates_main_binary-i386_Packages - open (2 Nessun file o directory)
99% [31 Packages bzip2 0] [In attesa degli header]                  31,9kB/s 1s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages                 
  Impossibile aprire il file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_edgy-updates_restricted_binary-i386_Packages - open (2 Nessun file o directory)
99% [32 Packages bzip2 0] [In attesa degli header]                  31,9kB/s 1s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages                   
  Impossibile aprire il file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_edgy-updates_universe_binary-i386_Packages - open (2 Nessun file o directory)
99% [33 Packages bzip2 0] [In attesa degli header]                  31,9kB/s 1s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages                 
  Impossibile aprire il file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_edgy-updates_multiverse_binary-i386_Packages - open (2 Nessun file o directory)
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages [14B]      
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages [14B]        
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages [14B]      
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages [14B]      
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages [14B]            
Get:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages [14B]      
Get:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages [14B]        
Get:42 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages [14B]            
Get:43 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages [14B]      
Get:44 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages [14B]        
99% [42 Packages bzip2 0] [In attesa degli header]                  31,9kB/s 1sbzip2: (stdin) is not a bzip2 file.
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages                     
  Il sottoprocesso bzip2 ha ritornato un codice d'errore (2)
99% [44 Packages bzip2 0] [In attesa degli header]                  31,9kB/s 1s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages                 
  Impossibile aprire il file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_edgy-backports_universe_binary-i386_Packages - open (2 Nessun file o directory)
Get:45 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages [14B]      
Get:46 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Packages [14B]       
Get:47 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Packages [14B]             
Get:48 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Packages [14B]       
Get:49 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Packages [14B]         
Get:50 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages [14B]             
Get:51 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages [14B]       
Get:52 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages [14B]         
Get:53 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages [14B]       
Scaricato 12,4MB in 5m46s (35,7kB/s)                                           
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg)  Impossibile risolvere 'archive.ubuntu.com'
Impossibile ottenere [http://www.getautomatix.com/apt/dists/edgy/Release.gpg](http://www.getautomatix.com/apt/dists/edgy/Release.gpg)  Impossibile risolvere 'www.getautomatix.com'
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.bz2)  Il sottoprocesso bzip2 ha ritornato un codice d'errore (2)
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.bz2)  Il sottoprocesso bzip2 ha ritornato un codice d'errore (2)
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.bz2)  Impossibile aprire il file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_edgy-updates_main_binary-i386_Packages - open (2 Nessun file o directory)
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.bz2)  Impossibile aprire il file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_edgy-updates_restricted_binary-i386_Packages - open (2 Nessun file o directory)
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.bz2)  Impossibile aprire il file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_edgy-updates_universe_binary-i386_Packages - open (2 Nessun file o directory)
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.bz2)  Impossibile aprire il file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_edgy-updates_multiverse_binary-i386_Packages - open (2 Nessun file o directory)
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.bz2)  Il sottoprocesso bzip2 ha ritornato un codice d'errore (2)
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.bz2)  Impossibile aprire il file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_edgy-backports_universe_binary-i386_Packages - open (2 Nessun file o directory)
Lettura della lista dei pacchetti in corso... Fatto
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-it (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_universe_i18n_Translation-it)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-it (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_main_i18n_Translation-it)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-it (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_restricted_i18n_Translation-it)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-it (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_universe_i18n_Translation-it)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-it (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_multiverse_i18n_Translation-it)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-updates_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-updates_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-updates_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-backports_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-backports_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-backports_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-backports_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-backports_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-backports_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-backports_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-backports_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-i386_Packages)
W: Ãˆ consigliabile eseguire apt-get update per correggere questi problemi
E: Impossibile scaricare alcune file di indice, essi verranno ignorati, oppure si useranno quelli precedenti.

---

