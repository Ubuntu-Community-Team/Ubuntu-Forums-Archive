---
title: "Blender does not start"
date: 2013-01-31
forum: General Help
---

### Post by Greenality on 2013-01-31
Hi,

i uses Ubuntu 12.04.1 LTS, and have used blender with no problems. But  for four days it does not start anymore, and I just don't know why. I  have to start it with the help of the terminal, but it just shows me  some informations i don't understand. 

```
linux@Linux-PC:~/Dokumente/blender-2.65-linux-glibc211-x86_64$ blender
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  32
  Current serial number in output stream:  32
Speicherzugriffsfehler (Speicherabzug geschrieben)
linux@Linux-PC:~/Dokumente/blender-2.65-linux-glibc211-x86_64$ 

```I already asked in some forums and they told me to type this in:

```

sudo apt-get update 
sudo apt-get upgrade 
sudo apt-get install -f 
sudo dpkg --configure -a

```
After this I get this: :)

```
linux@Linux-PC:~/Dokumente/blender-2.65-linux-glibc211-x86_64$ sudo apt-get update
[sudo] password for linux: 
Ign http://de.archive.ubuntu.com precise InRelease
Ign http://de.archive.ubuntu.com precise-updates InRelease                     
Ign http://de.archive.ubuntu.com precise-backports InRelease                   
OK   http://de.archive.ubuntu.com precise Release.gpg                          
OK   http://de.archive.ubuntu.com precise-updates Release.gpg                  
OK   http://de.archive.ubuntu.com precise-backports Release.gpg                
OK   http://de.archive.ubuntu.com precise Release                              
Ign http://security.ubuntu.com precise-security InRelease                      
OK   http://de.archive.ubuntu.com precise-updates Release                  
OK   http://de.archive.ubuntu.com precise-backports Release                    
OK   http://de.archive.ubuntu.com precise/main Sources                         
OK   http://de.archive.ubuntu.com precise/restricted Sources                   
OK   http://de.archive.ubuntu.com precise/universe Sources                     
OK   http://de.archive.ubuntu.com precise/multiverse Sources                   
OK   http://de.archive.ubuntu.com precise/main amd64 Packages                  
Ign http://extras.ubuntu.com precise InRelease                                 
OK   http://de.archive.ubuntu.com precise/restricted amd64 Packages            
OK   http://de.archive.ubuntu.com precise/universe amd64 Packages          
OK   http://de.archive.ubuntu.com precise/multiverse amd64 Packages        
OK   http://de.archive.ubuntu.com precise/main i386 Packages               
OK   http://de.archive.ubuntu.com precise/restricted i386 Packages         
OK   http://de.archive.ubuntu.com precise/universe i386 Packages           
OK   http://de.archive.ubuntu.com precise/multiverse i386 Packages         
OK   http://de.archive.ubuntu.com precise/main TranslationIndex            
OK   http://de.archive.ubuntu.com precise/multiverse TranslationIndex      
OK   http://de.archive.ubuntu.com precise/restricted TranslationIndex      
Hole:1 http://security.ubuntu.com precise-security Release.gpg [198 B]     
OK   http://de.archive.ubuntu.com precise/universe TranslationIndex        
OK   http://de.archive.ubuntu.com precise-updates/main Sources             
OK   http://de.archive.ubuntu.com precise-updates/restricted Sources       
OK   http://de.archive.ubuntu.com precise-updates/universe Sources         
OK   http://de.archive.ubuntu.com precise-updates/multiverse Sources       
OK   http://de.archive.ubuntu.com precise-updates/main amd64 Packages      
OK   http://de.archive.ubuntu.com precise-updates/restricted amd64 Packages
OK   http://de.archive.ubuntu.com precise-updates/universe amd64 Packages  
OK   http://de.archive.ubuntu.com precise-updates/multiverse amd64 Packages
OK   http://de.archive.ubuntu.com precise-updates/main i386 Packages       
OK   http://de.archive.ubuntu.com precise-updates/restricted i386 Packages 
OK   http://de.archive.ubuntu.com precise-updates/universe i386 Packages   
OK   http://de.archive.ubuntu.com precise-updates/multiverse i386 Packages 
OK   http://de.archive.ubuntu.com precise-updates/main TranslationIndex    
OK   http://de.archive.ubuntu.com precise-updates/multiverse TranslationIndex
OK   http://extras.ubuntu.com precise Release.gpg                          
OK   http://de.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hole:2 http://security.ubuntu.com precise-security Release [49,6 kB]       
OK   http://de.archive.ubuntu.com precise-updates/universe TranslationIndex    
OK   http://de.archive.ubuntu.com precise-backports/main Sources               
OK   http://de.archive.ubuntu.com precise-backports/restricted Sources         
OK   http://de.archive.ubuntu.com precise-backports/universe Sources           
OK   http://de.archive.ubuntu.com precise-backports/multiverse Sources         
OK   http://de.archive.ubuntu.com precise-backports/main amd64 Packages        
OK   http://de.archive.ubuntu.com precise-backports/restricted amd64 Packages  
OK   http://de.archive.ubuntu.com precise-backports/universe amd64 Packages    
OK   http://de.archive.ubuntu.com precise-backports/multiverse amd64 Packages  
OK   http://de.archive.ubuntu.com precise-backports/main i386 Packages         
OK   http://de.archive.ubuntu.com precise-backports/restricted i386 Packages   
OK   http://de.archive.ubuntu.com precise-backports/universe i386 Packages     
OK   http://de.archive.ubuntu.com precise-backports/multiverse i386 Packages   
OK   http://de.archive.ubuntu.com precise-backports/main TranslationIndex      
OK   http://extras.ubuntu.com precise Release                                  
OK   http://de.archive.ubuntu.com precise-backports/multiverse TranslationIndex
OK   http://de.archive.ubuntu.com precise-backports/restricted TranslationIndex
OK   http://de.archive.ubuntu.com precise-backports/universe TranslationIndex  
OK   http://de.archive.ubuntu.com precise/main Translation-de                  
OK   http://de.archive.ubuntu.com precise/main Translation-en                  
OK   http://de.archive.ubuntu.com precise/multiverse Translation-de            
OK   http://de.archive.ubuntu.com precise/multiverse Translation-en            
OK   http://de.archive.ubuntu.com precise/restricted Translation-de            
OK   http://de.archive.ubuntu.com precise/restricted Translation-en            
OK   http://de.archive.ubuntu.com precise/universe Translation-de              
OK   http://de.archive.ubuntu.com precise/universe Translation-en              
OK   http://de.archive.ubuntu.com precise-updates/main Translation-de          
OK   http://de.archive.ubuntu.com precise-updates/main Translation-en          
OK   http://de.archive.ubuntu.com precise-updates/multiverse Translation-de    
OK   http://de.archive.ubuntu.com precise-updates/multiverse Translation-en    
OK   http://de.archive.ubuntu.com precise-updates/restricted Translation-de    
OK   http://extras.ubuntu.com precise/main Sources  
OK   http://de.archive.ubuntu.com precise-updates/restricted Translation-en
OK   http://de.archive.ubuntu.com precise-updates/universe Translation-de
OK   http://de.archive.ubuntu.com precise-updates/universe Translation-en
OK   http://de.archive.ubuntu.com precise-backports/main Translation-en
OK   http://de.archive.ubuntu.com precise-backports/multiverse Translation-en
OK   http://de.archive.ubuntu.com precise-backports/restricted Translation-en
OK   http://de.archive.ubuntu.com precise-backports/universe Translation-en 
Hole:3 http://security.ubuntu.com precise-security/main Sources [62,8 kB]   
OK   http://extras.ubuntu.com precise/main amd64 Packages 
OK   http://extras.ubuntu.com precise/main i386 Packages  
Ign http://extras.ubuntu.com precise/main TranslationIndex 
Hole:4 http://security.ubuntu.com precise-security/restricted Sources [1.950 B]
Hole:5 http://security.ubuntu.com precise-security/universe Sources [20,0 kB]
Hole:6 http://security.ubuntu.com precise-security/multiverse Sources [1.379 B]
Hole:7 http://security.ubuntu.com precise-security/main amd64 Packages [225 kB]
Hole:8 http://security.ubuntu.com precise-security/restricted amd64 Packages [3.969 B]
Hole:9 http://security.ubuntu.com precise-security/universe amd64 Packages [62,8 kB]
Hole:10 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2.184 B]
Hole:11 http://security.ubuntu.com precise-security/main i386 Packages [233 kB]
Hole:12 http://security.ubuntu.com precise-security/restricted i386 Packages [3.968 B]
Hole:13 http://security.ubuntu.com precise-security/universe i386 Packages [64,1 kB]
Hole:14 http://security.ubuntu.com precise-security/multiverse i386 Packages [2.366 B]
OK   http://security.ubuntu.com precise-security/main TranslationIndex         
OK   http://security.ubuntu.com precise-security/multiverse TranslationIndex   
OK   http://security.ubuntu.com precise-security/restricted TranslationIndex   
OK   http://security.ubuntu.com precise-security/universe TranslationIndex     
OK   http://security.ubuntu.com precise-security/main Translation-en           
OK   http://security.ubuntu.com precise-security/multiverse Translation-en
OK   http://security.ubuntu.com precise-security/restricted Translation-en
OK   http://security.ubuntu.com precise-security/universe Translation-en
Ign http://extras.ubuntu.com precise/main Translation-de_DE
Ign http://extras.ubuntu.com precise/main Translation-de
Ign http://extras.ubuntu.com precise/main Translation-en
Es wurden 733 kB in 3 s geholt (190 kB/s)
Paketlisten werden gelesen... Fertig
linux@Linux-PC:~/Dokumente/blender-2.65-linux-glibc211-x86_64$ sudo apt-get upgrade
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Statusinformationen werden eingelesen... Fertig
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
linux@Linux-PC:~/Dokumente/blender-2.65-linux-glibc211-x86_64$ sudo apt-get install -f
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Statusinformationen werden eingelesen... Fertig
Die folgenden Pakete wurden automatisch installiert und werden nicht mehr benötigt:
  language-pack-kde-de-base kde-l10n-de libunistring0:i386
  language-pack-kde-zh-hans-base libgomp1:i386 libcroco3:i386
  language-pack-kde-de language-pack-kde-en kde-l10n-engb libgettextpo0:i386
  language-pack-zh-hans-base kde-l10n-zhcn language-pack-zh-hans
  language-pack-kde-zh-hans language-pack-kde-en-base
Verwenden Sie »apt-get autoremove«, um sie zu entfernen.
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
linux@Linux-PC:~/Dokumente/blender-2.65-linux-glibc211-x86_64$ sudo dpkg --configure -a
linux@Linux-PC:~/Dokumente/blender-2.65-linux-glibc211-x86_64$ blender
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  32
  Current serial number in output stream:  32
Speicherzugriffsfehler (Speicherabzug geschrieben)
linux@Linux-PC:~/Dokumente/blender-2.65-linux-glibc211-x86_64$ 

```Does anyone know what I should do  to fix this?

**I'm following to hear from you and thank you for your time. **:) :popcorn::guitar:

Yours sincerely
Greenality

---

