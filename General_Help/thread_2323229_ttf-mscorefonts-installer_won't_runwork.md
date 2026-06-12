---
title: "ttf-mscorefonts-installer won't run/work"
date: 2016-05-03
forum: General Help
---

### Post by Autodave on 2016-05-03
I installed Xubuntu 64 bit, 16.04, with no probs.  That was 9 days ago. Since then, I keep getting this message:

Failure to download extra data files

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

ttf-mscorefonts-installer

The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection.



I have tried clicking on the box to run the action now, but it never installs.  Any ideas?

---

### Post by grahammechanical on 2016-05-03
With MIcrosoft true type core fonts we get a Microsoft End User Licence Agreement (EULA). If we do not accept the agreement then the ttf-core fonts do not get installed and the ttf-mscorefonts-installer knows it has not finished its task and gives another offer. Try moving the dialog box to one side. Y9ou may see another dialog box underneath.

Regards.

---

### Post by Autodave on 2016-05-03
I will try that. However, I have been using Ubuntu for many years and I know about clicking that box: I am sure it was checked.  I'll let you know tomorrow when it pops up agin.

Well, there is nothing behind the box telling me again that the installation failed. I also tried last night to go to synaptic and I chose to reinstall it (it showed to be installed already). Got the same error again today. Any ideas what to try now?

---

### Post by QDR06VV9 on 2016-05-04
> **Autodave said:**
> Well, there is nothing behind the box telling me again that the installation failed. I also tried last night to go to synaptic and I chose to reinstall it (it showed to be installed already). Got the same error again today. Any ideas what to try now?
This happens from time to time i have seen it myself.
This works for me... run this command below, to fix the error
```
sudo apt-get install --reinstall ttf-mscorefonts-installer  

```
**And I know you already know this **but watch for the accept the EULA of Microsoft to use those font files.
This will reinstall the package, and download the data files needed to configure the package.
Kind Regards

---

### Post by Autodave on 2016-05-04
Tried that: here is part of what I got:

```
Get:1 [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe) [969 B]
Err:1 [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe)                  
  Hash Sum mismatch
Fetched 969 B in 1s (660 B/s)                                                  
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/andale32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
E: Failed to fetch [http://downloads.sourceforge.net/mirrorproblem?failedmirror=liquidtelecom.dl.sourceforge.net](http://downloads.sourceforge.net/mirrorproblem?failedmirror=liquidtelecom.dl.sourceforge.net)  Hash Sum mismatch

E: Download Failed
Setting up ttf-mscorefonts-installer (3.4+nmu1ubuntu2) ...
```

Any more ideas?

I am running 64 bit: is that the problem?

---

### Post by oldos2er on 2016-05-04
> **Autodave said:**
> I am running 64 bit: is that the problem?

No.

What else, if anything, is in /var/lib/update-notifier/package-data-downloads/partial/ ? ```
ll /var/lib/update-notifier/package-data-downloads/partial/
```

---

### Post by $yl9pAR%t on 2016-05-04
Please give us the output of this command:

```
apt-cache policy ttf-mscorefonts-installer
```

---

### Post by Autodave on 2016-05-04
> **mefisto888 said:**
> Please give us the output of this command:

```
apt-cache policy ttf-mscorefonts-installer
```

```
ttf-mscorefonts-installer:
  Installed: 3.4+nmu1ubuntu2
  Candidate: 3.4+nmu1ubuntu2
  Version table:
 *** 3.4+nmu1ubuntu2 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/multiverse amd64 Packages
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/multiverse i386 Packages
        100 /var/lib/dpkg/status
```
da

> **oldos2er said:**
> No.

What else, if anything, is in /var/lib/update-notifier/package-data-downloads/partial/ ? ```
ll /var/lib/update-notifier/package-data-downloads/partial/
```

```
$ ll /var/lib/update-notifier/package-data-downloads/partial/total 2136
drwxr-xr-x 2 root root   4096 May  4 19:21 ./
drwxr-xr-x 3 root root   4096 May  4 19:21 ../
-rw-r--r-- 1 root root 198384 Aug 15  2002 andale32.exe
-rw-r--r-- 1 root root    969 May  4 19:15 andale32.exe.FAILED
-rw-r--r-- 1 root root    969 May  4 19:21 arial32.exe.FAILED
-rw-r--r-- 1 root root 168176 Aug 15  2002 arialb32.exe
-rw-r--r-- 1 root root    969 May  2 07:35 arialb32.exe.FAILED
-rw-r--r-- 1 root root    969 May  4 07:35 comic32.exe.FAILED
-rw-r--r-- 1 root root    969 Apr 28 07:35 courie32.exe.FAILED
-rw-r--r-- 1 root root 392440 Aug 15  2002 georgi32.exe
-rw-r--r-- 1 root root 173288 Aug 15  2002 impact32.exe
-rw-r--r-- 1 root root 661728 Aug 15  2002 times32.exe
-rw-r--r-- 1 root root 357200 Aug 15  2002 trebuc32.exe
-rw-r--r-- 1 root root    969 Apr 23 21:06 verdan32.exe.FAILED
-rw-r--r-- 1 root root 185072 Aug 15  2002 webdin32.exe
dave@dave-p7-1534:~$
```

---

### Post by QDR06VV9 on 2016-05-04
This bug was reported fixed [https://answers.launchpad.net/ubuntu/+question/290405](https://answers.launchpad.net/ubuntu/+question/290405)

We may have to get rough with it
```
sudo rm -rf /var/lib/update-notifier/package-data-downloads/partial/*
```
Followed by
```
sudo apt-get --purge --reinstall install ttf-mscorefonts-installer
```

---

### Post by Autodave on 2016-05-04
> **oldos2er said:**
> No.

What else, if anything, is in /var/lib/update-notifier/package-data-downloads/partial/ ? ```
ll /var/lib/update-notifier/package-data-downloads/partial/
```

```
$ ll /var/lib/update-notifier/package-data-downloads/partial/total 2136
drwxr-xr-x 2 root root   4096 May  4 19:21 ./
drwxr-xr-x 3 root root   4096 May  4 19:21 ../
-rw-r--r-- 1 root root 198384 Aug 15  2002 andale32.exe
-rw-r--r-- 1 root root    969 May  4 19:15 andale32.exe.FAILED
-rw-r--r-- 1 root root    969 May  4 19:21 arial32.exe.FAILED
-rw-r--r-- 1 root root 168176 Aug 15  2002 arialb32.exe
-rw-r--r-- 1 root root    969 May  2 07:35 arialb32.exe.FAILED
-rw-r--r-- 1 root root    969 May  4 07:35 comic32.exe.FAILED
-rw-r--r-- 1 root root    969 Apr 28 07:35 courie32.exe.FAILED
-rw-r--r-- 1 root root 392440 Aug 15  2002 georgi32.exe
-rw-r--r-- 1 root root 173288 Aug 15  2002 impact32.exe
-rw-r--r-- 1 root root 661728 Aug 15  2002 times32.exe
-rw-r--r-- 1 root root 357200 Aug 15  2002 trebuc32.exe
-rw-r--r-- 1 root root    969 Apr 23 21:06 verdan32.exe.FAILED
-rw-r--r-- 1 root root 185072 Aug 15  2002 webdin32.exe
```

> **runrickus said:**
> This bug was reported fixed [https://answers.launchpad.net/ubuntu/+question/290405](https://answers.launchpad.net/ubuntu/+question/290405)

We may have to get rough with it
```
sudo rm -rf /var/lib/update-notifier/package-data-downloads/partial/*
```
Followed by
```
sudo apt-get --purge --reinstall install ttf-mscorefonts-installer
```

Did both of them: long story short, at the end of everything, it said everything was installed w/no errors.  I'll let you all know tomorrow when I get home from work and see if the message is back up again.

Thanks folks for your help. Have a good night. I have to go watch the Penguins beat the Capitols.......... :-)

---

### Post by stroudmw on 2016-08-10
I was having the same problems. Running 
*[COLOR=#000000][FONT=&quot]sudo rm -rf /var/lib/update-notifier/package-data-downloads/partial/*[/FONT][/COLOR]*[COLOR=#000000][FONT=&quot] 
followed by 
[/FONT][/COLOR]*[COLOR=#000000][FONT=&quot]sudo apt-get --purge --reinstall install ttf-mscorefonts-installer[/FONT][/COLOR]*[COLOR=#000000][FONT=&quot] 
fixed it. Thank you![/FONT][/COLOR]

---

### Post by gelfling6 on 2017-02-02
> **stroudmw said:**
> I was having the same problems. Running 
*[COLOR=#000000][FONT=&amp]sudo rm -rf /var/lib/update-notifier/package-data-downloads/partial/*[/FONT][/COLOR]*[COLOR=#000000][FONT=&amp] 
followed by 
[/FONT][/COLOR]*[COLOR=#000000][FONT=&amp]sudo apt-get --purge --reinstall install ttf-mscorefonts-installer[/FONT][/COLOR]*[COLOR=#000000][FONT=&amp] 
fixed it. Thank you![/FONT][/COLOR]

I'm running 16.04, and the last few months, the request to re-install the installer, has been hitting he exact same problem.. But......
the above sequence, is hitting the following:

```
 sudo rm -rf /var/lib/update-notifier/package-data-downloads/partial/* 
[sudo] password for gelfling6: 
gelfling6@JoGrant:~$ sudo apt-get --purge --reinstall install ttf-mscorefonts-installer 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/29.5 kB of archives.
After this operation, 0 B of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 583167 files and directories currently installed.)
Preparing to unpack .../ttf-mscorefonts-installer_3.4+nmu1ubuntu2_all.deb ...
mscorefonts-eula license has already been accepted
Unpacking ttf-mscorefonts-installer (3.4+nmu1ubuntu2) over (3.4+nmu1ubuntu2) ...
Processing triggers for fontconfig (2.11.94-0ubuntu1.1) ...
Processing triggers for update-notifier-common (3.168.3) ...
ttf-mscorefonts-installer: processing...
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/andale32.exe
Get:1 http://downloads.sourceforge.net/corefonts/andale32.exe [198 kB]
Fetched 198 kB in 8s (22.2 kB/s)                                               
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/andale32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/arial32.exe
Get:1 http://downloads.sourceforge.net/corefonts/arial32.exe [554 kB]
Fetched 554 kB in 27s (20.1 kB/s)                                              
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/arial32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/arialb32.exe
Get:1 http://downloads.sourceforge.net/corefonts/arialb32.exe [168 kB]
Fetched 168 kB in 7s (21.5 kB/s)                                               
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/arialb32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/comic32.exe
Get:1 http://downloads.sourceforge.net/corefonts/comic32.exe [246 kB]
Fetched 246 kB in 11s (20.8 kB/s)                                              
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/comic32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/courie32.exe
Get:1 http://downloads.sourceforge.net/corefonts/courie32.exe [646 kB]
Fetched 646 kB in 13s (46.9 kB/s)                                              
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/courie32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/georgi32.exe
Get:1 http://downloads.sourceforge.net/corefonts/georgi32.exe [392 kB]
Fetched 392 kB in 7s (55.5 kB/s)                                               
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/georgi32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/impact32.exe
Get:1 http://downloads.sourceforge.net/corefonts/impact32.exe [173 kB]
Fetched 173 kB in 5s (34.1 kB/s)                                               
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/impact32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/times32.exe
Get:1 http://downloads.sourceforge.net/corefonts/times32.exe [662 kB]
Fetched 662 kB in 21s (30.3 kB/s)                                              
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/times32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/trebuc32.exe
Get:1 http://downloads.sourceforge.net/corefonts/trebuc32.exe [357 kB]
Fetched 357 kB in 9s (36.2 kB/s)                                               
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/trebuc32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/verdan32.exe
Get:1 http://downloads.sourceforge.net/corefonts/verdan32.exe [352 kB]
Fetched 352 kB in 18s (19.3 kB/s)                                              
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/verdan32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/webdin32.exe
Get:1 http://downloads.sourceforge.net/corefonts/webdin32.exe [185 kB]
Fetched 185 kB in 2s (91.7 kB/s)                                               
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/webdin32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/andale32.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/arial32.exe
  extracting FONTINST.EXE
  extracting fontinst.inf
  extracting Ariali.TTF
  extracting Arialbd.TTF
  extracting Arialbi.TTF
  extracting Arial.TTF

All done, no errors.
Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/arialb32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/comic32.exe
  extracting fontinst.inf
  extracting Comicbd.TTF
  extracting Comic.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/courie32.exe
  extracting cour.ttf
  extracting courbd.ttf
  extracting courbi.ttf
  extracting fontinst.inf
  extracting couri.ttf
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/georgi32.exe
  extracting fontinst.inf
  extracting Georgiaz.TTF
  extracting Georgiab.TTF
  extracting Georgiai.TTF
  extracting Georgia.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/impact32.exe
  extracting fontinst.exe
  extracting Impact.TTF
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/times32.exe
  extracting fontinst.inf
  extracting Times.TTF
  extracting Timesbd.TTF
  extracting Timesbi.TTF
  extracting Timesi.TTF
  extracting FONTINST.EXE

All done, no errors.
Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/trebuc32.exe
  extracting FONTINST.EXE
  extracting trebuc.ttf
  extracting Trebucbd.ttf
  extracting trebucbi.ttf
  extracting trebucit.ttf
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/verdan32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting Verdanab.TTF
  extracting Verdanai.TTF
  extracting Verdanaz.TTF
  extracting Verdana.TTF

All done, no errors.
Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/webdin32.exe
  extracting fontinst.exe
  extracting Webdings.TTF
  extracting fontinst.inf
  extracting Licen.TXT

All done, no errors.
All fonts downloaded and installed.
Setting up ttf-mscorefonts-installer (3.4+nmu1ubuntu2) ...


```
The files seem to be downloading, and installing, but... still getting the 13: Permission-Denied .... is this just a fluke, or is it getting through?

---

### Post by wildmanne39 on 2017-02-02
@gelfling6, please start your own thread because it is better for you then posting in a thread that is solved.
Thanks

---

### Post by howefield on 2017-02-02
There is an issue with the 3.4 ttf-mscorefonts package that ships with 16.04.

Have you got the fonts downloaded, you should have Andale Mono, Arial Black, Arial, Comic Sans MS, Courier New, Georgia, Impact, Times New Roman, Trebuchet, Verdana and Webdings ? Load up, say, LibreOffice Writer and check for those fonts...

If the fonts are present, to get rid of the nag screen try..

```
sudo touch /var/lib/update-notifier/package-data-downloads/ttf-mscorefonts-installer
```

If that fails I'd suggest purging the package and installing the 3.6 version of the package.

```
wget http://ftp.de.debian.org/debian/pool/contrib/m/msttcorefonts/ttf-mscorefonts-installer_3.6_all.deb -P ~/Downloads
```

will download the package to your Downloads folder, and
 
```
sudo apt install ~/Downloads/ttf-mscorefonts-installer_3.6_all.deb
```

will install the package.

---

