---
title: "New Ubuntu 7.10 x64 install, need help getting x-fi drivs and firefox acroread plugin"
date: 2008-03-25
forum: General Help
---

### Post by mrsack on 2008-03-25
Got Ubuntu 7.10 x86_64 installed earlier today and it's going pretty good so far.  My big issues right now are getting sound working with my creative x-fi and getting a Firefox plugin so Acrobot reader open in a browser tab.

1.** X-fi drivers** - I have searched around for a while and tried multiple guides  but so far no luck. The only one I finally got to complete with no errors was this 

[http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg21618.html](http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg21618.html)

After rebooting, though, still nothing. aplay -l still results in "no soundcards" or whatever as well as the Volume Control.

2. **Acrobat reader plugin** - I got acrobat read 7 installed as well as the acroread-plugins, but PDF's won't open within firefox.  A couple google searches said to install mozilla-acroread but I can't find that with apt-get or synaptic.

Other than that, Ubuntu is pretty good right after an install...definitely better than when I messed with Ubuntu a few years ago.  Thanks in advance for any help!

---

### Post by mrsack on 2008-03-25
bump....anybody know?

---

### Post by mrsack on 2008-03-26
should i post this in a more specific forum? I assumed the General questions would have a lot more people looking so it would get answered quickly, but that doesn't seem to be the case

---

### Post by ibuclaw on 2008-03-26
Not too sure about X-Fi soundcard.
ALSA's current wiki says that it's unsupported,

OSS currently have a driver here:
[http://www.opensound.com/linux.html]("http://www.opensound.com/linux.html")
It's currently fresh out of beta, and I suspect that's where ALSA are trying to get the X-Fi Soundcard to work.

[Install Manual is here, be sure to follow it as OSS use different tools to ALSA.]("http://www.opensound.com/release/oss-install.pdf")

[And the Linux_x86 .deb file can be downloaded here.]("http://www.4front-tech.com/release/oss-linux_v4.0-1015_i386.deb")

As for the Acrobat plugin.
Add Medibuntu to your repository:
```

sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```
Then type in this
```
 sudo apt-get install mozilla-acroread 
```

If you still can't open them, remove this file
```
 rm $HOME/.mozilla/firefox/pluginreg.dat 
```
Firefox will take about 2 seconds longer to load as it recreates the plugin database, but it will run as normal thereafter.

Regards
Iain

---

### Post by mrsack on 2008-03-26
Thanks for the reply! I get the following when I try to apt-get install mozilla-acroread

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mozilla-acroread has no installation candidate

```

---

### Post by ibuclaw on 2008-03-26
Are you sure that you've added medibuntu to your repository?
Have you updated the sources?

Because the package is only availiable from them.

[Here is their package list for proof]("http://medibuntu.org/packages.php")
Hit Ctrl+F and type in "acroread"

---

### Post by mrsack on 2008-03-27
```
hayden@hayden-ubuntu:~$ sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
[sudo] password for hayden:
--12:35:01--  http://www.medibuntu.org/sources.list.d/gutsy.list
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving www.medibuntu.org... 87.98.242.10
Connecting to www.medibuntu.org|87.98.242.10|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 223 [text/plain]

100%[====================================>] 223           --.--K/s             

12:35:02 (68.16 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [223/223]

hayden@hayden-ubuntu:~$ wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
OK
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1) gutsy/restricted Translation-en_US
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Get:2 http://packages.medibuntu.org gutsy Release.gpg [189B]                   
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US           
Get:3 http://archive.ubuntu.com gutsy Release.gpg [191B]                       
Ign http://archive.ubuntu.com gutsy/main Translation-en_US                     
Get:4 http://archive.canonical.com gutsy Release.gpg [191B]                    
Ign http://archive.canonical.com gutsy/partner Translation-en_US               
Get:5 http://us.archive.ubuntu.com gutsy Release.gpg [191B]                    
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US                  
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US       
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US     
Get:6 http://security.ubuntu.com dapper-security Release.gpg [191B]            
Ign http://security.ubuntu.com dapper-security/main Translation-en_US          
Ign http://security.ubuntu.com dapper-security/multiverse Translation-en_US    
Ign http://packages.medibuntu.org gutsy/free Translation-en_US                 
Ign http://packages.medibuntu.org gutsy/non-free Translation-en_US             
Hit http://archive.ubuntu.com gutsy Release                                    
Hit http://archive.canonical.com gutsy Release                                 
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US              
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US            
Get:7 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]            
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US    
Hit http://packages.medibuntu.org gutsy Release                                
Get:8 http://security.ubuntu.com gutsy-security Release [51.2kB]               
Hit http://archive.ubuntu.com gutsy/main Packages                              
Hit http://archive.canonical.com gutsy/partner Packages                        
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com gutsy Release                            
Ign http://packages.medibuntu.org gutsy/free Packages                          
Get:9 http://us.archive.ubuntu.com gutsy-updates Release [58.5kB]              
Hit http://archive.canonical.com gutsy/partner Sources                         
Ign http://packages.medibuntu.org gutsy/non-free Packages                      
Hit http://packages.medibuntu.org gutsy/free Packages                          
Hit http://packages.medibuntu.org gutsy/non-free Packages                      
Get:10 http://security.ubuntu.com dapper-security Release [50.9kB]
Hit http://us.archive.ubuntu.com gutsy/main Packages                           
Hit http://us.archive.ubuntu.com gutsy/restricted Packages
Hit http://us.archive.ubuntu.com gutsy/main Sources
Hit http://us.archive.ubuntu.com gutsy/restricted Sources
Hit http://us.archive.ubuntu.com gutsy/universe Packages
Hit http://us.archive.ubuntu.com gutsy/universe Sources
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Get:11 http://security.ubuntu.com gutsy-security/main Packages [79.6kB]
Get:12 http://us.archive.ubuntu.com gutsy-updates/main Packages [252kB]
Get:13 http://security.ubuntu.com gutsy-security/restricted Packages [14B]
Get:14 http://security.ubuntu.com gutsy-security/main Sources [15.0kB]
Get:15 http://security.ubuntu.com gutsy-security/restricted Sources [14B]      
Get:16 http://security.ubuntu.com gutsy-security/universe Packages [55.7kB]
Get:17 http://security.ubuntu.com gutsy-security/universe Sources [7954B]      
Get:18 http://security.ubuntu.com gutsy-security/multiverse Packages [2872B]   
Get:19 http://security.ubuntu.com gutsy-security/multiverse Sources [812B]     
Get:20 http://security.ubuntu.com dapper-security/main Packages [142kB]        
Get:21 http://security.ubuntu.com dapper-security/multiverse Packages [7021B]  
Get:22 http://us.archive.ubuntu.com gutsy-updates/restricted Packages [4031B]  
Get:23 http://us.archive.ubuntu.com gutsy-updates/main Sources [70.3kB]        
Get:24 http://us.archive.ubuntu.com gutsy-updates/restricted Sources [937B]    
Get:25 http://us.archive.ubuntu.com gutsy-updates/universe Packages [78.5kB]   
Get:26 http://us.archive.ubuntu.com gutsy-updates/universe Sources [12.7kB]    
Get:27 http://us.archive.ubuntu.com gutsy-updates/multiverse Packages [9943B]
Get:28 http://us.archive.ubuntu.com gutsy-updates/multiverse Sources [1878B]
Fetched 903kB in 3s (278kB/s)                       
Reading package lists... Done
hayden@hayden-ubuntu:~$ sudo apt-get install mozilla-acroreadReading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mozilla-acroread has no installation candidate
hayden@hayden-ubuntu:~$ 

```

Ok, that exactly what I get from the terminal when following your instructions. I also went to the site, and saw that listed there. Weird that it is not getting recognized :-k

---

