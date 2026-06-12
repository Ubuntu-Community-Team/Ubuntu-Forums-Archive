---
title: "access shared folder from windows 10"
date: 2020-01-04
forum: General Help
---

### Post by cmacc77 on 2020-01-04
I want to create and share a folder on ubuntu accessible from my windows 10 pc.  I've tried a number of things via youtube video instructions and none seem to work.  I get an error at some point, look up how to overcome that error message, do that, then run into another error message.  when i installed it I updated it and downloaded half a GB of updates and installed them successfully.

at this point I'm not going to post specific error messages because they seem to be endless.

Is there a general software / utility download i need to install to get all the necessary utilities and software on my machine?

If not, does anyone have some fool proof instructions on how to share an ubuntu folder on a wifi network w a windows 10 pc?

Ubuntu 18.04.3 LTS

---

### Post by SeijiSensei on 2020-01-04
[https://tutorials.ubuntu.com/tutorial/install-and-configure-samba](https://tutorials.ubuntu.com/tutorial/install-and-configure-samba)

---

### Post by dragonfly41 on 2020-01-04
In my Windows 10 plus three separate Ubuntu installations I use the simple mechanism of creating a small NTFS partition alongside the Ubuntu EXT4 configuration. I keep notes in there to refer to on the rare occasion I run windows. For example [cherrytree editor]("https://www.giuspen.com/cherrytree/") installed in both Ubuntu and Windows can open shared notes (I keep them as ctd xml notes).

---

### Post by Morbius1 on 2020-01-04
There isn't enough information in your post to answer the question. It's not even clear if the issue is finding the Ubuntu server or connecting to it.

Why not post the output of the following commands so the folks here can see how you are set up:
```
testparm -s
```
```
net usershare info --long
```
```
hostname
```

---

### Post by cmacc77 on 2020-01-04
thanks for the assistance


I got this at restart samba at the end of step 3

~$ sudo service smbd restart
Job for smbd.service failed because the control process exited with error code.
See "systemctl status smbd.service" and "journalctl -xe" for details.

---

### Post by cmacc77 on 2020-01-05
thanks for the help, these were my results:

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Error loading services.

~$ net usershare info --long
Can't load /etc/samba/smb.conf - run testparm to debug it

so i did sudo tesparm (? not sure if that was right)
sudo testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Error loading services.

$ hostname
cmcclain-Inspiron-5520

---

### Post by Morbius1 on 2020-01-06
[1] Rename your existing smb.conf file:
```
sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.bak
```
[2] Copy a duplicate of the factory fresh smb.conf to the working directory:
```
sudo cp -a /usr/share/samba/smb.conf /etc/samba/
```
Run [highlight]sudo service smbd restart[/highlight] to make sure it runs without error.

[3] Create a test directory:
```
sudo mkdir /Test
```
[4] Take possession of the directory:
```
sudo chown cmcclain /Test
```
[5] Edit /etc/samba/smb.conf and at the bottom of the file add a share definition for /Test:
```
[Test]
path = /Test
read only = no
guest ok = yes
force user = cmcclain
```
Then restart smbd again:
```
sudo service smbd restart
```

[COLOR=#0000cd]* I'm assuming your user name of this system is cmcclain.*[/COLOR]

On your Win10 system open Explorer and access the machine this way:
```
\\cmcclain-Inspiron-5520.local
```
[COLOR=#0000cd]*Don't forget the .local at the end of the hostname.*[/COLOR]

You should see and be able to access the Test share assuming:

** A firewall is not in the way on your Linux box.
** And avahi-daemon is running [highlight]sudo service avahi-daemon status[/highlight]

---

### Post by HermanAB on 2020-01-06
Note that you don’t have to use Samba with Windows.  Windows also supports Anonymous FTP out of the box and an Anonymous FTP server is much easier to set up than Samba.

Yes, yes, FTP is not secure, but Samba isn’t secure either...

---

### Post by Morbius1 on 2020-01-06
Samba encrypted transport has been available since Samba 3.2 - which was somewhere around 2008. You can either require it on the server or ask for it on the client. You folks who keep posting your own "facts" about samba really need to update yourselves.

---

### Post by HermanAB on 2020-01-07
Sure, but has anybody (apart from the original developers) ever got Samba Encrypted Transport to work?

---

### Post by Morbius1 on 2020-01-07
I just did:

```

tester@vub1804:~$ sudo smbstatus -S
Service      pid     Machine       Connected at                     [COLOR=#0000cd]**Encryption**[/COLOR]   Signing     
---------------------------------------------------------------------------------------------
         
Test         2842    2605:a601:a1a4:d000:819c:989a:90b7:8f60 Tue Jan  7 06:49:31 AM 2020 EST  **[COLOR=#0000cd]AES-128-CCM[/COLOR]**  AES-128-CMAC

Test         2771    192.168.1.143 Tue Jan  7 06:38:32 AM 2020 EST  **[COLOR=#0000cd]AES-128-CCM[/COLOR]**  AES-128-CMAC
```

---

### Post by HermanAB on 2020-01-08
Cool!  I should try that.

We are digressing a bit from the original topic, but security is important.  Do you know which encryption algorithms are supported?  The problem being that AES128 is not considered secure by the cryptographers I work with (various reasons).

---

### Post by cmacc77 on 2020-01-10
k

---

### Post by cmacc77 on 2020-01-10
didn't work.  said could not find location.  does the windows firewall have anything to do with it?

---

### Post by Morbius1 on 2020-01-11
The windows firewall shouldn't have anything to do with this but the Linux firewall might. If you have it enabled disable it to see if it is in the way:
```
sudo ufw disable
```

I would suggest starting with some fundamentals. See if you can ping the Linux box from Win10:

First by the Linux machines ip address - to find it run ```
hostname -I
```.
THen ping - from Win10 - by that ip address:
```
ping 192.168.0.100
```
Then by it's mDNS host name:
```
ping  cmcclain-Inspiron-552.local         
```

---

### Post by bunny9000 on 2020-01-11
There used to be some GUI tools to get samba setup, but they seem to be broken in this version of ubuntu. There is an advance tool and it does work, but I honestly found it really confusing. It's generally because you have to be in the right group and samba password is seperate from your normal login. I always found it got a mess so once those handy simple tools broke since being back with ubuntu I SFTP all my files to and from my Linux box.

The worst method is just to make a SAMBA share and open it up to the whole wide world. Let anyone create and delete folders and you'll have yourself access. Creds don't matter then. But then anyone else who happens to connect to your computer will be able to have at your files. Don't take that advice. ;)

Since SAMBA is such a %^&£$%"£@ to setup these days I can give you two options that may actually work.

SFTP - Secure File Transfer Protocol. Like FTP, but with security goodness. Windows doesn't support it out of the box :( so you have to use something like winscp. On your linux box you then just install the openssh-server and voila. The only downside, although it's now secure and shiny you get a fairly big file transfer overhead as it encrypts everything on the fly. We're talking 14MB/s over a standard gigabit wired link and your CPU is going to take a bit of a hit. But it might be faster on a modern 6 or 8 core cpu. You'll also want to make sure you put a half decent password because you've just opened the box to SSH as well. It uses your standard user creds.

But wait! There's more! If I recall and, it's been a while you can get SAMBA working without much pain by setting it up via Webmin, a web based server manager. I think there are others like cockpit, but I used to setup samba for my test servers using Webmin I remember it being painless. Oh, overkill you say? How much do you really want to have samba working. ;)

And finally, the quickest and easiest. Just use windows as the file store and Linux as the main box. Windows file sharing TO linux is all so much less infuriating.

Good Luck - Have fun and remember to share your findings.

---

