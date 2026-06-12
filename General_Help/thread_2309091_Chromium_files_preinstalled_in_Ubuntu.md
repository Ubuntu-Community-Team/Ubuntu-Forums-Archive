---
title: "Chromium files preinstalled in Ubuntu?"
date: 2016-01-07
forum: General Help
---

### Post by KenUBF on 2016-01-07
Hello,  I have Ubuntu 14.04 LTS installed on my machine. I am still fairly new to Ubuntu and I installed the Chromium web browser. I didn't like it so I decided to stick with Firefox. When looking at my files I noticed a few files named Chromium, and this made me wonder if perhaps the browser and a few associated files did not properly uninstall. I searched online to be sure that there were no native files that happened to have the same name as the Chromium browser that the system might need and I found nothing about the system needing the few I deleted. Though, strangely, I did see what looks like a game with the name Chromium (see screenshot). Thinking these files were safe to delete I used the sudo command and deleted them in Nautilus. It's been a number of months and my system seems stable, but sometimes when I am running an update I watch the Terminal and I notice there is often a string among the information that says something like Chromium cannot be found... All updates install fine and work fine, but I'm beginning to wonder if I happened to delete something that my system needs? If that is the case, would it be possible to reinstall those files? Thank you for any information you can provide.

---

### Post by v3.xx on 2016-01-07
If you use Synaptic package manager, it will show all chromium installs.

[ATTACH=CONFIG]266605[/ATTACH]

To install synaptic from the terminal; enter:
```
sudo apt-get install synaptic
```

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9)

---

### Post by vasa1 on 2016-01-07
> **KenUBF said:**
> .., but **sometimes** when I am running an update I watch the Terminal and I notice there is **often** a string among the information that says **something like** Chromium cannot be found... ...
Try to provide the entire output of *sudo apt-get update* within code tags and _not_ as an image.

---

### Post by KenUBF on 2016-01-08
> **v3.xx said:**
> If you use Synaptic package manager, it will show all chromium installs.
 

 
 

 It looks like I do have some residual files. The entries with a green box next to them are the ones that are installed, correct? Would these be safe to delete? &#8220;Unity-scope-chromiumbooksm&#8221; and &#8220;chromium-codecs-ffmpeg-ext&#8221;? Apologies for the many questions, I just recently installed Synaptic and haven't learned how to use it yet.
 

 > **vasa1 said:**
> Try to provide the entire output of *sudo apt-get update* within code tags and _not_ as an image.


 Here is the output.... Nothing there, but I don't think I was performing this operation when it occurred. I cannot recall exactly what I was updating when I saw this message. I'll just have to update this if it happens again. Unless it has something to do with the above files...  Thank you so much for the replies.
 

 ```

 ubuntu@ubuntu1:~$ sudo apt-get update 
 [sudo] password for ubuntu:  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                        
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                       
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources                     
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                     
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources               
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                             
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources                 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources                    
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources               
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources              
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages              
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources                
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages        
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources              
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages          
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages             
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages        
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages       
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages               
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages         
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages         
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages       
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages           
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                   
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages     
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages         
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages        
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en              
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages          
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en        
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                     
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en             
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en          
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                                
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en 
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                   
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en 
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                    
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources           
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main amd64 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted amd64 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe amd64 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en 
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en 
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en               
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release    
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en 
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US            
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US            
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US              
 Reading package lists... Done                                                   
 ubuntu@ubuntu1:~$  
 
```

---

### Post by vasa1 on 2016-01-08
The "oxide" entries in your screenshot relate to Canonical's in-house browser found in Ubuntu and maybe Edubuntu.

The scopes are, so far, unique to Ubuntu.

You may get a cleaner view of "chrom"-related stuff installed on your system by running **dpkg --get-selections | grep chrom**.

---

### Post by vasa1 on 2016-01-08
Nothing seems amiss with the output of **sudo apt-get update** but ... 

[LIST]
[*]if you're new to Ubuntu and you're a bit conservative, you could do without the backports.
[*]you could also remove the "source" entries (if you don't plan to look at the source code of programs and most "average users" don't).
[*]I notice you have both amd64 and i386 entries. If you're on 64-bit and don't have any 32-bit applications or don't plan on installing 32-bit software you can stop i386 entries from showing up by running **sudo dpkg --remove-architecture i386**. (You can reverse that whenever you need by running **sudo dpkg --add-architecture i386**)
[*]if you're not particularly interested in "translations", get rid of those entries by creating **/etc/apt/apt.conf.d/99translations** with just this content: **Acquire::Languages "none";** you'll need *sudo* for that. 
[*]
[/LIST]

---

### Post by grahammechanical on 2016-01-08
One of the things that make Free & Open Source software (FOSS) so great is that anyone can use the code. If the software is well written & it does a good job, then why not use it? All Linux distributions use software from other Linux developers & projects.

One reason we use a package management system like apt and front-ends like Synaptic Package Manager and Software Centre is that the package manager keeps a list of all packages installed and then updates the list when packages are removed.

Yes, we can delete files using the terminal but then the package list still has a record of that package being on the system. Then when we set the package manager the task of checking for updates to installed packages it gets errors.

I have not installed Chromium but I do have installed

unity-scope-chromiumbookmarks
liboxideqt-qmiplugin
liboxideqtquick0
oxideqtcodecs
liboxideqtcore0

Some of that stuff may have come in with Chrome, which I do have installed but I suspect that most of it is part of a default installation of Ubuntu.

Oh, there is a game called Chromium B.S.U. It is in the software centre. It is a scrolling space shooter. Are you sure that you did not install it at some time?


Regards.

---

### Post by vasa1 on 2016-01-08
> **grahammechanical said:**
> ...
One reason we use a package management system like apt and front-ends like Synaptic Package Manager and Software Centre is that the package manager keeps a list of all packages installed and then updates the list when packages are removed.

Yes, **we can delete files using the terminal** but then the package list still has a record of that package being on the system. Then when we set the package manager the task of checking for updates to installed packages it gets errors.

...
Are you referring to *sudo apt-get remove* or *sudo apt-get purge* or are you cautioning against running something like *sudo rm package_name*?

---

### Post by KenUBF on 2016-01-08
It just so happened that an update for Firefox was just rolled out. I updated the system and when programs install you can click to open a terminal window that will show you all of the operations as it installs. I caught a glimpse of exactly what it said was missing: unity-scope-chromiumbookmarks. Which seems odd since I thought Synaptic said it was installed. Sorry I did not have time to take a screenshot. The program installed and the window closed before I could get one. 

> **grahammechanical said:**
> One of the things that make Free &  Open Source software (FOSS) so great is that anyone can use the code. If  the software is well written & it does a good job, then why not use  it? All Linux distributions use software from other Linux developers  & projects.

One reason we use a package management system like apt and front-ends  like Synaptic Package Manager and Software Centre is that the package  manager keeps a list of all packages installed and then updates the list  when packages are removed.

Yes, we can delete files using the terminal but then the package list  still has a record of that package being on the system. Then when we set  the package manager the task of checking for updates to installed  packages it gets errors.

I have not installed Chromium but I do have installed

unity-scope-chromiumbookmarks
liboxideqt-qmiplugin
liboxideqtquick0
oxideqtcodecs
liboxideqtcore0

Some of that stuff may have come in with Chrome, which I do have  installed but I suspect that most of it is part of a default  installation of Ubuntu.

Oh, there is a game called Chromium B.S.U. It is in the software centre.  It is a scrolling space shooter. Are you sure that you did not install  it at some time?


Regards.

It seems like it's nothing to be concerned about. Since I'm fairly new to Ubuntu I just thought I'd ask about it. Nope, don't have Chromium B.S.U. installed, since it says I can install it in the Software Center. But it sounds fun so I installed it just now. :- )   Yes, I agree. Open source also seems to be a lot more stable. I've been using Ubuntu for about two years but only recently decided to have it as the only OS on my machine. I love it. It doesn't get bogged down like Windows did after a few months and it seems much more secure. I have offically turned into an official Ubuntu fan, hence my screen name KenUBF (Ubuntu Fan). Thanks again for all of your help everyone. These forums have been invaluable to me with answering questions and helping me fix any issues I have run into while getting used to the new system. Take care all.

---

