---
title: "[SOLVED] Ubuntu Kubuntu"
date: 2007-11-23
forum: General Help
---

### Post by Nunu on 2007-11-23
HI Guys

I have both Ubuntu and Kubuntu 7.10. Now i am getting pretty much use to getting around GNOME and i am thinking its time to broaden the playing field. Do you think it is a good idea to add a kubuntu partition to my system or can i install the KDE front end on ubuntu and switch between GNOME and KDE. Which will be more stable. and if i have a single partition on a hard drive will i be able to install Kubuntu on a second partition on that same drive without affecting my ubuntu install?

---

### Post by PmDematagoda on 2007-11-23
I think having KDE and GNOME in one Ubuntu installation will be good enough and would be faster without having to waste time to switch between Ubuntu installations when you only want to switch between KDE and GNOME.

---

### Post by roaldz on 2007-11-23
If you just install kubuntu-desktop, you´d have both, but your menu´s will be twice as big...

---

### Post by Nunu on 2007-11-23
> **roaldz said:**
> If you just install kubuntu-desktop, you´d have both, but your menu´s will be twice as big...

Yeah thats true but that will also add some functionality to Both desktops that normally wouldn't be available right.

---

### Post by Nunu on 2007-11-23
Now the million dollar question is how do i install the KDE desktop ontop of ubuntu without affecting GNOME, and will I be able to choose between the two when i start a session. but most importantly where do i install it from?

---

### Post by PmDematagoda on 2007-11-23
You can follow this simple [guide]("http://www.psychocats.net/ubuntu/kde") on how to install and switch between KDE and GNOME.

---

### Post by Nunu on 2007-11-23
> **PmDematagoda said:**
> You can follow this simple [guide]("http://www.psychocats.net/ubuntu/kde") on how to install and switch between KDE and GNOME.

Absolutely brilliant i appreciate all the help guys, thank you very very much. I will give this a go as soon as i get home tonight. Thanks again.

---

### Post by Nunu on 2007-11-24
How can i install the requierd packages from the kubuntu CD?

---

### Post by PmDematagoda on 2007-11-24
Why do you want the Kubuntu  CD to install KDE on your PC, you can simply use the repos, or do you not have a fast internet connection?

---

### Post by boyturtle on 2007-11-24
>  Originally Posted by PmDematagoda  View Post
You can follow this simple guide on how to install and switch between KDE and GNOME.

Tried the above and after the command 
> sudo aptitude update && sudo aptitude install kubuntu-desktop

I got the following
> Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-en_GB
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-en_GB
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_GB            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_GB      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_GB        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                           
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy Release.gpg [191B]                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Translation-en_GB    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Translation-en_GB  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages          
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates Release.gpg [191B]  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main Sources                             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/multiverse Sources
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_GB
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_GB
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Fetched 192B in 0s (217B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "kubuntu-desktop"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done     

And no Kubuntu, have I missed something here?:confused:

---

### Post by PmDematagoda on 2007-11-24
Are you sure you have all the necessary repositories activated in Software Sources? I have the option of installing the kubuntu-desktop package in my system, so most likely it is something with what repositories you use.

---

### Post by boyturtle on 2007-11-24
Can you please tell me how to get the repositories, line by line please?

---

### Post by PmDematagoda on 2007-11-24
Open up the Software Sources application through System>Administration>System Sources. Then in the Ubuntu Software tab, enable all the choices except the Installable from CD-ROM/DVD ones. Then close it, it will ask you to reload the repository lists, do that and then try installing the kubuntu-desktop package again.

---

### Post by boyturtle on 2007-11-24
Thanks, that sorted it. 

Wow, a whole new interface. Loads of fun to be had:lolflag:

---

### Post by PmDematagoda on 2007-11-24
Glad to help:).

---

### Post by Nunu on 2007-11-26
> **PmDematagoda said:**
> Why do you want the Kubuntu  CD to install KDE on your PC, you can simply use the repos, or do you not have a fast internet connection?

Sorry for the long time since i replied. I actually have a brilliant internet connection problem is they still cap us in SA so i only have 2 gig a month to download with everything you go over you get charged an arm and a leg for (per meg out of bundle). so it gets a bit expensive when you reached your cap.

---

### Post by roaldz on 2007-11-26
> **Nunu said:**
> Sorry for the long time since i replied. I actually have a brilliant internet connection problem is they still cap us in SA so i only have 2 gig a month to download with everything you go over you get charged an arm and a leg for (per meg out of bundle). so it gets a bit expensive when you reached your cap.

Can´t you switch over to another ISP? 2GB is not much, I must say..

---

### Post by PmDematagoda on 2007-11-26
> **roaldz said:**
> Can´t you switch over to another ISP? 2GB is not much, I must say..

It is not much at all for really big internet users, but is considered to be more than enough by internet or ADSL newbies since they only usually download small files due to the speed of the connection. I thought so the same and took a package with a limit of 1Gb and a monthly rental of 10$ and 1$ per each Mb after the limit has been exceeded, I used it for 4 months and got a bill of 400$:(. Then I switched to a more expensive package with unlimited usage and it is very much cheaper:D.

---

### Post by roaldz on 2007-11-26
> **PmDematagoda said:**
> It is not much at all for really big internet users, but is considered to be more than enough by internet or ADSL newbies since they only usually download small files due to the speed of the connection. I thought so the same and took a package with a limit of 1Gb and a monthly rental of 10$ and 1$ per each Mb after the limit has been exceeded, I used it for 4 months and got a bill of 400$:(. Then I switched to a more expensive package with unlimited usage and it is very much cheaper:D.
I´m on a 20MBIT ADSL2+ line, on which I get 12.4 MBIT. Good enough for me, and no data limit or whatsoever (fair use policy). It costs me €24 per month, which equals to $35.

Ontopic:

Actually I´m a Kubuntu user too, but with feisty the desktop effects using Compiz Fusion were laggy, and I didn´t know what to love more, so I chose Gnome with CF.
Now I´ve seen gnome again for a while, I know why I am a KDE user. Gnome is much too simple for me. Kde gives me all the functionality I want, and more.
Question: Is Compiz Fusion still laggy with KDE? Some GTK Apps are still laggy with minimizing/maximizing. Amarok gives me no lag. What could my problem be? (Do I still have a problem?:P)

Roald

---

### Post by Nunu on 2007-11-27
Thats the benefits of living in a developing 3rd world country :)

---

