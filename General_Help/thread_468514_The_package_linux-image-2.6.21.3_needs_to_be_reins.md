---
title: "The package linux-image-2.6.21.3 needs to be reinstalled, but I can't find an archive"
date: 2007-06-08
forum: General Help
---

### Post by Captain Colonoscopy on 2007-06-08
Hello, I am new to the forums and reasonably new to Linux and Ubuntu. I am not a total n00b as I have managed to figure out a few things by myself and I am getting good at following other people's guides to get my bcm4311 wireless card working, desktop effects with ATI 200m, etc. 

So, on to my problem. For some reason my wireless card quit working and I thought it was something to do with my drivers so I ran fwcutter again and that didn't work. I noticed that the light/switch for the card was no longer lit up and pushing the button no longer did anything. So I googled and found some other people had had the same problems and written a guide to fixing it. So I followed it and somewhere in there it said I had to recompile my kernel or something. So I did that, using their directions, it looks to have finished correctly as I can still use my computer and the wireless works again. Now I am trying to get the fancy desktop effects working and all that. I got the XGL session thing going, desktop effects work now. Tried to install beryl and got the following error message when doing from the terminal:

root@poobuntu:~# apt-get install beryl emerald-themes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package linux-image-2.6.21.3 needs to be reinstalled, but I can't find an archive for it.

Opening up Synaptic Package Manager gets me the same error message. I can't seem to get around this one. I tried googling and searching the forums and I can't seem to find anything anywhere about this problem.''


Has anyone run into this before? I thought I might need to just update my repositories or something but I can't open Synaptic GUI and I don't know how to do that from a command line.

Any help would be greatly appreciated. Thanks!
 [[IMG]http://www.hardfolding.com/ftag1.php/mem/148779.png[/IMG]](http://www.hardfolding.com?go=38&id=148779)

---

### Post by ramjet_1953 on 2007-06-08
It sounds like you need to re-load the package information in Synaptic.

To do this, just open the Synaptic Package Manager and click on the [COLOR="Blue"]re-load button[/COLOR] in the top left corner of the window.
 
Or, if you like the terminal, just type in [COLOR="Red"]sudo apt-get update
[/COLOR]
Regards,
Roger :cool:

---

### Post by rbmorse on 2007-06-09
I don't show any kernel newer than 2.6.20-X for feisty in repositories. Am I missing something?

---

### Post by Captain Colonoscopy on 2007-06-09
Ramjet - I cannot reload from Synaptic Package Manager, as soon as I open it a pop up window with the above mentioned error opens and when I click on okay synaptic closes. When I run the sudo apt-get update from the terminal it looks like everything updates and reloads okay. Then when I open Synaptic I get the same error message again.

I have no idea how I ended up with this kernel. I followed some guide on recompiling the kernel and this is what I ended up with. Perhaps I got it from somewhere other than the ubuntu repositories?? The goofy thing is that in GRUB it still shows 2.6.20.16 as the version I am booting.



Is there some way I can roll back the kernal or something? I don't really want to wipe and reinstall if I don't have to. I would prefer to work through this and learn something while I am going it but I have run out of ideas. :(

Thanks for the help.

 [[IMG]http://www.hardfolding.com/ftag1.php/mem/148779.png[/IMG]](http://www.hardfolding.com?go=38&id=148779)

---

### Post by Captain Colonoscopy on 2007-06-10
So I thought I would just paste all the crap I have tried so far tonight, see if anyone has any ideas.

[I][COLOR="DarkRed"]root@poobuntu:/home/charles# sudo dpkg --configure -a
root@poobuntu:/home/charles# sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package linux-image-2.6.21.3 needs to be reinstalled, but I can't find an archive for it.[/COLOR][/I]
Obviously that didn't do much for me.


[I][COLOR="DarkRed"]root@poobuntu:/home/charles# aptitude clean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done [/COLOR][/I]
that looked promising . . . . then . . . .     


[I][COLOR="DarkRed"]root@poobuntu:/home/charles# sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package linux-image-2.6.21.3 needs to be reinstalled, but I can't find an archive for it.
[/COLOR][/I]

so I tried this:
[I][COLOR="DarkRed"]root@poobuntu:/home/charles# sudo aptitude update && sudo aptitude upgrade
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US                   
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release                                  
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages                            
Get:2 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]         
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US       
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US     
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US            
Get:5 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release.gpg [191B]                 
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US            
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US          
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Translation-en_US               
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                         
Get:7 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release [2965B]                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources              
Get:8 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Packages [5855B]              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources                    
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Sources                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Sources                
Fetched 9019B in 6s (1459B/s)                                                   
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages will be upgraded:
  libxvidcore4 linux-headers-2.6.20-16 linux-headers-2.6.20-16-generic 
  linux-image-2.6.20-16-generic linux-libc-dev 
5 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] Y
E: I wasn't able to locate a file for the linux-image-2.6.21.3 package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
root@poobuntu:/home/charles# [/COLOR][/I]

And now I am right back where I was at. Is it possible that I just need to add a repository for this kernal that I managed to install? If so, how do I do that from the command line because I cannot open the synaptic gui?

Thanks for any insight anyone might have.



 [[IMG]http://www.hardfolding.com/ftag1.php/mem/148779.png[/IMG]](http://www.hardfolding.com?go=38&id=148779)

---

### Post by Captain Colonoscopy on 2007-06-10
So I thought I would add the repos for the new Gutsy Gibbon and do an update, see if that fixed anything. Well, it didn't, I still ahve the same error message. I am wondering if I just need to add wherever I downloaded this new kernel from as a repo . . . . .

 [[IMG]http://www.hardfolding.com/ftag1.php/mem/148779.png[/IMG]](http://www.hardfolding.com?go=38&id=148779)

---

### Post by DagMan on 2007-06-10
try backing up your sources.list, updating apt with an empty sources.list, then restorting it to normal and updating again.

Question for if that doesn't work.  Did you follow a guide on how to make restricted modules work on a 2.6.21 kernel or custom kernel prior to this happening?  I followed one and it confused apt about packages so I undid the changes I had made in that tutorial.

---

### Post by Captain Colonoscopy on 2007-06-10
> **DagMan said:**
> 
Question for if that doesn't work.  Did you follow a guide on how to make restricted modules work on a 2.6.21 kernel or custom kernel prior to this happening?  I followed one and it confused apt about packages so I undid the changes I had made in that tutorial.

That is exactly what I did. For the life of me I can't find what guide I ended up following, it wasn't one posted on ubuntu forums. I am usually pretty good about bookmarking everything I come across that I use to piddle with linux but I didn't this time . .. 

On another note, I managed to kinda sorta fix my problem. For giggles I tried reinstalling the kernal using the following:
[I][COLOR="DarkRed"]sudo dpkg -i linux-image-2.6.21.3_x86-64bit_amd64.deb
sudo dpkg -i linux-headers-2.6.21.3_x86-64bit_amd64.deb[/COLOR][/I]

I rebooted and the 2.6.21.3 kernel showed up and I booted into it. When I got to the desktop the video was all screwed up and completely unusable. So I rebooted again and was able to select the 2.6.20.16 generic kernel and it works just fine. Synaptic is working just fine after I removed the Gutsy Gibbon repos. :)

So, now that I am able to install programs again, I think I am going to hunt around for a guide on editing my grub so it doesn't list the 2.6.21.3 kernel and leave it at that. If I get adventurous again I might try to figure out how to get my video working with the new kernel, but that will be a  while me thinks.:D


 [[IMG]http://www.hardfolding.com/ftag1.php/mem/148779.png[/IMG]](http://www.hardfolding.com?go=38&id=148779)

---

### Post by DagMan on 2007-06-10
maybe it was this
[http://ubuntuforums.org/showthread.php?t=441013](http://ubuntuforums.org/showthread.php?t=441013)

I had to delete the entries I made with the text editors.  Use the search function of gedit because I found that it wasn't at the end of the file anymore.  Back up the files first in case you screw them up a little worse on accident.

You won't be able to use the Gusty kernel btw.  You can download the source code and compile it to run on Feisty but with things going upstream version to version, the tools and libraries used in the Gusty kernel compilation aren't going to be really compatible with Feisty and as it gets more developed it will be more so this way.  Also, I looked at compiling it for Feisty recently and although there is a restricted modules package in Gusty the patches for those modules aren't necisarrily there.. or my wireless hasn't been added yet anyway.  None of the Ubuntu patches are in it just yet.

---

### Post by NfF on 2007-06-10
I see.
And i need help too!

how u upgrade the kernel without an internet connection?im using windows now,,,so anything i can download,like a patch or full source kernel? can anyone direct me to a site to download kernel ver 2.6.15????

and also, how do i run windows application in linux? like internet explorer 7?

---

### Post by Captain Colonoscopy on 2007-06-10
> **DagMan said:**
> maybe it was this
[http://ubuntuforums.org/showthread.php?t=441013](http://ubuntuforums.org/showthread.php?t=441013)




I looked at that thread but that wasn't what I did to bork Synaptic. I think I just didn't install something correctly before or after I compiled the new kernel. After I reinstall the kernel Synaptic works fine now but I can't boot into the new kernel without problems. I probably have to do a make menuconfig or something.

Oh well, I can get into 2.6.20.16 just fine now and install stuff again. :)

 [[IMG]http://www.hardfolding.com/ftag1.php/mem/148779.png[/IMG]](http://www.hardfolding.com?go=38&id=148779)

---

### Post by Captain Colonoscopy on 2007-06-10
> **NfF said:**
> I see.
And i need help too!

how u upgrade the kernel without an internet connection?im using windows now,,,so anything i can download,like a patch or full source kernel? can anyone direct me to a site to download kernel ver 2.6.15????

and also, how do i run windows application in linux? like internet explorer 7?



I have no idea how you would go about upgrading anything in linux without an active internet connection. You might try searching the forums or googling for the answer to that one.

From what I understand, you would use WINE to run windows apps in linux. How to use/install WINE I have no idea. Also, why would you want to run IE7 in linux??? I am pretty sure that is a sin or something around here. :D

 [[IMG]http://www.hardfolding.com/ftag1.php/mem/148779.png[/IMG]](http://www.hardfolding.com?go=38&id=148779)

---

### Post by mconsidine on 2007-06-10
Same problem here, trying to upgrade from Edgy to Fiesty.  I was not trying to recompile anything, but instead went through the normal path via Update Manager.

The problem seemed to crop up when it was cleaning up.  I was away for a few days and when I came back, there was a dialogue box saying that some apps would only be supported if "community" packages (or something like that) was selected.  Fine, I hit "ok".

Then I get a message saying there was an unexpected error in "unattended update".  Which ultimately led to the message 

"The package linux-image-2.6.17-11-generic needs to be reinstalled, but I can't find an archive for it."

Update manager no longer works.  Neither does Synaptic.  Tried command-line approaches and get the same message.

Anyone got any ideas how I can move forward on this?

Matt

---

### Post by Captain Colonoscopy on 2007-06-12
> **mconsidine said:**
> Same problem here, trying to upgrade from Edgy to Fiesty.  I was not trying to recompile anything, but instead went through the normal path via Update Manager.

The problem seemed to crop up when it was cleaning up.  I was away for a few days and when I came back, there was a dialogue box saying that some apps would only be supported if "community" packages (or something like that) was selected.  Fine, I hit "ok".

Then I get a message saying there was an unexpected error in "unattended update".  Which ultimately led to the message 

"The package linux-image-2.6.17-11-generic needs to be reinstalled, but I can't find an archive for it."

Update manager no longer works.  Neither does Synaptic.  Tried command-line approaches and get the same message.

Anyone got any ideas how I can move forward on this?

Matt

This is what I did to fix mine:

sudo dpkg -i linux-image-2.6.21.3_x86-64bit_amd64.deb
sudo dpkg -i linux-headers-2.6.21.3_x86-64bit_amd64.deb

do a cd /usr/src and then an ls and see what pops up in the terminal. I would imagine you will find a linux-image-2.6.17.11_xxxxxx and a linux-headers-2.6.17.11_xxxxxx. Put those file names in front of a sudo dkpg -i and see if that fixes for you. You might have to do an aptitude update/upgrade or something and restart afterwards.

Give it a shot and let us know if that works for you.



 [[IMG]http://www.hardfolding.com/ftag1.php/mem/148779.png[/IMG]](http://www.hardfolding.com?go=38&id=148779)

---

