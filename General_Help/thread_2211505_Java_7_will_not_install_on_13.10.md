---
title: "Java 7 will not install on 13.10"
date: 2014-03-16
forum: General Help
---

### Post by samwillc on 2014-03-16
I have tried the usual stuff:

[http://askubuntu.com/questions/126372/sha256sum-mismatch-jdk-7u3-linux-x64-tar-gz-error-when-trying-to-install-orac](http://askubuntu.com/questions/126372/sha256sum-mismatch-jdk-7u3-linux-x64-tar-gz-error-when-trying-to-install-orac)

On install:

```

Download done.
Removing outdated cached downloads...
sha256sum mismatch jdk-7u51-linux-x64.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

On sudo apt-get update:

```

W: GPG error: http://ppa.launchpad.net saucy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3766223989993A70
W: GPG error: http://ppa.launchpad.net saucy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3766223989993A70

```

I have installed oracle java 7 using the 'ppa:webupd8team/java' loads of times before and never had this issue. Any ideas? I need oracle 7 asap to do my work so an ever so slight panic going on. Thanks.

Sam.

---

### Post by r.stiltskin on 2014-03-16
sorry, that was wrong.  Will get back soon...

---

### Post by r.stiltskin on 2014-03-16
Did you follow the webupd8.org's [installation instructions]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html")?

What output did you get after running the first command
```

sudo add-apt-repository ppa:webupd8team/java
```

---

### Post by sammiev on 2014-03-16
> **r.stiltskin said:**
> Did you follow the webupd8.org's [installation instructions]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html")?

What output did you get after running the first command
```

sudo add-apt-repository ppa:webupd8team/java
```

+ 1 Works great here.

---

### Post by samwillc on 2014-03-16
I ended up reinstalling elementaryOS as ubuntu 13.10 crashed a few times (HUD crashed and a few cryptic internal errors), kept notifying me my bluetooth keyboard battery was low (??) and various other glitches. Possibly my hardware but for now I need something stable. However, same thing on fresh install:

```

Download done.
Removing outdated cached downloads...
sha256sum mismatch jdk-7u51-linux-x64.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up gsfonts-x11 (0.22) ...
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

No idea what's wrong! Entire thing here:

```

sam@sam-pc:~$ sudo add-apt-repository ppa:webupd8team/java
You are about to add the following PPA to your system:
 Oracle Java (JDK) Installer (automatically downloads and installs Oracle JDK6 / JDK7 / JDK8). There are no actual Java files in this PPA. More info: http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html

Debian installation instructions: http://www.webupd8.org/2012/06/how-to-install-oracle-java-7-in-debian.html
 More info: https://launchpad.net/~webupd8team/+archive/java
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmprwelJK/secring.gpg' created
gpg: keyring `/tmp/tmprwelJK/pubring.gpg' created
gpg: requesting key EEA14886 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmprwelJK/trustdb.gpg: trustdb created
gpg: key EEA14886: public key "Launchpad VLC" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
sam@sam-pc:~$ sudo apt-get update
Hit http://ppa.launchpad.net precise Release.gpg
Hit http://ppa.launchpad.net precise Release.gpg                              
Get:1 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Hit http://gb.archive.ubuntu.com precise Release.gpg                          
Hit http://gb.archive.ubuntu.com precise-updates Release.gpg                  
Hit http://gb.archive.ubuntu.com precise-backports Release.gpg                
Hit http://ppa.launchpad.net precise Release                                  
Hit http://gb.archive.ubuntu.com precise Release                              
Hit http://ppa.launchpad.net precise Release                                  
Hit http://gb.archive.ubuntu.com precise-updates Release                      
Get:2 http://ppa.launchpad.net precise Release [11.9 kB]                      
Hit http://gb.archive.ubuntu.com precise-backports Release                    
Hit http://gb.archive.ubuntu.com precise/main Sources                         
Hit http://gb.archive.ubuntu.com precise/restricted Sources                   
Hit http://gb.archive.ubuntu.com precise/universe Sources                     
Hit http://gb.archive.ubuntu.com precise/multiverse Sources                   
Hit http://gb.archive.ubuntu.com precise/main amd64 Packages                  
Hit http://ppa.launchpad.net precise/main Sources                             
Hit http://ppa.launchpad.net precise/main amd64 Packages              
Hit http://ppa.launchpad.net precise/main i386 Packages               
Ign http://ppa.launchpad.net precise/main TranslationIndex                    
Hit http://security.ubuntu.com precise-security Release.gpg                   
Hit http://gb.archive.ubuntu.com precise/restricted amd64 Packages    
Hit http://gb.archive.ubuntu.com precise/universe amd64 Packages      
Hit http://gb.archive.ubuntu.com precise/multiverse amd64 Packages    
Hit http://gb.archive.ubuntu.com precise/main i386 Packages           
Hit http://gb.archive.ubuntu.com precise/restricted i386 Packages     
Hit http://gb.archive.ubuntu.com precise/universe i386 Packages       
Hit http://gb.archive.ubuntu.com precise/multiverse i386 Packages     
Hit http://gb.archive.ubuntu.com precise/main TranslationIndex        
Hit http://gb.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources                     
Hit http://ppa.launchpad.net precise/main amd64 Packages              
Hit http://ppa.launchpad.net precise/main i386 Packages               
Ign http://ppa.launchpad.net precise/main TranslationIndex            
Hit http://gb.archive.ubuntu.com precise/restricted TranslationIndex  
Hit http://gb.archive.ubuntu.com precise/universe TranslationIndex    
Hit http://gb.archive.ubuntu.com precise-updates/main Sources         
Hit http://gb.archive.ubuntu.com precise-updates/restricted Sources   
Hit http://gb.archive.ubuntu.com precise-updates/universe Sources     
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Sources   
Hit http://gb.archive.ubuntu.com precise-updates/main amd64 Packages  
Hit http://gb.archive.ubuntu.com precise-updates/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com precise-updates/universe amd64 Packages
Hit http://gb.archive.ubuntu.com precise-updates/multiverse amd64 Packages
Hit http://gb.archive.ubuntu.com precise-updates/main i386 Packages   
Hit http://gb.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://gb.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://gb.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com precise-updates/main TranslationIndex
Get:3 http://ppa.launchpad.net precise/main Sources [1,211 B]         
Hit http://gb.archive.ubuntu.com precise-updates/multiverse TranslationIndex  
Get:4 http://ppa.launchpad.net precise/main amd64 Packages [2,834 B]  
Get:5 http://ppa.launchpad.net precise/main i386 Packages [2,834 B]   
Ign http://ppa.launchpad.net precise/main TranslationIndex            
Hit http://security.ubuntu.com precise-security Release                       
Hit http://gb.archive.ubuntu.com precise-updates/restricted TranslationIndex  
Hit http://gb.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/main Sources
Hit http://gb.archive.ubuntu.com precise-backports/restricted Sources
Hit http://gb.archive.ubuntu.com precise-backports/universe Sources   
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Sources 
Hit http://gb.archive.ubuntu.com precise-backports/main amd64 Packages
Hit http://gb.archive.ubuntu.com precise-backports/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com precise-backports/universe amd64 Packages
Hit http://gb.archive.ubuntu.com precise-backports/multiverse amd64 Packages
Hit http://gb.archive.ubuntu.com precise-backports/main i386 Packages 
Hit http://gb.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://gb.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://gb.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://gb.archive.ubuntu.com precise/main Translation-en_GB       
Hit http://gb.archive.ubuntu.com precise/main Translation-en          
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en_GB 
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en    
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en_GB 
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en
Hit http://security.ubuntu.com precise-security/main Sources          
Hit http://gb.archive.ubuntu.com precise/universe Translation-en_GB   
Hit http://gb.archive.ubuntu.com precise/universe Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en  
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/main Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/universe Translation-en
Hit http://security.ubuntu.com precise-security/restricted Sources    
Hit http://security.ubuntu.com precise-security/universe Sources
Hit http://security.ubuntu.com precise-security/multiverse Sources
Hit http://security.ubuntu.com precise-security/main amd64 Packages
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages
Hit http://security.ubuntu.com precise-security/universe amd64 Packages
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages
Hit http://security.ubuntu.com precise-security/main i386 Packages
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Ign http://ppa.launchpad.net precise/main Translation-en_GB
Ign http://ppa.launchpad.net precise/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Ign http://ppa.launchpad.net precise/main Translation-en_GB
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_GB
Ign http://ppa.launchpad.net precise/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Fetched 19.1 kB in 0s (21.6 kB/s)
Reading package lists... Done
sam@sam-pc:~$ sudo apt-get install oracle-java7-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-gstreamer-0.10 libpangomm-1.4-1 libsigc++-2.0-0c2a
  libglibmm-2.4-1c2a libcairomm-1.0-1 rsync libatkmm-1.6-1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gsfonts-x11 java-common
Suggested packages:
  default-jre equivs binfmt-support visualvm ttf-baekmuk ttf-unfonts
  ttf-unfonts-core ttf-kochi-gothic ttf-sazanami-gothic ttf-kochi-mincho
  ttf-sazanami-mincho ttf-arphic-uming
The following NEW packages will be installed:
  gsfonts-x11 java-common oracle-java7-installer
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 88.4 kB of archives.
After this operation, 476 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ppa.launchpad.net/webupd8team/java/ubuntu/ precise/main oracle-java7-installer all 7u51-0~webupd8~1 [17.6 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ precise/main java-common all 0.43ubuntu2 [61.7 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu/ precise/main gsfonts-x11 all 0.22 [9,108 B]
Fetched 88.4 kB in 0s (656 kB/s)       
Preconfiguring packages ...
Selecting previously unselected package java-common.
(Reading database ... 147063 files and directories currently installed.)
Unpacking java-common (from .../java-common_0.43ubuntu2_all.deb) ...
Selecting previously unselected package oracle-java7-installer.
Unpacking oracle-java7-installer (from .../oracle-java7-installer_7u51-0~webupd8~1_all.deb) ...
Selecting previously unselected package gsfonts-x11.
Unpacking gsfonts-x11 (from .../gsfonts-x11_0.22_all.deb) ...
Processing triggers for doc-base ...
Processing 2 added doc-base files...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for shared-mime-info ...
Processing triggers for fontconfig ...
Setting up java-common (0.43ubuntu2) ...
Setting up oracle-java7-installer (7u51-0~webupd8~1) ...
Downloading Oracle Java 7...
--2014-03-16 20:32:44--  http://download.oracle.com/otn-pub/java/jdk/7u51-b13/jdk-7u51-linux-x64.tar.gz
Resolving download.oracle.com (download.oracle.com)... 23.62.0.226, 23.62.0.225
Connecting to download.oracle.com (download.oracle.com)|23.62.0.226|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/7u51-b13/jdk-7u51-linux-x64.tar.gz [following]
--2014-03-16 20:32:44--  https://edelivery.oracle.com/otn-pub/java/jdk/7u51-b13/jdk-7u51-linux-x64.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 95.100.150.140
Connecting to edelivery.oracle.com (edelivery.oracle.com)|95.100.150.140|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/errors/download-fail-1505220.html [following]
--2014-03-16 20:32:44--  http://download.oracle.com/errors/download-fail-1505220.html
Connecting to download.oracle.com (download.oracle.com)|23.62.0.226|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `jdk-7u51-linux-x64.tar.gz'

     0K                                                      100%  335M=0s

2014-03-16 20:32:45 (335 MB/s) - `jdk-7u51-linux-x64.tar.gz' saved [5307/5307]

Download done.
Removing outdated cached downloads...
sha256sum mismatch jdk-7u51-linux-x64.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up gsfonts-x11 (0.22) ...
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
sam@sam-pc:~$ 

```

Seems it ends up here:

[http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html)

At no point was I prompted to accept the license terms, I would usually do that in the terminal, accept 'yes' using tab key then press enter. Any ideas?

**EDIT**

This seems to explain a few things. I literally installed java just the other day with the above method and no problems! Sadly I need it asap this time.

[http://tiemensfamily.com/TimOnCS/2014/03/15/oracle-adds-license-to-java7-installer-fails/](http://tiemensfamily.com/TimOnCS/2014/03/15/oracle-adds-license-to-java7-installer-fails/)

---

### Post by r.stiltskin on 2014-03-16
Seemingly everything worked until the script tried to extract the archive.  I was curious so I tried to
```
wget http://download.oracle.com/otn-pub/java/jdk/7u51-b13/jdk-7u51-linux-x64.tar.gz
```
and then I tried to extract it by
```
tar -xf jdk-7u51-linux-x64.tar.gz
```
unsuccessfully, it turned out.

But take a closer look at the output from your download:
```
Saving to: `jdk-7u51-linux-x64.tar.gz'

     0K                                                      100%  335M=0s

2014-03-16 20:32:45 (335 MB/s) - `jdk-7u51-linux-x64.tar.gz' saved [5307/5307]
```
5307 bytes!!  This is clearly not the entire sun/oracle jdk.  So I went to Oracle's website and did some hunting around.

Long story short, it seems Oracle has reorganized their download website, so webupd8.org's script won't work anymore.  But you can go to:

[http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html)

click to accept the license agreement and then click the appropriate file to download it.  As noted above you want:
jdk-7u51-linux-x64.tar.gz

The next problem is that as far as I can see there is no automatic installer for Debian-based systems.  There are some instructions [here]("http://docs.oracle.com/javase/7/docs/webnotes/install/linux/linux-jdk.html"), but very limited.  You can extract that tarball in your home directory and use it as a local copy.  I imagine webupd8.org will update their installer at some point but not fast enough for you.

Alternatively, you can  install a Linux distro that uses RPM, e.g. Fedora or Suse and download the RPM package from the oracle download page and you will be able to easily install it system-wide.

One other option: I haven't tried this, but if you want to experiment you can install **alien** and that's supposed to enable you to convert the RPM package into a .deb package which you can then install with dpkg.

---

### Post by r.stiltskin on 2014-03-16
Here's a workaround that I just tried and it seems to work.

After unsuccessfully running
```
sudo apt-get install oracle-java7-installer
```
you should have these four files in /var/cache/oracle-jdk7-installer:
-- jar.binfmt
-- javaws-wrapper.sh
-- jdk-7u51-linux-x64.tar.gz
-- wgetrc
but the tar.gz file is no good -- only 5307 bytes.

But go to [Oracle's new Java downloads page]("http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html"), accept the license agreement, and manually download that tarball.

Now copy that 138 MB tarball into /var/cache/oracle-jdk7-installer, overwriting the 'bogus' one.

Next, run these commands:
```

echo oracle-java7-installer shared/accepted-oracle-license-v1-1 select true | sudo /usr/bin/debconf-set-selections
sudo apt-get install oracle-java7-installer

```
and now it should install the jdk successfully without trying to download the tarball since it can use the file already existing in your cache.

---

### Post by samwillc on 2014-03-16
> **r.stiltskin said:**
> Seemingly everything worked until the script tried to extract the archive.  I was curious so I tried to
```
wget http://download.oracle.com/otn-pub/java/jdk/7u51-b13/jdk-7u51-linux-x64.tar.gz
```
and then I tried to extract it by
```
tar -xf jdk-7u51-linux-x64.tar.gz
```
unsuccessfully, it turned out.

But take a closer look at the output from your download:
```
Saving to: `jdk-7u51-linux-x64.tar.gz'

     0K                                                      100%  335M=0s

2014-03-16 20:32:45 (335 MB/s) - `jdk-7u51-linux-x64.tar.gz' saved [5307/5307]
```
5307 bytes!!  This is clearly not the entire sun/oracle jdk.  So I went to Oracle's website and did some hunting around.

Long story short, it seems Oracle has reorganized their download website, so webupd8.org's script won't work anymore.  But you can go to:

[http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html)

click to accept the license agreement and then click the appropriate file to download it.  As noted above you want:
jdk-7u51-linux-x64.tar.gz

The next problem is that as far as I can see there is no automatic installer for Debian-based systems.  There are some instructions [here]("http://docs.oracle.com/javase/7/docs/webnotes/install/linux/linux-jdk.html"), but very limited.  You can extract that tarball in your home directory and use it as a local copy.  I imagine webupd8.org will update their installer at some point but not fast enough for you.

Alternatively, you can  install a Linux distro that uses RPM, e.g. Fedora or Suse and download the RPM package from the oracle download page and you will be able to easily install it system-wide.

One other option: I haven't tried this, but if you want to experiment you can install **alien** and that's supposed to enable you to convert the RPM package into a .deb package which you can then install with dpkg.

Thanks. This update couldn't have happened at a worse time!

However, there is a FOURTH option. I have to use bluej for this assignment and I see on their website that it works with openjdk7. Might just get out of this mess yet.

Once this deadline's met then the pressure's off and there's no rush for oracle jdk, I can wait for a fix. I suppose if I was really depressed about the whole situation I could always virtualbox it with windows 7 and java/bluej. Have to be a last resort though!

Thanks for helping out.

Sam.

---

### Post by r.stiltskin on 2014-03-16
Read post #7.  It should solve it for you in 5 minutes.

---

### Post by QIII on 2014-03-16
While you have reinstalled a different distro and it doesn't matter in this case,  please don't make the mistake of starting over with the EugeneSan PPA.

If you do it that way, getting out of the mess can be irritating.


There is a section in the Java wiki in my signature where I give instructions for fixing the mess.

---

### Post by r.stiltskin on 2014-03-16
Sorry, there was an extra ']' at the beginning of the last command.  Fixed now.

---

### Post by samwillc on 2014-03-16
> **r.stiltskin said:**
> Read post #7.  It should solve it for you in 5 minutes.

Think we cross posted. Looks like a promising solution, thanks.

---

### Post by samwillc on 2014-03-17
Thanks for the help everyone. The webupd8 team update is only for 13.10:

[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

See comments for a number of fixes and if you're on 13.10, proceed as usual. I'm not so had to use another ppa.

---

### Post by samwillc on 2014-03-19
This has been fixed for v12.04 and v13.10 and newer.

```

sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

Works again as intended :)

---

