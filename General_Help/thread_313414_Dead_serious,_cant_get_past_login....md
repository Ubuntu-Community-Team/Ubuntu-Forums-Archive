---
title: "Dead serious, cant get past login..."
date: 2006-12-06
forum: General Help
---

### Post by burke9688 on 2006-12-06
Alright.
I'm using Ubuntu Edgy EFT 6.10 with
Gnome 2.16.1


So earlier today, I downloaded a bunch of the programs via Add Remove Progrms.
Re-Started computer, go to log back in.
Login works fine. Startup is fine.

Then I notice my res is in 600x800.
I go to change it. I cant.
I came here for help on it.
Got to some thread that said to run

**sudo /ect/init.d/gdm stop**

which i guess stopped gnome.

which effed up Ubuntu a lot.
I re-start, because it took me to a black screen.

Now I go to login, login works.
I get to the tan screen after that when the jungle music is supposed to play.
That never happens.
It freezes at that skin coloured background.
Plain tan page.
THen after about a minute, a large tan what looks like textarea appears in the top left corner.
I go to click on it, nothing.

So I uninstalled Ubuntu. Wanting, very badly to use it. cuzz it's fun.

Anyone think they can decode what I said, and help me? :D

---

### Post by ciscosurfer on 2006-12-06
I'm not quite sure what thread you were reading before that told you to stop GDM, but that was unnecessary.  I assume you were trying to get higher resolutions to appear (and use) instead of the 800x600.  To do this, you need to either modify your **/etc/X11/xorg.conf** file and add in new resolutions to your "Screen" section, subsection Modes (you can model yours after mine -- don't worry about everything else, I kept it in there so you would have a reference as to where to modify the Modes line):

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600]"
    Monitor        "Generic Monitor"
    Option         "HWCursor" "off"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


Or, you can enter the following from a terminal to accomplish the same task:```
**sudo dpkg-reconfigure -phigh xserver-xorg**
OR[B]
sudo dpkg-reconfigure xserver-xorg[/B]  <<FOR THE FULL MODIFICATION....THE FIRST ONE ABOVE WILL MODIFY RECENTLY CHANGED ELEMENTS.  IN OTHER WORDS, HIGH PRIORITY ELEMENTS
```So try installing Ubuntu again (b/c you said you uninstalled it) and see if your resolution is different this time around.  If not, take my advice from above, either modifying your **xorg.conf** file, or doing the same but through the command line.

Good Luck!

---

### Post by DougieFresh4U on 2006-12-06
First, 
Welcome to the community (is that Dansville as in N.Y.)I'm laughing at "The Jungle Music" :p  If you have a CD and don't have a lot of  data, just do a fresh install. I've done 12 re-installs in the last 2 months due to my 'F^*~ups Good luck!!

---

### Post by rabid emu on 2006-12-06
First off, this isn't windows, you don't need to restart the computer when you install stuff.  Similarly, if something isn't working (and Ubuntu was as a whole perfectly fine after your problem; your problem was with gnome or the X server most likely) there's no need to uninstall the entire OS.  Many people reformat their HDs when Windows crashes or gets a virus, but this is Linux.  No need for that stuff here.  There's tons of stuff you could have tried (maybe you didn't know about them, I don't know) to fix your system.

I don't know why you thought stopping gnome would be helpful to fixing your resolution, but whatever the reason (maybe it was legitimate, I have no idea), once gnome is screwed up (or perhaps X depending on the problem) you could have logged into a virtual terminal with ctrl+alt+f1 (or f2-f6 for that matter) and tried running "startx".  If that didn't work you could consider restoring xorg.conf, various gdm files, (if you had changed them at all) or uninstalling the programs you had just installed using apt.  If those still hadn't solved your problems, what I personally would have done would be to install Naim and go on the Ubuntu channel on irc.freenode.net and ask there, since I don't know that much about gdm or whatever specifically.  

Others can give you more specifics I'm sure, but the general point I'm trying to make is that in Linux you shouldn't just uninstall at the first sign of a problem.  Don't give up!

---

### Post by burke9688 on 2006-12-06
> **DougieFresh4U said:**
> First, 
Welcome to the community (is that Dansville as in N.Y.)I'm laughing at "The Jungle Music" :p  If you have a CD and don't have a lot of  data, just do a fresh install. I've done 12 re-installs in the last 2 months due to my 'F^*~ups Good luck!!

Well I just re-installed.
Got my wireless stuff configured.
Re-started, to confirm that it was indeed my wireless working, instead of Ethernet.

BOOM.
Same problem again.
My resolution was 1024x768, sitll too small for me.
But I was happy taht it was ok.

Re-started. Boom, stuck at the same spot.
Right before thee jungle music.


Thank youuuu :D-D
And, Dansville as in Michigan.
Smallest town in thee world :(](*,)

---

### Post by burke9688 on 2006-12-06
> **rabid emu said:**
> First off, this isn't windows, you don't need to restart the computer when you install stuff.  Similarly, if something isn't working (and Ubuntu was as a whole perfectly fine after your problem; your problem was with gnome or the X server most likely) there's no need to uninstall the entire OS.  Many people reformat their HDs when Windows crashes or gets a virus, but this is Linux.  No need for that stuff here.  There's tons of stuff you could have tried (maybe you didn't know about them, I don't know) to fix your system.

I don't know why you thought stopping gnome would be helpful to fixing your resolution, but whatever the reason (maybe it was legitimate, I have no idea), once gnome is screwed up (or perhaps X depending on the problem) you could have logged into a virtual terminal with ctrl+alt+f1 (or f2-f6 for that matter) and tried running "startx".  If that didn't work you could consider restoring xorg.conf, various gdm files, (if you had changed them at all) or uninstalling the programs you had just installed using apt.  If those still hadn't solved your problems, what I personally would have done would be to install Naim and go on the Ubuntu channel on irc.freenode.net and ask there, since I don't know that much about gdm or whatever specifically.  

Others can give you more specifics I'm sure, but the general point I'm trying to make is that in Linux you shouldn't just uninstall at the first sign of a problem.  Don't give up!


I read in a thread on this site, that if I were to stop GDM, that modifying X would go along a lot smoother.
So I did. It froze it.

So I uninstalled, cuzz I didnt know what else to do, and it stopped me from logging into windows.

Re-installed, got the same problem.

This time, I did nothing but install some drivers for my wireless card, and the directions I got from this forum said to re-start to make sure I was doing everything right.

---

### Post by ciscosurfer on 2006-12-06
Read my post above :-)

---

### Post by burke9688 on 2006-12-06
> **ciscosurfer said:**
> Read my post above :-)

I dont know if you read my post.
But my resolution isn't my problem.

I cant get to the terminal, or anything. To even worry about my res.


This is the best way to describe it.

I login, and get a blank screen.
Doesnt go past it.

I can boot via FailSafe Terminal, about it.
And windows is getting all sorts of errors now.

---

### Post by strabes on 2006-12-06
if you log in via failsafe terminal, you can run ```
sudo dpkg-reconfigure xserver-xorg
```

to set up your X server.

---

### Post by bscbrit on 2006-12-06
Strabes gave you good advice in the last post.  But I also have to ask, once you had reinstalled Ubuntu and BEFORE you installed your wifi drivers, was Ubuntu working fine?  If so, it seems like it was the installation of the wifi drivers that has somehow caused the problem - if not directly then because of something that you did during the installation.  If Ubuntu was not working fine then the wifi drivers are something of a red herring and we can try to solve your real problem.  Let me (and others) know and we will try to help.

---

### Post by burke9688 on 2006-12-06
> **bscbrit said:**
> Strabes gave you good advice in the last post.  But I also have to ask, once you had reinstalled Ubuntu and BEFORE you installed your wifi drivers, was Ubuntu working fine?  If so, it seems like it was the installation of the wifi drivers that has somehow caused the problem - if not directly then because of something that you did during the installation.  If Ubuntu was not working fine then the wifi drivers are something of a red herring and we can try to solve your real problem.  Let me (and others) know and we will try to help.


I'm going to give Strabe's advice some thinking, and probalby do it in about 2 minutes.

But Before  I installed my wifi drivers, ubuntu was working magnificently, it was actually the first time my ethernet cable has worked flawlessly.
The resason I dont normally use Ethernet, is because my computer is 100+ feet away from the router. And I have to move my computer really far to get close enough to hook it up.

But I still dont know what's causing the error.
I can login fine, but nothing more. I get to a blank screen afterl ogin and nothing happens. :/

---

### Post by burke9688 on 2006-12-06
I'm now thinking it has something to do with my wireless.

After I install my wifi stuff, re-boot just because I have to move my computer back into my room.
Cant login after that.
Weeelll, I login, but nothing past that.


Any possible reasons?

---

### Post by bscbrit on 2006-12-07
OK, please give me details of your wifi hardware, drivers and how you are trying to install them.

---

### Post by burke9688 on 2006-12-07
> **bscbrit said:**
> OK, please give me details of your wifi hardware, drivers and how you are trying to install them.

Alright. I'm using a NetGearWG311 v3 wireless card
I'm using these instructions here.
[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

About it. Every time I add ndiswrapper to startup, freeze.
Every time I dont add it, freeze...

---

### Post by bscbrit on 2006-12-07
I'm sure that you realise that the instructions that you are following are  not for your make of wireless card.  Which driver are you installing?

There is also another link that might be worth a look:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

and as you are an Edgy user, look also at the following:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper/edgy?highlight=%28wifi%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper/edgy?highlight=%28wifi%29)

---

### Post by burke9688 on 2006-12-07
> **bscbrit said:**
> I'm sure that you realise that the instructions that you are following are  not for your make of wireless card.  Which driver are you installing?

There is also another link that might be worth a look:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

and as you are an Edgy user, look also at the following:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper/edgy?highlight=%28wifi%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper/edgy?highlight=%28wifi%29)

Right now, I'm trying to find a linux driver for my Netgear card... I'm having a bit of trouble.

And then a installation for it. After that, I will post how re-booting and running basic things in Ubuntu goes!

Thank you!

---

### Post by bscbrit on 2006-12-07
Use the driver from the windows CD that came with the card.  Wrap it with ndiswrapper and it should work.

---

### Post by burke9688 on 2006-12-07
> **bscbrit said:**
> Use the driver from the windows CD that came with the card.  Wrap it with ndiswrapper and it should work.

Just got back from a fresh install, I installed the wrong drivers and it somehow deleted the files.

ANyways, past that.

I typed

sudo apt-get update

and got this at the VERY end



ormat
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages
  Sub-process gzip returned an error code (1)
Fetched 4B in 26s (0B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.



```

jakey@2BR00T4L4UZ:~$ sudo apt-get update
Get:1 http://us.archive.ubuntu.com edgy Release.gpg [191B]  
Ign http://us.archive.ubuntu.com edgy/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy/restricted Translation-en_US
Get:2 http://security.ubuntu.com edgy-security Release.gpg [191B]
Get:3 http://us.archive.ubuntu.com edgy-updates Release.gpg [191B]                                                          
Ign http://security.ubuntu.com edgy-security/main Translation-en_US                                                         
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US                                                        
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US                                                   
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US                                                  
Hit http://security.ubuntu.com edgy-security Release                                                                        
Hit http://us.archive.ubuntu.com edgy Release                                                                               
Hit http://us.archive.ubuntu.com edgy-updates Release                                                                       
Hit http://security.ubuntu.com edgy-security/main Packages                                                                  
Ign http://us.archive.ubuntu.com edgy/main Packages                                                                         
Hit http://security.ubuntu.com edgy-security/restricted Packages                                                            
Hit http://us.archive.ubuntu.com edgy/restricted Packages                                                                   
Hit http://security.ubuntu.com edgy-security/main Sources                                                                   
Hit http://us.archive.ubuntu.com edgy/main Sources                                                                          
Hit http://security.ubuntu.com edgy-security/restricted Sources                                                             
Hit http://us.archive.ubuntu.com edgy/restricted Sources                                                                    
Hit http://us.archive.ubuntu.com edgy-updates/main Packages                                                                 
Hit http://us.archive.ubuntu.com edgy-updates/restricted Packages                                                           
Hit http://us.archive.ubuntu.com edgy-updates/main Sources                                                                  
Hit http://us.archive.ubuntu.com edgy-updates/restricted Sources                                                            
Get:4 http://us.archive.ubuntu.com edgy/main Packages [1220kB]
99% [4 Packages gzip 0]  
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com edgy/main Packages
  Sub-process gzip returned an error code (1)
Fetched 4B in 26s (0B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```


What I was worried about, was it said 

E: Some inxed files failed to download, they have been ignored, or old ones used instead.


Is that "bad" by any means?

And how would I get the WindowsXP drivers OFF the cd?
Just drag and drop?

---

### Post by bscbrit on 2006-12-07
Don't worry about the message - perhaps some mirrors are incomplete or the server is temporarily down.

I think this will tell you what you need to know:

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

### Post by burke9688 on 2006-12-07
> **bscbrit said:**
> Don't worry about the message - perhaps some mirrors are incomplete or the server is temporarily down.

I think this will tell you what you need to know:

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)
Alright, do you suggest trying to do that at a later time?
My system says there are currently no updates for download.
So I don't think I'll be too worried about that tonight.

But, when I type in

make
in ndiswrapper-1.30$

i get this
a buncha errors



```

jakey@2BR00T4L4UZ:~/ndiswrapper-1.31$ make
make -C driver
make[1]: Entering directory `/home/jakey/ndiswrapper-1.31/driver'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/jakey/ndiswrapper-1.31/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  LD      /home/jakey/ndiswrapper-1.31/driver/built-in.o
  CC [M]  /home/jakey/ndiswrapper-1.31/driver/crt.o
  CC [M]  /home/jakey/ndiswrapper-1.31/driver/hal.o
  CC [M]  /home/jakey/ndiswrapper-1.31/driver/iw_ndis.o
  CC [M]  /home/jakey/ndiswrapper-1.31/driver/loader.o
  CC [M]  /home/jakey/ndiswrapper-1.31/driver/ndis.o
  CC [M]  /home/jakey/ndiswrapper-1.31/driver/ntoskernel.o
  CC [M]  /home/jakey/ndiswrapper-1.31/driver/ntoskernel_io.o
  CC [M]  /home/jakey/ndiswrapper-1.31/driver/pe_linker.o
  CC [M]  /home/jakey/ndiswrapper-1.31/driver/pnp.o
  CC [M]  /home/jakey/ndiswrapper-1.31/driver/proc.o
  CC [M]  /home/jakey/ndiswrapper-1.31/driver/rtl.o
  CC [M]  /home/jakey/ndiswrapper-1.31/driver/wrapmem.o
  CC [M]  /home/jakey/ndiswrapper-1.31/driver/wrapndis.o
  CC [M]  /home/jakey/ndiswrapper-1.31/driver/wrapper.o
  CC [M]  /home/jakey/ndiswrapper-1.31/driver/usb.o
  CC [M]  /home/jakey/ndiswrapper-1.31/driver/divdi3.o
  LD [M]  /home/jakey/ndiswrapper-1.31/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST
  CC      /home/jakey/ndiswrapper-1.31/driver/ndiswrapper.mod.o
  LD [M]  /home/jakey/ndiswrapper-1.31/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: Leaving directory `/home/jakey/ndiswrapper-1.31/driver'
make -C utils
make[1]: Entering directory `/home/jakey/ndiswrapper-1.31/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: expected specifier-qualifier-list before ‘size_t’
loadndisdriver.c: In function ‘load_file’:
loadndisdriver.c:67: error: ‘size_t’ undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected ‘;’ before ‘size’
loadndisdriver.c:68: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:71: warning: implicit declaration of function ‘basename’
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function ‘open’
loadndisdriver.c:73: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘syslog’
loadndisdriver.c:75: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:75: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘strerror’
loadndisdriver.c:75: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:76: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function ‘fstat’
loadndisdriver.c:81: warning: implicit declaration of function ‘close’
loadndisdriver.c:84: error: ‘size’ undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function ‘mmap’
loadndisdriver.c:86: error: ‘PROT_READ’ undeclared (first use in this function)
loadndisdriver.c:86: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: ‘MAP_FAILED’ undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function ‘strncpy’
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:95: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:96: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:69: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘parse_setting_line’:
loadndisdriver.c:109: warning: implicit declaration of function ‘isspace’
loadndisdriver.c:115: warning: implicit declaration of function ‘strchr’
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function ‘strchr’
loadndisdriver.c:115: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:118: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function ‘strlen’
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c: In function ‘read_conf_file’:
loadndisdriver.c:150: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:151: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:151: error: ‘config’ undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function ‘lstat’
loadndisdriver.c:158: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:160: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function ‘sscanf’
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:179: warning: implicit declaration of function ‘fopen’
loadndisdriver.c:179: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:183: warning: implicit declaration of function ‘fgets’
loadndisdriver.c:195: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:206: warning: implicit declaration of function ‘fclose’
loadndisdriver.c:150: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_bin_file’:
loadndisdriver.c:218: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:218: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:220: warning: implicit declaration of function ‘tolower’
loadndisdriver.c:222: warning: implicit declaration of function ‘chdir’
loadndisdriver.c:223: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:225: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:231: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:233: warning: implicit declaration of function ‘ioctl’
loadndisdriver.c:233: warning: implicit declaration of function ‘_IOW’
loadndisdriver.c:233: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘load_driver’:
loadndisdriver.c:250: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:250: error: ‘driver_dir’ undeclared (first use in this function)
loadndisdriver.c:252: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:256: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:256: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:258: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:260: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:262: warning: implicit declaration of function ‘opendir’
loadndisdriver.c:268: warning: implicit declaration of function ‘malloc’
loadndisdriver.c:268: warning: incompatible implicit declaration of built-in function ‘malloc’
loadndisdriver.c:272: warning: implicit declaration of function ‘memset’
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:273: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:281: warning: implicit declaration of function ‘readdir’
loadndisdriver.c:281: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:283: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:285: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function ‘stat’
loadndisdriver.c:288: error: dereferencing pointer to incomplete type
loadndisdriver.c:289: warning: implicit declaration of function ‘S_ISREG’
loadndisdriver.c:290: error: dereferencing pointer to incomplete type
loadndisdriver.c:295: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c:295: error: dereferencing pointer to incomplete type
loadndisdriver.c:297: warning: implicit declaration of function ‘strcasecmp’
loadndisdriver.c:297: error: dereferencing pointer to incomplete type
loadndisdriver.c:300: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:304: error: dereferencing pointer to incomplete type
loadndisdriver.c:306: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: error: dereferencing pointer to incomplete type
loadndisdriver.c:314: warning: implicit declaration of function ‘strcpy’
loadndisdriver.c:314: warning: incompatible implicit declaration of built-in function ‘strcpy’
loadndisdriver.c:315: error: dereferencing pointer to incomplete type
loadndisdriver.c:318: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:319: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:322: error: dereferencing pointer to incomplete type
loadndisdriver.c:283: warning: unused variable ‘statbuf’
loadndisdriver.c:345: error: expected expression before ‘struct’
loadndisdriver.c:347: warning: implicit declaration of function ‘closedir’
loadndisdriver.c:349: warning: implicit declaration of function ‘free’
loadndisdriver.c:356: warning: implicit declaration of function ‘munmap’
loadndisdriver.c:356: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:356: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:358: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:358: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c: In function ‘get_device’:
loadndisdriver.c:368: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:371: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:371: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:374: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:375: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:377: warning: implicit declaration of function ‘snprintf’
loadndisdriver.c:377: warning: incompatible implicit declaration of built-in function ‘snprintf’
loadndisdriver.c:408: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:368: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_device’:
loadndisdriver.c:420: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:420: error: ‘dir’ undeclared (first use in this function)
loadndisdriver.c:424: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:424: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:425: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:427: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:428: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:430: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:435: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:437: error: dereferencing pointer to incomplete type
loadndisdriver.c:440: error: dereferencing pointer to incomplete type
loadndisdriver.c:449: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘get_ioctl_device’:
loadndisdriver.c:466: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:466: error: ‘proc_misc’ undeclared (first use in this function)
loadndisdriver.c:474: warning: implicit declaration of function ‘strstr’
loadndisdriver.c:474: warning: incompatible implicit declaration of built-in function ‘strstr’
loadndisdriver.c:475: warning: implicit declaration of function ‘strtol’
loadndisdriver.c:475: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:485: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:485: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:490: warning: implicit declaration of function ‘unlink’
loadndisdriver.c:491: warning: implicit declaration of function ‘mknod’
loadndisdriver.c:491: error: ‘S_IFCHR’ undeclared (first use in this function)
loadndisdriver.c:491: error: ‘MISC_MAJOR’ undeclared (first use in this function)
loadndisdriver.c:492: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:497: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c: In function ‘main’:
loadndisdriver.c:513: warning: implicit declaration of function ‘openlog’
loadndisdriver.c:513: error: ‘LOG_PERROR’ undeclared (first use in this function)
loadndisdriver.c:513: error: ‘LOG_CONS’ undeclared (first use in this function)
loadndisdriver.c:513: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:513: error: ‘LOG_DEBUG’ undeclared (first use in this function)
loadndisdriver.c:515: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:517: warning: implicit declaration of function ‘strncmp’
loadndisdriver.c:519: warning: implicit declaration of function ‘printf’
loadndisdriver.c:519: warning: incompatible implicit declaration of built-in function ‘printf’
loadndisdriver.c:529: warning: implicit declaration of function ‘atoi’
loadndisdriver.c:544: warning: implicit declaration of function ‘atof’
loadndisdriver.c:551: warning: implicit declaration of function ‘strcmp’
loadndisdriver.c:558: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:592: warning: implicit declaration of function ‘closelog’
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/jakey/ndiswrapper-1.31/utils'
make: *** [all] Error 2
jakey@2BR00T4L4UZ:~/ndiswrapper-1.31$ 

```

listed there is my output when i type in 
"make" as say thee directions to install indiswrapper.

---

### Post by bscbrit on 2006-12-07
I'm afraid that that's me finished for tonight - but we can continue tomorrow evening if you wish?  Good Luck.

---

### Post by burke9688 on 2006-12-07
> **bscbrit said:**
> I'm afraid that that's me finished for tonight - but we can continue tomorrow evening if you wish?  Good Luck.

Thank you very much.
And yes, same time, same place!

---

### Post by burke9688 on 2006-12-07
new problemmm!


i try to do 

sudo apt-get update

and it says it cant download the last package.

so i cant install ndiswrapper untill i get the last package.

is there any way to do
sudo apt-get update without using terminal?

and i'm using NdisWrapper 1.31 :]

here is my output when i type it in.



```

jakey@2BR00T4L4UZ:~/ndiswrapper-1.31$ sudo apt-get update
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_US
Get:1 http://us.archive.ubuntu.com edgy Release.gpg [191B]                     
Get:2 http://security.ubuntu.com edgy-security Release.gpg [191B]
Ign http://us.archive.ubuntu.com edgy/main Translation-en_US
Ign http://security.ubuntu.com edgy-security/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy/restricted Translation-en_US
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US      
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US               
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US        
Get:3 http://us.archive.ubuntu.com edgy-updates Release.gpg [191B]             
Hit http://security.ubuntu.com edgy-security Release                           
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US           
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US     
Hit http://security.ubuntu.com edgy-security/main Packages                     
Ign http://us.archive.ubuntu.com edgy-updates/universe Translation-en_US       
Hit http://security.ubuntu.com edgy-security/restricted Packages               
Hit http://us.archive.ubuntu.com edgy Release                                  
Hit http://security.ubuntu.com edgy-security/main Sources                      
Hit http://us.archive.ubuntu.com edgy-updates Release                          
Hit http://security.ubuntu.com edgy-security/restricted Sources                
Ign http://us.archive.ubuntu.com edgy/main Packages                            
Hit http://security.ubuntu.com edgy-security/universe Packages                 
Hit http://us.archive.ubuntu.com edgy/restricted Packages                      
Hit http://us.archive.ubuntu.com edgy/main Sources                             
Hit http://us.archive.ubuntu.com edgy/restricted Sources                       
Hit http://us.archive.ubuntu.com edgy/universe Packages                        
Hit http://us.archive.ubuntu.com edgy-updates/main Packages                    
Hit http://us.archive.ubuntu.com edgy-updates/restricted Packages
Hit http://us.archive.ubuntu.com edgy-updates/main Sources
Hit http://us.archive.ubuntu.com edgy-updates/restricted Sources
Hit http://us.archive.ubuntu.com edgy-updates/universe Packages
Get:4 http://us.archive.ubuntu.com edgy/main Packages [1220kB]
99% [4 Packages gzip 0]             
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com edgy/main Packages
  Sub-process gzip returned an error code (1)
Fetched 4B in 32s (0B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```


At the end. It says.


```

Get:4 http://us.archive.ubuntu.com edgy/main Packages [1220kB]
99% [4 Packages gzip 0]             
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com edgy/main Packages
  Sub-process gzip returned an error code (1)
Fetched 4B in 32s (0B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```


ANy way to fix that?

---

### Post by bscbrit on 2006-12-08
Use System -> Administration -> Synaptic, search for ndiswrapper, select it and then press 'Apply'.  Done.

---

