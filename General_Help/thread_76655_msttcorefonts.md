---
title: "msttcorefonts"
date: 2005-10-15
forum: General Help
---

### Post by JediPottsy on 2005-10-15
Having problems with msttcorefonts, they wont download:

```
You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--19:12:10--  http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... failed: Connection timed out.
--19:12:20--  http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Connection timed out.
--19:12:30--  http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving twtelecom.dl.sourceforge.net... failed: Connection timed out.
--19:12:40--  http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving aleron.dl.sourceforge.net... failed: Connection timed out.
--19:12:51--  http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving cesnet.dl.sourceforge.net... failed: Connection timed out.
--19:13:01--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libid3tag0 (0.15.1b-7) ...

Setting up libmad0 (0.15.1b-2.1) ...

Setting up mpg321 (0.2.10.3) ...

Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

any suggestions?

---

### Post by Hikaru79 on 2005-10-15
If the sf.net mirrors are timing out, there's nothing you can do except wait. But don't worry -- this is SourceForge, they'll be back up before you know it. Simply try again in an hour or two :)

---

### Post by xyzzyman on 2005-10-15
Check this thread:

[http://ubuntuforums.org/showthread.php?t=75413]("http://ubuntuforums.org/showthread.php?t=75413")

I had the same problem. I wasn't behind a proxy or anything, but I had to turn off passive_ftp for wget in /etc/wgetrc

---

### Post by JediPottsy on 2005-10-16
is there any other way to install msttcorefonts....even with taking passive ftp off, it wont download....GRRRRR!!!!   :mad:

---

### Post by lithorus on 2005-10-16
[QUOTE=xyzzyman]Check this thread:

[http://ubuntuforums.org/showthread.php?t=75413]("http://ubuntuforums.org/showthread.php?t=75413")

I had the same problem. I wasn't behind a proxy or anything, but I had to turn off passive_ftp for wget in /etc/wgetrc[/QUOTE]
But if you look at the log it's using http and not ftp.

---

### Post by andril on 2005-10-18
I also "had" this issue but I resolved it by using the Ubuntu 5.04 Add-On CD. Look in this thread [http://www.ubuntuforums.org/showthread.php?t=30187&highlight=Ubuntu+5.04+Add-On+CD](http://www.ubuntuforums.org/showthread.php?t=30187&highlight=Ubuntu+5.04+Add-On+CD)

to download the CD. :KS

BTW: Does anyone know how to get rid of this error?
"E: msttcorefonts: subprocess post-installation script returned error exit status 1"

---

### Post by Petrush on 2005-10-19
Still haven't got this to work. Tried to add proxies in /etc/wgetrc but no success. Have others managed to install msttcorefonts?

Is it possible to manually download the fonts, and run the script using them?

---

### Post by XavMP on 2005-10-25
I've read on
[http://ubuntuforums.org/showthread.php?t=75413]("http://ubuntuforums.org/showthread.php?t=75413")
and modified my /etc/wgetrc. file to include proxy information. 

I't works ¡¡

---

### Post by arXonik on 2005-10-25
i had the same problem, and simply did not wish to sht around with the settings, especially when everything else was working fine apart from font download and i just wanted to have them, so here is what i did

**PLEASE NOTE**: none of the steps require you to be in sudo mode, so please DON'T USE IT!

1. open [SF Microsoft core fonts site]("http://sourceforge.net/project/showfiles.php?group_id=34153") and download the individual font files (those with the *.exe extension) into one directory, say fonts in your home directory

2. open terminal, change into the fonts directory and use **probably** "cabextract * -F *.ttf" command, am not completely sure, since am not at home and cannot doublecheck, this way cabextract extracts only the font files

**NOW**: if you are using your workstation as a single user workstation and do not care about the systemwide settings, read on, otherwise, see NOTES

3. create directory .fonts in your home directory and copy all corefonts into this directory *.TTF as well as *.ttf

4. change into directory .fonts and run fc-cache et voila that is what worked for me

**NOTES**: If you want to do the changes systemwide, you need to copy the fonts into the /usr/share/fonts/truetype folder and run the fc-cache command as sudo in the said folder, I GUESS

---

### Post by jeffreyvergara.NET on 2005-10-25
or you can try automatix

---

### Post by JediPottsy on 2005-10-26
automatix .... you know that it does exactly the same commands as i do, just automated

---

### Post by jonathanjg on 2005-11-22
Interestingly enough, I am also experiencing the same problem - it seems to be a speed issue with sf - I can manually download the "andale.exe" file from a host I have in the states, but not from machines I have locally. So its not like the files have been removed, its just that you are really experiencing a time out!

---

### Post by jonathanjg on 2005-11-25
[QUOTE=jonathanjg]Interestingly enough, I am also experiencing the same problem - it seems to be a speed issue with sf - I can manually download the "andale.exe" file from a host I have in the states, but not from machines I have locally. So its not like the files have been removed, its just that you are really experiencing a time out![/QUOTE]

This worked for me, but there is probably a more elegant way to do this (but not at 2am!!):-

[LIST=1][*]Get the following files from a friend, another pc or download manually from the internet by some means (like in my earlier post above):-
andale32.exe  comic32.exe   impact32.exe  verdan32.exe
arial32.exe   courie32.exe  times32.exe   webdin32.exe
arialb32.exe  georgi32.exe  trebuc32.exe
[*]Create the following directory and put them into it: /tmp/mstt/
[*]Manually launch the postinstall script, telling it to use your local copy:
/usr/sbin/update-ms-fonts /tmp/mstt
[*] Remove your temp directory
rm -rf /tmp/mstt/
[*] To ensure apt/dpkg is happy rerun
 apt-get install msttcorefonts[/LIST]

---

### Post by doronunu on 2005-12-03
u can just write :

```
sudo apt-get install cabextract
```

it will install msttcorefonts to your machine

---

### Post by neoflight on 2006-01-10
[QUOTE=Petrush]Still haven't got this to work. Tried to add proxies in /etc/wgetrc but no success. Have others managed to install msttcorefonts?

Is it possible to manually download the fonts, and run the script using them?[/QUOTE]

i set the DNS servers right in in the netwrok setup and it worked....earlier it was assigned some random ones...it worked....

---

### Post by bking on 2006-04-08
[QUOTE=jonathanjg]This worked for me, but there is probably a more elegant way to do this (but not at 2am!!):-

[LIST=1][*]Get the following files from a friend, another pc or download manually from the internet by some means (like in my earlier post above):-
andale32.exe  comic32.exe   impact32.exe  verdan32.exe
arial32.exe   courie32.exe  times32.exe   webdin32.exe
arialb32.exe  georgi32.exe  trebuc32.exe
[*]Create the following directory and put them into it: /tmp/mstt/
[*]Manually launch the postinstall script, telling it to use your local copy:
/usr/sbin/update-ms-fonts /tmp/mstt
[*] Remove your temp directory
rm -rf /tmp/mstt/
[*] To ensure apt/dpkg is happy rerun
 apt-get install msttcorefonts[/LIST][/QUOTE]

After a whole afternoon searching these forums and messing around, the above instructions WORK!! Thanks so much! All is well.

I downloaded the fonts directly from the sourceforge website here:
[http://sourceforge.net/project/showfiles.php?group_id=34153&release_id=105355](http://sourceforge.net/project/showfiles.php?group_id=34153&release_id=105355)

Thank you again,
Becki :D

---

### Post by Danny Boy on 2006-04-19
I'm running Dapper and had to add sudo to the begining of steps 3 and 5

---

### Post by ramdez on 2006-04-23
Worked like a charm jonathanjg. thx

---

### Post by starscalling on 2006-04-24
seems msttcorefonts works great from here ~_~



The following NEW packages will be installed
  cabextract msttcorefonts
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
Need to get 66.8kB of archives.
After unpacking 315kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe cabextract 1.1-1 [44.7kB]
Get: 2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse msttcorefonts 1.2ubuntu2 [ 22.1kB]
Fetched 66.8kB in 1s (40.3kB/s)
Preconfiguring packages ...
Selecting previously deselected package cabextract.
(Reading database ... 84924 files and directories currently installed.)
Unpacking cabextract (from .../cabextract_1.1-1_i386.deb) ...
Selecting previously deselected package msttcorefonts.
Unpacking msttcorefonts (from .../msttcorefonts_1.2ubuntu2_all.deb) ...
Setting up cabextract (1.1-1) ...
Setting up msttcorefonts (1.2ubuntu2) ...
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
warning: /usr/share/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--22:44:46--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.ex](http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.ex) e
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... 193.190.198.97
Connecting to belnet.dl.sourceforge.net|193.190.198.97|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&fai](http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&fai) ledmirror=belnet.dl.sourceforge.net [following]
--22:44:47--  [http://prdownloads.sourceforge.net/corefonts/andale32.exe?download](http://prdownloads.sourceforge.net/corefonts/andale32.exe?download) &failedmirror=belnet.dl.sourceforge.net
           => `./andale32.exe?download&failedmirror=belnet.dl.sourceforge.net'
Resolving prdownloads.sourceforge.net... 66.35.250.217
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 12,233        --.--K/s

22:44:47 (105.28 KB/s) - `./andale32.exe?download&failedmirror=belnet.dl.sourcef orge.net' saved [12233]

--22:44:47--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/arialb32.ex](http://belnet.dl.sourceforge.net/sourceforge/corefonts/arialb32.ex) e
           => `./arialb32.exe'
Resolving belnet.dl.sourceforge.net... 193.190.198.97
Connecting to belnet.dl.sourceforge.net|193.190.198.97|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/arialb32.exe?download&fai](http://prdownloads.sourceforge.net/corefonts/arialb32.exe?download&fai) ledmirror=belnet.dl.sourceforge.net [following]
--22:44:48--  [http://prdownloads.sourceforge.net/corefonts/arialb32.exe?download](http://prdownloads.sourceforge.net/corefonts/arialb32.exe?download) &failedmirror=belnet.dl.sourceforge.net
           => `./arialb32.exe?download&failedmirror=belnet.dl.sourceforge.net'
Resolving prdownloads.sourceforge.net... 66.35.250.217
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 12,233        --.--K/s

22:44:48 (82.87 KB/s) - `./arialb32.exe?download&failedmirror=belnet.dl.sourcefo rge.net' saved [12233]

--22:44:48--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/arial32.exe](http://belnet.dl.sourceforge.net/sourceforge/corefonts/arial32.exe)
           => `./arial32.exe'
Resolving belnet.dl.sourceforge.net... 193.190.198.97
Connecting to belnet.dl.sourceforge.net|193.190.198.97|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&fail](http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&fail) edmirror=belnet.dl.sourceforge.net [following]
--22:44:49--  [http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&](http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&) failedmirror=belnet.dl.sourceforge.net
           => `./arial32.exe?download&failedmirror=belnet.dl.sourceforge.net'
Resolving prdownloads.sourceforge.net... 66.35.250.217
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 12,216        --.--K/s

22:44:49 (84.40 KB/s) - `./arial32.exe?download&failedmirror=belnet.dl.sourcefor ge.net' saved [12216]

--22:44:49--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/comic32.exe](http://belnet.dl.sourceforge.net/sourceforge/corefonts/comic32.exe)
           => `./comic32.exe'
Resolving belnet.dl.sourceforge.net... 193.190.198.97
Connecting to belnet.dl.sourceforge.net|193.190.198.97|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/comic32.exe?download&fail](http://prdownloads.sourceforge.net/corefonts/comic32.exe?download&fail) edmirror=belnet.dl.sourceforge.net [following]
--22:44:50--  [http://prdownloads.sourceforge.net/corefonts/comic32.exe?download&](http://prdownloads.sourceforge.net/corefonts/comic32.exe?download&) failedmirror=belnet.dl.sourceforge.net
           => `./comic32.exe?download&failedmirror=belnet.dl.sourceforge.net'
Resolving prdownloads.sourceforge.net... 66.35.250.217
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 12,216        --.--K/s

22:44:50 (87.40 KB/s) - `./comic32.exe?download&failedmirror=belnet.dl.sourcefor ge.net' saved [12216]

--22:44:50--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/courie32.ex](http://belnet.dl.sourceforge.net/sourceforge/corefonts/courie32.ex) e
           => `./courie32.exe'
Resolving belnet.dl.sourceforge.net... 193.190.198.97
Connecting to belnet.dl.sourceforge.net|193.190.198.97|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/courie32.exe?download&fai](http://prdownloads.sourceforge.net/corefonts/courie32.exe?download&fai) ledmirror=belnet.dl.sourceforge.net [following]
--22:44:51--  [http://prdownloads.sourceforge.net/corefonts/courie32.exe?download](http://prdownloads.sourceforge.net/corefonts/courie32.exe?download) &failedmirror=belnet.dl.sourceforge.net
           => `./courie32.exe?download&failedmirror=belnet.dl.sourceforge.net'
Resolving prdownloads.sourceforge.net... 66.35.250.217
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 12,233        --.--K/s

22:44:51 (83.61 KB/s) - `./courie32.exe?download&failedmirror=belnet.dl.sourcefo rge.net' saved [12233]

--22:44:51--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/georgi32.ex](http://belnet.dl.sourceforge.net/sourceforge/corefonts/georgi32.ex) e
           => `./georgi32.exe'
Resolving belnet.dl.sourceforge.net... 193.190.198.97
Connecting to belnet.dl.sourceforge.net|193.190.198.97|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/georgi32.exe?download&fai](http://prdownloads.sourceforge.net/corefonts/georgi32.exe?download&fai) ledmirror=belnet.dl.sourceforge.net [following]
--22:44:52--  [http://prdownloads.sourceforge.net/corefonts/georgi32.exe?download](http://prdownloads.sourceforge.net/corefonts/georgi32.exe?download) &failedmirror=belnet.dl.sourceforge.net
           => `./georgi32.exe?download&failedmirror=belnet.dl.sourceforge.net'
Resolving prdownloads.sourceforge.net... 66.35.250.217
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 12,233        --.--K/s

22:44:52 (90.03 KB/s) - `./georgi32.exe?download&failedmirror=belnet.dl.sourcefo rge.net' saved [12233]

--22:44:52--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/impact32.ex](http://belnet.dl.sourceforge.net/sourceforge/corefonts/impact32.ex) e
           => `./impact32.exe'
Resolving belnet.dl.sourceforge.net... 193.190.198.97
Connecting to belnet.dl.sourceforge.net|193.190.198.97|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/impact32.exe?download&fai](http://prdownloads.sourceforge.net/corefonts/impact32.exe?download&fai) ledmirror=belnet.dl.sourceforge.net [following]
--22:44:52--  [http://prdownloads.sourceforge.net/corefonts/impact32.exe?download](http://prdownloads.sourceforge.net/corefonts/impact32.exe?download) &failedmirror=belnet.dl.sourceforge.net
           => `./impact32.exe?download&failedmirror=belnet.dl.sourceforge.net'
Resolving prdownloads.sourceforge.net... 66.35.250.217
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 12,233        --.--K/s

22:44:53 (95.62 KB/s) - `./impact32.exe?download&failedmirror=belnet.dl.sourcefo rge.net' saved [12233]

--22:44:53--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://belnet.dl.sourceforge.net/sourceforge/corefonts/times32.exe)
           => `./times32.exe'
Resolving belnet.dl.sourceforge.net... 193.190.198.97
Connecting to belnet.dl.sourceforge.net|193.190.198.97|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/times32.exe?download&fail](http://prdownloads.sourceforge.net/corefonts/times32.exe?download&fail) edmirror=belnet.dl.sourceforge.net [following]
--22:44:53--  [http://prdownloads.sourceforge.net/corefonts/times32.exe?download&](http://prdownloads.sourceforge.net/corefonts/times32.exe?download&) failedmirror=belnet.dl.sourceforge.net
           => `./times32.exe?download&failedmirror=belnet.dl.sourceforge.net'
Resolving prdownloads.sourceforge.net... 66.35.250.217
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 12,216        --.--K/s

22:44:54 (107.25 KB/s) - `./times32.exe?download&failedmirror=belnet.dl.sourcefo rge.net' saved [12216]

--22:44:54--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/trebuc32.ex](http://belnet.dl.sourceforge.net/sourceforge/corefonts/trebuc32.ex) e
           => `./trebuc32.exe'
Resolving belnet.dl.sourceforge.net... 193.190.198.97
Connecting to belnet.dl.sourceforge.net|193.190.198.97|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/trebuc32.exe?download&fai](http://prdownloads.sourceforge.net/corefonts/trebuc32.exe?download&fai) ledmirror=belnet.dl.sourceforge.net [following]
--22:44:54--  [http://prdownloads.sourceforge.net/corefonts/trebuc32.exe?download](http://prdownloads.sourceforge.net/corefonts/trebuc32.exe?download) &failedmirror=belnet.dl.sourceforge.net
           => `./trebuc32.exe?download&failedmirror=belnet.dl.sourceforge.net'
Resolving prdownloads.sourceforge.net... 66.35.250.217
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 12,233        --.--K/s

22:44:55 (98.00 KB/s) - `./trebuc32.exe?download&failedmirror=belnet.dl.sourcefo rge.net' saved [12233]

--22:44:55--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/verdan32.ex](http://belnet.dl.sourceforge.net/sourceforge/corefonts/verdan32.ex) e
           => `./verdan32.exe'
Resolving belnet.dl.sourceforge.net... 193.190.198.97
Connecting to belnet.dl.sourceforge.net|193.190.198.97|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/verdan32.exe?download&fai](http://prdownloads.sourceforge.net/corefonts/verdan32.exe?download&fai) ledmirror=belnet.dl.sourceforge.net [following]
--22:44:55--  [http://prdownloads.sourceforge.net/corefonts/verdan32.exe?download](http://prdownloads.sourceforge.net/corefonts/verdan32.exe?download) &failedmirror=belnet.dl.sourceforge.net
           => `./verdan32.exe?download&failedmirror=belnet.dl.sourceforge.net'
Resolving prdownloads.sourceforge.net... 66.35.250.217
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 12,233        --.--K/s

22:44:55 (96.81 KB/s) - `./verdan32.exe?download&failedmirror=belnet.dl.sourcefo rge.net' saved [12233]

--22:44:55--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/webdin32.ex](http://belnet.dl.sourceforge.net/sourceforge/corefonts/webdin32.ex) e
           => `./webdin32.exe'
Resolving belnet.dl.sourceforge.net... 193.190.198.97
Connecting to belnet.dl.sourceforge.net|193.190.198.97|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/webdin32.exe?download&fai](http://prdownloads.sourceforge.net/corefonts/webdin32.exe?download&fai) ledmirror=belnet.dl.sourceforge.net [following]
--22:44:56--  [http://prdownloads.sourceforge.net/corefonts/webdin32.exe?download](http://prdownloads.sourceforge.net/corefonts/webdin32.exe?download) &failedmirror=belnet.dl.sourceforge.net
           => `./webdin32.exe?download&failedmirror=belnet.dl.sourceforge.net'
Resolving prdownloads.sourceforge.net... 66.35.250.217
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 12,233        --.--K/s

22:44:56 (83.79 KB/s) - `./webdin32.exe?download&failedmirror=belnet.dl.sourcefo rge.net' saved [12233]

--22:44:56--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32](http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32). exe
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... 69.16.168.245
Connecting to easynews.dl.sourceforge.net|69.16.168.245|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198,384 (194K) [application/octet-stream]

100%[====================================>] 198,384      186.03K/s

22:44:58 (185.43 KB/s) - `./andale32.exe' saved [198384/198384]

--22:44:58--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/arialb32](http://easynews.dl.sourceforge.net/sourceforge/corefonts/arialb32). exe
           => `./arialb32.exe'
Resolving easynews.dl.sourceforge.net... 69.16.168.245
Connecting to easynews.dl.sourceforge.net|69.16.168.245|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 168,176 (164K) [application/octet-stream]

100%[====================================>] 168,176      180.33K/s

22:44:59 (180.03 KB/s) - `./arialb32.exe' saved [168176/168176]

--22:44:59--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/arial32.e](http://easynews.dl.sourceforge.net/sourceforge/corefonts/arial32.e) xe
           => `./arial32.exe'
Resolving easynews.dl.sourceforge.net... 69.16.168.245
Connecting to easynews.dl.sourceforge.net|69.16.168.245|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 554,208 (541K) [application/octet-stream]

100%[====================================>] 554,208      204.01K/s

22:45:02 (203.47 KB/s) - `./arial32.exe' saved [554208/554208]

--22:45:02--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/comic32.e](http://easynews.dl.sourceforge.net/sourceforge/corefonts/comic32.e) xe
           => `./comic32.exe'
Resolving easynews.dl.sourceforge.net... 69.16.168.245
Connecting to easynews.dl.sourceforge.net|69.16.168.245|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 246,008 (240K) [application/octet-stream]

100%[====================================>] 246,008      180.60K/s

22:45:03 (180.40 KB/s) - `./comic32.exe' saved [246008/246008]

--22:45:03--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/courie32](http://easynews.dl.sourceforge.net/sourceforge/corefonts/courie32). exe
           => `./courie32.exe'
Resolving easynews.dl.sourceforge.net... 69.16.168.245
Connecting to easynews.dl.sourceforge.net|69.16.168.245|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 646,368 (631K) [application/octet-stream]

100%[====================================>] 646,368      254.55K/s

22:45:06 (253.83 KB/s) - `./courie32.exe' saved [646368/646368]

--22:45:06--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/georgi32](http://easynews.dl.sourceforge.net/sourceforge/corefonts/georgi32). exe
           => `./georgi32.exe'
Resolving easynews.dl.sourceforge.net... 69.16.168.245
Connecting to easynews.dl.sourceforge.net|69.16.168.245|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 392,440 (383K) [application/octet-stream]

100%[====================================>] 392,440      498.27K/s

22:45:07 (497.13 KB/s) - `./georgi32.exe' saved [392440/392440]

--22:45:07--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/impact32](http://easynews.dl.sourceforge.net/sourceforge/corefonts/impact32). exe
           => `./impact32.exe'
Resolving easynews.dl.sourceforge.net... 69.16.168.245
Connecting to easynews.dl.sourceforge.net|69.16.168.245|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 173,288 (169K) [application/octet-stream]

100%[====================================>] 173,288      433.09K/s

22:45:08 (431.86 KB/s) - `./impact32.exe' saved [173288/173288]

--22:45:08--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/times32.e](http://easynews.dl.sourceforge.net/sourceforge/corefonts/times32.e) xe
           => `./times32.exe'
Resolving easynews.dl.sourceforge.net... 69.16.168.245
Connecting to easynews.dl.sourceforge.net|69.16.168.245|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 661,728 (646K) [application/octet-stream]

100%[====================================>] 661,728      443.17K/s

22:45:09 (441.98 KB/s) - `./times32.exe' saved [661728/661728]

--22:45:09--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/trebuc32](http://easynews.dl.sourceforge.net/sourceforge/corefonts/trebuc32). exe
           => `./trebuc32.exe'
Resolving easynews.dl.sourceforge.net... 69.16.168.245
Connecting to easynews.dl.sourceforge.net|69.16.168.245|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 357,200 (349K) [application/octet-stream]

100%[====================================>] 357,200      422.85K/s

22:45:10 (421.59 KB/s) - `./trebuc32.exe' saved [357200/357200]

--22:45:10--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/verdan32](http://easynews.dl.sourceforge.net/sourceforge/corefonts/verdan32). exe
           => `./verdan32.exe'
Resolving easynews.dl.sourceforge.net... 69.16.168.245
Connecting to easynews.dl.sourceforge.net|69.16.168.245|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 351,992 (344K) [application/octet-stream]

100%[====================================>] 351,992      367.40K/s

22:45:11 (366.14 KB/s) - `./verdan32.exe' saved [351992/351992]

--22:45:11--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/webdin32](http://easynews.dl.sourceforge.net/sourceforge/corefonts/webdin32). exe
           => `./webdin32.exe'
Resolving easynews.dl.sourceforge.net... 69.16.168.245
Connecting to easynews.dl.sourceforge.net|69.16.168.245|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 185,072 (181K) [application/octet-stream]

100%[====================================>] 185,072      334.75K/s

22:45:12 (334.08 KB/s) - `./webdin32.exe' saved [185072/185072]

Extracting cabinet: andale32.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
Extracting cabinet: arialb32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
Extracting cabinet: arial32.exe
  extracting FONTINST.EXE
  extracting fontinst.inf
  extracting Ariali.TTF
  extracting Arialbd.TTF
  extracting Arialbi.TTF
  extracting Arial.TTF

All done, no errors.
Extracting cabinet: comic32.exe
  extracting fontinst.inf
  extracting Comicbd.TTF
  extracting Comic.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: courie32.exe
  extracting cour.ttf
  extracting courbd.ttf
  extracting courbi.ttf
  extracting fontinst.inf
  extracting couri.ttf
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: georgi32.exe
  extracting fontinst.inf
  extracting Georgiaz.TTF
  extracting Georgiab.TTF
  extracting Georgiai.TTF
  extracting Georgia.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: impact32.exe
  extracting fontinst.exe
  extracting Impact.TTF
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: times32.exe
  extracting fontinst.inf
  extracting Times.TTF
  extracting Timesbd.TTF
  extracting Timesbi.TTF
  extracting Timesi.TTF
  extracting FONTINST.EXE

All done, no errors.
Extracting cabinet: trebuc32.exe
  extracting FONTINST.EXE
  extracting trebuc.ttf
  extracting Trebucbd.ttf
  extracting trebucbi.ttf
  extracting trebucit.ttf
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: verdan32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting Verdanab.TTF
  extracting Verdanai.TTF
  extracting Verdanaz.TTF
  extracting Verdana.TTF

All done, no errors.
Extracting cabinet: webdin32.exe
  extracting fontinst.exe
  extracting Webdings.TTF
  extracting fontinst.inf
  extracting Licen.TXT

All done, no errors.
All fonts downloaded and installed.

nekostar@dapper:~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree... Done
msttcorefonts is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

---

### Post by Danny Boy on 2006-04-26
I have an extra freebie hosting account with Godaddy, so I put up the font files. The site only has 5 GB transer so get it while it lasts. GoDaddy may kill it (they suck ](*,) )but it should work for a while. By the way if hosting the file infringes on copyright or something I'll trash the file just let me know. 

[Download]("http://www.scnyonline.com/ubuntu/mstt.tar.gz")

Download the file and extact to /tmp then follow this procedure: Skip steps 1 & 2..

[QUOTE=jonathanjg]This worked for me, but there is probably a more elegant way to do this (but not at 2am!!):-

   1. Get the following files from a friend, another pc or download manually from the internet by some means (like in my earlier post above):-
      andale32.exe comic32.exe impact32.exe verdan32.exe
      arial32.exe courie32.exe times32.exe webdin32.exe
      arialb32.exe georgi32.exe trebuc32.exe
   2. Create the following directory and put them into it: /tmp/mstt/
   3. Manually launch the postinstall script, telling it to use your local copy:
      /usr/sbin/update-ms-fonts /tmp/mstt
   4. Remove your temp directory
      rm -rf /tmp/mstt/
   5. To ensure apt/dpkg is happy rerun
      apt-get install msttcorefonts[/quote]

---

### Post by arnieboy on 2006-04-26
if u are behind a proxy which is preventing **wget** from working.. u can try the following post:
[http://ubuntuforums.org/showpost.php?p=541276&postcount=1006](http://ubuntuforums.org/showpost.php?p=541276&postcount=1006)

---

### Post by JediPottsy on 2006-06-09
nop i dont use a proxy

---

### Post by pedro.php on 2006-06-19
[QUOTE=Danny Boy]I have an extra freebie hosting account with Godaddy, so I put up the font files. The site only has 5 GB transer so get it while it lasts. GoDaddy may kill it (they suck ](*,) )but it should work for a while. By the way if hosting the file infringes on copyright or something I'll trash the file just let me know. 

[Download]("http://www.scnyonline.com/ubuntu/mstt.tar.gz")

Download the file and extact to /tmp then follow this procedure: Skip steps 1 & 2..[/QUOTE]
I've downloaded fonts from this link: [http://prdownloads.sourceforge.net/corefonts/](http://prdownloads.sourceforge.net/corefonts/)
after, follow the steps 2 and 3. **And it works**!!!

Best regards.

---

### Post by jazzykay on 2006-09-03
Thank you for the solution. 
This worked great and prevented me from going batty...

Cheers and many thanks!!!

---

### Post by thebigfatgeek on 2006-09-29
I have found that if your network setup requires going through (normally an ADSL) router which is used to resolve DNS queries, that the downloads fail. If you set your DNS entries to your real DNS settings rather than your router, sourceforge tends to resolve ok, and msttcorefonts download ok afterwards.

---

### Post by raul_ on 2006-10-10
```

 /usr/sbin/update-
update-alternatives       update-gconf-defaults     update-pango-modules
update-binfmts            update-gdkpixbuf-loaders  update-pangox-aliases
update-ca-certificates    update-gtk-immodules      update-passwd
update-catalog            update-inetd              update-rc.d
update-default-aspell     update-initramfs          update-usbids
update-default-ispell     update-java-alternatives  update-xmlcatalog
update-default-wordlist   update-mime               update-xpdfrc
update-dictcommon-aspell  update-mozilla-chrome
update-flashplugin        update-openoffice-dicts

```

No update-ms-fonts here :-?

---

### Post by dagnabit dang doohickey on 2006-10-10
[Official Distribution of Webcore Fonts for Linux]("http://avi.alkalay.net/linux/docs/font-howto/Font.html#msfonts") [avi.alkalay.net]

[This]("http://freshmeat.net/projects/msfonts/") is the freshmeat page for the above distribution.

They have a tar.gz you can use for a manual install. Also available is an .rpm (if you're into that kind of thing ;) )

---

### Post by raul_ on 2006-10-10
How do u install them? there is no MAKE or anything like that..

---

### Post by dagnabit dang doohickey on 2006-10-10
You can place them in a subdirectory in /usr/share/fonts/truetype (I placed them in /usr/share/fonts/truetype/msttcorefonts).

I think the easiest way to install msttcorefonts is to use the Ubuntu Add/Remove Applications tool. But if my memory is correct that left me short a few fonts (I think Trebuchet was one of them), so I added the missing fonts from the link in my previous post.

---

### Post by raul_ on 2006-10-10
Yeah i already did that =) i didn't notice they were working because they don't show up in the amsn fonts. but they appear in firefox fonts.

---

### Post by dagnabit dang doohickey on 2006-10-10
I don't use amsn, so I'm not sure, but this may be helpful:

> If aMSN won't see your TrueType? fonts, try running: 

```
cd /path/to/your/TTF/fonts
mkfontdir -o fonts.dir
mkfontscale -o fonts.scale
fc-cache -fv
xset +fp /path/to/your/TTF/fonts
xset fp rehash
```

and adding the last 2 lines to your .xinitrc

I found the above info [here]("http://amsn.sourceforge.net/wiki/tiki-index.php?page=Installation+Instructions#tcl/tk"). You'll need to scroll down a little to see it.

---

### Post by raul_ on 2006-10-10
i get this error
```

raul@raul:/usr/share/fonts/truetype$ sudo xset +fp /usr/share/fonts/truetype/
xset:  bad font path element (#76), possible causes are:
    Directory does not exist or has wrong permissions
    Directory missing fonts.dir
    Incorrect font server address or syntax

```

and plus, i can't find .xinitrc with "locate" =\

---

### Post by dagnabit dang doohickey on 2006-10-10
You may have to create a .xinitrc in your home directory. Check out man xinit for more info on this.

As for your error, I am unsure of the cause of the error, but when looking at the man page for mkfontdir, it makes no mention of the -o option. In any case, since one of the possible reasons for the error is a missing fonts.dir, you might want to:

```
ls -a /usr/share/fonts/truetype
```

and see if fonts.dir is there.

---

### Post by dagnabit dang doohickey on 2006-10-10
btw: I'm kinda thinking you might want to start a new topic for this issue, so we don't jack this thread, while also inviting others who may have more   insight into this issue. You've got me trailblazin' my know-how here. ;)

---

### Post by raul_ on 2006-10-10
[http://www.ubuntuforums.org/showthread.php?t=243407&highlight=amsn+fonts]("http://www.ubuntuforums.org/showthread.php?t=243407&highlight=amsn+fonts")

Here ;)

---

### Post by loyeyoung on 2006-11-01
This is to document what the problem is with this package and how to fix it. 

The instructions that are given previously clearly will work. The instructions I am about to give will shed some light on the underlying problem and would actually fix the problem. I will submit them in a bug report to the package maintainer. 

The problems everyone is having are the result of issues in the "/usr/sbin/update-ms-fonts" script that ships as a part of msttcorefonts. Until the .deb is fixed upstream, you'll have to edit the script manually. To fix, open the script in your favorite text editor (as root), and:

(1) Immediately after the FONTDIR variable declaration, add:

> if [ -n "$FONTDIR" ] ; then
   mkdir -p "$FONTDIR"
fi

The script won't put the files in a directory that doesn't exist. (At least it didn't for me.) A simple "if" statement was all that was needed.

(2) In the wget command, the dns-timeout and connect-timeout parameters are too short. Change them both to 20. 

The reason that using "prdownloads.sourceforge.net" doesn't work in the script is that it always redirects you to a mirror. The mirrors already listed in the script are the mirrors of prdownloads. Once the timeouts are set reasonably, the downloads will work. No need to reconfigure wget itself. 

(3) Also in the wget command, the "--directory-prefix" is set at ".". Change the "." to "$SCRATCHDIR". 

For some reason, the script got confused about what directory it was working in, and put the files in the wrong directory. When cabextract comes along to extract, it needs to be able to find the cabs where they're supposed to be. 

After you have edited the script, save it, and open up a terminal or console: 
> 
#sudo update-ms-fonts
#sudo apt-get install msttcorefonts

You may also have to register the fonts in your various applications (e.g., Firefox, x-ttcidfont-conf, and defoma) depending on how you have font management set up on your box. 

Hook 'em Horns.

Loye Young
Laredo, Texas

---

### Post by nkayesmith on 2007-01-08
> **jeffreyvergara.NET said:**
> or you can try automatix

This doesn't work - it uses the same package (msttcorefonts).

---

### Post by nkayesmith on 2007-01-08
I have packaged the bugfixes suggested loyeyong into a new .deb file, and put it up at [http://download.formationos.net](http://download.formationos.net). It works for me! - pm me if there are any problems.

---

### Post by odwyerda on 2008-04-29
Ok this is a very old post but Im confused,
I go into /usr/sbin/
but there is no update-ms-fonts file for me to change!

I get this error
```
......Error parsing proxy URL http://:8080/: Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This from what I understand should fix it. 
Now I only installed Ubuntu today so I am a complete fresher at this


DAve

---

