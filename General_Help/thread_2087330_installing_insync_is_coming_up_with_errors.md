---
title: "installing insync is coming up with errors"
date: 2012-11-23
forum: General Help
---

### Post by sdowney717 on 2012-11-23
[https://www.insynchq.com/linux](https://www.insynchq.com/linux)

I tried their method with editing the source list  and also the direct deb downloads 
I am running gnome3 and cinnamon .
any one care to try  and see what is up with this?

---

### Post by sdowney717 on 2012-11-23
trying with a different set of instructions and still errors!
this site did have a working key add command

[http://handytutorial.com/install-insync-in-ubuntu-12-0412-10-from-official-repository/](http://handytutorial.com/install-insync-in-ubuntu-12-0412-10-from-official-repository/)

```
scott@scott-P5QC:~$ wget -O - https://d2t3ff60b2tol4.cloudfront.net/services@insynchq.com.gpg.key | sudo apt-key add -
--2012-11-23 10:03:13--  https://d2t3ff60b2tol4.cloudfront.net/services@insynchq.com.gpg.key
Resolving d2t3ff60b2tol4.cloudfront.net (d2t3ff60b2tol4.cloudfront.net)... 216.137.33.17, 216.137.33.22, 216.137.33.23, ...
Connecting to d2t3ff60b2tol4.cloudfront.net (d2t3ff60b2tol4.cloudfront.net)|216.137.33.17|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 11965 (12K) [application/octet-stream]
Saving to: `STDOUT'

100%[======================================>] 11,965      --.-K/s   in 0.02s   

2012-11-23 10:03:13 (547 KB/s) - written to stdout [11965/11965]

OK
scott@scott-P5QC:~$ sudo apt-get update
Ign http://apt.insynchq.com precise InRelease
Ign http://us.archive.ubuntu.com precise InRelease                             
Ign http://us.archive.ubuntu.com precise-updates InRelease                     
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Hit http://us.archive.ubuntu.com precise-updates Release.gpg                   
Get:1 http://apt.insynchq.com precise Release.gpg [490 B]                      
Hit http://us.archive.ubuntu.com precise Release                               
Hit http://apt.insynchq.com precise Release                                    
Ign http://extras.ubuntu.com precise InRelease                                 
Hit http://us.archive.ubuntu.com precise-updates Release                       
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://dl.google.com stable InRelease                                      
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://dl.google.com stable InRelease                                      
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Ign http://archive.canonical.com precise InRelease                             
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Hit http://us.archive.ubuntu.com precise-updates/main Sources                  
Hit http://us.archive.ubuntu.com precise-updates/restricted Sources            
Hit http://us.archive.ubuntu.com precise-updates/universe Sources              
Hit http://us.archive.ubuntu.com precise-updates/multiverse Sources            
Ign http://dl.google.com stable InRelease                                      
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://security.ubuntu.com precise-security Release.gpg                    
Hit http://us.archive.ubuntu.com precise-updates/main i386 Packages            
Hit http://us.archive.ubuntu.com precise-updates/restricted i386 Packages      
Hit http://us.archive.ubuntu.com precise-updates/universe i386 Packages        
Hit http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages      
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://dl.google.com stable Release.gpg                                    
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://extras.ubuntu.com precise Release                                   
Hit http://security.ubuntu.com precise-security Release                        
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Ign http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://archive.canonical.com precise Release                               
Hit http://dl.google.com stable Release.gpg                                    
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://security.ubuntu.com precise-security/main Sources                   
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://archive.canonical.com precise/partner i386 Packages                 
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://dl.google.com stable Release.gpg                                    
Hit http://security.ubuntu.com precise-security/restricted Sources             
Hit http://security.ubuntu.com precise-security/universe Sources               
Hit http://security.ubuntu.com precise-security/multiverse Sources             
Hit http://security.ubuntu.com precise-security/main i386 Packages             
Hit http://security.ubuntu.com precise-security/restricted i386 Packages       
Ign http://ppa.launchpad.net precise Release                                   
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://security.ubuntu.com precise-security/universe i386 Packages         
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages       
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Hit http://dl.google.com stable Release                                        
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://dl.google.com stable Release                                        
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://dl.google.com stable Release                                        
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://dl.google.com stable/main TranslationIndex                          
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://archive.canonical.com precise/partner Translation-en_US   
Ign http://archive.canonical.com precise/partner Translation-en      
Err http://ppa.launchpad.net precise/main Sources                         
  404  Not Found
Err http://ppa.launchpad.net precise/main i386 Packages                   
  404  Not Found
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://dl.google.com stable/main Translation-en_US
Ign http://dl.google.com stable/main Translation-en
Ign http://dl.google.com stable/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://dl.google.com stable/main Translation-en
Ign http://dl.google.com stable/main Translation-en_US
Ign http://dl.google.com stable/main Translation-en
Fetched 490 B in 2s (177 B/s)
W: Failed to fetch http://apt.insynchq.com/ubuntu/dists/precise/Release  Unable to find expected entry 'non-free/source/Sources' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://ppa.launchpad.net/mozillateam/ppa/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/mozillateam/ppa/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
scott@scott-P5QC:~$ sudo apt-get install insync-beta-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  insync-beta-gnome-cinnamon-common
The following NEW packages will be installed:
  insync-beta-gnome insync-beta-gnome-cinnamon-common
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B/6,881 kB of archives.
After this operation, 18.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 658286 files and directories currently installed.)
Unpacking insync-beta-gnome-cinnamon-common (from .../insync-beta-gnome-cinnamon-common_0.9.25_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/insync-beta-gnome-cinnamon-common_0.9.25_i386.deb (--unpack):
 trying to overwrite '/usr/bin/insync', which is also in package insync-beta-ubuntu 0.9.19
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Selecting previously unselected package insync-beta-gnome.
Unpacking insync-beta-gnome (from .../insync-beta-gnome_0.9.27_all.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/insync-beta-gnome-cinnamon-common_0.9.25_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
scott@scott-P5QC:~$ 

```

---

### Post by sdowney717 on 2012-11-23
picture in synaptic

---

### Post by SlugSlug on 2012-11-23
I think you missed the non-free bit out when adding repo

deb [http://apt.insynchq.com/](http://apt.insynchq.com/)[DISTRIBUTION] [CODENAME] non-free


you may also want to remove those mozilla repos - they are not up to date

---

### Post by sdowney717 on 2012-11-23
I also found out I already had it installed or what?
which I vaguely recall. Hey am I confused or what!:)
No idea what I have already done somehow.

Anyway it seems to be working?? links my google drive account with nautilus

the circular icon in the folder means it is syncing, check marks mean synced. Although dont know if it means duplications exist on my hard drive?

If I upload to gdrive, does it then download the same onto my PC?
If I delete from insync folder, does it delete from google drive?
If I copy picture to insync folder, does it copy to google drive?

to get the pic, I clicked on insync application which authorized my google drive account with insync usage.

---

### Post by SlugSlug on 2012-11-23
dunno. I use ubuntu one ;)

---

### Post by sdowney717 on 2012-11-23
does ubuntu one make duplicate copy of synced files on your PC or do you tell it which folders to sync?

Google drive I think i get 4gb free.

after a few minutes, all my insync google drive icons have the check mark.

---

### Post by SlugSlug on 2012-11-23
by default you get a ubuntuone folder in your home folder that is sync'd with any pc that uses your credentials. You can add other folders or files and you get 5gig.

Delete a file on one pc and it's deleted off them all

---

### Post by sdowney717 on 2012-11-23
interesting about syncing with another PC.

So I could have my daughters win7 laptop setup with ubuntu one and mine on the same account and can share picture files easily?

anymore details on this for login? I am setting up ubuntu one for me right now.

ubuntuone is taking long time to do something

they dont tell you but I let it run for 5 minutes then I just click next and have a list of folders to sync.
Will those folder names sync to win7 PC? and create if they dont exist?

---

### Post by sdowney717 on 2012-11-23
got an error using ubuntu one.
I selected my picture folder 1.3gb
I created a folder called ubuntu1sync

any ideas?

---

### Post by SlugSlug on 2012-11-23
not sure what that is. Just try get one folder working first (default is ubuntuone)

---

### Post by sdowney717 on 2012-11-23
it may actually be working, I went back and clicked ubuntu 1 icon and it says 6% for syncing.

---

### Post by sdowney717 on 2012-11-23
added ubuntu one indicator applet.
you can see the progress and status.
open the control panel
nice!

[http://www.omgubuntu.co.uk/2012/04/ubuntu-one-indicator-applet-adds-new-features](http://www.omgubuntu.co.uk/2012/04/ubuntu-one-indicator-applet-adds-new-features)

---

### Post by sdowney717 on 2012-11-23
Insync
to make the indicator applet appear I have to run 
insync in terminal
I suppose you could start this up automatically.

Test
I restarted PC
added a file to my Insync folder
run the insync program
It synced the file to google drive.

I will do some testing to see what it does while running.

```
scott@scott-P5QC:~$ insync
OK: gdata imported
importing client...
loading client...
importing core1...
importing core2...
importing core3...
importing core4...
importing core utils...
importing gevent itc...
importing std libs...
OK
<module 'isyncd.client' from '/usr/lib/insync/library.zip/isyncd/client.pyc'>
/usr/lib/insync
C functions loaded: 0
C functions failed: 0
/usr/lib/insync
C functions loaded: 3645
C functions failed: 589
('Applet', <linux.indicator_applet.Applet object at 0xa3f536c>)
<class 'isyncd.client.ClientListener'>
importing clientenv...
<module 'isyncd.clientenv' from '/usr/lib/insync/library.zip/isyncd/clientenv.pyc'>
/usr/lib/insync
[ falling back to loading from current process ]
[[dynamic library loaded: ]]
C functions loaded: 4
C functions failed: 0
/usr/lib/insync
[ falling back to loading from current process ]
[[dynamic library loaded: ]]
C functions loaded: 101
C functions failed: 0
<module 'linux.fsimpl' from '/usr/lib/insync/library.zip/linux/fsimpl.pyc'>
running __main__
loading.........
<linux.fsimpl.LinuxFSImpl object at 0xca980ec>
<linux.platform_impl.LinuxClientPlatform object at 0xa15f4cc>
<isyncd.clientenv.ClientEnvironment object at 0xca8c3ec>
<__main__.LinuxListener object at 0xca832cc>
calling client init
creating client state...
client state ok
1
2
('set startup setting :: is_auto_start', True)
client - config loaded
client - init db
client init complete
[client created] <isyncd.client.Client object at 0xca834cc>
--start - [unix socket server thread]
starting client...
importing gevent...
running mainloop...
starting applet mainloop
____________ LinuxFSWatcher - calling "_init" _________________
______________ LinuxFSWatcher - calling "_start" _________________
('new watch', u'/home/scott/Insync')
('new watch', u'/home/scott/Insync/sdowney717@gmail.com')
('new watch', u'/home/scott/Insync/sdowney717@gmail.com/pdf test')
('new watch', u'/home/scott/Insync/sdowney717@gmail.com/pdf test/midi')
('new watch', u'/home/scott/Insync/sdowney717@gmail.com/wedding shower pictures')
('new watch', u'/home/scott/Insync/sdowney717@gmail.com/wedding shower pictures/28')
('new watch', u'/home/scott/Insync/sdowney717@gmail.com/house repairs')
('new watch', u'/home/scott/Insync/sdowney717@gmail.com/house repairs/08')
('new watch', u'/home/scott/Insync/sdowney717@gmail.com/house repairs/08/15')
('new watch', u'/home/scott/Insync/sdowney717@gmail.com/house repairs/08/05')
('new watch', u'/home/scott/Insync/sdowney717@gmail.com/house repairs/08/18')
('new watch', u'/home/scott/Insync/sdowney717@gmail.com/house repairs/08/11')
('new watch', u'/home/scott/Insync/sdowney717@gmail.com/house repairs/08/14')
('new watch', u'/home/scott/Insync/sdowney717@gmail.com/house repairs/08/07')
('new watch', u'/home/scott/Insync/sdowney717@gmail.com/house repairs/08/16')
('new watch', u'/home/scott/Insync/sdowney717@gmail.com/house repairs/08/13')
('new watch', u'/home/scott/Insync/sdowney717@gmail.com/house repairs/08/17')
('new watch', u'/home/scott/Insync/sdowney717@gmail.com/house repairs/08/12')
('new watch', u'/home/scott/Insync/sdowney717@gmail.com/house repairs/07')
('new watch', u'/home/scott/Insync/sdowney717@gmail.com/house repairs/07/10')
('new watch', u'/home/scott/Insync/sdowney717@gmail.com/house repairs/07/23')
('new watch', u'/home/scott/Insync/sdowney717@gmail.com/house repairs/07/14')
('new watch', u'/home/scott/Insync/sdowney717@gmail.com/house repairs/07/29')
('new watch', u'/home/scott/Insync/sdowney717@gmail.com/house repairs/07/26')
('new watch', u'/home/scott/Insync/sdowney717@gmail.com/house repairs/07/24')
('new watch', u'/home/scott/Insync/sdowney717@gmail.com/house repairs/07/21')
('new watch', u'/home/scott/Insync/sdowney717@gmail.com/house repairs/07/17')
('new watch', u'/home/scott/Insync/sdowney717@gmail.com/house repairs/07/30')
('new watch', u'/home/scott/Insync/sdowney717@gmail.com/odd stuff from hard drive')
('new watch', u'/home/scott/Insync/sdowney717@gmail.com/odd stuff from hard drive/fre')
('new watch', u'/home/scott/Insync/sdowney717@gmail.com/odd stuff from hard drive/lawnboy')
('new watch', u'/home/scott/Insync/sdowney717@gmail.com/odd stuff from hard drive/midi')
USING PYTHREAD INOTIFY
enter thread
-fswatch- starting sync loop
('on client state change', 'SYNCING')
(u'/home/scott/Insync/sdowney717@gmail.com/wedding shower pictures/28/Untitled_Screencast2.webm', 'SYNCING')
(u'/home/scott/Insync/sdowney717@gmail.com/wedding shower pictures/28', 'DES_SYNCING')
(u'/home/scott/Insync/sdowney717@gmail.com/wedding shower pictures', 'DES_SYNCING')
(u'/home/scott/Insync/sdowney717@gmail.com', 'DES_SYNCING')

(insync:24898): Gtk-WARNING **: Invalid icon size 24


(insync:24898): Gtk-WARNING **: Invalid icon size 24

('on client state change', 'SYNCED')
(u'/home/scott/Insync/sdowney717@gmail.com/wedding shower pictures/28/Untitled_Screencast2.webm', 'SYNCED')
(u'/home/scott/Insync/sdowney717@gmail.com/wedding shower pictures/28', 'SYNCED')
(u'/home/scott/Insync/sdowney717@gmail.com/wedding shower pictures', 'SYNCED')
(u'/home/scott/Insync/sdowney717@gmail.com', 'SYNCED')
('METHOD', 'quota:105248911187594415233')
('METHOD', u'activity:fs:sdowney717@gmail.com/wedding shower pictures/28/Untitled_Screencast2.webm')

(insync:24898): Gtk-WARNING **: Invalid icon size 24


(insync:24898): Gtk-WARNING **: Invalid icon size 24


(insync:24898): Gtk-WARNING **: Invalid icon size 24


(insync:24898): Gtk-WARNING **: Invalid icon size 24


```

---

### Post by sdowney717 on 2012-11-23
yes that works, deleted file in the insync folder, and it automatically deletes it in the google drive folder.

> ('<file moved out of watched dir>', u'/home/scott/Insync/sdowney717@gmail.com/wedding shower pictures/28/Untitled_Screencast2.webm', 5074)
('on client state change', 'SYNCING')
(u'/home/scott/Insync/sdowney717@gmail.com/wedding shower pictures/28', 'DES_SYNCING')
(u'/home/scott/Insync/sdowney717@gmail.com/wedding shower pictures', 'DES_SYNCING')
(u'/home/scott/Insync/sdowney717@gmail.com', 'DES_SYNCING')
('on client state change', 'SYNCED')
(u'/home/scott/Insync/sdowney717@gmail.com/wedding shower pictures/28', 'SYNCED')
(u'/home/scott/Insync/sdowney717@gmail.com/wedding shower pictures', 'SYNCED')
(u'/home/scott/Insync/sdowney717@gmail.com', 'SYNCED')
(u'/home/scott/Insync/sdowney717@gmail.com/wedding shower pictures/28', 'DES_SYNCING')
(u'/home/scott/Insync/sdowney717@gmail.com/wedding shower pictures', 'DES_SYNCING')
(u'/home/scott/Insync/sdowney717@gmail.com', 'DES_SYNCING')
('on client state change', 'SYNCING')
(u'/home/scott/Insync/sdowney717@gmail.com/wedding shower pictures/28', 'SYNCED')
(u'/home/scott/Insync/sdowney717@gmail.com/wedding shower pictures', 'SYNCED')
(u'/home/scott/Insync/sdowney717@gmail.com', 'SYNCED')
('on client state change', 'SYNCED')



---

### Post by sdowney717 on 2012-11-23
I found there is an insync icon you can click to run the applet. 
So you dont need terminal to do this.

So with both of these, I can automatically sync and web store  5gb  with google drive and 5 gb with ubuntu one for free.

---

### Post by jalirious on 2012-12-05
insync runs fine for me on 64b 12.04

* can link the google drives of however many google accounts you have (limitless cloud storage in 5gb pieces)

* need to add it to startup applications

* sudo ln -s /home/username/Insync /media/ext_hd/Insync

(limited storage space on my home partition)

---

### Post by sdowney717 on 2012-12-06
> sudo ln -s /home/username/Insync /media/ext_hd/Insync

What does that line do for you?

---

### Post by jalirious on 2013-02-01
That is a symbolic link. It's one way to get around that you can change the set directory of insync.

---

