---
title: "Crash to login continuous loop. Halp!"
date: 2007-12-07
forum: General Help
---

### Post by Mnemonica on 2007-12-07
Mmmk. I was trying to uninstall compiz-fusion and was deleting repositories... I'm guessing that I deleted something major, because when I logged out and back in, it just brought me to a certain point and then stopped loading. That was fixed when I reinstalled gnome through recovery mode. But now, I attempted to update something to do with fx (I have very little clue about what I'm doing) and the walkthrough I was using told me to hit ctrl+alt+backspace... Which I did. But not, when I go to login I get to the brown screen before all of my desktop settings load... It flashes black a couple of times, goes to some text, and then reloads the login screen...

I've searched the forums and googled this high and low... And to no avail. I use this computer to take notes for class, and I have finals coming up... So I kind of need those notes. I understand that there won't be an easy fix for this and I'm willing to work with the terminal and whatever else.

I just need help. Lots of it.

Also, when I issue: sudo apt-get update

I eventually get this error:
   Reading package lists... Done
W: GPG erorr: [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3C33E735F854AFD7
W: You may want to run apt-get update to correct these problems

When I run update again I get the same error, exactly.

P.S. I'm running 7.10

---

### Post by braacken on 2007-12-07
I've had similar adventures as well.  Sometimes you may need to reinstall xorg/xsession items in the repos.  This may just be confined to ATI drivers.  But, if I make a mistake in setting up compiz et cetera, I usually have to reinstall xorg and use default monitor in order to get a display

---

### Post by Mnemonica on 2007-12-07
Alright. Sounds like it's worth a shot. Now if you would be so kind as to explain that in the simplest terms possible ( Like, actually tell me what to do), I would probably owe this semester's GPA to you.

---

### Post by Mnemonica on 2007-12-07
Ok, so after some private messaging, I got into failsafe GNOME. I tried to find a way to start compiz and came across

```
sudo SKIP_CHECKS=yes compiz

```

And I get this error:

```
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
Starting emerald
Xlib:  extension "GLX" missing on display ":0.0".
/usr/bin/compiz.real (core) - Fatal: Root visual is not a GL visual
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

When I enter

```
sudo apt-get update
```

it puts out

```
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 http://us.archive.ubuntu.com gutsy Release.gpg [191B]                    
Get:2 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Get:3 http://archive.canonical.com gutsy Release.gpg [191B]                    
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US           
Get:4 http://hendrik.kaju.pri.ee feisty Release.gpg [189B]                     
Ign http://archive.canonical.com gutsy/partner Translation-en_US               
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US     
Ign http://hendrik.kaju.pri.ee feisty/screenlets Translation-en_US             
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US       
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US     
Hit http://hendrik.kaju.pri.ee feisty Release                                  
Err http://hendrik.kaju.pri.ee feisty Release                                  
  
Get:5 http://archive.canonical.com gutsy Release [6998B]                       
Get:6 http://archive.canonical.com gutsy/partner Packages [2619B]              
Get:7 http://hendrik.kaju.pri.ee feisty Release [3687B]                        
Ign http://hendrik.kaju.pri.ee feisty Release                                  
Hit http://hendrik.kaju.pri.ee feisty/screenlets Packages                      
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US        
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US
Get:8 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com gutsy Release
Hit http://us.archive.ubuntu.com gutsy-updates Release              
Get:9 http://security.ubuntu.com gutsy-security Release [51.2kB]    
Hit http://us.archive.ubuntu.com gutsy/main Packages
Hit http://us.archive.ubuntu.com gutsy/restricted Packages
Hit http://us.archive.ubuntu.com gutsy/main Sources   
Hit http://us.archive.ubuntu.com gutsy/restricted Sources
Hit http://us.archive.ubuntu.com gutsy/universe Packages
Hit http://us.archive.ubuntu.com gutsy/universe Sources
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Get:10 http://security.ubuntu.com gutsy-security/main Packages [45.9kB]
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources    
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages          
Get:11 http://security.ubuntu.com gutsy-security/restricted Packages [14B]
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources      
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Get:12 http://security.ubuntu.com gutsy-security/main Sources [7790B]
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources      
Get:13 http://security.ubuntu.com gutsy-security/restricted Sources [14B]
Get:14 http://security.ubuntu.com gutsy-security/universe Packages [25.7kB]
Get:15 http://security.ubuntu.com gutsy-security/universe Sources [4368B]      
Get:16 http://security.ubuntu.com gutsy-security/multiverse Packages [2903B]   
Get:17 http://security.ubuntu.com gutsy-security/multiverse Sources [833B]     
Fetched 153kB in 6s (23.0kB/s)                                                 
Reading package lists... Done
W: GPG error: http://hendrik.kaju.pri.ee feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3C33E735F854AFD7
W: Duplicate sources.list entry http://archive.canonical.com gutsy/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_gutsy_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

Same problems as before, the only difference is that I can get into failsafe GNOME and when I'm in failsafe I can't enable desktop effects.

P.S. braacken suggested that I run

```
sudo apt-get install gdm

```

I did so and got this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gdm is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.

```

---

### Post by Mnemonica on 2007-12-07
I know double/triple posting is discouraged in most forums... But I'm looking for some help here. Even if you don't have a direct solution, could someone at least post some suggestions? Or am I completely screwed?

---

