---
title: "Can't install screenlets, why???"
date: 2008-01-01
forum: General Help
---

### Post by arashiko28 on 2008-01-01
This is the most weird thing, I have all day trying to workaround and nothing. I downloaded from screenlets.org the screenlets core package. Now, on the readme file says to get into the folder by terminal and do make install, that goes well, no errors. The second part is to make the menu. this is what I get:
> laptop:~/screenlets-0.0.10$ sudo make menu
[sudo] password for ***:
make -C desktop-menu
make[1]: Entering directory `/home/stephanie/screenlets-0.0.10/desktop-menu'
cp /home/stephanie/.config/menus/applications.menu /home/stephanie/.config/menus/applications.menu.bak
cp: cannot stat `/home/stephanie/.config/menus/applications.menu': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/stephanie/screenlets-0.0.10/desktop-menu'
make: *** [menu] Error 2


Any ideas? I'm tired of gdesklets and want something more stylish. Besides, can't get to install anything new there either. please help:confused:

---

### Post by hardyn on 2008-01-01
if you google around, a third party has made a .deb for the screelets, MUCH easier.

and no, i do not remember where i found it :)

---

### Post by arashiko28 on 2008-01-01
All right, now i know why it doesn't find it. instead of:> `/home/stephanie/.config/menus/applications.menu I have:
> /home/stephanie/.config/menus/applications-merged

Is there any way to change manually this directory name? or manually install it there? I think that will resolve the problem. meanwhile, i'll keep googling for the .deb package.

---

### Post by arashiko28 on 2008-01-02
Well, didn't found the .deb package, so had to do it the hard way. I'll put it here so if anyone needs it.

Step 1
> sudo gedit /etc/apt/sources.list

Step 2
Add either or both of these in the bottom of the list
> deb [http://hendrik.kaju.pri.ee/ubuntu/](http://hendrik.kaju.pri.ee/ubuntu/) gutsy screenlets
> deb [http://download.tuxfamily.org/screenlets](http://download.tuxfamily.org/screenlets) gutsy screenlets

Step 3
> sudo apt-get update

Step4
> sudo apt-get install screenlets

That should make them available at the menu under applications - others or system - preferences - screenlets manager.

I'm still working in making it run at startup.

For making it available on all desktops, go to properties and in the options tab mark stick to desktop. unmark keep above and keep bellow, if you have a sidebar unmark keep above and mark keep bellow. This way the sidebar will be under the screenlets, but the screenlets under your active window. :)

---

### Post by arashiko28 on 2008-01-02
**BUMP**

I have tried all!! everything I have seen in the forum for making the screenlets run at startup. It just keeps deleting from the startup list on sessions and in the screenlet manager, the option of making it autorun, also deletes it self. Please help... once or twice to do this is ok, but every time I turn on the computer? that's way too much!

---

### Post by hardyn on 2008-01-02
[http://www.screenlets.org/index.php/FAQ#Installation_instructions_for_Ubuntu_users_.28Edgy_Eft.2FFeisty_Fawn.2FGutsy_Gibbon.29](http://www.screenlets.org/index.php/FAQ#Installation_instructions_for_Ubuntu_users_.28Edgy_Eft.2FFeisty_Fawn.2FGutsy_Gibbon.29)

has instructions to add a new repository for a deb file.

---

### Post by arashiko28 on 2008-01-02
Thanks, but I already have it installed and running. Except for the fact that everytime i turn on my computer or restart, have to select the screenlets one by one, because the option of autorun at startup, deselect by itself and don't save that only change. All the others are intact.

---

### Post by jetta on 2008-01-03
> **arashiko28 said:**
> Thanks, but I already have it installed and running. Except for the fact that everytime i turn on my computer or restart, have to select the screenlets one by one, because the option of autorun at startup, deselect by itself and don't save that only change. All the others are intact.

I also had the same problem too, I install it from the website that hardyn gave, maybe someone could help us here.

---

### Post by hardyn on 2008-01-04
sure there is, but it also got me at first.  It is written on the same web page i believe.  you have to set each widget, through the widget to load automatically at startup.  I am not infront of my computer (nor will be for a few weeks) so i cant tell you exactly how to do it, but i assure you, its there and is pretty easy; just picking a checkbox.

---

### Post by lovhorror on 2008-03-16
couldn't find package screenlets

WTF?!

Full issue:
> cory@lovhorror-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                  
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg                           
Get:2 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US            
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Get:6 [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy Release.gpg [189B]                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources                               
Ign [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy/screenlets Translation-en_US              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                           
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources           
Get:7 [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy Release [6702B]               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources                            
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Translation-en_US            
Get:8 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages         
Ign [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy Release                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Get:9 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release [14.2kB]          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages        
Ign [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy/screenlets Packages
Err [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy/screenlets Packages              
  404 Not Found
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Packages
Get:10 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Sources [37B]
Err [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Packages
  404 Not Found
Fetched 21.3kB in 2s (7574B/s)
Failed to fetch [http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/screenlets/binary-i386/Packages.gz](http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/screenlets/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://download.tuxfamily.org/3vldeb/dists/feisty/eyecandy/binary-i386/Packages.gz](http://download.tuxfamily.org/3vldeb/dists/feisty/eyecandy/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
W: GPG error: [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3C33E735F854AFD7
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
cory@lovhorror-desktop:~$ sudo apt-get install screenlets
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package screenlets

---

### Post by ShodanjoDM on 2008-03-16
Have you checked this site: [http://getdeb.net/release.php?id=2128](http://getdeb.net/release.php?id=2128) ?

---

### Post by lovhorror on 2008-03-16
<3

---

