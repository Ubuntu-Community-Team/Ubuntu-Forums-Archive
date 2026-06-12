---
title: "Icon game"
date: 2007-12-19
forum: General Help
---

### Post by BluePlum on 2007-12-19
I was watching this [http://www.youtube.com/watch?v=ZD7QraljRfM](http://www.youtube.com/watch?v=ZD7QraljRfM) video on youtube and at 1.51 he does some cool stuff with all the icons, Do i need beryl to do that? or someother program?

---

### Post by danwood76 on 2007-12-19
I think thats the launcher bar hes using, looks similar to OSX.

regards,
Danny

---

### Post by BluePlum on 2007-12-19
I use awn, Were do i get OSX

---

### Post by steeleyuk on 2007-12-19
The panel at the top is Kiba-dock.

---

### Post by forestpixie on 2007-12-19
try looking in the desktop customization forum - that's where most of that stuff is - and you can get osx from apple :)

This thread might help though
[http://ubuntuforums.org/showthread.php?t=490398&highlight=osx+launcher](http://ubuntuforums.org/showthread.php?t=490398&highlight=osx+launcher)

---

### Post by BluePlum on 2007-12-19
Im installing Kiba-dock right now

---

### Post by BluePlum on 2007-12-19
Awww i dont no how to do it, i tryd to follow the steps at [http://ubuntuforums.org/showthread.php?t=554127&highlight=kiba](http://ubuntuforums.org/showthread.php?t=554127&highlight=kiba) but i dont think it worked

---

### Post by BluePlum on 2007-12-19
Can anyone explain to me in Alot of detail how to install kiba-dock? Please

---

### Post by danwood76 on 2007-12-19
> **BluePlum said:**
> Awww i dont no how to do it, i tryd to follow the steps at [http://ubuntuforums.org/showthread.php?t=554127&highlight=kiba](http://ubuntuforums.org/showthread.php?t=554127&highlight=kiba) but i dont think it worked

Did you get any errors during the building process?

If it worked ok running kiba-dock in the terminal should run it, if any errors occur when running this command post them here!

---

### Post by BluePlum on 2007-12-19
I exited the terminal, Can you tell me What to post?  i think when i did the part were i have to post the link for were the software comes from, it didnt work, not 100% tho. I just need a simplier guide

---

### Post by danwood76 on 2007-12-19
Im just gonna re-post the important bits you need to do, this is assuming you are running 32 bit ubuntu.

These commands are pasted into the terminal.

First of all install the build depencies:

```
sudo apt-get install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0 pidgin-dev libpurple-dev
```

Then make the directory to install kiba-dock into and download the sources.

```

mkdir kiba-dock
cd kiba-dock
svn co https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/ akamaru
svn co https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dock/ kiba-dock
svn co https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-plugins/ kiba-plugins
svn co https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dbus-plugins/ kiba-dbus-plugins
```

Then building the sources, copy each line one at a time and make sure you do them all.

```
cd akamaru/
./autogen.sh --prefix=/usr --exec-prefix=/usr
sudo make install
cd ..
```

```
cd kiba-dock/
./autogen.sh
sudo make install 
cd ..
```

```
cd kiba-plugins/
./autogen.sh
sudo make install 
cd ..
```

```
cd kiba-dbus-plugins/
./autogen.sh
sudo make install
cd ..
```

Then just type kiba-dock and press retun and it should load up.
if you get any errors at any point just post them here, I have never compiled or installed this I am just going by what the other thread says.

regards,
Danny

---

### Post by BluePlum on 2007-12-19
andrew@Andrew:~$ mkdir kiba-dock
mkdir: cannot create directory `kiba-dock': File exists
andrew@Andrew:~$ cd kiba-dock
andrew@Andrew:~/kiba-dock$ svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/) akamaru
Error validating server certificate for 'https://kibadock.svn.sourceforge.net:443':
 - The certificate is not issued by a trusted authority. Use the
   fingerprint to validate the certificate manually!
Certificate information:
 - Hostname: *.svn.sourceforge.net
 - Valid: from Tue, 09 Oct 2007 14:15:07 GMT until Mon, 08 Dec 2008 15:15:07 GMT
 - Issuer: Equifax Secure Certificate Authority, Equifax, US
 - Fingerprint: fb:75:6c:40:58:ae:21:8c:63:dd:1b:7b:6a:7d:bb:8c:74:36:e7:8a
(R)eject, accept (t)emporarily or accept (p)ermanently? p
svn: PROPFIND request failed on '/svnroot/kibadock/trunk/akamaru'
svn: PROPFIND of '/svnroot/kibadock/trunk/akamaru': Server certificate verification failed: issuer is not trusted ([https://kibadock.svn.sourceforge.net](https://kibadock.svn.sourceforge.net))
andrew@Andrew:~/kiba-dock$ cd akamaru/
bash: cd: akamaru/: No such file or directory
andrew@Andrew:~/kiba-dock$ ./autogen.sh --prefix=/usr --exec-prefix=/usr
bash: ./autogen.sh: No such file or directory
andrew@Andrew:~/kiba-dock$ sudo make install
[sudo] password for andrew:
make: *** No rule to make target `install'.  Stop.
andrew@Andrew:~/kiba-dock$ cd ..
andrew@Andrew:~$ 

It asked me to reject it, temp it, or permenently it. I hit P. Then i didnt under stand if if had to enter each of those commands 1 line at a time of from each of them. But then The kiba infront of my username dispeared so i stoped thinking its not working

---

### Post by danwood76 on 2007-12-19
well you didnt actually fetch the source packages.
When you hit p it didnt actually authenticate.

Try doing it again, instead of p hit t and make sure you press enter.
I just checked it out and downloaded the source succesfully so im unsure what is going on at your end.

---

### Post by BluePlum on 2007-12-19
andrew@Andrew:~$ mkdir kiba-dock
mkdir: cannot create directory `kiba-dock': File exists
andrew@Andrew:~$ cd kiba-dock
andrew@Andrew:~/kiba-dock$ svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/) akamaru
Error validating server certificate for 'https://kibadock.svn.sourceforge.net:443':
 - The certificate is not issued by a trusted authority. Use the
   fingerprint to validate the certificate manually!
Certificate information:
 - Hostname: *.svn.sourceforge.net
 - Valid: from Tue, 09 Oct 2007 14:15:07 GMT until Mon, 08 Dec 2008 15:15:07 GMT
 - Issuer: Equifax Secure Certificate Authority, Equifax, US
 - Fingerprint: fb:75:6c:40:58:ae:21:8c:63:dd:1b:7b:6a:7d:bb:8c:74:36:e7:8a
(R)eject, accept (t)emporarily or accept (p)ermanently? t
svn: PROPFIND request failed on '/svnroot/kibadock/trunk/akamaru'
svn: PROPFIND of '/svnroot/kibadock/trunk/akamaru': Server certificate verification failed: issuer is not trusted ([https://kibadock.svn.sourceforge.net](https://kibadock.svn.sourceforge.net))
andrew@Andrew:~/kiba-dock$ 


Firewall stoping? Anyother way i can do it?

---

### Post by danwood76 on 2007-12-19
you need to download the source code in order to compile the program so in short no.
I dont know why your getting that error but it could be a firewall issue.

Try turning your firewall off, I cant really help much further.

---

### Post by BluePlum on 2007-12-19
Still nothing, Can u direct me to a thread for this problem?

---

### Post by danwood76 on 2007-12-19
search for it, I cant help as ive never had any issues getting packages from svn.

sorry.

---

### Post by BluePlum on 2007-12-19
Search but no find, Anyone No anything about this kind of stuff? suggestions appreciated.:KS

---

### Post by BluePlum on 2007-12-20
Anyone?

---

### Post by BluePlum on 2007-12-20
"twiddles thumbs"

---

### Post by BluePlum on 2007-12-21
Comeon guys.... your smart help a noob

---

### Post by danwood76 on 2007-12-21
Theres a package called rapidsvn which is a graphical version of the svn package.
you could try installing that and using that to download the source.

Also you may want to re install the subversion and libsvn packages.

Do you have your internet through a router? and has that router got a firewall enabled coz that could give you problems also.

regards,
Danny

---

### Post by BluePlum on 2007-12-21
Im on wireless internet, which goes thru an ADSL box so dont think theres a firewall in there. How do i do these other steps

---

### Post by danwood76 on 2007-12-21
Well, open up synaptic and search for svn.

Right click on libsvn1 and subversion (names of the packages) and click reinstall then apply. 
Then after that is done search for rapidsvn and right click and select install, accept the dependencies and click apply.

Once this is complete rapidsvn should be installed and accessable by doing alt+F2 and typing rapidsvn and pressing enter.

In rapidsvn click repositories and checkout for the URLs use the following:
```

https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/
https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dock/
https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-plugins/
https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dbus-plugins/

```

you will want to set the destination for each URL to be different, I reccomend creating the following directories somewhere useful:
1st Link: akamaru
2nd Link: kiba-dock
3rd Link: kiba-plugins
4th Link: kiba-dbus-plugins

once you have checked out each module you can follow the rest of the instructions I posted earlier:
[QUOTE=danwood76]
Then building the sources, copy each line one at a time and make sure you do them all.

Code:

cd akamaru/
./autogen.sh --prefix=/usr --exec-prefix=/usr
sudo make install
cd ..

Code:

cd kiba-dock/
./autogen.sh
sudo make install 
cd ..

Code:

cd kiba-plugins/
./autogen.sh
sudo make install 
cd ..

Code:

cd kiba-dbus-plugins/
./autogen.sh
sudo make install
cd ..

Then just type kiba-dock and press retun and it should load up.
if you get any errors at any point just post them here, I have never compiled or installed this I am just going by what the other thread says.[/QUOTE]

regards,
Danny

---

### Post by BluePlum on 2007-12-21
Wat do you mean sub packages?

---

### Post by danwood76 on 2007-12-21
I didnt use the term sub packages :S I assume you mean svn.

svn is a system that is used to update online source code, it allows you to obtain the latest subversion of the software.
In synaptic you need to resinstall svn (subversion) and also install the GUI frontend for svn to allow you to download the source code of the app bar you want to install.

---

### Post by BluePlum on 2007-12-21
Rapidsvn wasnt installed... Installing it now

---

### Post by BluePlum on 2007-12-21
Alot of stuff is happening in terminal, I think its finaly working.

---

### Post by BluePlum on 2007-12-21
andrew@Andrew:~$ kiba-dock

** (kiba-dock:27903): WARNING **: Error (main.c @ line 252):
        Failed to locate Plugins at '/usr/local/lib/kiba-dock'
Please install the Plugins at '/usr/local/lib/kiba-dock' or use the '--plugin-path' command line parameter.



Anyone no what that means?

---

### Post by danwood76 on 2007-12-21
You probably havent compiled or installed the plugins.
This could be because of a missing package dependency.

Were there any errors when you ran these commands:
cd kiba-plugins/
./autogen.sh
sudo make install
cd ..

Code:

cd kiba-dbus-plugins/
./autogen.sh
sudo make install
cd ..

---

### Post by BluePlum on 2007-12-23
Here It is,:

andrew@Andrew:~$ cd kiba-plugins/
bash: cd: kiba-plugins/: No such file or directory
andrew@Andrew:~$ ./autogen.sh
bash: ./autogen.sh: No such file or directory
andrew@Andrew:~$ sudo make install
make: *** No rule to make target `install'.  Stop.
andrew@Andrew:~$ cd ..cd kiba-dbus-plugins/
bash: cd: ..cd: No such file or directory
andrew@Andrew:~$ ./autogen.sh
bash: ./autogen.sh: No such file or directory
andrew@Andrew:~$ sudo make install
make: *** No rule to make target `install'.  Stop.
andrew@Andrew:~$ cd ..

---

### Post by BluePlum on 2007-12-23
Its been an hour!

---

### Post by danwood76 on 2007-12-23
> **BluePlum said:**
> Here It is,:

andrew@Andrew:~$ cd kiba-plugins/
bash: cd: kiba-plugins/: No such file or directory
andrew@Andrew:~$ ./autogen.sh
bash: ./autogen.sh: No such file or directory
andrew@Andrew:~$ sudo make install
make: *** No rule to make target `install'.  Stop.
andrew@Andrew:~$ cd ..cd kiba-dbus-plugins/
bash: cd: ..cd: No such file or directory
andrew@Andrew:~$ ./autogen.sh
bash: ./autogen.sh: No such file or directory
andrew@Andrew:~$ sudo make install
make: *** No rule to make target `install'.  Stop.
andrew@Andrew:~$ cd ..

It sounds like you either havent downloaded the source for those two plugin sets or youve named the directory you dumped them into something different.

You need to try and understand what your doing in the terminal, you see cd ..... is change directory to wherever you put the path, so if you downloaded the plugins source to /home/andrew/kiba-plugins (/home/andrew will be your home folder) then you would put cd kiba-plugins from the first terminal (as it opens in your home directory). I dont think you quite have the knowledge to compile this stuff from source. If one command fails its best not to try the next one as it will also fail if it relies on the first.

---

### Post by BluePlum on 2007-12-23
So could you tell me what i need to do?

---

### Post by BluePlum on 2008-02-07
Bump. Waited for so kong and still no reply? HELP???

---

