---
title: "Update Manager, Software Center, apt-get update &amp; upgrade all seg faulting"
date: 2015-04-16
forum: General Help
---

### Post by davehk on 2015-04-16
Since the recent upgrade to 12.04 Kernel Linux 3.2.0-39-generic-pae, all the above programs have been crashing with segmentation faults. I've tried deleting the files in /var/cache/apt as recommended in various places but this does not help. 

Any advice on how to fix this would be appreciated. All other programs are running with no problems.

Thanks,

Dave

Log file entries:

Apr 16 10:39:11 namrok3 kernel: [ 1377.814037] apport-gtk[5901]: segfault at a7903e20 ip b4bad301 sp a98fd240 error 6 in libapt-pkg.so.4.12.0[b4ad7000+125000]
Apr 16 10:39:22 namrok3 kernel: [ 1389.036479] update-manager[5974]: segfault at a64f6e20 ip b4bad301 sp bfdd48d0 error 6 in libapt-pkg.so.4.12.0[b4ad7000+125000]
Apr 16 10:39:36 namrok3 kernel: [ 1403.271276] apport-gtk[6069]: segfault at a7903e20 ip b4bad301 sp a98fd240 error 6 in libapt-pkg.so.4.12.0[b4ad7000+125000]

interesting that this is common to all three: libapt-pkg.so.4.12.0[b4ad7000+125000]

---

### Post by kc1di on 2015-04-16
I'm not sure what may be causing the problem but there are a couple ways you can try to workaround the problem. 
1.  return to the old kernel, (unless there is some compelling reason you need the new one) 

2.  turn off apport (In a terminal type:```
sudo service apport stop
``` this will temporarily turn apport off, if that clears the problem let us know will tell you how to make it permanent)

good Luck ;)

---

### Post by dino99 on 2015-04-16
by the way you still have the choice to downgrade apt to narrow down the issue
[https://launchpad.net/ubuntu/+source/apt](https://launchpad.net/ubuntu/+source/apt)

its easyto do via synaptic (if not also crashing) or with dpkg -i after downloading into an empty folder

---

### Post by ian-weisser on 2015-04-16
I would try reinstalling libapt first.
```
sudo apt-get install --reinstall libapt-pkg4.12
```
If it segfaults, please show us the output.


If the reinstall works but doesn't fix the problem:
1) I would not disable apport. You *want* the crash report to be transmitted. The crash report includes the data developers need to fix the problem, and adds heat to the stats at errors.ubuntu.com

2) I would look through the apt bug reports at Launchpad to see if an existing bug matches your problem.

---

### Post by davehk on 2015-04-16
apport doesn't seem to want  to stop, just sits there:

dave@namrok3:~$ sudo service apport status
apport stop/waiting

---

### Post by davehk on 2015-04-16
Re: I would try reinstalling libapt first.

apt-get segfaults so can't reintsall:

Apr 16 11:40:57 apt-get[25186]: segfault at b58d3e20 ip b76a0301 sp bfaa9670 error 6 in libapt-pkg.so.4.12.0[b75ca000+125000]
Apr 16 11:40:57 namrok3 kernel: [ 5084.159292] apt-get[25280]: segfault at b5973e20 ip b7740301 sp bf9f4cd0 error 6 in libapt-pkg.so.4.12.0[b766a000+125000]

Console output  - it reads package list up to95% then stops with no error message:

dave@namrok3:~$ sudo apt-get install --reinstall libapt-pkg4.12
dave@namrok3:~$ lists... 95%

---

### Post by davehk on 2015-04-16
> **kc1di said:**
> I'm not sure what may be causing the problem but there are a couple ways you can try to workaround the problem. 
1.  return to the old kernel, (unless there is some compelling reason you need the new one) 

2.  turn off apport (In a terminal type:```
sudo service apport stop
``` this will temporarily turn apport off, if that clears the problem let us know will tell you how to make it permanent)

good Luck ;)

Synaptic crashes with the same segfault data - so how would I go about returning to the old kernel?

Looks like downgrading apt may be the only way, which I guess I'll have to do via dpkg -i - is the steps documented anywhere?

As a last resort I have a system image from 6th January plus recent backups of all the user files.

Thanks to all for all the help so far!

---

### Post by kc1di on 2015-04-16
Try going back to the former kernel , you can do so by hitting the shift key at the beginning of the boot to display the grub menu.  select the older kernel and once booted up 
then install the  libapt-pkg4.12  package and reboot try newer kernel again.

---

### Post by davehk on 2015-04-16
Unfortunately I cannot boot the earlier version - I get a "file not found" error.
There are two versions of the kernel 3.2.0-39-generic-pae (the default) and 3.2.0-39-generic-pae (recovery mode - seems to freeze during boot?), 
then two version of 3.2.0-39-generic without the "pae" - one normal mode one recovery mode - which boot into an invalid graphics mode so I get no display,
and a 12.something version which give the file not found error.

---

### Post by ian-weisser on 2015-04-16
Please show us as much of the output as you can.
What file isn't found?
During which part of the boot process?

---

### Post by davehk on 2015-04-16
I can't capture the output as only GRUB is running when I get the file not found message. I'll copy it down and post it here shortly.

---

### Post by ian-weisser on 2015-04-16
Or post a clear photo

---

### Post by davehk on 2015-04-16
Nothing much to photo....

I select kernel 2.6.32-46-generic from the grub menu, and hit return. The screen clears and I get:

ERROR 15: File not found

Press any key.....

which returns me to the grub boot menu

(I suspect my problems booting the non-PAE kernel may be something to do with having 4G of RAM and an NVIDIA graphics card)

---

### Post by ian-weisser on 2015-04-16
Grub Error 15 (File Not Found) means that it cannot locate kernel 2.6.32-46 where you told it to look. There might be some relation to your 4G of RAM and NVIDIA card, but I cannot image what that relationship might be.

Grub doesn't scan all disks looking for bootable systems at boot - it relies upon the various systems updating Grub's list when they change.
At boot, Grub simply presents you the list.

Was your recent upgrade, by chance, interrupted before it was complete? Or did it have errors?

You seem to have two separate problems: A corrupt libapt package (or a corrupt libapt file), and a missing older kernel.

How much time do you want to invest in diagnosing these problems before it's worthwhile to reinstall?
There's no easy way to reinstall libapt...without using apt.

---

### Post by davehk on 2015-04-17
Thanks - I didn't think the 4GB/NVIDIA issue was anything to do with the file not found error, rather to do with the non-pae kernel that IS found booting into an invalid graphics state.

I seem to remember that there was a glitch with the recent upgrade. I thought I'd told it to do the updates, but then it came up with the same updates again and, perhaps foolishly, I told it to go ahead - it then completed apparently successfully (though clearly not!).

Anyway, if I'm going to have to re-install, I'm thinking it might be time to upgrade to the next LTS version with a clean install, so I'm currently copying off all the files i'll need to recreate web-servers and e-mail accounts, etc. after that.

---

### Post by davehk on 2015-04-20
It seems to me that this is a hole that should be plugged. Corruption of one file or library of an application should not require the re-install of the whole operating system.

I don't know how linux handles libraries. Is there no way of just replacing the faulty file, if I have a good version stored in a backup? Or are the links to the libraries absolute, requiring the file to be in the same physical location on the disc? For that matter, there should be a way of replacing a file with a good copy in the same place on the disc, as the file will be exactly the same size.

---

### Post by ian-weisser on 2015-04-20
> **davehk said:**
> Corruption of one file or library of an application should not require the re-install of the whole operating system.

Certainly not.
The way the package manager installs/removes packages is public, open, and learned by generations of users.
One normal way to fix a corrupt-file problem would be to merely reinstall the package. Easy - one command to the package manager.

But in this case, the package manager is what's broken. It cannot reinstall itself. A functioning package manger *can* reinstall or update itself.

If you are familiar with the concepts of manually downloading and decompressing .deb files, substitution is easy. Merely tedious.
Downloading and manually replacing the libapt libraries could take you as little as 5 or 10 minutes...once you can get into your system. And that might (or might not) solve that particular problem. The crash might have a different cause entirely.
Your GRUB problem seems a little more complex. It's hard to tell - all we know is that GRUB can't locate any of your installed kernels. That could have a lot of possible causes. Fixing the symptom is easy - create a boot-repair media...but without addressing the cause, the problem may promptly recur.

So, are you saying you want to spend time diagnosing, learning, and fixing?
Most of the tools you need are already on your system. We can guide you. Do you have the occasional time available? Might be one day, might be a week.

---

### Post by davehk on 2015-04-20
OK, I have the time to give this a go..

I have already downloaded libapt-pkg4.12_0.8.16~exp12ubuntu10.22_i386.deb as described in post #3 above, and I have that in an empty folder. Do it just use dpgk -i to install it, or or there other steps needed to replace the fault version that is already there?

Thanks,

Dave

---

### Post by davehk on 2015-04-20
Looking at the grub issue - it looks like /boot/grub has kernel versions from 3.2.0-39-generic-pae dates 27 Nov 2013, up to 3.2.0-80-generic-pae date 23 March 2015. However the system is still running on 3.2.0-39, but /boot/grub/menu.lst only contains the following entries:

title		Ubuntu 12.04.2 LTS, kernel 3.2.0-39-generic-pae
root		(hd0,0)
kernel		/boot/vmlinuz-3.2.0-39-generic-pae root=UUID=195b0fde-6111-4c0f-931e-005965a38c34 ro quiet splash 
initrd		/boot/initrd.img-3.2.0-39-generic-pae
quiet

title		Ubuntu 12.04.2 LTS, kernel 3.2.0-39-generic-pae (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-3.2.0-39-generic-pae root=UUID=195b0fde-6111-4c0f-931e-005965a38c34 ro  single
initrd		/boot/initrd.img-3.2.0-39-generic-pae

title		Ubuntu 12.04.2 LTS, kernel 3.2.0-39-generic
root		(hd0,0)
kernel		/boot/vmlinuz-3.2.0-39-generic root=UUID=195b0fde-6111-4c0f-931e-005965a38c34 ro quiet splash 
initrd		/boot/initrd.img-3.2.0-39-generic
quiet

title		Ubuntu 12.04.2 LTS, kernel 3.2.0-39-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-3.2.0-39-generic root=UUID=195b0fde-6111-4c0f-931e-005965a38c34 ro  single
initrd		/boot/initrd.img-3.2.0-39-generic

title		Ubuntu 12.04.2 LTS, kernel 2.6.32-46-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-46-generic root=UUID=195b0fde-6111-4c0f-931e-005965a38c34 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-46-generic
quiet

title		Ubuntu 12.04.2 LTS, kernel 2.6.32-46-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-46-generic root=UUID=195b0fde-6111-4c0f-931e-005965a38c34 ro  single
initrd		/boot/initrd.img-2.6.32-46-generic

title		Ubuntu 12.04.2 LTS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

So it looks as if kernel upgrades are not actually being used! Is this right or am I not understanding something? Would it be OK to edit the 2.6.32-46 entries to point to the latest version and give it a go?

Thanks.

---

### Post by davehk on 2015-04-20
Thinking further -- could my apt problem not actually be a problem with apt at all, but be due to the fact that I have the latest version of apt but am (apparently) running a very old kernel, and that something in the kernel referenced by apt has moved in the latest version, thus causing a seg fault when it tries to access that location with the older kernel running? Just rambling thoughts, perhaps, but I've seen those sorts of issues in the past with mainframe OS's like VAX/VMS etc.

---

### Post by ian-weisser on 2015-04-20
> **davehk said:**
> I have already downloaded libapt-pkg4.12_0.8.16~exp12ubuntu10.22_i386.deb as described in post #3 above, and I have that in an empty folder. Do it just use dpkg -i to install it

Yes. Try using sudo dpkg -i /path/to/libapt-pkg4.12_0.8.16~exp12ubuntu10.22_i386.deb , and see what happens.
Best case: The apt problem is fixed.
Worst case: dpkg returns an error...I *like* error messages. It means I can stop guessing.


> **davehk said:**
> [C]ould my apt problem not  actually be a problem with apt at all, but be due to the fact that I  have the latest version of apt but am (apparently) running a very old  kernel[...?]

Perhaps. Anything is possible. I would be surprised, but life is full of surprises.
I suppose we will find out soon....


> **davehk said:**
> Looking at the grub issue - it looks like /boot/grub has kernel versions from 3.2.0-39-generic-pae dates 27 Nov 2013, up to 3.2.0-80-generic-pae date 23 March 2015. However the system is still running on 3.2.0-39, but /boot/grub/menu.lst only contains the following entries:

Ah, so 'update-grub', which is supposed to run after every kernel update, seems a likely culprit.
Please try running 'sudo update-grub' manually, and post the output (with all the error messages) here.

You can certainly edit /boot/grub/grub.cfg manually ('sudo nano /boot/grub/grub.cfg') and see what happens. Save a backup of the file first, of course. Note that when 'update-grub' works properly, it will overwrite that file, destroying any changes you make.

---

### Post by matt_symes on 2015-04-20
Hi

This is not a cache issue is it ?

What happens if you copy and paste this into the terminal ?

```
sudo apt-get -o 'APT::Cache-Limit=100000000' update
```

Does it fall over ?

Can you also post the output of

```
grep -n "^[^#]" /etc/apt/sources.list{,.d/*}
```

This will show all your sources.

Kind regards

---

### Post by davehk on 2015-04-21
OK, using dpgk to reinstall libapt runs with no apparent errors but the libapt problem is not fixed.

Output from dpkg:

dave@namrok3:~/kits/libapt$ sudo dpkg -i /home/dave/kits/libapt/libapt-pkg4.12_0.8.16~exp12ubuntu10.22_i386.deb
[sudo] password for dave: 
(Reading database ... 1514805 files and directories currently installed.)
Preparing to replace libapt-pkg4.12 0.8.16~exp12ubuntu10.22 (using .../libapt-pkg4.12_0.8.16~exp12ubuntu10.22_i386.deb) ...
Unpacking replacement libapt-pkg4.12 ...
Setting up libapt-pkg4.12 (0.8.16~exp12ubuntu10.22) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
dave@namrok3:~/kits/libapt$ 

re: "this is not a cache issue:

I don't think so: 

dave@namrok3:~/kits/libapt$ sudo apt-get -o 'APT::Cache-Limit=100000000' update
Ign cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213) precise/main TranslationIndex
Ign cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213) precise/restricted TranslationIndex
Ign cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213) precise/main Translation-en_GB
Ign cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213) precise/main Translation-en
Ign cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213) precise/restricted Translation-en_GB
Ign cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213) precise/restricted Translation-en
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release.gpg                           
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release                               
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [54.3 kB]            
Get:4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release [196 kB]            
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [127 kB]        
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release.gpg                    
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [3,759 B] 
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [35.0 kB]   
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [535 kB]  
Hit [http://download.virtualbox.org](http://download.virtualbox.org) precise Release.gpg                         
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Sources                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release                        
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe TranslationIndex             
Get:9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Sources [487 kB]       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://download.virtualbox.org](http://download.virtualbox.org) precise Release                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main i386 Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse i386 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted i386 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main TranslationIndex          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse TranslationIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted TranslationIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe TranslationIndex      
Hit [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib i386 Packages               
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [8,939 B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,650 B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [120 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Translation-en            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Translation-en      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://download.virtualbox.org](http://download.virtualbox.org) precise/non-free i386 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Translation-en        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Get:13 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Sources [7,981 B]
Get:14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Sources [112 kB]  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib TranslationIndex            
Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/non-free TranslationIndex           
Get:15 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main i386 Packages [929 kB]
Get:16 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted i386 Packages [13.6 kB]
Get:17 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse i386 Packages [16.6 kB]
Get:18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe i386 Packages [265 kB]
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en_GB                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en_GB          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en_GB          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en_GB        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en           
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en_GB  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en_GB  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en_GB    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en       
Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib Translation-en_GB           
Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib Translation-en
Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/non-free Translation-en_GB
Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/non-free Translation-en
Fetched 2,914 kB in 4s (678 kB/s)                   
dave@namrok3:~/kits/libapt$ 

output from grep -n "^[^#]" /etc/apt/sources.list{,.d/*}:

dave@namrok3:~/kits/libapt$ grep -n "^[^#]" /etc/apt/sources.list{,.d/*}
/etc/apt/sources.list:5:deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213)]/ precise main restricted
/etc/apt/sources.list:6:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise main restricted multiverse
/etc/apt/sources.list:7:deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise main restricted
/etc/apt/sources.list:11:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates main restricted multiverse
/etc/apt/sources.list:12:deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates main restricted
/etc/apt/sources.list:19:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise universe
/etc/apt/sources.list:20:deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise universe
/etc/apt/sources.list:21:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates universe
/etc/apt/sources.list:22:deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates universe
/etc/apt/sources.list:45:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted multiverse
/etc/apt/sources.list:46:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
/etc/apt/sources.list:47:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
/etc/apt/sources.list:48:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
/etc/apt/sources.list:50:deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib non-free # disabled on upgrade to precise
/etc/apt/sources.list:51:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports main universe multiverse restricted
/etc/apt/sources.list:53:deb [http://ppa.launchpad.net/mscore-ubuntu/mscore-stable/ubuntu](http://ppa.launchpad.net/mscore-ubuntu/mscore-stable/ubuntu) precise main
/etc/apt/sources.list:54:deb-src [http://ppa.launchpad.net/mscore-ubuntu/mscore-stable/ubuntu](http://ppa.launchpad.net/mscore-ubuntu/mscore-stable/ubuntu) precise main
/etc/apt/sources.list.d/akirad.list.distUpgrade:5:deb [http://ppa.launchpad.net/akirad/akirad/ubuntu](http://ppa.launchpad.net/akirad/akirad/ubuntu) lucid main #Akirad Repository - Main
/etc/apt/sources.list.d/akirad.list.distUpgrade:7:deb [http://ppa.launchpad.net/akirad/ppa/ubuntu](http://ppa.launchpad.net/akirad/ppa/ubuntu) lucid main #Akirad Repository - Main
/etc/apt/sources.list.d/google-chrome.list:3:deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
/etc/apt/sources.list.d/google-chrome.list.distUpgrade:3:deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
/etc/apt/sources.list.d/google-chrome.list.save:3:deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
/etc/apt/sources.list.d/google-earth.list:3:deb [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable main
/etc/apt/sources.list.d/google-earth.list.save:3:deb [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable main
/etc/apt/sources.list.d/lucid-partner.list:4:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
/etc/apt/sources.list.d/lucid-partner.list.distUpgrade:4:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
/etc/apt/sources.list.d/lucid-partner.list.save:4:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
/etc/apt/sources.list.d/medibuntu.list.distUpgrade:2:deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free #Medibuntu - Ubuntu 10.04 "lucid lynx"
/etc/apt/sources.list.d/noobslab-indicators-precise.list:1:deb [http://ppa.launchpad.net/noobslab/indicators/ubuntu](http://ppa.launchpad.net/noobslab/indicators/ubuntu) precise main
/etc/apt/sources.list.d/noobslab-indicators-precise.list:2:deb-src [http://ppa.launchpad.net/noobslab/indicators/ubuntu](http://ppa.launchpad.net/noobslab/indicators/ubuntu) precise main
/etc/apt/sources.list.d/noobslab-indicators-precise.list.save:1:deb [http://ppa.launchpad.net/noobslab/indicators/ubuntu](http://ppa.launchpad.net/noobslab/indicators/ubuntu) precise main
/etc/apt/sources.list.d/noobslab-indicators-precise.list.save:2:deb-src [http://ppa.launchpad.net/noobslab/indicators/ubuntu](http://ppa.launchpad.net/noobslab/indicators/ubuntu) precise main
/etc/apt/sources.list.d/openoffice.list.distUpgrade:1:deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main # disabled on upgrade to lucid
/etc/apt/sources.list.d/pidgin-ppa.list.distUpgrade:1:deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) lucid main # disabled on upgrade to lucid
/etc/apt/sources.list.d/shiki-mediainfo-lucid.list:1:deb [http://ppa.launchpad.net/shiki/mediainfo/ubuntu](http://ppa.launchpad.net/shiki/mediainfo/ubuntu) precise main # disabled on upgrade to precise
/etc/apt/sources.list.d/shiki-mediainfo-lucid.list.distUpgrade:1:deb [http://ppa.launchpad.net/shiki/mediainfo/ubuntu](http://ppa.launchpad.net/shiki/mediainfo/ubuntu) lucid main
/etc/apt/sources.list.d/shiki-mediainfo-lucid.list.save:1:deb [http://ppa.launchpad.net/shiki/mediainfo/ubuntu](http://ppa.launchpad.net/shiki/mediainfo/ubuntu) precise main # disabled on upgrade to precise
/etc/apt/sources.list.d/tsbarnes-indicator-keylock-lucid.list:1:deb [http://ppa.launchpad.net/tsbarnes/indicator-keylock/ubuntu](http://ppa.launchpad.net/tsbarnes/indicator-keylock/ubuntu) precise main # disabled on upgrade to precise
/etc/apt/sources.list.d/tsbarnes-indicator-keylock-lucid.list.distUpgrade:1:deb [http://ppa.launchpad.net/tsbarnes/indicator-keylock/ubuntu](http://ppa.launchpad.net/tsbarnes/indicator-keylock/ubuntu) lucid main
/etc/apt/sources.list.d/tsbarnes-indicator-keylock-lucid.list.save:1:deb [http://ppa.launchpad.net/tsbarnes/indicator-keylock/ubuntu](http://ppa.launchpad.net/tsbarnes/indicator-keylock/ubuntu) precise main # disabled on upgrade to precise
/etc/apt/sources.list.d/tualatrix-ppa-precise.list:1:deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) precise main
/etc/apt/sources.list.d/tualatrix-ppa-precise.list:2:deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) precise main
/etc/apt/sources.list.d/tualatrix-ppa-precise.list.save:1:deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) precise main
/etc/apt/sources.list.d/tualatrix-ppa-precise.list.save:2:deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) precise main
/etc/apt/sources.list.d/umang-indicator-stickynotes-precise.list:1:deb [http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu](http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu) precise main
/etc/apt/sources.list.d/umang-indicator-stickynotes-precise.list:2:deb-src [http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu](http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu) precise main
/etc/apt/sources.list.d/umang-indicator-stickynotes-precise.list.save:1:deb [http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu](http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu) precise main
/etc/apt/sources.list.d/umang-indicator-stickynotes-precise.list.save:2:deb-src [http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu](http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu) precise main
dave@namrok3:~/kits/libapt$ 


Thanks again to all  for the help!

---

### Post by matt_symes on 2015-04-21
Hi

In your first post, you suggested in the post title that *apt-get update* was crashing but in your last post (#23) *apt-get update* ran without crashing.

So to clarify, is *apt-get update* crashing if you don't pass the option *APT::Cache-Limit=100000000* to it but not crashing if you do pass that option to it ? I'm a bit confused as to when this problem is being triggered.

BTW: Your sources look alright although you may want to clear up some of the .distUpgrade files to help clarity. You upgraded from 10.04 to 12.04 ?

Kind regards

---

### Post by davehk on 2015-04-21
> **matt_symes said:**
> Hi

In your first post, you suggested in the post title that *apt-get update* was crashing but in your last post (#23) *apt-get update* ran without crashing.

So to clarify, is *apt-get update* crashing if you don't pass the option *APT::Cache-Limit=100000000* to it but not crashing if you do pass that option to it ? I'm a bit confused as to when this problem is being triggered.

BTW: Your sources look alright although you may want to clear up some of the .distUpgrade files to help clarity. You upgraded from 10.04 to 12.04 ?

Kind regards

Hmm - I'm confused now too........

When I run apt-get update with no options, it always stops at the point where it has read 95% of the package lists and then stops with a segfault as per my post#4:

Apr 21 10:22:00 namrok3 kernel: [ 6152.642229] apt-get[2761]: segfault at b591de20 ip b76eb301 sp bf948090 error 6 in libapt-pkg.so.4.12.0[b7615000+125000]

The first time I ran it with the options specified, it ran OK.

When I ran again it with the options specified, after your post above, it NOW segfaults in the same way as without the options, which is different from what it did when I posted the output above!!:

Apr 21 10:23:14 namrok3 kernel: [ 6226.321459] apt-get[3316]: segfault at b5931e20 ip b76fe301 sp bff3ff00 error 6 in libapt-pkg.so.4.12.0[b7628000+125000]


in both cases there are no error message displayed on the console. This now seems to be repeatable. I can't esplain why it ran correctly with the options the first time, but then fails when I run it with the same options now, except that the first time I ran it with the options, it was immediately after a reboot. I'll try that to see if it makes any difference......

No, the command with the options still stops after the message "Reading package lists,,, 95%" with a segfault:

Apr 21 10:32:00 namrok3 kernel: [  180.789210] show_signal_msg: 51 callbacks suppressed
Apr 21 10:32:00 namrok3 kernel: [  180.789213] apt-get[3634]: segfault at b596de20 ip b773a301 sp bfd90160 error 6 in libapt-pkg.so.4.12.0[b7664000+125000]

Why it appears to have run correctly once I have no idea! Yes, I upgraded from 10.04 LTS to 12.04 LTS.

---

### Post by matt_symes on 2015-04-21
Hi

Just to check it's not the cache (i suspect we may be flogging a dead horse here but it's worth trying as the segfault looks to be a memory issue), open a terminal and copy and paste this into it. This will increase the starting value for the cache.

```
echo "APT::Cache-Start 200000000;" | sudo tee /etc/apt/apt.conf.d/80inccache
```

Check apt likes it with 

```
apt-config dump | grep Cache-Start
```

After that, try to update

```
sudo apt-get update
```

If that works then try 

```
sudo apt-get install htop
```

If that all works, after that try software-center and update-manager.

Post back on efficacy.

Kind regards

---

### Post by davehk on 2015-04-21
Whoop! Whoop! It's now all working!

So it looks like it was a cache issue after all - I wonder why, though, as I've not messed with any of the settings. Is there some housekeeping I should be doing tostop a recurrence?


! Thanks so much.

Now to try and boot the latest kernel - and to see why update-grub doesn't seem to be run after a kernel update.

---

### Post by matt_symes on 2015-04-21
Hi

> **davehk said:**
> Whoop! Whoop! It's now all working!

So it looks like it was a cache issue after all - I wonder why, though, as I've not messed with any of the settings. Is there some housekeeping I should be doing tostop a recurrence?

! Thanks so much.

Now to try and boot the latest kernel - and to see why update-grub doesn't seem to be run after a kernel update.

Let's do some cleaning up.

From the terminal

```
sudo rm /etc/apt/sources.list.d/*.distUpgrade
```

This will delete all the old sources that were disabled when you upgraded from 10.04 to 12.04.

Then let's clean up the caches. You may have already run some of these but do them again.

```
sudo apt-get clean
```

```
sudo apt-get autoremove
```

Delete any PPAs that you no longer use. You can do this using the GUI or the command line.

After deleting any PPAs you no longer use, delete the lists cache....

```
sudo rm -r /var/lib/apt/lists/*
```

....and then regenerate it

```
sudo apt-get update
```

As for the grub issue, start another thread and i'll keep my eyes open for it.

**EDIT:**

And if, after the reboot, things are still good then please mark this thread as [SOLVED].

Kind regards

---

### Post by dino99 on 2015-04-21
your latest posts let me think about the 'rebuilding index' failling to complete, probably due to some oldish 10.04's settings laying around either into the .local, .gconf, .gnome2 or .config files. They all can be renamed (with _old or deleted if you does not care about your custom settings) as they are created again on the next boot.

Your transition troubles confirm again that a fresh clean install is way better than an LTS > LTS dist-upgrade
Dont hesitate to clean the system (gtkorphan/autoremove) and glance at broken links into /etc/rc?.d (delete them in case)

---

### Post by davehk on 2015-04-21
> **9d9 said:**
> your latest posts let me think about the 'rebuilding index' failling to complete, probably due to some oldish 10.04's settings laying around either into the .local, .gconf, .gnome2 or .config files. They all can be renamed (with _old or deleted if you does not care about your custom settings) as they are created again on the next boot.

Your transition troubles confirm again that a fresh clean install is way better than an LTS > LTS dist-upgrade
Dont hesitate to clean the system (gtkorphan/autoremove) and glance at broken links into /etc/rc?.d (delete them in case)

Indeed - so when I go to 14.04 I'm going to buy a new HDD, so that I can go back to 12.04 until I've got 14.04 how I want it, and then mount the old system disk and copy all my files across.

---

### Post by davehk on 2015-04-21
matt - all cleanup done and rebooted - all good, many thanks. Will start a new thead on the update-grub issue in due course.

Many thanks to all who contributed to helping me fix this problem.

Dave

---

