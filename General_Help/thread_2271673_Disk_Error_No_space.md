---
title: "Disk Error? No space"
date: 2015-03-31
forum: General Help
---

### Post by 171742 on 2015-03-31
Hello,

I have ubuntu 14.4 lts and am am a complete newbie, so all without terminal is welcome.

Suddenly my disk seems nearly full, but the disk manager does not show anything anymore. When I try to get the size by opening properties of my home folder it counts for ages and does not come to a number. Tried to run bleachbit, but it always stalls.

What to do?

Thanks!

---

### Post by v3.xx on 2015-03-31
> am a complete newbie, so all without terminal is welcome.
I guess I represent the unwelcome :) I need to know what the terminal says.

Please run a update in terminal and post any errors [(using code tags).]("http://ubuntuforums.org/showthread.php?p=12776168#post12776168")
```
sudo apt-get update
```
Also please post the output of
```
df -h
```

---

### Post by Mark Phelps on 2015-03-31
> so all without terminal is welcome.You're going to learn that diagnostics, which are vital to repairing problems in Linux systems, almost always require terminal usage.  You don't need the terminal to use Ubuntu, but you do need it to diagnose and repair it.

---

### Post by 171742 on 2015-04-01
> **v3.xx said:**
> I guess I represent the unwelcome :) I need to know what the terminal says.

Hello,

ok, I can manage that. Now the disk usage tool shows something, but all is still all full.

Please run a update in terminal and post any errors [(using code tags).]("http://ubuntuforums.org/showthread.php?p=12776168#post12776168")
```
sudo apt-get update
```

Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates InRelease                      
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty Release.gpg                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://apt.insynchq.com](http://apt.insynchq.com) trusty InRelease                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates Release.gpg                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports Release.gpg                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty Release                                
Hit [http://apt.insynchq.com](http://apt.insynchq.com) trusty/non-free amd64 Packages                     
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates Release                        
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports Release                      
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [63,5 kB]             
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/main Sources                           
Hit [http://apt.insynchq.com](http://apt.insynchq.com) trusty/contrib amd64 Packages                      
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/main amd64 Packages                    
Hit [http://apt.insynchq.com](http://apt.insynchq.com) trusty/non-free i386 Packages                      
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/restricted amd64 Packages              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/universe amd64 Packages                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [76,1 kB]        
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/multiverse amd64 Packages              
Hit [http://apt.insynchq.com](http://apt.insynchq.com) trusty/contrib i386 Packages                       
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/restricted i386 Packages               
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [2.061 B]  
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/multiverse i386 Packages               
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [18,0 kB]    
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/main Translation-en                    
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [1.905 B]  
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/multiverse Translation-en              
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [251 kB]  
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/universe Translation-en                
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/main Sources                   
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages [8.875 B]
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/restricted Sources             
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/universe Sources               
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/multiverse Sources             
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages [89,7 kB]
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/main amd64 Packages            
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/restricted amd64 Packages      
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/universe amd64 Packages        
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages [3.459 B]
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages      
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/main i386 Packages             
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [242 kB]  
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/restricted i386 Packages       
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/universe i386 Packages         
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [8.846 B]
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/multiverse i386 Packages       
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [89,7 kB]
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/universe Translation-en        
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/main Sources                 
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [3.628 B]
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/restricted Sources           
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/universe Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/multiverse Sources           
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/main amd64 Packages          
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/restricted amd64 Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/universe amd64 Packages      
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/main i386 Packages           
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/universe i386 Packages       
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/multiverse Translation-en
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/restricted Translation-en
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/universe Translation-en
Ign [http://apt.insynchq.com](http://apt.insynchq.com) trusty/contrib Translation-en_US        
Ign [http://apt.insynchq.com](http://apt.insynchq.com) trusty/contrib Translation-en                 
Ign [http://apt.insynchq.com](http://apt.insynchq.com) trusty/non-free Translation-en_US            
Ign [http://apt.insynchq.com](http://apt.insynchq.com) trusty/non-free Translation-en
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/main Translation-en_US
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/multiverse Translation-en_US
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/restricted Translation-en_US
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/universe Translation-en_US
Fetched 860 kB in 4s (177 kB/s)
Reading package lists... Done



Also please post the output of
```
 
```

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6       105G   98G  1,9G  99% /
none            4,0K     0  4,0K   0% /sys/fs/cgroup
udev            2,0G  4,0K  2,0G   1% /dev
tmpfs           396M  1,4M  394M   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            2,0G   84K  2,0G   1% /run/shm
none            100M   56K  100M   1% /run/user



Thanks!

---

### Post by Holger_Gehrke on 2015-04-01
> **171742 said:**
> 
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6       105G   98G  1,9G  99% /


Okay, that's your root file system and it's full. Let's check your home directory and it's subdirectories for size next:
```

du -c --max-depth 1 ~|sort -g

```
This command gives you a list of all direct subdirectories (that's what the --max-depth 1 option does) of your home directory (~ is a shorthand for /home/"your user name") with their size and a summary (the -c option) sorted by the sizes. This should make up 80% or more of the used space.

---

### Post by 171742 on 2015-04-01
Hey,

thanks, it says this:

o@o-HP-Compaq-6910p-KL536AV:~$ sudo du -c --max-depth 1 ~|sort -g
[sudo] password for o: 
^C
o@o-HP-Compaq-6910p-KL536AV:~$ du -c --max-depth 1 ~|sort -g
du: cannot read directory &#8216;/home/o/.cache/dconf&#8217;: Permission denied
^C
o@o-HP-Compaq-6910p-KL536AV:~$ 


This is by the way were bleachbit stopped as well:a config.

---

### Post by Holger_Gehrke on 2015-04-01
> **171742 said:**
> 
o@o-HP-Compaq-6910p-KL536AV:~$ du -c --max-depth 1 ~|sort -g
du: cannot read directory ‘/home/o/.cache/dconf’: Permission denied
^C
o@o-HP-Compaq-6910p-KL536AV:~$ 


This is by the way were bleachbit stopped as well:a config.

Did you abort by hitting ctrl-c when you got that error ? You shouldn't have. It continues to run ('du' sends it's output to 'sort', which won't start output until it has everything so it can do it's job; error messages are output on a separate channel (which does not get sent to 'sort'), but both du and sort continue to work; it's actually more a warning).

The error itself is somewhat strange, too. ' ~/.cache/dconf' should be readable for you ...

---

### Post by v3.xx on 2015-04-01
I bet your /boot is full of kernels.

[http://ubuntuforums.org/showthread.php?t=2270545](http://ubuntuforums.org/showthread.php?t=2270545)

---

### Post by 171742 on 2015-04-02
Hello,

I did not abort, it just says that.

---

### Post by 171742 on 2015-04-02
> **v3.xx said:**
> I bet your /boot is full of kernels.

[http://ubuntuforums.org/showthread.php?t=2270545](http://ubuntuforums.org/showthread.php?t=2270545)

Hello,

but I can install or deinstall stuff, seems not to be the problem. Or how to find out? Cant really understand the other thread in terms of this.

---

### Post by 171742 on 2015-04-02
Now it said:

du: cannot read directory &#8216;/home/o/.cache/dconf&#8217;: Permission denied
4    /home/o/.gphoto
4    /home/o/Public
4    /home/o/Templates
4    /home/o/Videos
8    /home/o/bin
8    /home/o/Desktop
8    /home/o/.ssh
8    /home/o/.xpaint
12    /home/o/.dbus
12    /home/o/.gnome
24    /home/o/.shutter
36    /home/o/.pki
36    /home/o/.sauerbraten
44    /home/o/.gkrellm2
48    /home/o/.gnucash
52    /home/o/.gconf
72    /home/o/.warzone2100-3.1
84    /home/o/.java
92    /home/o/.aqbanking
140    /home/o/.openshot
228    /home/o/.kde
392    /home/o/.gstreamer-0.10
568    /home/o/Wallpapers
708    /home/o/.fontconfig
948    /home/o/.widelands
988    /home/o/.lastpass
2940    /home/o/.compiz
3888    /home/o/.macromedia
12916    /home/o/.adobe
41952    /home/o/sane-backends
69656    /home/o/Music
152836    /home/o/.dropbox-dist
162296    /home/o/.cache
163656    /home/o/.mozilla
180184    /home/o/.dropbox
193696    /home/o/.config
476708    /home/o/.local
606028    /home/o/Windows und Tools
1016520    /home/o/.wine
1040516    /home/o/f1Sr7S.PHB
1374684    /home/o/.recoll
23831996    /home/o/VirtualBox VMs
28952668    /home/o/.thunderbird
31790096    /home/o/Dropbox
90078604    /home/o
90078604    total

---

### Post by sudodus on 2015-04-02
```
23831996    /home/o/[COLOR=#ff0000]VirtualBox[/COLOR] VMs
28952668    /home/o/[COLOR=#ff0000].thunderbird[/COLOR]
31790096    /home/o/[COLOR=#ff0000]Dropbox[/COLOR]
90078604    /home/o
90078604    total 				
```

Most of the space is used by files in 3 directories.

If you ***boot from an external drive***, for example your Ubuntu install DVD or USB drive, you can mount /dev/sda6 and remove some files, that are not so important (maybe back them up into some other [external] drive before removing them.

---

### Post by 171742 on 2015-04-02
ok, thanks, must have been copying local folders in thinderbird!

---

