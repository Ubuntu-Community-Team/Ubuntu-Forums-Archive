---
title: "Cant remove Java 7 (Ubuntu 14.04)"
date: 2014-04-22
forum: General Help
---

### Post by Hvidemose on 2014-04-22
I'm currently trying to remove java 7 from ubuntu 14.04, so that i can install it all probably again.
The problem is, that no matter what i try, I cant seem to get it uninstalled.
Can any one help here?

---

### Post by grumblebum2 on 2014-04-22
How did you install in the first place?
...what methods are you using to try and uninstall it?

---

### Post by slickymaster on 2014-04-22
As you don't state what Java you have installed, I'll mention the way to remove OpenJDK and Oracle Java 7.

To uninstall OpenJDK:```
sudo apt-get purge openjdk*
```Then uninstall OpenJDK related packages:```
sudo apt-get purge icedtea-* openjdk-*
```If you want to check that all OpenJDK packages have been removed, just run the following```
sudo dpkg --list | grep -i jdk
```

To uninstall Oracle Java 7, you should first check the exact version of Java you have installed before uninstalling it:```
java -version
javac -version
which javaws
```Next, remove the symlinks (please note that you have to replace the word **version** with your Java version):```
sudo update-alternatives --remove "java" "/usr/lib/jvm/jdk<version>/bin/java"
sudo update-alternatives --remove "javac" "/usr/lib/jvm/jdk<version>/bin/javac"
sudo update-alternatives --remove "javaws" "/usr/lib/jvm/jdk<version>/bin/javaws"
```
After that:```
cd /usr/lib/jvm
sudo rm -rf jdk<version>
```
Then do:```
sudo update-alternatives --config java
sudo update-alternatives --config javac
sudo update-alternatives --config javaws
```
Finally edit your **/etc/environment** file:```
sudo nano  /etc/environment
```delete the line with **JAVA_HOME 1**, save the file and close it.

---

### Post by Hvidemose on 2014-04-22
Ah, true. Its the Oracle Java 7. It doesn't seem towork. I dont know if it says any thing, but its stored in/usr/lib/jvm/java-7-oracle.
Here is the respond I got from codes:

```
whiteboy@whiteboy-U31SD:~$ sudo dpkg --list | grep -i jdk
[sudo] password for whiteboy: 
whiteboy@whiteboy-U31SD:~$ java -version
The program 'java' can be found in the following packages:
 * default-jre
 * gcj-4.8-jre-headless
 * openjdk-7-jre-headless
 * gcj-4.6-jre-headless
 * openjdk-6-jre-headless
Try: sudo apt-get install <selected package>
whiteboy@whiteboy-U31SD:~$ javac -version
javac 1.7.0_55
whiteboy@whiteboy-U31SD:~$ which javaws
whiteboy@whiteboy-U31SD:~$ sudo update-alternatives --remove"java" "/usr/lib/jvm/jdk1.7.0_55/bin/java"
update-alternatives: warning: /etc/alternatives/java is dangling;it will be updated with best choice
whiteboy@whiteboy-U31SD:~$ sudo update-alternatives --remove"javac" "/usr/lib/jvm/jdk1.7.0_55/bin/javac"
whiteboy@whiteboy-U31SD:~$ sudo update-alternatives --remove"javaws" "/usr/lib/jvm/jdk1.7.0_55/bin/javaws"
update-alternatives: warning: alternative/usr/lib/jvm/java-8-oracle/jre/bin/javaws (part of link group javaws)doesn't exist; removing from list of alternatives
update-alternatives: warning: /etc/alternatives/javaws isdangling; it will be updated with best choice

whiteboy@whiteboy-U31SD:~$ cd /usr/lib/jvm
whiteboy@whiteboy-U31SD:/usr/lib/jvm$ sudo rm -rf jdk1.7.0_55
whiteboy@whiteboy-U31SD:/usr/lib/jvm$ sudo update-alternatives--config java
update-alternatives: warning: /etc/alternatives/java is dangling;it will be updated with best choice
There is only one alternative in link group java (providing/usr/bin/java): /usr/lib/jvm/java-8-oracle/jre/bin/java
Nothing to configure.
whiteboy@whiteboy-U31SD:/usr/lib/jvm$ sudo update-alternatives--config javac
There is only one alternative in link group javac (providing/usr/bin/javac): /usr/lib/jvm/java-7-oracle/bin/javac
Nothing to configure.
whiteboy@whiteboy-U31SD:/usr/lib/jvm$ sudo update-alternatives--config javaws
update-alternatives: warning: /etc/alternatives/javaws isdangling; it will be updated with best choice
There is only one alternative in link group javaws (providing/usr/bin/javaws): /usr/lib/jvm/java-8-oracle/jre/bin/javaws
Nothing to configure.
```

And the doc says:

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/$

---

### Post by slickymaster on 2014-04-23
> **Hvidemose said:**
> Ah, true. Its the Oracle Java 7. It doesn't seem towork. I dont know if it says any thing, but its stored in/usr/lib/jvm/java-7-oracle.
Here is the respond I got from codes:

```
whiteboy@whiteboy-U31SD:~$ sudo dpkg --list | grep -i jdk
[sudo] password for whiteboy: 
whiteboy@whiteboy-U31SD:~$ java -version
The program 'java' can be found in the following packages:
 * default-jre
 * gcj-4.8-jre-headless
 * openjdk-7-jre-headless
 * gcj-4.6-jre-headless
 * openjdk-6-jre-headless
Try: sudo apt-get install <selected package>
whiteboy@whiteboy-U31SD:~$ javac -version
javac 1.7.0_55
whiteboy@whiteboy-U31SD:~$ which javaws
whiteboy@whiteboy-U31SD:~$ sudo update-alternatives --remove"java" "/usr/lib/jvm/jdk1.7.0_55/bin/java"
update-alternatives: warning: /etc/alternatives/java is dangling;it will be updated with best choice
whiteboy@whiteboy-U31SD:~$ sudo update-alternatives --remove"javac" "/usr/lib/jvm/jdk1.7.0_55/bin/javac"
whiteboy@whiteboy-U31SD:~$ sudo update-alternatives --remove"javaws" "/usr/lib/jvm/jdk1.7.0_55/bin/javaws"
update-alternatives: warning: alternative/usr/lib/jvm/java-8-oracle/jre/bin/javaws (part of link group javaws)doesn't exist; removing from list of alternatives
update-alternatives: warning: /etc/alternatives/javaws isdangling; it will be updated with best choice

whiteboy@whiteboy-U31SD:~$ cd /usr/lib/jvm
whiteboy@whiteboy-U31SD:/usr/lib/jvm$ sudo rm -rf jdk1.7.0_55
whiteboy@whiteboy-U31SD:/usr/lib/jvm$ **[COLOR=#ff0000]sudo update-alternatives--config java[/COLOR]**
update-alternatives: warning: /etc/alternatives/java is dangling;it will be updated with best choice
There is only one alternative in link group java (providing/usr/bin/java): /usr/lib/jvm/java-8-oracle/jre/bin/java
Nothing to configure.
whiteboy@whiteboy-U31SD:/usr/lib/jvm$ **[COLOR=#ff0000]sudo update-alternatives--config javac[/COLOR]**
There is only one alternative in link group javac (providing/usr/bin/javac): /usr/lib/jvm/java-7-oracle/bin/javac
Nothing to configure.
whiteboy@whiteboy-U31SD:/usr/lib/jvm$ **[COLOR=#ff0000]sudo update-alternatives--config javaws[/COLOR]**
update-alternatives: warning: /etc/alternatives/javaws isdangling; it will be updated with best choice
There is only one alternative in link group javaws (providing/usr/bin/javaws): /usr/lib/jvm/java-8-oracle/jre/bin/javaws
Nothing to configure.
```

And the doc says:

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/$

Even though that's not the culprit of the mess you apparently might be facing, you misstyped the commands I've marked in red. You missed a space between 'update-alternatives' and '--config'

Besides Java 7, you seem to also have Java 8 installed. Can you please run the the following commands and post the results you get:```
dpkg --get-selections | grep java
``````
ls /usr/bin/ | grep java
``````
ls /etc/alternatives/ | grep java
```

---

### Post by Hvidemose on 2014-04-23
Thanks! Yes, here you go:

```
whiteboy@whiteboy-U31SD:~$ dpkg --get-selections | grep java
gir1.2-javascriptcoregtk-3.0			install
libjavascriptcoregtk-3.0-0:amd64		install

whiteboy@whiteboy-U31SD:~$ ls /usr/bin/ | grep java
java
javac
javadoc
javafxpackager
javah
javap
java_vm
javaws

whiteboy@whiteboy-U31SD:~$ ls /etc/alternatives/ | grep java
java
java.1.gz
javac
javac.1.gz
javadoc
javadoc.1.gz
javafxpackager
javafxpackager.1.gz
javah
javah.1.gz
javap
javap.1.gz
java_vm
javaws
javaws.1.gz
mozilla-javaplugin.so
whiteboy@whiteboy-U31SD:~$ 

```

---

### Post by slickymaster on 2014-04-24
Please run```
sudo dpkg -r --force-all oracle-jdk7-installer
```and once again post the output you got.

---

### Post by Hvidemose on 2014-04-24
Hmm, it came up with this respons:

```
whiteboy@whiteboy-U31SD:~$ sudo dpkg -r --force-all oracle-jdk7-installer[sudo] password for whiteboy: 
dpkg: warning: ignoring request to remove oracle-jdk7-installer which isn't installed
whiteboy@whiteboy-U31SD:~$ 

```

---

### Post by slickymaster on 2014-04-24
Please run:```
sudo apt-get autoremove && sudo apt-get autoclean && sudo apt-get update
```and again post its output.

---

### Post by Hvidemose on 2014-04-24
Came up with this:

```
whiteboy@whiteboy-U31SD:~$ sudo apt-get autoremove && sudo apt-get autoclean && sudo apt-get updateReading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del wine-compholio 1.7.16-1~ubuntu14.04.1 [1.229 kB]
Del wine-compholio-i386 1.7.16-1~ubuntu14.04.1 [16,2 MB]
Del wine-compholio-amd64 1.7.16-1~ubuntu14.04.1 [16,5 MB]
Ign http://dk.archive.ubuntu.com trusty InRelease
Ign http://dk.archive.ubuntu.com trusty-updates InRelease                      
Ign http://dk.archive.ubuntu.com trusty-backports InRelease                    
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://dk.archive.ubuntu.com trusty Release.gpg                            
Hit http://dk.archive.ubuntu.com trusty-updates Release.gpg                    
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://dk.archive.ubuntu.com trusty-backports Release.gpg                  
Hit http://dk.archive.ubuntu.com trusty Release                                
Hit http://dk.archive.ubuntu.com trusty-updates Release                        
Hit http://extras.ubuntu.com trusty Release.gpg                                
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://dk.archive.ubuntu.com trusty-backports Release                      
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release                                    
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://dk.archive.ubuntu.com trusty/main Sources                           
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://dk.archive.ubuntu.com trusty/restricted Sources                     
Hit http://dk.archive.ubuntu.com trusty/universe Sources                       
Hit http://dk.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://dk.archive.ubuntu.com trusty/main amd64 Packages                    
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://dk.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://dk.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://dk.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://dk.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://dk.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://extras.ubuntu.com trusty/main Sources                     
Hit http://ppa.launchpad.net trusty Release.gpg                      
Hit http://dk.archive.ubuntu.com trusty/universe i386 Packages       
Hit http://dk.archive.ubuntu.com trusty/multiverse i386 Packages     
Hit http://extras.ubuntu.com trusty/main amd64 Packages              
Hit http://ppa.launchpad.net trusty Release.gpg                      
Hit http://dk.archive.ubuntu.com trusty/main Translation-en                    
Hit http://dk.archive.ubuntu.com trusty/main Translation-da                    
Hit http://dk.archive.ubuntu.com trusty/multiverse Translation-en    
Hit http://ppa.launchpad.net trusty Release.gpg                      
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://dk.archive.ubuntu.com trusty/multiverse Translation-da              
Hit http://dk.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://dk.archive.ubuntu.com trusty/restricted Translation-da    
Hit http://ppa.launchpad.net trusty Release.gpg                      
Hit http://dk.archive.ubuntu.com trusty/universe Translation-en      
Hit http://dk.archive.ubuntu.com trusty/universe Translation-da      
Hit http://dk.archive.ubuntu.com trusty-updates/main Sources                   
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://dk.archive.ubuntu.com trusty-updates/restricted Sources             
Hit http://dk.archive.ubuntu.com trusty-updates/universe Sources               
Hit http://dk.archive.ubuntu.com trusty-updates/multiverse Sources             
Hit http://dk.archive.ubuntu.com trusty-updates/main amd64 Packages  
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Ign http://security.ubuntu.com trusty-security InRelease             
Hit http://dk.archive.ubuntu.com trusty-updates/restricted amd64 Packages
Hit http://ppa.launchpad.net trusty Release                          
Hit http://dk.archive.ubuntu.com trusty-updates/universe amd64 Packages        
Hit http://dk.archive.ubuntu.com trusty-updates/multiverse amd64 Packages      
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://dk.archive.ubuntu.com trusty-updates/main i386 Packages             
Hit http://dk.archive.ubuntu.com trusty-updates/restricted i386 Packages       
Hit http://dk.archive.ubuntu.com trusty-updates/universe i386 Packages         
Hit http://dk.archive.ubuntu.com trusty-updates/multiverse i386 Packages       
Hit http://dk.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://dk.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://dk.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://dk.archive.ubuntu.com trusty-updates/universe Translation-en        
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]           
Hit http://ppa.launchpad.net trusty Release                                    
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://ppa.launchpad.net trusty Release                                    
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://dk.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://dk.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://dk.archive.ubuntu.com trusty-backports/universe Sources             
Ign http://extras.ubuntu.com trusty/main Translation-da                        
Hit http://dk.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://ppa.launchpad.net trusty Release                          
Hit http://dk.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://dk.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://dk.archive.ubuntu.com trusty-backports/universe amd64 Packages
Hit http://dk.archive.ubuntu.com trusty-backports/multiverse amd64 Packages
Hit http://dk.archive.ubuntu.com trusty-backports/main i386 Packages  
Hit http://ppa.launchpad.net trusty/main amd64 Packages              
Hit http://dk.archive.ubuntu.com trusty-backports/restricted i386 Packages
Hit http://dk.archive.ubuntu.com trusty-backports/universe i386 Packages
Hit http://dk.archive.ubuntu.com trusty-backports/multiverse i386 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://dk.archive.ubuntu.com trusty-backports/main Translation-en
Hit http://dk.archive.ubuntu.com trusty-backports/multiverse Translation-en
Get:2 http://security.ubuntu.com trusty-security Release [58,5 kB]
Hit http://dk.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://dk.archive.ubuntu.com trusty-backports/universe Translation-en
Hit http://ppa.launchpad.net trusty/main i386 Packages   
Hit http://ppa.launchpad.net trusty/main amd64 Packages  
Hit http://ppa.launchpad.net trusty/main i386 Packages   
Hit http://ppa.launchpad.net trusty/main amd64 Packages  
Hit http://ppa.launchpad.net trusty/main i386 Packages   
Hit http://ppa.launchpad.net trusty/main amd64 Packages                  
Hit http://ppa.launchpad.net trusty/main i386 Packages
Ign http://dk.archive.ubuntu.com trusty/main Translation-en_US
Ign http://dk.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://dk.archive.ubuntu.com trusty/restricted Translation-en_US
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Ign http://dk.archive.ubuntu.com trusty/universe Translation-en_US
Ign http://dk.archive.ubuntu.com trusty-updates/main Translation-en_US
Ign http://dk.archive.ubuntu.com trusty-updates/main Translation-da
Hit http://ppa.launchpad.net trusty/main i386 Packages
Ign http://dk.archive.ubuntu.com trusty-updates/multiverse Translation-en_US
Ign http://dk.archive.ubuntu.com trusty-updates/multiverse Translation-da
Ign http://dk.archive.ubuntu.com trusty-updates/restricted Translation-en_US
Ign http://dk.archive.ubuntu.com trusty-updates/restricted Translation-da
Ign http://dk.archive.ubuntu.com trusty-updates/universe Translation-en_US
Ign http://dk.archive.ubuntu.com trusty-updates/universe Translation-da
Ign http://dk.archive.ubuntu.com trusty-backports/main Translation-en_US
Ign http://dk.archive.ubuntu.com trusty-backports/main Translation-da
Ign http://dk.archive.ubuntu.com trusty-backports/multiverse Translation-en_US
Get:3 http://security.ubuntu.com trusty-security/main Sources [2.642 B]
Ign http://dk.archive.ubuntu.com trusty-backports/multiverse Translation-da    
Ign http://dk.archive.ubuntu.com trusty-backports/restricted Translation-en_US
Ign http://dk.archive.ubuntu.com trusty-backports/restricted Translation-da
Ign http://dk.archive.ubuntu.com trusty-backports/universe Translation-en_US   
Ign http://dk.archive.ubuntu.com trusty-backports/universe Translation-da
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Get:4 http://security.ubuntu.com trusty-security/restricted Sources [14 B]
Hit http://ppa.launchpad.net trusty/main amd64 Packages               
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Get:5 http://security.ubuntu.com trusty-security/universe Sources [14 B]
Get:6 http://security.ubuntu.com trusty-security/multiverse Sources [14 B]
Get:7 http://security.ubuntu.com trusty-security/main amd64 Packages [3.866 B]
Get:8 http://security.ubuntu.com trusty-security/restricted amd64 Packages [14 B]
Get:9 http://security.ubuntu.com trusty-security/universe amd64 Packages [1.199 B]
Get:10 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [14 B]
Get:11 http://security.ubuntu.com trusty-security/main i386 Packages [3.902 B]
Get:12 http://security.ubuntu.com trusty-security/restricted i386 Packages [14 B]
Get:13 http://security.ubuntu.com trusty-security/universe i386 Packages [1.206 B]
Get:14 http://security.ubuntu.com trusty-security/multiverse i386 Packages [14 B]
Hit http://security.ubuntu.com trusty-security/main Translation-en      
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-da
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-da
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-da
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-da
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-da
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-da
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-da
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-da
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-da
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Ign http://security.ubuntu.com trusty-security/main Translation-en_US          
Ign http://security.ubuntu.com trusty-security/main Translation-da             
Ign http://security.ubuntu.com trusty-security/multiverse Translation-en_US    
Ign http://security.ubuntu.com trusty-security/multiverse Translation-da       
Ign http://security.ubuntu.com trusty-security/restricted Translation-en_US    
Ign http://security.ubuntu.com trusty-security/restricted Translation-da       
Ign http://security.ubuntu.com trusty-security/universe Translation-en_US      
Ign http://security.ubuntu.com trusty-security/universe Translation-da         
Fetched 72,4 kB in 11s (6.157 B/s)                                             
Reading package lists... Done
whiteboy@whiteboy-U31SD:~$
```

---

### Post by slickymaster on 2014-04-24
Apparently everything went fine.

You said in your first post that you wanted to reinstall Java again. Are you planning to install Java 7 or Java 8?

---

### Post by Hvidemose on 2014-04-24
Yes, thank you very much. It seems to be gone. Is there any way to delete the folder /usr/lib/jvm/java-7-oracle?

I don't really know what the best option would be. So I probably need a bit of advice on that. But maybe just use the OpenJDK from seofwarecenter?

---

### Post by slickymaster on 2014-04-24
> **Hvidemose said:**
> Yes, thank you very much. It seems to be gone. Is there any way to delete the folder /usr/lib/jvm/java-7-oracle?

Just run```
[COLOR=#000000][FONT=Ubuntu Mono]sudo rm [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]-[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]rf [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]/[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]usr[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]/[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]lib[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]/[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]jvm[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]/[/FONT][/COLOR]
```You should also remove Java configs and cache directory, running:```
sudo bash -c 'ls -d /home/*/.java' | xargs sudo rm -rf
```
> **Hvidemose said:**
> I don't really know what the best option would be. So I probably need a bit of advice on that. But maybe just use the OpenJDK from seofwarecenter?
The difference between Oracle JDK and Open JDK are a consequence of the goal of each one (OpenJDK is meant to be the reference implementation, open to the community, while Oracle is meant to be a commercial one). They both have "almost" the same code of the classes in the Java API; but the code for the virtual machine itself used to be different, and when it comes to libraries, OpenJDK tends to use open libraries while Oracle tends to use closed ones.
As of Java 7, Oracle replaced a number of closed source parts with their open source equivalent. The code for the virtual machine is actually almost completely identical, but there are a couple of libraries which are closed. For instance, the [font library]("http://technfun.wordpress.com/2013/01/18/last-difference-openjdk-oracle-jdk").

---

### Post by Hvidemose on 2014-04-24
Thanks mate! Awesome help, that i would newer have figured out on my own.
I installed the open, which works just fine.
Cheers!

---

### Post by slickymaster on 2014-04-24
You're welcome. I'm just glad it's fixed now.

Please don't forget to mark the thread as solved, using the thread tools in the top right, so other people searching the forums know that this thread provides a working solution.

---

