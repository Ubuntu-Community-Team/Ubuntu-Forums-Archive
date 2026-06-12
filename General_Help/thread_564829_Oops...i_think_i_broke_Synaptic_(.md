---
title: "Oops...i think i broke Synaptic :("
date: 2007-10-01
forum: General Help
---

### Post by WolfByte on 2007-10-01
Hiyas all

Just decided to have a look in Synaptic this evening to try remove an application i had installed previously. Synaptic has been working well after i've installed said application as i've done a few updates since, and even continued to work after that.

What i get now when i run "synaptic" from the terminal is this...

Fontconfig error: "~/.fonts.conf", line 2: not well-formed (invalid token)
Segmentation fault (core dumped)

If i simply try run Synaptic from System -> Administration it simply flashes on and off the screen. At the same time everytime i run Synaptic it seems to cut any network connections i have running. ie. the internet.

Hopefully someone here could point me in the right direction and save me a reload. 

Thanks in advance
Wolfy

---

### Post by bapoumba on 2007-10-01
Please open a terminal (> Accessories > Terminal) and paste the complete output to:
```
sudo aptitude update
```

---

### Post by WolfByte on 2007-10-01
Alright, tried that and this is what i get...

user@computer:~$ sudo aptitude update
Password:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]             
Get:2 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty Release.gpg [191B]                    
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/main Translation-en_ZA                  
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/restricted Translation-en_ZA            
Get:3 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]         
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/universe Translation-en_ZA              
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/multiverse Translation-en_ZA            
Get:4 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates Release.gpg [191B]            
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/main Translation-en_ZA          
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]             
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/restricted Translation-en_ZA    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_ZA           
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty Release                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_ZA       
Get:6 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_ZA     
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates Release                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_ZA           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_ZA       
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_ZA     
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/main Packages                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_ZA     
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/restricted Packages                     
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/main Sources                            
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages                
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/restricted Sources                      
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/universe Packages                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_ZA       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                          
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/universe Sources                        
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/multiverse Packages                     
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/multiverse Sources                      
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/main Packages                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_ZA     
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_ZA         
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/restricted Packages             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_ZA       
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_ZA            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_ZA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_ZA
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/main Sources         
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/restricted Sources   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_ZA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release               
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
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_ZA                   
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release          
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages
Fetched 8B in 1m19s (0B/s)
Reading package lists... Done
user@computer:~$ synaptic
Fontconfig error: "~/.fonts.conf", line 2: not well-formed (invalid token)
Segmentation fault (core dumped)
user@computer:~$ 

Does this help at all?

---

### Post by shad0w_walker on 2007-10-01
Have you tried getting rid of the file it mentions in the error? Most programs generate new files like that automatically, so i suggest giving this a try.

1. Find the file in question. (It will be hidden in nautilus, hit ctrl+H to show hidden files)
2. Rename it to something different and unlikely to be used by anything (.fonts.conf.bakup for example)
3. Try running synaptic again.

Hopefully synaptic will regenerate the file correctly and the problem will be sorted, then you can delete the old file and carry on normally. If synaptic doesn't regenerate the file then you can just change the file name back, no harm done.

---

### Post by WolfByte on 2007-10-01
I'm not sure if that was a step forward or a step back. I tried that suggestion, and i get this...

user@computer:~$ sudo mv ~/.fonts.conf ~/.fonts.conf.backup
user@computer:~$ synaptic
Segmentation fault (core dumped)
user@computer:~$

---

### Post by bapoumba on 2007-10-01
Are you using compiz?
Do you remember which package you installed just before you got this error?

---

### Post by shad0w_walker on 2007-10-01
Well thats some kind of progress i guess. I have attached the contents of my .fonts.conf file  if you want to try one that is known working.

Can't make this an attachment as the attach option won't allow me to upload it.
```
<?xml version="1.0"?><!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>none</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>
```

---

### Post by bapoumba on 2007-10-01
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>
</fontconfig>
```
Here is mine (on Xfce)
Please try to place a new line in yours :
<?xml version="1.0"?> [COLOR="Red"]<-- here[/COLOR]
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

Line 2 malformed ;)

---

### Post by WolfByte on 2007-10-01
Putting anything back into ~/.fonts.conf brings me right back to square one. :(

The package i installed right before this all happened was the Vodafone Mobile Connect software for linux, and a few updates i can't remember the names.

---

### Post by WolfByte on 2007-10-01
I managed to remove the Vodafone software, but no dice. Same problem and error.

---

### Post by bapoumba on 2007-10-01
The error points at line 2. Did you try to add a line break (or <enter>, how is this called in English?) where I suggested ?

---

### Post by WolfByte on 2007-10-01
Yep, when i try that i just get back to this error...

Segmentation fault (core dumped)

---

### Post by bapoumba on 2007-10-01
Arf..
I'll keep looking then.
Edit: apt-get and synaptic are running fine, you can update/upgrade in the mean time.

Have you tried:
```
sudo aptitude update
sudo aptitude dist-upgrade
```
To see if there is some issue with the package "synaptic" ?

---

### Post by WolfByte on 2007-10-01
Interesting note...just saw somewhere someone mentioning wine.

I took the chance and removed wine, and now synaptic opens fine. :)

I'm guessing it's either a bug or a conflict with something else i have on my pc.

---

### Post by bapoumba on 2007-10-01
> **WolfByte said:**
> Interesting note...just saw somewhere someone mentioning wine.

I took the chance and removed wine, and now synaptic opens fine. :)

I'm guessing it's either a bug or a conflict with something else i have on my pc.
W00t :)

---

### Post by skillllllz on 2007-10-01
> **WolfByte said:**
> 
What i get now when i run "synaptic" from the terminal...


Note: Synaptic is a graphical application that should be run as a privileged user.

To run **graphical** applications as a privileged user, prefix the command with 'gksu'.
 
 Like this ~~> gksu synaptic

To run **non-graphical** applications as a privileged user, prefix the command with 'sudo'.

Like this ~~> sudo apt-get update

---

### Post by scruff on 2007-10-01
> **WolfByte said:**
> 
Hopefully someone here could point me in the right direction and save me a reload. 

Thanks in advance
Wolfy

First thing is, you almost **never** need to reload Linux. Everything is a file and other than hard drive corruption, anything can be fixed (one of the million ( but best) reasons *nix is the smartest OS design EVER).

Did you remove your file, or rename/move it? If you still have it, post it so we can look at the offending line 2.

---

### Post by scruff on 2007-10-01
Heh - sorry. Didn't even notice there was a 2nd page to this thread... I was posting off the end of page 1 :)

---

### Post by WolfByte on 2007-10-03
It happens to the best of us :D

Odd thing is, i removed wine and Synaptic started working again. Being the curious person i am, i tempted fate and reinstalled wine from Synaptic again and it works...everything is still working. Must've been one of those "A butterfly flaps it's wings in Timbuktu" things ;)

---

### Post by Poene on 2007-10-03
> **bapoumba said:**
> Please open a terminal (> Accessories > Terminal) and paste the complete output to:
```
sudo aptitude update
```

This fixed my error too. 

My error was ```
 peter@peter-desktop:~$ sudo apt-get install azureus
Reading package lists... Done
Segmentation fault (core dumped)
peter@peter-desktop:~$ 
```

Thanks dude!

---

