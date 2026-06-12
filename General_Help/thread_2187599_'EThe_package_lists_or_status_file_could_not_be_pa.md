---
title: "'E:The package lists or status file could not be parsed or opened'"
date: 2013-11-12
forum: General Help
---

### Post by azitizz on 2013-11-12
Im getting the "no entrey" symbol on my dsahboard, with the error message whe I click on it: "[B][I]An error occurred, please run package manager from the right click menu or apt-get in terminal to see what is wrong. The error message was: 'Error: opening the cache (E:encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/
ca.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened"[/I][/B]

Also it seems to not be able to report the problem as I get these other two error messages (see screenshots)

And when I try to check for updates the error message comes up "***This is a serious problem. Try again later. If this problem appears again, please report an error to the developers.***"

Thanks for any help anyone can provide.
[ATTACH=CONFIG]247790[/ATTACH][ATTACH=CONFIG]247791[/ATTACH]

---

### Post by Bashing-om on 2013-11-12
azitizz; Hi !

The error related to "/var/lib/apt/lists/" indicates the control file is in an inconsistent state.

Remove the control files; terminal commands:
```

sudo rm -fr /var/lib/apt/lists

```
Rebuild those index files:
```

sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update

```
and now let's see the system update:
```

sudo apt-get upgrade

```


[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by azitizz on 2013-11-12
> **Bashing-om said:**
> azitizz; Hi !

The error related to "/var/lib/apt/lists/" indicates the control file is in an inconsistent state.

Remove the control files; terminal commands:
```

sudo rm -fr /var/lib/apt/lists

```
Rebuild those index files:
```

sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update

```
and now let's see the system update:
```

sudo apt-get upgrade

```


[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

Thank you! it worked!

---

### Post by Bashing-om on 2013-11-12
azitizz; Great !

Please mark this thread as solved,; aids others seeking a similar solution and helps keep the forum tidy.

[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

### Post by chester2 on 2013-11-13
Thanks also,
same problem same solution,

Great indeed

C

---

### Post by azitizz on 2013-12-02
The same message appeared again today. I entered the commands as above and it worked again, but Im wondering if this will be recurring or if its indicating a deeper problem?

Thanks again.
M

---

### Post by Bashing-om on 2013-12-02
azitizz; Hi !

Happening once more this soon might be reason for concern.
As the message says, maybe there is a problem with  the sources.list files or a 3rd party PPA.
We can look:
```

cat -n /etc/apt/sources.list
ls -la  /etc/apt/sources.list.d

```
If all looks good, we can see what the package manager thinks:
```

dpkg -C
sudo apt-get install -f

```

[INDENT][INDENT]there is cause and effect
[/INDENT][/INDENT]

---

### Post by azitizz on 2013-12-03
> **Bashing-om said:**
> azitizz; Hi !

Happening once more this soon might be reason for concern.
As the message says, maybe there is a problem with  the sources.list files or a 3rd party PPA.
We can look:
```

cat -n /etc/apt/sources.list
ls -la  /etc/apt/sources.list.d

```


Thanks for the help. So heres whats come out of the above commands:

```
michael@Michael-Sat-L350D:~$ cat -n /etc/apt/sources.list
     1	# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ dists/precise/main/binary-i386/
     2	
     3	# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ dists/precise/restricted/binary-i386/
     4	# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ precise main restricted
     5	
     6	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     7	# newer versions of the distribution.
     8	deb http://ca.archive.ubuntu.com/ubuntu/ precise main restricted
     9	deb-src http://ca.archive.ubuntu.com/ubuntu/ precise main restricted
    10	
    11	## Major bug fix updates produced after the final release of the
    12	## distribution.
    13	deb http://ca.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    14	deb-src http://ca.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    15	
    16	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    17	## team. Also, please note that software in universe WILL NOT receive any
    18	## review or updates from the Ubuntu security team.
    19	deb http://ca.archive.ubuntu.com/ubuntu/ precise universe
    20	deb-src http://ca.archive.ubuntu.com/ubuntu/ precise universe
    21	deb http://ca.archive.ubuntu.com/ubuntu/ precise-updates universe
    22	deb-src http://ca.archive.ubuntu.com/ubuntu/ precise-updates universe
    23	
    24	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    25	## team, and may not be under a free licence. Please satisfy yourself as to 
    26	## your rights to use the software. Also, please note that software in 
    27	## multiverse WILL NOT receive any review or updates from the Ubuntu
    28	## security team.
    29	deb http://ca.archive.ubuntu.com/ubuntu/ precise multiverse
    30	deb-src http://ca.archive.ubuntu.com/ubuntu/ precise multiverse
    31	deb http://ca.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    32	deb-src http://ca.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    33	
    34	## N.B. software from this repository may not have been tested as
    35	## extensively as that contained in the main release, although it includes
    36	## newer versions of some applications which may provide useful features.
    37	## Also, please note that software in backports WILL NOT receive any review
    38	## or updates from the Ubuntu security team.
    39	deb http://ca.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    40	deb-src http://ca.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    41	
    42	deb http://security.ubuntu.com/ubuntu precise-security main restricted
    43	deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
    44	deb http://security.ubuntu.com/ubuntu precise-security universe
    45	deb-src http://security.ubuntu.com/ubuntu precise-security universe
    46	deb http://security.ubuntu.com/ubuntu precise-security multiverse
    47	deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
    48	
    49	## Uncomment the following two lines to add software from Canonical's
    50	## 'partner' repository.
    51	## This software is not part of Ubuntu, but is offered by Canonical and the
    52	## respective vendors as a service to Ubuntu users.
    53	# deb http://archive.canonical.com/ubuntu precise partner
    54	# deb-src http://archive.canonical.com/ubuntu precise partner
    55	
    56	## This software is not part of Ubuntu, but is offered by third-party
    57	## developers who want to ship their latest software.
    58	deb http://extras.ubuntu.com/ubuntu precise main
    59	deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu precise main
    60	deb-src http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu precise main
    61	deb-src http://extras.ubuntu.com/ubuntu precise main
    62	deb http://security.ubuntu.com/ubuntu lucid-security main
    63	deb-src http://security.ubuntu.com/ubuntu lucid-security main
michael@Michael-Sat-L350D:~$ ls -la  /etc/apt/sources.list.d
total 36
drwxr-xr-x 2 root root 4096 Nov  9 21:33 .
drwxr-xr-x 6 root root 4096 Dec  2 13:16 ..
-rw-r--r-- 1 root root  148 Nov  9 21:33 brousselle-slowmovideo-precise.list
-rw-r--r-- 1 root root  148 Oct  8 16:22 brousselle-slowmovideo-precise.list.save
-rw-r--r-- 1 root root  170 Nov  9 21:33 danielrichter2007-grub-customizer-precise.list
-rw-r--r-- 1 root root  180 Nov  9 21:33 google-talkplugin.list
-rw-r--r-- 1 root root  180 Oct  8 16:22 google-talkplugin.list.save
-rw-r--r-- 1 root root  169 Nov  9 21:33 private-ppa.launchpad.net_commercial-ppa-uploaders_master-pdf-editor_ubuntu.list
-rw-r--r-- 1 root root    0 Sep 13 18:04 stebbins-handbrake-releases-precise.list
-rw-r--r-- 1 root root   81 Sep 13 18:04 stebbins-handbrake-releases-precise.list.save
michael@Michael-Sat-L350D:~$ 

```

Should I go ahead and try the other?

Thanks again,
M

---

### Post by Bashing-om on 2013-12-03
azitizz; Hi !

In /etc/apt/sources.list:
> 
62	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main
63	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main

Not a source for precise ... delete those lines:
and also in  /etc/apt/sources.list:
> 
59	deb [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu) precise main
60	deb-src [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu) precise main

duplicated in /etc/apt/sources.list.d directory:
> 
-rw-r--r-- 1 root root    0 Sep 13 18:04 stebbins-handbrake-releases-precise.list
-rw-r--r-- 1 root root   81 Sep 13 18:04 stebbins-handbrake-releases-precise.list.save

Remove the lines for the PPA in /etc/apt/sources.list.d. Chances are there are two versions of handbrake installed. The file size is 0 for stebbins-handbrake-releases-precise.list so it is of no value and maybe the package manager is hollering about bad formatting (??).
Now unless it is your desire to keep the version from the PPA, I would remove the PPA (ppa purge) and use what is within the repository. The version in the repository is tested and validated to work well in that install, whereas with the PPA you are the tester.

Either way, we need to make sure there is not two version of handbrake installed.
check:
```

dpkg -l handbrake
apt-cache policy handbrake

```
Let's see what that returns.

The package manager
[INDENT][INDENT]tells no lies
[/INDENT][/INDENT]

---

### Post by azitizz on 2013-12-03
> **Bashing-om said:**
> 

In /etc/apt/sources.list:

Not a source for precise ... delete those lines:
and also in  /etc/apt/sources.list:

duplicated in /etc/apt/sources.list.d directory:


Thanks Bashing

Excuse my ignorance, but I cant seem to see the above lines you said to remove in my softare sources list. I tried accessing it by simply navigating to the folder with the file manager, and clicking on the file "sources.list" in the folder "apt", heres what comes up (screewnshot) I also just used the software centre to access it but same list.
[ATTACH=CONFIG]248329[/ATTACH]

> **Bashing-om said:**
> 
Either way, we need to make sure there is not two version of handbrake installed.
check:
Code:
```
dpkg -l handbrake
apt-cache policy handbrake
```
Let's see what that returns.


Heres the result:
```
michael@Michael-Sat-L350D:~$ dpkg -l handbrake
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  handbrake      <none>         (no description available)
michael@Michael-Sat-L350D:~$ apt-cache policy handbrake
handbrake:
  Installed: (none)
  Candidate: (none)
  Version table:
michael@Michael-Sat-L350D:~$
```

---

### Post by Bashing-om on 2013-12-03
azitizz; Hey ,

Let's use the text editor to edit a file: directly
Standard operating procedure is to always make a backup of any file that is edited - never can tell what might perchance.
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list-bac
gksudo gedit /etc/apt/sources.list

```
Remove the two lines in question, or if you prefer, comment out those lines by placing a "#" at the start of the lines.
save the file and exit back to terminal.
//
As to the out put of "dpkg" and "apt-cache" .. apparently handbrake is not the correct identifier for the application.
A bit of looking about maybe "handbrake-gtk" and "handbrake-cli" ?;
Try:
```

dpkg -l handbrake-gtk
dpkg -l handbrake-cli
apt-cache policy handbrake-gtk
apt-cache policy handbrake-cli

```
and if still no return (!!).
We go hunting !
```

sudo find / -name "handbrake*"

```
[INDENT][INDENT]we will get to the bottom of things
[/INDENT][/INDENT]

---

### Post by azitizz on 2013-12-05
> **Bashing-om said:**
> 
Remove the two lines in question, or if you prefer, comment out those lines by placing a "#" at the start of the lines.
save the file and exit back to terminal.

found the lines and deleted them. (I made a backup)

> **Bashing-om said:**
> 
As to the out put of "dpkg" and "apt-cache" .. apparently handbrake is not the correct identifier for the application.
A bit of looking about maybe "handbrake-gtk" and "handbrake-cli" ?;
Try:
```

dpkg -l handbrake-gtk
dpkg -l handbrake-cli
apt-cache policy handbrake-gtk
apt-cache policy handbrake-cli

```
and if still no return (!!).
We go hunting !
```

sudo find / -name "handbrake*"

```
[INDENT][INDENT]we will get to the bottom of things
[/INDENT][/INDENT]

Heres the result of all the trues, looks like something came up...

```
michael@Michael-Sat-L350D:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list-bac
[sudo] password for michael: 
michael@Michael-Sat-L350D:~$ gksudo gedit /etc/apt/sources.list
michael@Michael-Sat-L350D:~$ dpkg -l handbrake-gtk
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  handbrake-gtk  0.9.9ppa1~prec versatile DVD ripper and video transcoder - 
michael@Michael-Sat-L350D:~$ dpkg -l handbrake-cli
No packages found matching handbrake-cli.
michael@Michael-Sat-L350D:~$ apt-cache policy handbrake-gtk
handbrake-gtk:
  Installed: 0.9.9ppa1~precise1
  Candidate: 0.9.9ppa1~precise1
  Version table:
 *** 0.9.9ppa1~precise1 0
        100 /var/lib/dpkg/status
michael@Michael-Sat-L350D:~$ apt-cache policy handbrake-cli
N: Unable to locate package handbrake-cli
michael@Michael-Sat-L350D:~$ sudo find / -name "handbrake*"
/usr/share/doc/handbrake-gtk
/home/michael/Downloads/handbrake-gtk_0.9.9ppa1~precise1_amd64.deb
/var/lib/dpkg/info/handbrake-gtk.list
/var/lib/dpkg/info/handbrake-gtk.md5sums
michael@Michael-Sat-L350D:~$ 
```

---

### Post by Bashing-om on 2013-12-05
azitizz; Well ...
Sorta confusing .. the out put of "dpkg" says handbrake is installed and no complaints, but then why does "find" not find the install location ?

Is handbrake functional ?

And what returns from :
```

cat /var/lib/dpkg/info/handbrake-gtk.list

```
And we can look about some more.

On a better note, the package manager I expect is all happy now,

[INDENT][INDENT]sometimes I wonder, other times I do not know
[/INDENT][/INDENT]

---

### Post by azitizz on 2013-12-24
> **Bashing-om said:**
> azitizz; Well ...

And what returns from :
```

cat /var/lib/dpkg/info/handbrake-gtk.list

```


Heres what come out:
```
michael@Michael-Sat-L350D:~$ cat /var/lib/dpkg/info/handbrake-gtk.list
/.
/usr
/usr/bin
/usr/bin/ghb
/usr/share
/usr/share/doc
/usr/share/doc/handbrake-gtk
/usr/share/doc/handbrake-gtk/changelog.gz
/usr/share/doc/handbrake-gtk/copyright
/usr/share/icons
/usr/share/icons/hicolor
/usr/share/icons/hicolor/16x16
/usr/share/icons/hicolor/16x16/apps
/usr/share/icons/hicolor/16x16/apps/hb-icon.png
/usr/share/icons/hicolor/256x256
/usr/share/icons/hicolor/256x256/apps
/usr/share/icons/hicolor/256x256/apps/hb-icon.png
/usr/share/icons/hicolor/48x48
/usr/share/icons/hicolor/48x48/apps
/usr/share/icons/hicolor/48x48/apps/hb-icon.png
/usr/share/icons/hicolor/32x32
/usr/share/icons/hicolor/32x32/apps
/usr/share/icons/hicolor/32x32/apps/hb-icon.png
/usr/share/icons/hicolor/128x128
/usr/share/icons/hicolor/128x128/apps
/usr/share/icons/hicolor/128x128/apps/hb-icon.png
/usr/share/icons/hicolor/22x22
/usr/share/icons/hicolor/22x22/apps
/usr/share/icons/hicolor/22x22/apps/hb-icon.png
/usr/share/icons/hicolor/64x64
/usr/share/icons/hicolor/64x64/apps
/usr/share/icons/hicolor/64x64/apps/hb-icon.png
/usr/share/icons/hicolor/24x24
/usr/share/icons/hicolor/24x24/apps
/usr/share/icons/hicolor/24x24/apps/hb-icon.png
/usr/share/applications
/usr/share/applications/ghb.desktop
michael@Michael-Sat-L350D:~$ 

```

I Havent got the "no entry" symbol with the same error msg again since...

But trying to update the packages, I get the following error message and I cant complete the update:
[ATTACH=CONFIG]248870[/ATTACH]
Can it be related?

---

### Post by Bashing-om on 2013-12-25
azitizz; Hey,

Hard to say from that screen shot what is not taking place.
Post back the output of terminal codes:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f
sudo dpkg -C

``` that dpkg command takes an upper case "c".

To show what the package manager thinks.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by azitizz on 2013-12-25
> **Bashing-om said:**
> azitizz; Hey,

Hard to say from that screen shot what is not taking place.
Post back the output of terminal codes:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f
sudo dpkg -C

``` that dpkg command takes an upper case "c".

To show what the package manager thinks.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

Funny, it seems to have iupgrded just fine this way. Howver my internet froze in the process, but seemingly after everythign was downloaded, as it continued to install without any error messages. Something was frozen and I had to reboot, so I can only post the output of the last two commands:

```
michael@Michael-Sat-L350D:~$ sudo apt-get install -f
[sudo] password for michael: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-ubuntuoneui-3.0 libubuntuoneui-3.0-1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
michael@Michael-Sat-L350D:~$ sudo dpkg -C
michael@Michael-Sat-L350D:~$ 
```

Not sure if that reveals anything....but looks fairly uneventful.

---

### Post by Bashing-om on 2013-12-25
azitizz; Looks wonderful to me !

Run:
```

sudo apt-get update
sudo apt-get upgrade

```
If it again runs clean, play with your system. I bet all is in order .

Else, well we are here !

[INDENT][INDENT]all's well that ends well[/INDENT][/INDENT]

---

### Post by azitizz on 2013-12-25
Alls looking good. Thaks very much. All except for my overheating problem... If you got any pointers how to diagnose and solve this this would be so nice. 

problem seems my fans wont respond to changes in cpu temp. In windows works fine. And after I suspend the computer once in Ubuntu the fans work as they should. So I always try and suspend once after everytime I boot up, but of course I forget once in a while and it results in a dramatic and unexpected shutdown in the middle of something.

I did have this probelm once before and it got solved but my search for the solution again is dautning with so may suggestions for the solution and most not working...

---

### Post by Bashing-om on 2013-12-25
azitizz; Great !

For the overheating problem... just try disabling hibernate in Windows, particularly so if it is Windows8.
That way Windows releases the control of the hardware.
If the situation persist, by all means open another thread, so those with the knowledge sees the post.

[INDENT][INDENT]it could happen
[/INDENT][/INDENT]

---

