---
title: "First Class client from Softarc"
date: 2006-11-13
forum: General Help
---

### Post by patanjali on 2006-11-13
Iam trying to install the First Class client for Linux.  The zip file is downloaded and the files extracted, but Synaptic can't see them (because they are not a package?)

Now what?  How do I install this?  ](*,) 

Regards

patanjali

---

### Post by aysiu on 2006-11-13
If it's a .tar.gz file, it's very likely you'll have to compile it from source.

Read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by patanjali on 2006-11-13
The file I am trying to install has .tar.bz2 as extensions to its name.  When I try to untar it I get a message "not a .gz file".

How do I proceed.  Thanks for the help by the way!

Patanjali

---

### Post by aysiu on 2006-11-13
What happens when you double-click the .tar.gz2? Does it let you extract it that way?

---

### Post by patanjali on 2006-11-13
Yes, and I have done this, but I can't find an application in the extracted files.:( 

P

---

### Post by aysiu on 2006-11-13
Can you list the contents of that directory here?

Let's say, for example, it's a folder called FirstClass on your desktop, you would type in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
cd ~/Desktop/FirstClass
ls
``` and then post the output back here.

---

### Post by patanjali on 2006-11-13
I have two directories from the zip file the first is called opt.  The output of ls is

jack@Phoenix:~$ cd Desktop
jack@Phoenix:~/Desktop$ cd opt
jack@Phoenix:~/Desktop/opt$ ls
firstclass
jack@Phoenix:~/Desktop/opt$

The second directory is called usr and the output from ls for this is 

jack@Phoenix:~/Desktop/usr$ ls
share
jack@Phoenix:~/Desktop/usr$

P

---

### Post by aysiu on 2006-11-13
So once you extract the FirstClass .tar.bz2, it create a directory called */opt*, and within that is a directory called *usr*, which in turn has a directory called *share*.

What's inside *share*?

---

### Post by aysiu on 2006-11-13
By the way, I noticed you downloaded the generic version instead of the Debian one. Why don't we try the Debian one for now? It may be easier.

Paste these commands into the terminal: ```
wget -c http://www3.firstclass.com/ClientDownloads/FC81ClientDownloadFiles/fcc-8.101-1-Linux-i686.deb
sudo dpkg -i fcc-8.101-1-Linux-i686.deb
```

---

### Post by patanjali on 2006-11-13
ok I did that and I got a >deb file downloaded.  I put in my pass word  to dpkg the file and got the following output, which I guess means installing the two packages mentioned.

jack@Phoenix:~$ sudo dpkg -i fcc-8.101-1-Linux-i686.deb
Password:
Selecting previously deselected package fcc.
(Reading database ... 61366 files and directories currently installed.)
Unpacking fcc (from fcc-8.101-1-Linux-i686.deb) ...
dpkg: dependency problems prevent configuration of fcc:
 fcc depends on libqt3-mt | libqt3c102-mt; however:
  Package libqt3-mt is not installed.
  Package libqt3c102-mt is not installed.
dpkg: error processing fcc (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fcc
jack@Phoenix:~$

I am going to try installing these packages and see what transpires.  I will probably need more help later, but I will post how I get on anyway.

Thanks a lot

P

---

### Post by aysiu on 2006-11-13
Copy and paste these commands into the terminal. I've tested it. It works. The .tar.bz2 is a precompiled binary. So all you have to do is run it, basically: ```
wget -c http://www3.firstclass.com/ClientDownloads/FC81ClientDownloadFiles/fcc-8.101-1-Linux.i686.tar.bz2
tar xvfj fcc-8.101-1-Linux.i686.tar.bz2
cd opt
sudo mv firstclass /opt
cd ..
cd usr/share/applications
sudo mv fcc.desktop /usr/share/applications/
cd /opt/firstclass/
sudo chmod +x fcc
sudo ln -s fcc /usr/bin/fcc
```

---

### Post by aysiu on 2006-11-13
I've created a script of these instructions, too. It's available on my Ubuntu webpage:
[http://www.psychocats.net/ubuntu/firstclass](http://www.psychocats.net/ubuntu/firstclass)

---

### Post by patanjali on 2006-11-15
I now have First Class Client launcher under Applications-->Internet but when I click it I get the timer which runs for a while, but the program never gets  started.

Help!:???:

---

### Post by aysiu on 2006-11-15
> **patanjali said:**
> I now have First Class Client launcher under Applications-->Internet but when I click it I get the timer which runs for a while, but the program never gets  started.

Help!:???:
Did you install it by running the script or by using the .deb file?

---

### Post by patanjali on 2006-11-15
I used the script you gave me.

Patanjali

---

### Post by aysiu on 2006-11-15
Can you post the terminal output of these commands (in this order)? ```
cd /opt
ls
cd firstclass
ls
fcc
./fcc
```

---

### Post by patanjali on 2006-11-15
Here is the output:

jack@Phoenix:/$ cd /opt
jack@Phoenix:/opt$ ls
firstclass
jack@Phoenix:/opt$ cd firstclass
jack@Phoenix:/opt/firstclass$ ls
download  fcc      fcctemp  fcp             Images   settings
fcapps    fcc.rez  fcfonts  firstclass.png  plugins  tools
jack@Phoenix:/opt/firstclass$ fcc
bash: fcc: command not found
jack@Phoenix:/opt/firstclass$ ./fcc
./fcc: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory
jack@Phoenix:/opt/firstclass$

p

---

### Post by aysiu on 2006-11-15
That's weird. I tested the script out on a live CD (default Ubuntu... it was Kubuntu, actually), and it didn't complain about any missing libraries. The weird part is that that library isn't even in the Ubuntu repositories.

Any chance you could have removed a library or something?

---

### Post by gare on 2006-11-26
Hi -- First Thanks for posting your script and howto at 

[http://www.psychocats.net/ubuntu/firstclass](http://www.psychocats.net/ubuntu/firstclass)

Thought you would want to know that there is one typo in the script installfirstclass.sh:

> 
sudo mv opt/firstclass /opt

should be 

> sudo mv opt/firstclass /opt/firstclass

Otherwise, the script worked great on my Ubuntu 6.1 Edgy Eft!  Thanks so much!

---

### Post by aysiu on 2006-11-26
I appreciate the note, but it's not a typo, actually. That command moves the firstclass folder in opt to /opt so that you now have /opt/firstclass.

Try it if you don't believe me.

---

### Post by ayoli on 2006-12-03
> **patanjali said:**
> Here is the output:

jack@Phoenix:/$ cd /opt
jack@Phoenix:/opt$ ls
firstclass
jack@Phoenix:/opt$ cd firstclass
jack@Phoenix:/opt/firstclass$ ls
download  fcc      fcctemp  fcp             Images   settings
fcapps    fcc.rez  fcfonts  firstclass.png  plugins  tools
jack@Phoenix:/opt/firstclass$ fcc
bash: fcc: command not found
jack@Phoenix:/opt/firstclass$ ./fcc
./fcc: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory
jack@Phoenix:/opt/firstclass$

p

> **aysiu said:**
> That's weird. I tested the script out on a live CD (default Ubuntu... it was Kubuntu, actually), and it didn't complain about any missing libraries. The weird part is that that library isn't even in the Ubuntu repositories.

Any chance you could have removed a library or something?

the missing package is libqt3-mt which comes with kde not with gnome, but is installable.

---

### Post by aysiu on 2006-12-03
> **ayoli said:**
> the missing package is libqt3-mt which comes with kde not with gnome, but is installable.
Thanks for letting me know. I've updated the script to make sure *libqt3-mt* is installed.

---

### Post by ayoli on 2006-12-04
> **aysiu said:**
> Thanks for letting me know. I've updated the script to make sure *libqt3-mt* is installed.

```
ldd /opt/firstclass/fcc
```

will show you all libs used by fcc

---

### Post by gare on 2006-12-06
Thanks for clarification! sry to clutter forum & thanks again for the walk through.  I set up some dirs w/ same logic and the mv command worked just as you described.  I have no explanation for the error I encountered; perhaps a permissions problem or other situation I created.

---

### Post by timh on 2007-01-05
There is a new version out now (8.315-2)

[http://www.galacticomm.org/downloads/fcc-8.315-2-Linux-i686.deb?FCItemID=S01C26E28](http://www.galacticomm.org/downloads/fcc-8.315-2-Linux-i686.deb?FCItemID=S01C26E28)

They have a .deb package, but it doesn't seem to work. It installs fine, but hangs when first run (splash screen, then just sits). (on a clean install of 6.10 on an acer 5670 laptop)

Anyone else able to get it to run?

---

### Post by Toddy on 2007-01-07
Thanks aysiu.  Your FirstClass script worked a treat.

---

### Post by aysiu on 2007-01-07
> **Toddy said:**
> Thanks aysiu.  Your FirstClass script worked a treat.
You're welcome!

---

### Post by pshuttle on 2007-02-01
Hi,

I am having problems with the script youhave kindly provided on your website aysiu.  I follow the instructions to the letter but when I try to run the FCC client I get this error message: 

bash: /usr/bin/fcc: cannot execute binary file

I will post below the terminal output when i run the script.

Please help as I am really stuck and could do with some help. 

Thanks in advance,

Pete 


[FONT="Courier New"][FONT="Courier New"]manager@manager-desktop:~$ 
manager@manager-desktop:~$ cd ~/Desktop
manager@manager-desktop:~/Desktop$ chmod +x installfirstclass.sh
manager@manager-desktop:~/Desktop$ ./installfirstclass.sh 

Making sure that the proper library is installed to run FirstClass

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_GB         
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Translation-en_GB
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Sources
Fetched 3B in 4s (1B/s)  
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

Downloading the FirstClass client

--09:35:43--  [http://www3.firstclass.com/ClientDownloads/FC81ClientDownloadFiles/fcc-8.101-1-Linux.i686.tar.bz2](http://www3.firstclass.com/ClientDownloads/FC81ClientDownloadFiles/fcc-8.101-1-Linux.i686.tar.bz2)
           => `fcc-8.101-1-Linux.i686.tar.bz2'
Resolving www3.firstclass.com... 198.133.37.8
Connecting to www3.firstclass.com|198.133.37.8|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,509,601 (3.3M) [application/octet-stream]

100%[====================================>] 3,509,601     64.74K/s    ETA 00:00

09:36:37 (63.42 KB/s) - `fcc-8.101-1-Linux.i686.tar.bz2' saved [3509601/3509601]


Unzipping the installation files

opt/firstclass/
opt/firstclass/download/
opt/firstclass/fcc.rez
opt/firstclass/fcapps
opt/firstclass/settings/
opt/firstclass/settings/home.fc
opt/firstclass/plugins/
opt/firstclass/fcc
opt/firstclass/fcfonts
opt/firstclass/fcp/
opt/firstclass/fcp/High-Speed Internet.FCP
opt/firstclass/fcp/Local Network.FCP
opt/firstclass/fcp/Dialup Internet.FCP
opt/firstclass/fcp/Internet.FCP
opt/firstclass/firstclass.png
opt/firstclass/Images/
opt/firstclass/fcctemp/
opt/firstclass/tools/
opt/firstclass/tools/american.fcc
opt/firstclass/tools/user.fct
opt/firstclass/tools/american.fct
usr/share/applications/fcc.desktop

Removing the zipped file


Moving FirstClass to its own directory


Removing obsolete directory


Making sure menu entry is in place


Removing other obsolete directory


Making the FirstClass launcher executable


Making the FirstClass launcher universal


Done. Now FirstClass client should be installed

manager@manager-desktop:~/Desktop$ fcc
bash: /usr/bin/fcc: cannot execute binary file
manager@manager-desktop:~/Desktop$ 

[/FONT][/FONT]

---

### Post by aysiu on 2007-02-01
It's actually been a while since I wrote that script. I haven't tested it recently, but it worked at the time.

Can you try this?

```
cd /opt/firstclass
sudo chmod +x fcc
./fcc
``` If that works, maybe we can figure out what went wrong.

---

### Post by pshuttle on 2007-02-05
Hi,

I will try it this afternoon and post the results.

Cheers,

Pete

---

### Post by pshuttle on 2007-02-05
Ok I tried again but it still did not work :( . Here is the terminal response:

manager@manager-desktop:/opt/firstclass$ sudo chmod +x fcc
Password:
manager@manager-desktop:/opt/firstclass$ fcc
bash: /usr/bin/fcc: cannot execute binary file
manager@manager-desktop:/opt/firstclass$manager@manager-desktop:/opt/firstclass$ 

Any ideas?

Cheers,

Pete

---

### Post by aysiu on 2007-02-05
What about ```
cd /opt/firstclass
./fcc
```?

---

### Post by pshuttle on 2007-02-06
Ok same error message.

What do you think is actually wrong here?

[FONT="Comic Sans MS"]manager@manager-desktop:~$ cd /opt/firstclass
manager@manager-desktop:/opt/firstclass$ ./fcc
bash: ./fcc: cannot execute binary file
manager@manager-desktop:/opt/firstclass$ fcc
^[[3~bash: /usr/bin/fcc: cannot execute binary file
manager@manager-desktop:/opt/firstclass$ [/FONT]

I really appreciate the help by the way :)

Pete

---

### Post by aysiu on 2007-02-06
I don't know what to tell you.

I just ran the script on the Ubuntu Edgy live CD and it appears to work just fine (see attached screenshot).

Is there anyone else who's experiencing this problem? Any ideas what might be causing it?

---

### Post by pshuttle on 2007-02-06
Hmm very strange. It is almost like Ubuntu does not know what to do with the fcc file? It does not seem to know how to launch it.

I will remove First Class again and follow your instructions again to see what happens.

Pete

---

### Post by pshuttle on 2007-02-08
Just thought of a reason why this is not working. I am running Ubuntu on an iMac G5 64bit processor - will this cause problems for some programs?

Pete

---

### Post by aysiu on 2007-02-08
That could be it.

If you're using PowerPC or 64-bit, I don't know if that binary will work.

---

### Post by seshomaru samma on 2007-02-11
Just wanted to thank Aysiu . I'm an OU student (open university UK) which uses First Class , I always assumed it wont run on Linux cause they openly state that it's only for Windows,
I followed Aysiu directions :
```
wget -c http://www3.firstclass.com/ClientDownloads/FC81ClientDownloadFiles/fcc-8.101-1-Linux-i686.deb
sudo dpkg -i fcc-8.101-1-Linux-i686.deb
```
and I have First Class on my Ubuntu now!
thanks

---

### Post by Mip5 on 2007-02-22
> **aysiu said:**
> I've created a script of these instructions, too. It's available on my Ubuntu webpage:
[http://www.psychocats.net/ubuntu/firstclass](http://www.psychocats.net/ubuntu/firstclass)

Thanks for the script. I'm running this on a amd64 kubuntu Edgy install.

It installed well, but launching it gave the following error:

fcc: error while loading shared libraries: libasound.so.2: cannot open shared object file: No such file or directory

I looked in /opt/firstclass and can see that libasound.so.2 is a link:
 
23 2006-10-31 21:57 libasound.so.2 -> /usr/lib/libasound.so.2

I followed that link, and saw that it is a link as well:

lrwxrwxrwx  1 root root       18 2007-02-21 21:10 libasound.so.2 -> libasound.so.2.0.0

That file does exist:
-rw-r--r--  1 root root   883416 2006-07-13 07:56 libasound.so.2.0.0

I'm not sure where this is breaking down.

Any ideas? 

Thanks in advance!

---

### Post by aysiu on 2007-02-22
I don't know if it'll work on AMD64, to be honest.

---

### Post by Mip5 on 2007-02-22
> **aysiu said:**
> I don't know if it'll work on AMD64, to be honest.

Yeah, it appears not to work. I don't understand why it wouldn't work. I don't really care about sound. Is there a way I could make it ignore the libasound file?

I wonder if it would work if I compiled it from source?

Thanks for your work on this anyway. I really do find the effort and helpfulness from folks like yourself inspiring. 

M

---

### Post by aysiu on 2007-02-22
It would probably work if compiled from source. The version I use in the script is a precompiled binary, and I'm guessing the binary is precompiled for x86, not AMD64.

---

### Post by gare on 2007-03-09
Hi - Just installed the Linux Debian Intel version from here:

[http://www.firstclass.com/clientdownloads/FC83LinuxDownloadPage](http://www.firstclass.com/clientdownloads/FC83LinuxDownloadPage)

Nice Installer; even overwrote my previous install.

So far, so good...

---

### Post by dstubb on 2007-03-22
Can anyone confirm if this works on PPC?  We have ubuntu on our slot load iMacs and would be great to put FC on them.

---

### Post by aysiu on 2007-03-22
Since it's a precompiled binary, I don't think it'd work on PPC.

Maybe SoftArc has released the source code, and you could compile it for PPC?

**Edit**: Nope. When you check [the download page at SoftArc](http://www.firstclass.com/ClientDownloads/FC83LinuxDownloadPage), you see four Intel binaries for Fedora, SuSE, Debian, and "generic."

---

### Post by gare on 2007-04-05
> **gare said:**
> Hi - Just installed the Linux Debian Intel version from here:

[http://www.firstclass.com/clientdownloads/FC83LinuxDownloadPage](http://www.firstclass.com/clientdownloads/FC83LinuxDownloadPage)

Nice Installer; even overwrote my previous install.

So far, so good...

This stopped working after the first time.  :(

---

### Post by pgn674 on 2007-04-24
As instructed here:
[http://www.psychocats.net/ubuntu/firstclass](http://www.psychocats.net/ubuntu/firstclass)
I'm posting in this thread that there is now a FirstClass version 8.315-2 available for Linux, here:
[http://www.firstclass.com/clientdownloads/FC83LinuxDownloadPage](http://www.firstclass.com/clientdownloads/FC83LinuxDownloadPage)

---

### Post by aysiu on 2007-04-24
> **pgn674 said:**
> As instructed here:
[http://www.psychocats.net/ubuntu/firstclass](http://www.psychocats.net/ubuntu/firstclass)
I'm posting in this thread that there is now a FirstClass version 8.315-2 available for Linux, here:
[http://www.firstclass.com/clientdownloads/FC83LinuxDownloadPage](http://www.firstclass.com/clientdownloads/FC83LinuxDownloadPage)
Thanks for letting me know. I'll update it as soon as I've tested a new version.

---

### Post by aysiu on 2007-04-24
I've updated the page, but from now on, it's in the community docs.

The Debian package makes the script a little obsolete.

[https://help.ubuntu.com/community/FirstClass](https://help.ubuntu.com/community/FirstClass)

---

### Post by il-luzhin on 2007-08-21
fcc suddenly stopped working.  
```
fcc: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory
```

I have reinstalled libqt-mt a number of times including dev and headers using symantec.  Seemed to work but when I tried to remove/install these libs using apt-get it "couldn't find packages".  

As a last ditch effort (I know, a long shot) I also reinstalled fcc-8.315-2-Linux-i686.deb a few times using dpkg but alas, I have failed.  I must have done a good job screwing up this time.  

Any suggestion appreciated.  Thanks.

---

### Post by black_box_beast on 2007-08-30
I am having the same libqt error.  I had it running fin on my 32-bit intel laptop, but i haven't been able to get it running on my amd 64 machine.  I'd appreciate any help or ideas on how to solve this problem.  

Thanks

Evan

---

### Post by vmartel08 on 2007-09-24
I installed FirstClass Client 8.315-2 for Linux (Debian Intel) on Ubuntu 7.04 Feisty Fawn.

I double clicked on the file fcc-8.315-2-Linux-i686.deb and acknowledged the installation of the required packages.

When I run /usr/bin/fcc, the program starts and I get :

```

vilevesq@vilevesq-tp:~$ fcc
WARNING: X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
WARNING: Failed to open device
WARNING: X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
WARNING: Failed to open device
SARegisterProtocolApp(nntp,/usr/bin/konqueror)
SARegisterProtocolApp(http,/usr/bin/konqueror)
SARegisterProtocolApp(https,/usr/bin/konqueror)
SARegisterProtocolApp(ftp,/usr/bin/konqueror)
SARegisterProtocolApp(mailto,fcc)
FirstClass Client 8.315-2
Qt Toolkit Version 3.3.7
Word Size=32 Big Endian=FALSE

```

When I log in, I obtain :

```
RezFile:Desktop_CadetNet_LF2.jpg Version:c15ba848
RezFile:Desktop_JCR_LF2.jpg Version:c15cf57c
RequestFail rc:1010 from ObjID:-1 OpenerObjID:-1
Fileprintf:FileName:Desktop_CadetNet_LF2.jpg open msg:reFailedItem, closing,deleting

(lots more)

RequestFail rc:1010 from ObjID:-1 OpenerObjID:-1
Fileprintf:FileName:Desktop_CadetNet_LF2.jpg open msg:reFailedItem, closing,deleting
Segmentation fault (core dumped)

```

and the client crashes instantly.

Maybe someting is missing (some package or library) or corrupted. Anybody has a suggestion so I can correct this issue ?

---

### Post by cusavior on 2007-12-04
For those who were trying to run FirstClass CLient on AMD64, I found a way to get it running.  I ran across some notes on how to get Skype running on Ubuntu AMD64 ([http://vegdave.wordpress.com/2007/03/22/notes-on-installing-skype-on-ubuntuamd64/]("http://vegdave.wordpress.com/2007/03/22/notes-on-installing-skype-on-ubuntuamd64/")), and it seems that the same process works for the 32 bit precompiled fcc binary.

You have to download the 32 bit version of libqt3-mt from [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") and install it with the --force-architecture flag

```
dpkg --force-architecture -i libqt3-mt_3.3.8really3.3.7-0ubuntu11_i386.deb
```

Then to run FirstClass, use:

```
linux32 /opt/firstclass/fcc
```

The only thing I'm not sure of is if this will cause problems with other applications that expect to have the 64 bit version of libqt3 ... but at least it gets FirstClass working on my laptop.

EDIT:  well, it turns out that this does in fact break other programs.  However, I coppied the library into the lib32 directory and reinstalled the 64bit version with apt-get and now everything seems to work:
```

sudo cp /usr/lib/libqt-mt.so.3.3.7 /usr/lib32/
sudo ln -s /usr/lib32/libqt-mt.so.3.3.7 /usr/lib32/libqt-mt.so.3
sudo apt-get install libqt3-mt

```

---

### Post by il-luzhin on 2008-01-12
O cusavior, that's as close as I've ever come. Thanks for the pointers but I wonder if anyone has a suggestion.

It tells me my user name or password is incorrect, which it is not.

In case anyone can help,
```

SARegisterProtocolApp(ftp,/usr/bin/konqueror)
SARegisterProtocolApp(mailto,fcc)
FirstClass Client 8.315-2
Qt Toolkit Version 3.3.7
Word Size=32 Big Endian=FALSE
Error: Attempt to free invalid pointer (0xF660B008).
         * Stack frame looks damaged.  Possible buffer overflow.
         * Stack frame looks damaged.  Possible buffer overflow.


```

---

### Post by pazzypunk on 2008-01-20
I'm also trying to install on a AMD64 and running into problems.  I seemed to have been able to go through the steps of the installation (trying cusavior's approach) but when I try to run linux32 /opt/firstclass/fcc, it tells me that there is no file or directory.  When I look at the contents of the directory, I can see fcc there, but I've had no luck trying to run it.  I always get the reply "no such file or directory."

---

### Post by _oOMOo_ on 2008-01-31
I downloaded the libqt3-mt_3.3.8really3.3.7-0ubuntu11_i386.deb as cusavior suggested, to my Desktop, then extracted the .deb then data.tar.gz on the Desktop too.

Then I copied the whole of the contents of the extracted lib folder into lib32 like this:

```
sudo cp -R /home/$username/Desktop/usr/lib/* /usr/lib32/
```

and firstclass works now.

---

### Post by black_box_beast on 2008-02-02
Thanks _oOMOo_ for the help. Not sure why I didn't think to do that.

---

### Post by ipx on 2008-06-16
Thanks alot for the script, though I dont know if this is correct;
Your website states this;
> 
Installing FirstClass
Paste these commands in the terminal:
```
wget -c http://www3.firstclass.com/ClientDownloads/FC83ClientDownloadFiles/fcc-8.315-2-Linux-i686.deb
sudo ln -s /opt/firstclass/fcc /usr/bin/fcc 
```

That's it. Keep in mind that the launcher for FirstClass will be the word fcc (for FirstClass Client).

Right. So, first you download the .deb-file. Secondly, you make a symbolic link from a file that yet does not exist? Where is the install? :)

(Actually I know how to do it, im just more or less curious if this is a way to go or not)

Am I right when I say that there should be one line in the middle;
```
sudo dpkg -i fcc-8.315-2-Linux-i686.deb
```?

Also, the website was updated today "Page updated 06/16/2008" so I guess it might've been some hasty mistake. :)

---

### Post by ipx on 2008-06-16
> **ipx said:**
> Thanks alot for the script, though I dont know if this is correct;
Your website states this;

Right. So, first you download the .deb-file. Secondly, you make a symbolic link from a file that yet does not exist? Where is the install? :)

(Actually I know how to do it, im just more or less curious if this is a way to go or not)

Am I right when I say that there should be one line in the middle;
```
sudo dpkg -i fcc-8.315-2-Linux-i686.deb
```?

Also, the website was updated today "Page updated 06/16/2008" so I guess it might've been some hasty mistake. :)


EDIT: I want to clarify that im not complaining in any way!

---

### Post by aysiu on 2008-06-16
You're correct, and I've updated the site.

---

