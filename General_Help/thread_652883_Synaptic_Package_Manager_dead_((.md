---
title: "Synaptic Package Manager dead :(("
date: 2007-12-29
forum: General Help
---

### Post by xaxas on 2007-12-29
I can't install anything :((

Pleaze, can anyone help ...

Look what happens in the console :((
```
xaxas@cybertron:~$ sudo apt-get install kino
[sudo] password for xaxas:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bochsbios vgabios libares0
Use 'apt-get autoremove' to remove them.
Suggested packages:
  vorbis-tools sox mjpegtools lame
The following NEW packages will be installed:
  kino
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

```

this fails in the Synaptic Package Manager two and says: 

```
dpkg: unable to stat triggers deferred file '/var/lib/dpkg/triggers/Unicorp:' Input/output error 
```:((

pleaze help :((

---

### Post by TidusBlade on 2007-12-29
I think you might have another Synaptic open or something? Anything installing anything or open anywhere will usually cause this, so close them all if any.

---

### Post by xaxas on 2007-12-29
nothing's open :((
tryed rebooting a couple of times :((
no result :(

---

### Post by mali2297 on 2007-12-29
Post the output of
```

ls -l / | grep var

```

---

### Post by xaxas on 2007-12-29
```
xaxas@cybertron:~$ ls -l / | grep var
drwxr-xr-x  15 root root  4096 2007-10-16 02:31 var

```

---

### Post by PmDematagoda on 2007-12-29
Do:-
```
sudo rm /var/cache/apt/archives/lock
```

See if that solves your problem.

---

### Post by xaxas on 2007-12-29
Allmost the same :((

```
xaxas@cybertron:~$ sudo apt-get install kino
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bochsbios vgabios libares0
Use 'apt-get autoremove' to remove them.
Suggested packages:
  vorbis-tools sox mjpegtools lame
The following NEW packages will be installed:
  kino
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4354kB of archives.
After unpacking 9495kB of additional disk space will be used.
dpkg: unable to stat triggers deferred file `/var/lib/dpkg/triggers/Unincorp': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by mali2297 on 2007-12-29
Try
```

sudo apt-get clean
sudo apt-get update

```

---

### Post by xaxas on 2007-12-29
the same
:((

yeah, i kno it's ```
sudo apt-get update
```

---

### Post by gunja99 on 2007-12-29
Do you have x running and the update manager there is reporting there is available updates, if so update from here. U seem to have rebooted, and therefore it's a strange problem

---

### Post by mali2297 on 2007-12-29
OK, try moving the problematic file.
```

sudo mv /var/lib/dpkg/triggers/Unicorp /var/backups/Unicorp.bak

```

If it does not help, you can move it back with
```

sudo mv /var/backups/Unicorp.bak /var/lib/dpkg/triggers/Unicorp

```

---

### Post by xaxas on 2007-12-29
just re-rebooted and no change :(
Only thing x is sleeping and it's the x-sesssion-manager :((

the ```
sudo mv /var/lib/dpkg/triggers/Unicorp /var/backups/Unicorp.bak
```
says this :( ```
mv: cannot stat `/var/lib/dpkg/triggers/Unicorp': No such file or directory
```

also this happens
```
xaxas@cybertron:~$ /var/lib/dpkg/triggers/Unincorp
bash: /var/lib/dpkg/triggers/Unincorp: Permission denied
```

---

### Post by mali2297 on 2007-12-29
Post the output of
```

ls -l /var/lib/dpkg/triggers

```

Do you use Automatix?

---

### Post by xaxas on 2007-12-29
```
xaxas@cybertron:~$ ls -l /var/lib/dpkg/triggers
total 8
-rw-r--r-- 1 root root  6 2007-12-22 00:16 ldconfig
-rw------- 1 root root  0 2007-12-29 22:00 Lock
-rw-r--r-- 1 root root 16 2007-10-16 02:17 update-initramfs
?--------- ? ?    ?     ?                ? /var/lib/dpkg/triggers/Unincorp

```

I installed automatix but never installed anything with it ...

I am runing Gutsy on a Intel Core2 Duo E6750 2,66 GHz processor with Asus P5B SE mainboard and nvidia 8600GT

---

### Post by mali2297 on 2007-12-29
> **xaxas said:**
> ```
xaxas@cybertron:~$ ls -l /var/lib/dpkg/triggers
total 8
-rw-r--r-- 1 root root  6 2007-12-22 00:16 ldconfig
-rw------- 1 root root  0 2007-12-29 22:00 Lock
-rw-r--r-- 1 root root 16 2007-10-16 02:17 update-initramfs
?--------- ? ?    ?     ?                ? /var/lib/dpkg/triggers/Unincorp

```

I installed automatix but never installed anything with it ...

I am runing Gutsy on a Intel Core2 Duo E6750 2,66 GHz processor with Asus P5B SE mainboard and nvidia 8600GT

That looks really strange. :-k

Try
```

sudo rm /var/lib/dpkg/triggers/Unincorp

```

---

### Post by xaxas on 2007-12-30
Now thhe error is (1) not (2) :((
```
xaxas@cybertron:~$ sudo rm /var/lib/dpkg/triggers/Unincorp
[sudo] password for xaxas:
xaxas@cybertron:~$ sudo apt-get install kinoReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bochsbios vgabios libares0
Use 'apt-get autoremove' to remove them.
Suggested packages:
  vorbis-tools sox mjpegtools lame
The following NEW packages will be installed:
  kino
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4354kB of archives.
After unpacking 9495kB of additional disk space will be used.
Selecting previously deselected package kino.
(Reading database ... dpkg: error processing /var/cache/apt/archives/kino_1.1.0-3ubuntu2_i386.deb (--unpack):
 unable to open files list file for package `ffmpeg': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/kino_1.1.0-3ubuntu2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

And with the Synaptic I get this:
[[IMG]http://img201.imageshack.us/img201/7388/screenshotzw3.th.png[/IMG]](http://img201.imageshack.us/my.php?image=screenshotzw3.png)

---

### Post by mali2297 on 2007-12-30
Try this again
```

sudo apt-get clean
sudo apt-get update

```

When you get an error about dpkg not being able to read some file, try (re)moving the file in question. It seems to get you one step further each time.

---

### Post by xaxas on 2007-12-30
```
xaxas@cybertron:~$ sudo apt-get clean
[sudo] password for xaxas:
xaxas@cybertron:~$ sudo apt-get update
Get:1 http://archive.canonical.com gutsy Release.gpg [191B]
Ign http://archive.canonical.com gutsy/partner Translation-en_US               
Get:2 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US           
Get:3 http://archive.ubuntu.com gutsy Release.gpg [191B]                       
Ign http://archive.ubuntu.com gutsy/main Translation-en_US                     
Hit http://archive.canonical.com gutsy Release                                 
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com gutsy-security Release                
Ign http://archive.ubuntu.com gutsy/universe Translation-en_US       
Ign http://archive.ubuntu.com gutsy/restricted Translation-en_US   
Ign http://archive.ubuntu.com gutsy/multiverse Translation-en_US   
Get:4 http://archive.ubuntu.com gutsy-backports Release.gpg [191B] 
Ign http://archive.ubuntu.com gutsy-backports/main Translation-en_US
Ign http://archive.ubuntu.com gutsy-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com gutsy-backports/universe Translation-en_US
Ign http://archive.ubuntu.com gutsy-backports/multiverse Translation-en_US
Get:5 http://www.getautomatix.com gutsy Release.gpg [189B]                     
Ign http://www.getautomatix.com gutsy/main Translation-en_US                   
Get:6 http://archive.ubuntu.com gutsy-updates Release.gpg [191B]               
Ign http://archive.ubuntu.com gutsy-updates/main Translation-en_US  
Ign http://archive.ubuntu.com gutsy-updates/restricted Translation-en_US       
Ign http://archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Hit http://archive.ubuntu.com gutsy Release                          
Hit http://archive.ubuntu.com gutsy-backports Release                
Hit http://archive.canonical.com gutsy/partner Packages                        
Hit http://security.ubuntu.com gutsy-security/main Packages                    
Hit http://archive.ubuntu.com gutsy-updates Release                            
Hit http://archive.canonical.com gutsy/partner Sources                         
Hit http://www.getautomatix.com gutsy Release                                  
Hit http://security.ubuntu.com gutsy-security/restricted Packages    
Hit http://security.ubuntu.com gutsy-security/universe Packages    
Hit http://security.ubuntu.com gutsy-security/multiverse Packages  
Hit http://archive.ubuntu.com gutsy/main Packages                  
Hit http://archive.ubuntu.com gutsy/universe Packages
Hit http://archive.ubuntu.com gutsy/restricted Packages
Hit http://archive.ubuntu.com gutsy/multiverse Packages
Hit http://archive.ubuntu.com gutsy-backports/main Packages
Hit http://archive.ubuntu.com gutsy-backports/restricted Packages
Hit http://archive.ubuntu.com gutsy-backports/universe Packages
Hit http://archive.ubuntu.com gutsy-backports/multiverse Packages
Hit http://www.getautomatix.com gutsy/main Packages
Hit http://archive.ubuntu.com gutsy-updates/main Packages
Hit http://archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://archive.ubuntu.com gutsy-updates/universe Packages
Hit http://archive.ubuntu.com gutsy-updates/multiverse Packages
Fetched 6B in 0s (7B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
xaxas@cybertron:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
xaxas@cybertron:~$ sudo -i
root@cybertron:~# dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
/usr/sbin/update-initramfs: 515: awk: Input/output error
dpkg: subprocess post-installation script returned error exit status 127

```

---

### Post by mali2297 on 2007-12-30
OK, I am running out of ideas... :-k

Try
```

sudo touch /var/lib/dpkg/triggers/Unincorp
sudo chmod a+r /var/lib/dpkg/triggers/Unincorp
sudo dpkg --configure -a

```

Also, post the output of
```

cat -n /usr/sbin/update-initramfs | grep -A10 510

```

---

### Post by meindian523 on 2007-12-30
Um,is it Uni **[COLOR="Red"]n[/COLOR]** corp or Unicorp?

---

### Post by xaxas on 2007-12-30
tryed both ways :((

```

xaxas@cybertron:~$ sudo touch /var/lib/dpkg/triggers/Unincorp
[sudo] password for xaxas:
xaxas@cybertron:~$ sudo chmod a+r /var/lib/dpkg/triggers/Unincorp
xaxas@cybertron:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
/usr/sbin/update-initramfs: 515: awk: Input/output error
dpkg: subprocess post-installation script returned error exit status 127
xaxas@cybertron:~$ sudo chmod a+r /var/lib/dpkg/triggers/Unicorp
chmod: cannot access `/var/lib/dpkg/triggers/Unicorp': No such file or directory
xaxas@cybertron:~$ sudo touch /var/lib/dpkg/triggers/Unicorp
xaxas@cybertron:~$ sudo chmod a+r /var/lib/dpkg/triggers/Unicorp
xaxas@cybertron:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
/usr/sbin/update-initramfs: 515: awk: Input/output error
dpkg: subprocess post-installation script returned error exit status 127

```

---

### Post by mali2297 on 2007-12-30
I think you misspelled it in your first post and that it is *Unincorp*. I use Feisty so I can't check, I do not even have a *triggers* directory. That is also why I am curious about the line 515 in /usr/sbin/update-initramfs, please post the output of
```

cat -n /usr/sbin/update-initramfs | grep -A10 510

```

---

### Post by xaxas on 2007-12-30
```
xaxas@cybertron:~$ cat -n /usr/sbin/update-initramfs | grep -A10 510
   510                  delete
   511                  ;;
   512          u)
   513                  update
   514                  ;;
   515  esac
xaxas@cybertron:~$ 

```

---

### Post by mali2297 on 2007-12-31
I am sorry, but I do not think that I can help you any further. :-|

I suggest that you either [report a bug]("http://www.ubuntu.com/community/ReportProblem") or simply reinstall Ubuntu.

---

### Post by xaxas on 2007-12-31
How do u reinstall ubuntu ?
Does it have a reinstall function like Windows or do i have to format and loose everything :(

---

### Post by mali2297 on 2007-12-31
> **xaxas said:**
> 
Does it have a reinstall function like Windows or do i have to format and loose everything :(

No, you will have to do a clean new installation. It is at times like these that you wish you had a separate home partition. You can still setup one before you reinstall, see for example
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

With a little luck, you will then preserve your personal data. It is still advisable to backup things that are important to you.

Happy new year.
/Martin

---

