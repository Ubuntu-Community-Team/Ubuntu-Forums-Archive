---
title: "Software Updater MySQL failure after installing Percona MySQL"
date: 2014-02-07
forum: General Help
---

### Post by hawstom on 2014-02-07
I successfully installed Percona's MySQL 5.6 using an AppArmor force command, which resolved a package conflict between Percona's MySQL 5.6 and the standard Ubuntu MySQL 5.5

```
sudo apt-get -f install -o Dpkg::Options::="--force-overwrite"

```

But now Ubuntu Software Updater fails trying to update MySQL 5.5.  How can I get this to stop?  Can I get the updater to stop tryiing to update MySQL 5.5?  I am anxious to work with somebody to resolve this Software Updater problem.

Tom

---

### Post by ubudog on 2014-02-07
Try running the command:
```
sudo dpkg --configure -a
```

---

### Post by hawstom on 2014-02-11
Thank you very much for your reply.  I did as you suggested, and the Software Updater appeared this morning as shown:

[FONT=Courier New]```
Software Updater

Updated software is available for this computer.  Do you 
want to install it now?

* Details of updates
    | Install                                    | Download
---------------------------------------------------------------------
    X Security updates                             1.9 MB
        X MySQL database core client libraries     1.9 MB

---------------------------------------------------------------------
The update has already been downloaded

```[/FONT]

It looks like the system is still trying to update MySQL 5.5.

---

### Post by ubudog on 2014-02-11
Could you post the output of:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by hawstom on 2014-02-11
Thank you so much for hanging with me on this issue, ubudog!

Errors were encountered while processing:
 /var/cache/apt/archives/mysql-client-core-5.5_5.5.35-0ubuntu0.13.10.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

The output is long.  I hope this is all of it.
```

Get:1 http://dl.google.com stable Release.gpg [198 B]                                                                                                                           
Ign http://us.archive.ubuntu.com saucy InRelease                                                                    
Get:2 http://dl.google.com stable Release [1,347 B]                                                              
Ign http://archive.canonical.com saucy InRelease                                                                    
Ign http://extras.ubuntu.com saucy InRelease                                               
Hit http://repo.percona.com saucy/main Sources                                             
Ign http://us.archive.ubuntu.com saucy-updates InRelease                                   
Get:3 http://dl.google.com stable/main i386 Packages [758 B]                                                     
Ign http://us.archive.ubuntu.com saucy-security InRelease                                                                                
Hit http://repo.percona.com saucy/main i386 Packages                                                              
Hit http://archive.canonical.com saucy Release.gpg                                                                
Get:4 http://extras.ubuntu.com saucy Release.gpg [72 B]                                                           
Hit http://us.archive.ubuntu.com saucy Release.gpg                                          
Hit http://archive.canonical.com saucy Release                                                                    
Hit http://extras.ubuntu.com saucy Release                                                                         
Get:5 http://us.archive.ubuntu.com saucy-updates Release.gpg [933 B]                                               
Get:6 http://us.archive.ubuntu.com saucy-security Release.gpg [933 B]                                              
Hit http://archive.canonical.com saucy/partner Sources                                                            
Hit http://extras.ubuntu.com saucy/main Sources                                                                   
Hit http://us.archive.ubuntu.com saucy Release                                              
Hit http://archive.canonical.com saucy/partner i386 Packages                                                                             
Hit http://extras.ubuntu.com saucy/main i386 Packages                                                            
Ign http://dl.google.com stable/main Translation-en_GB                                                           
Get:7 http://us.archive.ubuntu.com saucy-updates Release [49.6 kB]                                               
Ign http://dl.google.com stable/main Translation-en                                                                          
Ign http://repo.percona.com saucy/main Translation-en_GB                                                             
Get:8 http://us.archive.ubuntu.com saucy-security Release [49.6 kB]                         
Ign http://repo.percona.com saucy/main Translation-en                                          
Hit http://us.archive.ubuntu.com saucy/main i386 Packages                                      
Hit http://us.archive.ubuntu.com saucy/restricted i386 Packages       
Hit http://us.archive.ubuntu.com saucy/universe i386 Packages         
Hit http://us.archive.ubuntu.com saucy/multiverse i386 Packages       
Hit http://us.archive.ubuntu.com saucy/main Translation-en_GB         
Hit http://us.archive.ubuntu.com saucy/main Translation-en            
Hit http://us.archive.ubuntu.com saucy/multiverse Translation-en_GB   
Hit http://us.archive.ubuntu.com saucy/multiverse Translation-en      
Hit http://us.archive.ubuntu.com saucy/restricted Translation-en_GB   
Ign http://archive.canonical.com saucy/partner Translation-en_GB      
Hit http://us.archive.ubuntu.com saucy/restricted Translation-en
Ign http://extras.ubuntu.com saucy/main Translation-en_GB
Ign http://archive.canonical.com saucy/partner Translation-en
Hit http://us.archive.ubuntu.com saucy/universe Translation-en_GB
Ign http://extras.ubuntu.com saucy/main Translation-en
Hit http://us.archive.ubuntu.com saucy/universe Translation-en
Get:9 http://us.archive.ubuntu.com saucy-updates/main i386 Packages [200 kB]
Get:10 http://us.archive.ubuntu.com saucy-updates/restricted i386 Packages [14 B]
Get:11 http://us.archive.ubuntu.com saucy-updates/universe i386 Packages [148 kB]
Get:12 http://us.archive.ubuntu.com saucy-updates/multiverse i386 Packages [1,777 B]
Hit http://us.archive.ubuntu.com saucy-updates/main Translation-en_GB
Get:13 http://us.archive.ubuntu.com saucy-updates/main Translation-en [94.1 kB]
Hit http://us.archive.ubuntu.com saucy-updates/multiverse Translation-en_GB
Hit http://us.archive.ubuntu.com saucy-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com saucy-updates/restricted Translation-en_GB
Hit http://us.archive.ubuntu.com saucy-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com saucy-updates/universe Translation-en_GB
Get:14 http://us.archive.ubuntu.com saucy-updates/universe Translation-en [75.5 kB]
Get:15 http://us.archive.ubuntu.com saucy-security/main i386 Packages [80.7 kB]                                                                                                 
Get:16 http://us.archive.ubuntu.com saucy-security/restricted i386 Packages [14 B]                                                                                              
Get:17 http://us.archive.ubuntu.com saucy-security/universe i386 Packages [31.9 kB]                                                                                             
Get:18 http://us.archive.ubuntu.com saucy-security/multiverse i386 Packages [1,385 B]                                                                                           
Get:19 http://us.archive.ubuntu.com saucy-security/main Translation-en [43.4 kB]                                                                                                
Hit http://us.archive.ubuntu.com saucy-security/multiverse Translation-en                                                                                                       
Hit http://us.archive.ubuntu.com saucy-security/restricted Translation-en                                                                                                       
Get:20 http://us.archive.ubuntu.com saucy-security/universe Translation-en [19.3 kB]                                                                                            
Ign http://us.archive.ubuntu.com saucy-security/main Translation-en_GB                                                                                                          
Ign http://us.archive.ubuntu.com saucy-security/multiverse Translation-en_GB                                                                                                    
Ign http://us.archive.ubuntu.com saucy-security/restricted Translation-en_GB                                                                                                    
Ign http://us.archive.ubuntu.com saucy-security/universe Translation-en_GB                                                                                                      
Fetched 799 kB in 9s (85.9 kB/s)                                                                                                                                                
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  espeak espeak-data firefox firefox-globalmenu firefox-locale-en google-talkplugin libavcodec53 libavformat53 libavutil51 libespeak1 libgadu3 libpostproc52 libswscale2
  mysql-client-core-5.5
14 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 47.2 MB/49.1 MB of archives.
After this operation, 1,101 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://dl.google.com/linux/talkplugin/deb/ stable/main google-talkplugin i386 5.1.4.0-1 [11.4 MB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ saucy-updates/main libavutil51 i386 6:0.8.10-0ubuntu0.13.10.1 [62.6 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ saucy-updates/main libavcodec53 i386 6:0.8.10-0ubuntu0.13.10.1 [2,484 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ saucy-updates/main libavformat53 i386 6:0.8.10-0ubuntu0.13.10.1 [458 kB]                                                             
Get:5 http://us.archive.ubuntu.com/ubuntu/ saucy-updates/main libespeak1 i386 1.47.11-1ubuntu0.1 [151 kB]                                                                       
Get:6 http://us.archive.ubuntu.com/ubuntu/ saucy-updates/main espeak-data i386 1.47.11-1ubuntu0.1 [991 kB]                                                                      
Get:7 http://us.archive.ubuntu.com/ubuntu/ saucy-updates/main libpostproc52 i386 6:0.8.10-0ubuntu0.13.10.1 [33.7 kB]                                                            
Get:8 http://us.archive.ubuntu.com/ubuntu/ saucy-updates/main libswscale2 i386 6:0.8.10-0ubuntu0.13.10.1 [83.1 kB]                                                              
Get:9 http://us.archive.ubuntu.com/ubuntu/ saucy-updates/main espeak i386 1.47.11-1ubuntu0.1 [68.2 kB]                                                                          
Get:10 http://us.archive.ubuntu.com/ubuntu/ saucy-updates/main firefox i386 27.0+build1-0ubuntu0.13.10.1 [30.8 MB]                                                              
Get:11 http://us.archive.ubuntu.com/ubuntu/ saucy-updates/main firefox-globalmenu i386 27.0+build1-0ubuntu0.13.10.1 [8,960 B]                                                   
Get:12 http://us.archive.ubuntu.com/ubuntu/ saucy-updates/main firefox-locale-en i386 27.0+build1-0ubuntu0.13.10.1 [608 kB]                                                     
Get:13 http://us.archive.ubuntu.com/ubuntu/ saucy-updates/main libgadu3 i386 1:1.11.2-1ubuntu1.1 [72.2 kB]                                                                      
Fetched 47.2 MB in 1min 16s (613 kB/s)                                                                                                                                          
(Reading database ... 318540 files and directories currently installed.)
Preparing to replace libavutil51:i386 6:0.8.9-0ubuntu0.13.10.1 (using .../libavutil51_6%3a0.8.10-0ubuntu0.13.10.1_i386.deb) ...
Unpacking replacement libavutil51:i386 ...
Preparing to replace libavcodec53:i386 6:0.8.9-0ubuntu0.13.10.1 (using .../libavcodec53_6%3a0.8.10-0ubuntu0.13.10.1_i386.deb) ...
Unpacking replacement libavcodec53:i386 ...
Preparing to replace libavformat53:i386 6:0.8.9-0ubuntu0.13.10.1 (using .../libavformat53_6%3a0.8.10-0ubuntu0.13.10.1_i386.deb) ...
Unpacking replacement libavformat53:i386 ...
Preparing to replace libespeak1:i386 1.47.11-1 (using .../libespeak1_1.47.11-1ubuntu0.1_i386.deb) ...
Unpacking replacement libespeak1:i386 ...
Preparing to replace espeak-data:i386 1.47.11-1 (using .../espeak-data_1.47.11-1ubuntu0.1_i386.deb) ...
Unpacking replacement espeak-data:i386 ...
Preparing to replace libpostproc52:i386 6:0.8.9-0ubuntu0.13.10.1 (using .../libpostproc52_6%3a0.8.10-0ubuntu0.13.10.1_i386.deb) ...
Unpacking replacement libpostproc52:i386 ...
Preparing to replace libswscale2:i386 6:0.8.9-0ubuntu0.13.10.1 (using .../libswscale2_6%3a0.8.10-0ubuntu0.13.10.1_i386.deb) ...
Unpacking replacement libswscale2:i386 ...
Preparing to replace espeak 1.47.11-1 (using .../espeak_1.47.11-1ubuntu0.1_i386.deb) ...
Unpacking replacement espeak ...
Preparing to replace firefox 26.0+build2-0ubuntu0.13.10.2 (using .../firefox_27.0+build1-0ubuntu0.13.10.1_i386.deb) ...
Unpacking replacement firefox ...
Preparing to replace firefox-globalmenu 26.0+build2-0ubuntu0.13.10.2 (using .../firefox-globalmenu_27.0+build1-0ubuntu0.13.10.1_i386.deb) ...
Unpacking replacement firefox-globalmenu ...
Preparing to replace firefox-locale-en 26.0+build2-0ubuntu0.13.10.2 (using .../firefox-locale-en_27.0+build1-0ubuntu0.13.10.1_i386.deb) ...
Unpacking replacement firefox-locale-en ...
Preparing to replace google-talkplugin 4.9.1.0-1 (using .../google-talkplugin_5.1.4.0-1_i386.deb) ...
Unpacking replacement google-talkplugin ...
Preparing to replace libgadu3 1:1.11.2-1ubuntu1 (using .../libgadu3_1%3a1.11.2-1ubuntu1.1_i386.deb) ...
Unpacking replacement libgadu3 ...
Preparing to replace mysql-client-core-5.5 5.5.34-0ubuntu0.13.10.1 (using .../mysql-client-core-5.5_5.5.35-0ubuntu0.13.10.2_i386.deb) ...
Unpacking replacement mysql-client-core-5.5 ...
dpkg: error processing /var/cache/apt/archives/mysql-client-core-5.5_5.5.35-0ubuntu0.13.10.2_i386.deb (--unpack):
 trying to overwrite '/usr/bin/mysql', which is also in package percona-server-client-5.6 5.6.15-rel63.0-519.saucy
No apport report written because MaxReports has already been reached
                                                                    dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for doc-base ...
Processing 1 changed doc-base file...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus ...
Processing triggers for mime-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-client-core-5.5_5.5.35-0ubuntu0.13.10.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by ubudog on 2014-02-11
Hey,

Try the solution from [this]("http://ubuntuforums.org/showthread.php?t=1930919&page=2&p=11715547#post11715547") post.

---

### Post by hawstom on 2014-02-13
Thank you for following up with this answer!  I removed the following lines from /var/lib/dpkg/status . the next time I started Software Updater, MySQL was not on the list.  When I clicked Install, Software Updater finished successfully.  You did it!  Thank you so much.  I could not have done this without this help.

```

Package: mysql-client-core-5.5
Status: install ok installed
Priority: optional
Section: database
Installed-Size: 6554
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: mysql-5.5
Version: 5.5.34-0ubuntu0.13.10.1
Replaces: mysql-client (<< 5.5.34-0ubuntu0.13.10.1), mysql-client-5.0, mysql-client-core-5.1
Depends: libc6 (>= 2.4), libgcc1 (>= 1:4.1.1), libreadline6 (>= 6.0), zlib1g (>= 1:1.1.4)
Breaks: mysql-client (<< 5.5.34-0ubuntu0.13.10.1), mysql-client-5.0, mysql-client-core-5.1
Description: MySQL database core client binaries
 MySQL is a fast, stable and true multi-user, multi-threaded SQL database
 server. SQL (Structured Query Language) is the most popular database query
 language in the world. The main goals of MySQL are speed, robustness and
 ease of use.
 .
 This package includes the core client files, as used by Akonadi.
Homepage: http://dev.mysql.com/
Original-Maintainer: Debian MySQL Maintainers <pkg-mysql-maint@lists.alioth.debian.org>

```

---

### Post by ubudog on 2014-02-13
Awesome!  Glad it worked.

---

