---
title: "Why doesn't home networking work with Ubuntu?"
date: 2007-01-21
forum: General Help
---

### Post by thenetduck on 2007-01-21
Hi, 
 My brother and myself are trying to share folders from one computer to another and we both are using ubuntu edgy. We are having problems because at first I thought it was cool that all we needed to do is right click on the folder we wanted to share and click "share folder" but it seems like the option was put there with no functionality. It seems like a simple task to just share a folder over a network but it doesn't work. Sorrry to vent, I need help doing this but it seems that none really has a good answer on how to network two computers using Ubuntu together. Using Windows it took like 3 min but I have spent hours with Ubuntu with no success. Does anyone know hwo to network to computers together so they can both share files from one another? Thanks,
 The Net Duck

---

### Post by Garyu on 2007-01-21
There are many ways to network with Ubuntu. For example:

1) SSH
Secure shell (I think?). With this you can log on to computers over your LAN and run commands or do whatever in terminal mode. Did your brother lock himself in your room with your computer? Just SSH into your own computer and kick him out, kill his processes and reboot your computer over LAN. While you're at it, copy some files to the computer you are at.

You need to install SSH-server, because at least last I checked only the client was installed by default. Just go to Synaptic and search for ssh and install basically everything.

In terminal mode, use "ssh IP-number" to connect to a host. Then you can run commands like normal, only they are run on the host computer not the one you're sitting on. Use "scp" command to copy files over the network.

In nautilus: Press Ctrl-L to show "Location" (or change your settings so it is always visible), then type in "ssh://ip-number/" to connect to a host. You can drag and drop files like normal. No setup is needed (only install on all computers and use).

There are SSH-clients for windows machines as well. Just google for it.

2)
SAMBA
Windows uses some sort of SMB protocol to share files over a network, so the thing to use if you want to share files with windows computers is SAMBA. 

Go to main menu System -> Administration -> Network. In the General tab, make sure your domain is MSHOME (at least for talking to XP Home computers). You might want to check the box here too, but I'm actually not sure what this does. I've never configured samba the GUI way. Anyway, after this you should be able to right-click a folder and share it. 

If the GUI-way doesn't work for you, you will have to go through manual setup. 
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)

3)
NFS
Network File System is a common way to share files. Personally, I've never even considered using it after I discovered the power of SSH. And I only use SAMBA on other networks where there are Windows computers. Using Samba for linux-to-linux file sharing (like some do) is just not well thought through. NFS is an option, but for me SSH has always been the best choice.

There are other ways too (vsftpd for FTP-sharing and so on) but one of the above should be the best choice for you depending on your LAN-configuration and personal preferences...

---

### Post by lamadredelsapo on 2007-01-21
Thanks for the info, i was quite stuck at that problem.

---

### Post by tom56 on 2007-01-21
When you right click and click share folder, a dialogue should come up asking whether you want to use Samba or NFS. If you are sharing with another Ubuntu computer choose NFS. It should now be visible to the other guy under "Network Servers".

EDIT: Also there are a load of solutions out there that make use of Apple's Bonjour, such as GShare - [http://yimports.com/~cpinto/projects/gnome/gshare/](http://yimports.com/~cpinto/projects/gnome/gshare/). However, the method above should work and is supported by default.

---

### Post by thenetduck on 2007-01-21
That's the think, I choose NFS but it doesn't show up on his computer... I can't imagine why? Does our router have to be configure in a sertain way?

---

### Post by Garyu on 2007-01-21
> **thenetduck said:**
> That's the think, I choose NFS but it doesn't show up on his computer... I can't imagine why? Does our router have to be configure in a sertain way?

For a proper guide on NFS installation, see this:
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by houstonbofh on 2007-01-21
You can also mount FTP sites as a drive on the desktop.  So ProFTPd on both systems will also work.  I find FTP to be the most stable way top move files.

---

### Post by rianquinn on 2007-01-21
I use FTP. It works great. 

sudo apt-get install pure-ftpd 

Thats all you need to do. I have had so many problems with Samba and NFS. And believe me the GUI's in Ubuntu and Kubuntu simply do not work out of box. 

For example, to get windows to read your Samba shares you need to setup passwords for all of your users. The GUI's do not do this, or even hint that needs to be done. Kubuntu's Samba setup is terrible (although KDE's default Samba setup is not any better). 

The other thing I noticed is that you need a windows machine in your network to make Samba work correctly. For some reason you can correctly setup Samba and nothing shows up in Nuatilus or Konqueror  until a Windows machine is introduced into the picture. Then all of a sudden everything works fine. Go figure.... Windows helping Linux work. 

I really wish the Ubuntu developers could make Windows networking as easy as Microsoft makes it. So that I could easily setup Windows Networking and be done.

---

### Post by thenetduck on 2007-01-21
How do you use pure-ftpd ?

---

### Post by Garyu on 2007-01-21
> **rianquinn said:**
> I really wish the Ubuntu developers could make Windows networking as easy as Microsoft makes it. So that I could easily setup Windows Networking and be done.

Microsoft makes networking easy? Bah. I've spent hour upon hour with trying to make MS networks work. Sometimes it works and you don't know why, and then it stops working without any explanation to why it wouldn't work. With linux (Ubuntu) it works every time, with the following very easy steps:

1) sudo apt-get install ssh-server sshfs
2) Ctrl-L in Nautilus, "ssh://computer/", drag and drop files
3) To mount a network share, look at [this]("https://help.ubuntu.com/community/SSHFS")

For more information about SSH:
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

The only thing that could make it any easier is if ssh-server was installed by default. Now only the client is default. If you want access from Microsoft stations: [http://www.putty.nl/](http://www.putty.nl/)

I have actually had a few problems on my home network quite recently. What caused the errors? A friend of mine was trying to connect his laptop through my network while he was visiting. XP Home made the router die (a D-Link router). Don't ask me how, I haven't got a clue. Every 10 minutes or so we would have to restart the router. When the Microsoft XP Home laptop was disconnected, the errors disappeared. With three Ubuntu computers on my LAN I have never encountered this problem before. And you're saying Microsoft makes networking easy?  ](*,) 

Have you ever tried networking a computer with XP Home and connect a computer with XP Professional? The XPPro uses "WORKGROUP" while the workgroup of XPHome is "MSHOME". If you are very lucky they will see eachother on the network, but you will never be able to share files between them. Changing the name of the workgroup on one of the computers will...not help at all. Why? Who knows. Home and Pro are invisible to eachother on a network, that's just the way it is. I've tried this with several different computers and I always end up with the same results. Two XP machines can only talk if they are exactly the same versions. And you're saying Microsoft makes networking easy? ](*,) 

Linux is the best thing that ever happened to anything called a network. Which is why most servers on the internet run linux. And you don't need to be a computer wizard to make things work, as you need to be with MS products.

As for using Samba for linux-to-linux networking, why would anyone want to do that? And using FTP on a LAN, sure, it works, but why not use SSH which is 10 times better in every aspect?

---

### Post by BLTicklemonster on 2007-01-21
> **Garyu said:**
> There are many ways to network with Ubuntu. For example:

1) SSH
Secure shell (I think?). With this you can log on to computers over your LAN and run commands or do whatever in terminal mode. Did your brother lock himself in your room with your computer? Just SSH into your own computer and kick him out, kill his processes and reboot your computer over LAN. While you're at it, copy some files to the computer you are at.

You need to install SSH-server, because at least last I checked only the client was installed by default. Just go to Synaptic and search for ssh and install basically everything.

In terminal mode, use "ssh IP-number" to connect to a host. Then you can run commands like normal, only they are run on the host computer not the one you're sitting on. Use "scp" command to copy files over the network.

In nautilus: Press Ctrl-L to show "Location" (or change your settings so it is always visible), then type in "ssh://ip-number/" to connect to a host. You can drag and drop files like normal. No setup is needed (only install on all computers and use).

There are SSH-clients for windows machines as well. Just google for it.

2)
SAMBA
Windows uses some sort of SMB protocol to share files over a network, so the thing to use if you want to share files with windows computers is SAMBA. 

Go to main menu System -> Administration -> Network. In the General tab, make sure your domain is MSHOME (at least for talking to XP Home computers). You might want to check the box here too, but I'm actually not sure what this does. I've never configured samba the GUI way. Anyway, after this you should be able to right-click a folder and share it. 

If the GUI-way doesn't work for you, you will have to go through manual setup. 
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)

3)
NFS
Network File System is a common way to share files. Personally, I've never even considered using it after I discovered the power of SSH. And I only use SAMBA on other networks where there are Windows computers. Using Samba for linux-to-linux file sharing (like some do) is just not well thought through. NFS is an option, but for me SSH has always been the best choice.

There are other ways too (vsftpd for FTP-sharing and so on) but one of the above should be the best choice for you depending on your LAN-configuration and personal preferences...

I followed your gui setup, and this shows up in /smb.conf

[Samba Music Shared]
path = /media/hda5/Shared
available = yes
browsable = yes
public = yes
writable = no

but I can't see this on an xp machine on my network. Heck, I can't see anything from here, either.

I did sudo /etc/init.d/samba too.

I can't understand why there's no wizard for retards like me. I just want to share my files. (funny I can share files illegally with a breeze using frostwire, but I can't share stuff from one side of my house to the other with linux's networking without searching for answers for hours on end)

---

### Post by thenetduck on 2007-01-21
> **Garyu said:**
> 
2) Ctrl-L in Nautilus, "ssh://computer/", drag and drop files


Ok does this mean the computers "Name" like Ubuntu-Desktopcomputer or does this mean that computers IP adress? Little confused. Thanks, 
Also, when using SSH, I have to know that computers username and password. In my situation, my brother does not want to know that everytime I share something, we just need to share a folder.

 The Net Duck

---

### Post by Garyu on 2007-01-21
> **thenetduck said:**
> Ok does this mean the computers "Name" like Ubuntu-Desktopcomputer or does this mean that computers IP adress? Little confused. Thanks, 

 The Net Duck

Well, that depends on whether or not you have netbios support on your system. With netbios support, use the name, without netbios support, use the IP-address. If you don't know, use the IP-address as that will always work.

To get netbios support all you need to do is install winbind and add WINS-support as described in this howto: 
[http://www.ubuntuforums.org/showthread.php?t=88206](http://www.ubuntuforums.org/showthread.php?t=88206)

Samba can also be used to provide netbios names, described here:
[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

---

### Post by Garyu on 2007-01-21
> **BLTicklemonster said:**
> I followed your gui setup, and this shows up in /smb.conf

but I can't see this on an xp machine on my network. Heck, I can't see anything from here, either.

I can't understand why there's no wizard for retards like me. I just want to share my files.

You might want to compare your smb.conf with the one in this howto:
[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)
This howto is written for Dapper though (or even Breezy?), so it won't look exactly the same, but maybe you can extract something to add to your smb.conf to make it work. Configuring Samba will often mean some hassling with /etc/samba/smb.conf to make sure all the settings are set right. They are working on a GUI tool for this which will be included in Feisty Fawn, but until then we will have to edit text files. If you use Samba, it means you are using Windows, so why don't you do yourself a favor and migrate 100% to Ubuntu instead? ;-)

Anyway, I provided a fairly simple guide for SSH above, just look at the post directly above the one you made. Use that instead (even on windows) and you will see that it is a lot more easy to setup and use than Samba will ever be. :cool:

---

### Post by BLTicklemonster on 2007-01-22
> **Garyu said:**
> Microsoft makes networking easy? Bah. I've spent hour upon hour with trying to make MS networks work. Sometimes it works and you don't know why, and then it stops working without any explanation to why it wouldn't work. With linux (Ubuntu) it works every time, with the following very easy steps:

1) sudo apt-get install ssh-server sshfs
2) Ctrl-L in Nautilus, "ssh://computer/", drag and drop files
3) To mount a network share, look at [this]("https://help.ubuntu.com/community/SSHFS")

For more information about SSH:
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

The only thing that could make it any easier is if ssh-server was installed by default. Now only the client is default. If you want access from Microsoft stations: [http://www.putty.nl/](http://www.putty.nl/)

I have actually had a few problems on my home network quite recently. What caused the errors? A friend of mine was trying to connect his laptop through my network while he was visiting. XP Home made the router die (a D-Link router). Don't ask me how, I haven't got a clue. Every 10 minutes or so we would have to restart the router. When the Microsoft XP Home laptop was disconnected, the errors disappeared. With three Ubuntu computers on my LAN I have never encountered this problem before. And you're saying Microsoft makes networking easy?  ](*,) 

Have you ever tried networking a computer with XP Home and connect a computer with XP Professional? The XPPro uses "WORKGROUP" while the workgroup of XPHome is "MSHOME". If you are very lucky they will see eachother on the network, but you will never be able to share files between them. Changing the name of the workgroup on one of the computers will...not help at all. Why? Who knows. Home and Pro are invisible to eachother on a network, that's just the way it is. I've tried this with several different computers and I always end up with the same results. Two XP machines can only talk if they are exactly the same versions. And you're saying Microsoft makes networking easy? ](*,) 

Linux is the best thing that ever happened to anything called a network. Which is why most servers on the internet run linux. And you don't need to be a computer wizard to make things work, as you need to be with MS products.

As for using Samba for linux-to-linux networking, why would anyone want to do that? And using FTP on a LAN, sure, it works, but why not use SSH which is 10 times better in every aspect?

Nice try, but that does not work at all. 

Windows is easier, I don't see how you can say it's not, then post that mish mash of stuff that doesn't even work.

---

### Post by BLTicklemonster on 2007-01-22
> **Garyu said:**
> You might want to compare your smb.conf with the one in this howto:
[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)
This howto is written for Dapper though (or even Breezy?), so it won't look exactly the same, but maybe you can extract something to add to your smb.conf to make it work. Configuring Samba will often mean some hassling with /etc/samba/smb.conf to make sure all the settings are set right. They are working on a GUI tool for this which will be included in Feisty Fawn, but until then we will have to edit text files. If you use Samba, it means you are using Windows, so why don't you do yourself a favor and migrate 100% to Ubuntu instead? ;-)

Anyway, I provided a fairly simple guide for SSH above, just look at the post directly above the one you made. Use that instead (even on windows) and you will see that it is a lot more easy to setup and use than Samba will ever be. :cool:

No no no no, I might want to use the windows machines for sharing files, and keep linux as an oddity, which it is at present. There is no way I'm going to waste any time ***_guessing_*** at getting a network going in linux when I can run a wizard in windows and be done with it in no time flat. "and it works".

---

### Post by thenetduck on 2007-01-22
> **BLTicklemonster said:**
> No no no no, I might want to use the windows machines for sharing files, and keep linux as an oddity, which it is at present. There is no way I'm going to waste any time ***_guessing_*** at getting a network going in linux when I can run a wizard in windows and be done with it in no time flat. "and it works".

Although I it kind of sucks. I would have to agree. Memorizing ip address is something I don't think that average user really wants to do. The great thing about Ubuntu is that we know there is a problem now we can fix it! 

 The Net Duck

---

### Post by chipmonk010 on 2007-01-22
If you dont want to memorize ip addresses just put them in your host file

sudo gedit /etc/host

192.168.1.40 server
192.168.1.30 laptop 

etc

or goto System > administration >networking >click on hosts tab


I wont get involved with the windoz vs linux networking debate but i will say linux acts as expected when you know what your doing windoz on the other hand acts like a drunk baby no matter how consistent the user:biggrin:

---

### Post by Garyu on 2007-01-22
> **chipmonk010 said:**
> I wont get involved with the windoz vs linux networking debate but i will say linux acts as expected when you know what your doing windoz on the other hand acts like a drunk baby no matter how consistent the user:biggrin:

Exactly the point I was trying to make. Thank you for clarifying. :)
(this is true for most things though, not only networking)

---

### Post by BLTicklemonster on 2007-01-22
Three of you each post a thread


'HOW DO I SET UP A HOME NETWORK'

Three days apart, then go look at your replies and tell me if any one of them is the same.


:wink: 


I'm sure it's a no brainer once you get it, but I"ve been messing with ubuntu for a a year now, and every once in a while I figure maybe this will be the time I get it, and it never fails, I end up back where I started. IT OUGHT TO BE SIMPLE AND STRAIGHT FORWARD.

---

### Post by dexter on 2007-01-22
It's strange that none off those efforts have worked. Are you sure the network is configured properly ? Can you ping the other machines ?

---

### Post by Henry Rayker on 2007-01-22
After reading a samba tutorial, I had no problem setting up the networking. My Windows XP computers, though, don't operate properly at all. I can run the network configuration wizard until my fingers fall off, but they won't see one another (or my Ubuntu machines) if they don't want to...sometimes it takes a restart (or five)...my Ubuntu machines, so long as they are actually ON the network, they work all the time.

I use Thunar on my laptop and set up fusesmb here (as well as on my girlfriend's desktop...even though she's in gnome...it just feels easier to her).

I won't argue that there is more work involved with Ubuntu's networking capabilities, but once you do it (correctly) it will work...you can't say that much for Windows XP.

---

### Post by BLTicklemonster on 2007-01-22
I found this:
```

First, in a terminal, issue this command:
Code:

[CODE]sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.backup
```

Then this command:
Code:

```
sudo gedit /etc/samba/smb.conf
```

Then, in Gedit, paste this. Change "workgroup =" to match that of your Windows XP workgroup:
Code:

```
[global] 
workgroup = Service 
security = share 
include = /etc/samba/smbshared.conf 
wins support = no
```

Save the document. Next, issue this command.
Code:

```
sudo gedit /etc/samba/smbshared.conf
```

When Gedit comes up, paste this. Replace $$$$ with your user name leaving everything else even the quotes. Replace the "path =" with the path to the directory you wish to share:
Code:

```
[Shared] ; user="$$$$" 
force user = $$$$ 
path = /path/to/shared/directory 
writable = yes 
public = yes
```

Save the document. Reboot your PC. Also, this is assuming that you have samba installed.

Code:

```
sudo apt-get install samba
```[/CODE]


and will give it a shot tonight.

---

### Post by chipmonk010 on 2007-01-22
BL ill show you how I do things on my network perhaps it will help.

I use samba for linux to windows and linux to linux transfers heres what you need

step 1:

sudo apt-get install samba

step 2:

sudo gedit /etc/samba/smb.conf

select all > delete

*file should be empty

step 3:

enter this:

[global]
workgroup = workgroup 
netbios name = computer-name
security = share
browseable = yes
hosts allow = 192.168.1.

[share-name]
path=/path/to/share
read only = no
guest ok = yes

....as many shares as you want

step 4:

enter in terminal:

sudo /etc/init.d/samba restart

step 5:
repeat on second ubuntu comp

now you can access shared folders on comp 2 from comp 1 by going to Places > Network servers> server name > share name

no gui setup but still very doable

hope this helps

chipmonk010

---

### Post by BLTicklemonster on 2007-01-22
> **chipmonk010 said:**
> BL ill show you how I do things on my network perhaps it will help.

I use samba for linux to windows and linux to linux transfers heres what you need

step 1:

sudo apt-get install samba

step 2:

sudo gedit /etc/samba/smb.conf

select all > delete

*file should be empty

step 3:

enter this:

[global]
workgroup = workgroup 
netbios name = computer-name
security = share
browseable = yes
hosts allow = 192.168.1.

[share-name]
path=/path/to/share
read only = no
guest ok = yes

....as many shares as you want

step 4:

enter in terminal:

sudo /etc/init.d/samba restart

step 5:
repeat on second ubuntu comp

now you can access shared folders on comp 2 from comp 1 by going to Places > Network servers> server name > share name

no gui setup but still very doable

hope this helps

chipmonk010

That looks closer to what I posted. thanks. you clarified the share all you want thing I was going to ask about. I'll try it when I get done farting around.

---

### Post by chipmonk010 on 2007-01-22
> That looks closer to what I posted. thanks. you clarified the share all you want thing I was going to ask about. I'll try it when I get done farting around.

yes i forgot to mention this will allow anyone on your home network to read and write to the share

---

### Post by mdurham on 2007-01-23
Is it necessary to open a port(s) in the firewall for samba shares to work?

---

### Post by chipmonk010 on 2007-01-23
> Is it necessary to open a port(s) in the firewall for samba shares to work?

If you have a home network connected to the internet through a router/firewall and you have a firewall installed on your computer (aka firestarter) then you would have to allow the port in firestarter yes. You SHOULD NOT open the samba port of your router. Sambas port range is 137-139.

As an added side note that is really the topic of another discussion if you have a router(that has a built in firewall) there isnt really any reason to run firestarter on a home network its like running a double firewall it just adds confusion and more work when it comes to simple tasks like this.

The only time I would run firestarter would be if i was connected directly to the internet(no router) or was on an unsecure LAN (wireless hot spot, work, or office network)

---

### Post by mdurham on 2007-01-23
Thanks for the info chipmonk010

---

### Post by BLTicklemonster on 2007-01-23
It shows up on the xp boxes, and they show up on it, but that's it. No files. And it asks for passwords. Like I'm worried my kids are going to steal sensitive .. no wait, its a computer, you'd have to be a fool to keep sensitive information on a computer. 

I still don't see how you folks can do linux networking and not windows. That's pretty funny.

---

### Post by chipmonk010 on 2007-01-23
> It shows up on the xp boxes, and they show up on it, but that's it. No files. And it asks for passwords. Like I'm worried my kids are going to steal sensitive .. no wait, its a computer, you'd have to be a fool to keep sensitive information on a computer.

I still don't see how you folks can do linux networking and not windows. That's pretty funny.

you did it EXACTLY as i posted above? 

would you mind posting your smb.conf file?

---

### Post by BLTicklemonster on 2007-01-23
```
[global]
workgroup = MSHOME
netbios name = Tsark
security = share
browseable = yes
hosts allow = 192.168.1.

[share-name]
path=/media/hda5/Shared
read only = no
guest ok = yes
```

---

### Post by chipmonk010 on 2007-01-23
run this in a terminal:

chmod 7777 /media/hda5/Shared

this allows any user to read or write to the folder, im sorry i overlooked this part since when i tested the setup i posted i accessed it from my laptop on which i have the same username

this can also be done in the file browser by right clicking the shared folder >properties> permissions and select 'create and delete files' from each drop menu that has 'folder access' next to it

---

### Post by Dragon43 on 2007-02-01
Confussed old man checking in with a password question.  I hope this is the right place to post it.

I have read the whole thread so far and need one more thing answered.

I have on my 'inhouse' network: LinkSys BEFSR 81,
2 Win 98se boxes (loose collection of cheap parts) 
-- CPU's = 600Hz, 100Hz front side buss, etc.
One older HP laptop with XP home ( I hate XP )
One older "Emachine" with Ubuntu 6.06 LTS installed on it.
WilBlue Satellite ( Fastest thing we can get up here.)

******************

I have been using the Ubuntu for about 5 days now ( find it intersting and I like it) and everything is working except except one thing so far.  I can see all the computers from each other and they all show up on the network but to look into the Ubuntu machine, the Win boxes ask for a passowrd.

I see that sort of mentioned in this thread.  Where do I find that password?  

I don't mind using a password as I do not transfere stuff but maybe once a day or so.

Help !!!!!

My setup as of now.-

[http://www1.webng.com/Dragon43/cudsk02.jpg](http://www1.webng.com/Dragon43/cudsk02.jpg)

Can anyone point me in the correct direction?

Thanks

Gus aka Dragon43 aka 3½¢

---

### Post by Garyu on 2007-02-01
> **Dragon43 said:**
> I see that sort of mentioned in this thread.  Where do I find that password?  

I don't use windows, but in places where I have set up windows to work with ubuntu I make sure that the username is exactly the same on the windows machine as it is on ubuntu. Then I can use my ubuntu password to look at the shares on the ubuntu machine.

---

### Post by Dragon43 on 2007-02-02
Well, I messed it up.  Lost all internet connection.

Fought it for masny hours and now am almost back to where I was.  I am on the internet and as far as the in house network goes, I can see other computers under PLACES- NETWORK SERVERS - WINDOWS NETWORK-DOMAIN NAME (XXXX) and (-- desktop configuration unknown) off to the right.
Click on that and I see icons fdor the computers on the network but the only one which will open is this one, none of the Win Boxes will open and they were opening beofre I mucked it up. ::: sigh :::

Any ideas or help onsettings that need to be changed?

I am going to try more searches while I wait.

I am not going to change anything more until I have better info cause this is a steep learning curve for me and I have gained enough ground that I don't want to re-install and loose all the stuff I have worked through so far.

Garyu, thanks for the suggestion.  I will try it after I can fix this latest goof.  Any ideas for me?

Help !!!!!

---

### Post by BLTicklemonster on 2007-02-02
I've basically given up on any chance of networking ubuntu. I email stuff to myself with gmail if I need anything. Sharing my other stuff around the house is just a non starter now.

---

### Post by BLTicklemonster on 2007-02-02
Tell you what. Someone humor me, tell me how to remove all the networking "stuff" I've done so I can start from scratch and try again, please?

---

### Post by thenetduck on 2007-02-02
Maybe this is something they will fix on the next release of ubuntu? If not we should make sure it's at the top of the list. I feel like this is very important.

 The Net Duck

---

### Post by BLTicklemonster on 2007-02-03
You got that right. Look at every thread here about having problems networking, and at all the various ways it can be done. Excuse me? "if that doesn't work, try this..." I expected more.

---

### Post by chipmonk010 on 2007-02-03
> **thenetduck said:**
> Maybe this is something they will fix on the next release of ubuntu? If not we should make sure it's at the top of the list. I feel like this is very important.

 The Net Duck

I am not convinced its an ubuntu problem since for some(like myself) it works fine. I have a feeling it has more to do with windows not wanting to play nice.

> You got that right. Look at every thread here about having problems networking, and at all the various ways it can be done. Excuse me? "if that doesn't work, try this..." I expected more.

thats an example of one on one help for YOUR situation not a link to a howto what more is there to expect?

Sometimes networking especially when windoZ is concerned can be quirky so trial and error is sometimes needed 

if you want to start from scratch try removing samba:
sudo apt-get remove --purge samba
and reinstall it:
sudo apt-get install samba

i dont know what other "networking stuff" you have done but that will start you over with samba.

---

### Post by thenetduck on 2007-02-03
Well the thing is it works just find windows to windows networking but when it comes to Linux to Linux networking it seems to never work. Have you been able to get the Linux to Linux networking to work fine? 
 
  The Net Duck

---

### Post by chipmonk010 on 2007-02-03
> **thenetduck said:**
> Well the thing is it works just find windows to windows networking but when it comes to Linux to Linux networking it seems to never work. Have you been able to get the Linux to Linux networking to work fine? 
 
  The Net Duck

Yes. I have windows to windows, linux to windows, and linux to linux all working fine. Everyone can see everyone and access folders and files etc. I mainly use samba for all of the above just cuz its easy to just browse to folders. But NFS is also configured on my server in case i ever want to mount a network share. 

my earlier instructions were based on my actual setup that works. Its hard to really figure it out fully without being there in person but i will help as much as i can, because the ability for people to network with ubuntu is very important.

---

### Post by Dragon43 on 2007-02-04
Thanks for the info on starting over Chipmonk010.  I am about to that point.

The 'How too's' are all good but they are for XP or 2000 Pro, this old guy on Win-98 is not getting there.

Thje sad part is that a few days ago I had it seeing my copmuters and being able to get into them so I could move stuff even if I had to do all from the Ubuntu machine.  Now, since I tried to make it work both ways, I can't go either way and I can only get on the web.  Even the latest upgrades won't download, the list won't even download.  :: sigh :::

I hate to blow off SAMBA and start over, I fear I will never get back.

*::: writing down your directions and hoping. :::*

---

### Post by Dragon43 on 2007-02-04
WOW !!!  Thanks ....  It worked.  I can see the other Win-98se boxes. (2) and Ubuntu Box.

I can move stuff from the "U" box so even though I can't see into the "U" computer from the Win boxes, I don't care.  I thought I was going to have to start completely over.

Now I need to find out what the "U" Box IP# is so I can configure  ZoneAlarm.

Anyone know  how to do that?

---

### Post by Garyu on 2007-02-04
> **Dragon43 said:**
> Now I need to find out what the "U" Box IP# is so I can configure  ZoneAlarm.
Anyone know  how to do that?

ifconfig

run that command in a terminal.

---

### Post by Dragon43 on 2007-02-04
Thanks [COLOR="Blue"]Garyu[/COLOR], I kept missing the [COLOR="DarkOrange"]'p'[/COLOR] to[COLOR="Lime"] 'f'[/COLOR] switch.  I was seeing what I was expecting to see instead of what was really there.

---

### Post by BLTicklemonster on 2007-02-04
> **chipmonk010 said:**
> I am not convinced its an ubuntu problem since for some(like myself) it works fine. I have a feeling it has more to do with windows not wanting to play nice.



thats an example of one on one help for YOUR situation not a link to a howto what more is there to expect?

Sometimes networking especially when windoZ is concerned can be quirky so trial and error is sometimes needed 

if you want to start from scratch try removing samba:
sudo apt-get remove --purge samba
and reinstall it:
sudo apt-get install samba

i dont know what other "networking stuff" you have done but that will start you over with samba.


Purging. I'll look back over this thread carefully to see what to do when I install again. Thank you.

(how can I get it to work without a password? I don't have anything here or on other computers that would be worth anyone's effort to hack into. These things are for fun, not banking.)

---

### Post by chipmonk010 on 2007-02-04
> **BLTicklemonster said:**
> Purging. I'll look back over this thread carefully to see what to do when I install again. Thank you.

(how can I get it to work without a password? I don't have anything here or on other computers that would be worth anyone's effort to hack into. These things are for fun, not banking.)

As long as you do it the way i outlined you shouldnt have to type passwords.

if you do try adding:

writable = yes

to your samba share example:

[share-name]
path=/path/to/share
read only = no
guest ok = yes
writable = yes

and also make sure you chmod the shared folder like i said above.

---

### Post by mgmiller on 2007-02-04
Here is the method I used to create NFS sharing on my Ubuntu network.  It allows streaming of video with vlc and mplayer and does not require a password.

  
```
Part ONE:
NFS installation on the server


Install NFS by typing the next lines on the prompt.


sudo apt-get install debconf

sudo apt-get install libc6

sudo apt-get install libwrap0
sudo apt-get install nfs-common

sudo apt-get install sysvinit

sudo apt-get install nfs-kernel-server


Make a directory that can be accessed by anyone by typing


“mkdir /nameofthedirectory”

“chmod a+rw /nameofthedirectory”
Example...
All I did was take my existing /home/marty and chmod it.
chmod a+rw /home/marty

By using "sudo gedit /etc/exports"
change /etc/exports to add the line:

/nameofthedirectory 192,168,1,0/255,255,255,0(rw,root_squash,sync)
Example...
This is what my /etc/exports looks like:
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
/home/marty     192.168.1.0/255.255.255.0(rw,sync,no_root_squash)



type “exportfs -av” to activate

type “rpcinfo -p” to test


Part TWO:
NFS installation on the client


Make a directory to mount the server map to by typing


mkdir /mnt/nameofmountmap
Example:
sudo mkdir /mnt/server


Change the permissions, so you can read and write in it by typing


chmod a+rw /mnt/nameofmountmap
Example:
sudo chmod a+rw /mnt/server

Using "sudo gedit /etc/fstab"
change /etc/fstab to add the line:

192,168,1,NNN:/nameofdirectory /mnt/nameofmountmap nfs rw,hard,intr 0 0
(NNN is the end of the ip-adress of the server)
Example:
192.168.1.4:/home/marty	/home/marty/server nfs soft 0 0 

Or you can use the "hard" option instead.  If you use "soft" as above, if the 
server is down when you start the remote machine, you won't get an error message and 
a simple sudo mount -a after the server is booted will mount up the share.

If you use "hard" as below, you will get errors if you try to start up and the server is down
for some reason.  I use the "soft" option.

nameofserver:/nameofdirectory /mnt/nameofmountmap nfs rw,hard,intr 0 0

Finally,
Mount by typing

sudo mount -a

Finally, when it is all working, you should be able to use nautilus on the remote machine
to browse to the folder you have designated as the mount point on the remote machine. 
In this case it is /mnt/server.  
Once it is open and showing all the files, in nautilus, click on Bookmarks>Add Bookmark to create a
 quick link to the mount point.  Now it is on your Places menu and a single click there will instantly
open the share.  You can also stream over this kind of share with vlc and totem, etc.
```

I hope this makes it a little easier to understand.  I put in explanations for why you are doing stuff as well as examples of the commands to clarify things, but it makes it kind of wordy.  Try reading through it all once or twice to wrap your head around it before you try doing it.  It's really not that hard.

Good luck all.

---

### Post by ifross on 2007-02-04
Use the method above, but if you are worried about security (as you are making it writable, i would specify the ip address you want to share to in your exports file:
/path/to/folder 192.168.0.34(rw,sync,no_root_squash)

OR if you want to be all neat and tidy, ad the computers in your network to your /etc/hosts file:

192.168.0.35 desktop1
192.168.0.66 desktop2

etc

then you only have to -put the hostname in the exports file:
/path/to/folder desktop1(rw,sync,no_root_squash) desktop2(ro)

---

### Post by BLTicklemonster on 2007-02-04
This is absurd. I tried your way, and the nfs way, neither of which worked.

---

### Post by Dragon43 on 2007-02-04
Since no one is saying, I'll assume you all are talking about networking with XP, home or pro.

All my trials and tribulations are with Win-98se.

I be good to go now.  I will not try to get the Windows boxes to see into the Ubuntu box because that seems to be a real bucket of worms and I can see into all the other boxes from the Ubuntu box so I can move any files I want to from it.

Of course the Windows boxes can see each other and move files just fine.  Since both the computers I use are side by side for now, it is just a slight twist of the  chair to each keyboard and monitor.

I understand that if you have to dual boot because you have only one computer that things are a bit different.

If I did not already have spare 98se boxes that I make up for 'give aways' to those who can't afford even a used computer or to young kids of 10 -14 that want/need a computer of their own, I would be looking for a discard computer or going to a junk store and getting an old Win-98 Box from a school replacement or checking 'Craigs List' for one that someone is giving away.  

I much prefer to not be risking a bad HD crash with my main machine and having a spare, even if it is just a Win 98 machine, I will not be locked out from help if I really mess something up.

If you are poor like us, a free  from relatives or a $50 computer from a yard sale is a thing of joy.

YMMV

PS:  I am using 6.06 Ubuntu.

---

### Post by airtonix on 2007-04-16
wow, [BLTicklemonster]("http://ubuntuforums.org/member.php?u=44485")... i thought you were more level-headed than your replies here....your anger seems to be getting in front of your cognetive powers.
what ubuntu version are you using? feisty samba/ssh/nfs works perfectly for me.

if you are still on dapper, move to feisty. it has many more improvements in the gui hand holding world.

**Samba Passwords: **
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba) tells you to edit a file and store the username and password there. (think its iunsecure? well thats how windows does it as well, this is why we linux nuts prefer ssh or nfs as they are much more efficient on bandwidth and also transparently tighter on security)

[start rant]
I am a much more placid person now that i dont have to try to get windows netowrking operating in a secure and reliable fashion. When i did use windows....i went through five keyboards in the space of about three months.....they now look like lego bits.
I find it funny that windows still does not a native encrypted client to navigate network folders/shares/drives...
 [start sracasm]
Or is that becuase Microsoft expects everyone to present their files and folders for inspection by the M$CEO commisar (not bill)....ergo everyone is guilty   until proven innocent...and even then since we are spending time inspecting each of you there must be something guilty about you
 [end sarcasm]
[end rant]

Sigh...even mounting drives is automatic now....ie : 
i look into the computer:// directory in nautilus and i find all these drives that I know exist within my computer case, and double clikcing on one begines the process of mounting it, which requires a admin password...after which it is mounted for this session only.

**Seamless Networking**
and the rest of you follow this guide for a networking setup that feels more like how you use it on windozer : (ignore that it is in xubuntu) [http://ubuntuforums.org/showthread.php?t=304131&highlight=fusesmb](http://ubuntuforums.org/showthread.php?t=304131&highlight=fusesmb)

im using this fusesmb now and its great....both ways i can move a file....


lastly if you have built up a conceptual visulisation of how a network should operate from your experiences with windows....then throw out that conception.
microsoft dont get technical on the operating system becuase it equals more support time on the phone which they'd rather not employ people for.
Which is funny cause when you treat people like children they become children....so when micorsoft dumbs down the way their GUI system interacts wit he computer...the end result is dumbed down users who in effect start doing stupid things nad ergo create more problems for everyone (if not mostly by conceptualising stupid scenarios on how a network operates).
so this is why you never get any really indication about what is going on in your system.

have you tried to change the IP address in Vista? do it. compare the process to WinXP and Win98...and then compare it to Ubuntu Dapper or Feisty.

for me Vista took me an extra four or five clicks and windows to get to the actual tcp/ip properties dialouge box. in the others (winxp through to ubuntu) it is only a matter of right clicking the network icon in the notification bar and selecting properties..

so you can see microsoft are furthering heir road plan to ibfuscate the "real computer" from the user. This is ok in a network-business-enviroment where you have people from the genreal public accessing your pool of computers(like at libraries or if your renting a computer), but at home this is unacceptable.

so when you tell me that windows networking is easy i gotta laugh so hard i need to change my pants. becuase i cant tell you with out $$$$ you will not be able to do decent networking in windows.


btw BLticklemonster...is taht you in your avatar? looks great...no really im not taking the piss...looks very MilSpec. lol bigups.

---

### Post by BLTicklemonster on 2007-04-16
Shucks, you caught me having a bad scalp day, what can I say?

The new Feisty does networking automagically, so that's on less hassle. 

BUT, thank you for taking the time to share all that. That's useful information to have handy. I will need the password setting stuff so I can get to my ubuntu shared folders, I guess.

So thanks very much for the reply. 

And yes, that's what I look like when I'm in a happy mood.

---

### Post by wilberfan on 2007-04-22
I wanted to give a hats-off to Garyu for his suggestion regarding ssh....   So far, it seems a really effortless way to browse from one Feisty machine to the other!     A couple of drawbacks I have encountered in only a few minutes of playing, though,  is that Amarok and Krusader don't seem to support the ssh protocol...   :(     I have the kubuntut-desktop installed.  I mostly run gnome, however.)  

I have *never* been able to get Nautilus and Samba to play nice together--not on edgy and now on feisty, too...

Krusader seems to love samba, though... [ shrugs ] 

I've also found that the [Thunar-Native-Windows-Network-Browsing thread]("http://ubuntuforums.org/showthread.php?t=304131") works pretty well on my Feisty gnome/xubuntu machine...

---

### Post by Angellis_ater on 2007-04-23
Hi!

I have a small problem that I need to get working.

I have two computers attached via a normal switch, which means that they have different IPs and all that and aren't really apart of my "internal" network, although they're both in the same house.

Now, I've installed sshfs, open-ssh, (both client and server) on both and I can access the secondary computer from the main computer through Nautilus using "ssh:IP.NU.MB.ER/Shared Folder" and saving the username and password on my keyring. That's fine and dandy - now, I can't do the same thing from the secondary computer to this one, that's problem number 1.

Problem 2 is that I can play some files from the secondary computer (ogg-files), but not others (mp3, avi) on the primary computer. If I send a file or files to the secondary from the primary computer, they're all locked from using since the rights attached to them are specific for the primary computer user.

How do I get all of this to work? Please help!

---

### Post by berserker on 2007-04-25
> **chipmonk010 said:**
> [global]
workgroup = workgroup 
netbios name = computer-name
security = share
browseable = yes
hosts allow = 192.168.1.

[share-name]
path=/path/to/share
read only = no
guest ok = yes

....as many shares as you want

step 4:

enter in terminal:

sudo /etc/init.d/samba restart

This works perfectly on my system.  The only glitch was I had to access the network from my Windows XP VMWare session to "kick start" samba from the Linux side and now my Ubuntu box and Windows computers can see each other.  Thanks!

Hint:  I added ```
server string =
``` to the [global] section so that my Linux share only shows the name of the share "berserker" and not "Samba 3.0.24 (berserker)".

---

### Post by airtonix on 2007-05-01
Angellis_ater :
comp1= computer with good ssh
comp2= computer that cant ssh

did you take care of firewall rules?
did you log into comp1 from comp2 using your password on comp1?

comp1
did you install firestarter the GUI frontend to control the firewall that is part of your linux-kernel? 

1 - if not install it :
> sudo apt-get install firestarter2 - then run firestarter
3 - goto the policy tab
4 - right click on the upper pane (where we white-list computers to access this computer) and click 'add-rule'
5 - enter the IP address of comp2 and a comment if you want.
6 - then click the button labeled 'apply policy' at the top of the firestarter app.
7 - re-attempt your ssh connection again from comp2 it should work now.

---

### Post by BLTicklemonster on 2007-09-27
for the record:

I still have no working network here between my ubuntu and my xp machines.

the xp machines all see each other and work fine. The ubuntu machine shows up in each of them, but if I click on the icon, I am told there are permission problems, etc. 

If I am on my ubuntu machine, and click System, Administration, Network, and click on Windows Network, the next window that comes up is blank.

Once upon a time while using an earlier ubuntu, I at least could browse the windows machines. I'm using Gutsy now, and there's nothing.

Here is my samba.conf now:


[global]
workgroup = MSHOME
netbios name = bill-desktop
security = share
browseable = yes
hosts allow = 192.168.1.0

[samba]
path = /home/bill/samba
available = yes
read only = no
guest ok = yes
writable = yes
browsable = yes
public = yes
writable = yes
security = share

here is an earlier rendition of it:


[global]
workgroup = mshome
netbios name = bill-desktop
security = share
browseable = yes
hosts allow = 192.168.1.

[samba]
path = /home/bill/samba
available = yes
browsable = yes
public = yes
writable = yes
security = share

Neither way worked.

Anyone got any ideas?

---

### Post by BLTicklemonster on 2008-03-02
Ahem.

---

### Post by Dragon43 on 2008-03-02
I'm on gutsy also and I can see into the XP machines.  I have never been able to see into the Ubuntu machine with 6.06 dapper or 7.10 gutsy which I'm using now.

Sorry, no clue about why you can't get to the XP machines.
I have XP- Pro if that may make a difference.

I don't mess with those settings you are showing.  I just do the regular boxes that come up with System-Administration - Network - Network Settings and make sure all my info matches with the XP machines and all the names and 192.168.1. x or y numbers all agree and also agree with my firewall (Zone Alarm Free) settings and then I can see one way, LINUX into XP....  I had to mess with it for a while and make sure the settings held.  I also never use 'WORKGROUP' but a XXXX of my own home network on a Link Sys Router/switch... I have always done this since I first tried networking way back and had 10 - 15 computers around town in my network with me.  Some I could even open....  I just had a 'hub' back then.  I don't go no where near an DSL-Cable-LAN connection without a Router/switch between me and the net, even with just a single computer.

YMMV

---

### Post by BLTicklemonster on 2008-03-02
At this point, I can see the other machines, but I have to enter a password to log on. 

I followed the directions in the link that's in my sig (which worked flawlessly for me for a short period of time, thank you. Which leads me to believe something has been changed somewhere along the way in the updates) and I'm stuck. I entered everything like I did before, but now it won't accept my password at all.

---

### Post by Dragon43 on 2008-03-02
**BLTicklemonster  **  ::::: Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, ...... Your link worked.......  Wheeeeeee,  Have I said Thank you???   I have   been fighting this for a year......  Ye Haw !!!!!!  You da man......

Did I tell you it worked.  Your link......  Yepper......  ::: pant pant ::::: I'm about to go wonky I'm so pleased.......

:D :D  :D

---

### Post by BLTicklemonster on 2008-03-02
lmao. sad as it seems, even though it doesn't work any more, it's the best one I've found so far.









... wish it worked. :)

---

### Post by 3rdalbum on 2008-03-02
This is definitely a case of "Whatever you know is easiest". I've been using Linux for a couple of years and Samba was very easy for me to set up. I've barely ever used Windows, so I really did struggle to get Windows to recognise the shared folder. Took me longer to get Windows playing nicely than it did to get Samba sharing the folder! :-)

---

### Post by BLTicklemonster on 2008-03-02
Oh I can share the folder, no problem. Easy as pie. The problem for me has been, for the most part, getting my password to work. I can't log on when I try to view one of the other shares on the network.

---

