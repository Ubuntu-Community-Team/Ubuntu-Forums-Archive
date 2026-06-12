---
title: "Error from lsb_release -a"
date: 2017-07-12
forum: General Help
---

### Post by Alan5127 on 2017-07-12
Hi All,

I am getting an error from running an 'lsb_release -a' as follows:

```


username@machinename:/var/lib/apt$ lsb_release -a

Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/lsb_release.py", line 32, in get_distro_info
    csvfile = open('/usr/share/distro-info/%s.csv' % origin.lower())
FileNotFoundError: [Errno 2] No such file or directory: '/usr/share/distro-info/debian.csv'

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/bin/lsb_release", line 25, in <module>
    import lsb_release
  File "/usr/lib/python3/dist-packages/lsb_release.py", line 51, in <module>
    get_distro_info()
  File "/usr/lib/python3/dist-packages/lsb_release.py", line 35, in get_distro_info
    csvfile = open('/usr/share/distro-info/debian.csv')
FileNotFoundError: [Errno 2] No such file or directory: '/usr/share/distro-info/debian.csv'


```


I came across this when trying to diagnose an update error, and Bucky Ball, as an aside, mentioned the command to determine my exact version of Ubuntu.  This is a link to that thread in case the two issues are related:

[https://ubuntuforums.org/showthread.php?t=2365720](https://ubuntuforums.org/showthread.php?t=2365720)


How do I go about diagnosing and fixing the error shown above from 'lsb_release -a'?  It looks like perhaps I have a problem with 'python3' - should I uninstall and reinstall (or just reinstall it over the top of the existing one) or is there a danger in trying that?

I would also note that, as far as I can tell, I have no directory called:

/usr/share/distro-info/

and therefore no file therein called 'debian.csv'

It seemed odd that there should be a file with that name on my Ubuntu machine at all (although I believe that Ubuntu might have been originally based on Debian, so perhaps not so unlikely), but I thought I would look to see if that file exists anywhere on my machine, so I did a 'find' and got the following (null) result but including a permission error despite running it using sudo - I don't know if that is expected or not:

```


username@machinename:/$ sudo find / -name debian.csv

find: ‘/run/user/1001/gvfs’: Permission denied


```

If I change directory into '/run/user/1001/gvfs/', and run 'ls' or 'ls -la', it (apparently) works fine, but reports no files (or sub-directories) in there.  However, if I try 'sudo ls' from that directory, I get the permission denied error which seems really weird.


Any suggestions welcome!


Thanks,

Alan.

---

### Post by vasa1 on 2017-07-12
Please try the following commands:```
cat /etc/*-release
cat /var/log/installer/media-info
cat /etc/debian_version
env | grep XDG_CURRENT_DESKTOP
echo $DESKTOP_SESSION
```And better not to mess with anything with "python" in the file's name!

Could you also try to recollect 
whether you've done a clean install of Ubuntu 16.04 or an upgrade from an earlier version
whether you've installed any ppa at all

---

### Post by steeldriver on 2017-07-12
The error from `find` concerning gvfs is normal

It sounds like your distro-info-data package is missing or corrupted - does

```

dpkg --audit distro-info-data

```

reveal anything?

---

### Post by vasa1 on 2017-07-12
And here's one more, based on steeldriver's post:```
**locate distro-info**
/usr/share/distro-info
/usr/share/distro-info/debian.csv
/usr/share/distro-info/ubuntu.csv
/usr/share/doc/distro-info-data
/usr/share/doc/distro-info-data/README.Debian
/usr/share/doc/distro-info-data/changelog.gz
/usr/share/doc/distro-info-data/copyright
/var/lib/dpkg/info/distro-info-data.list
/var/lib/dpkg/info/distro-info-data.md5sums
```

---

### Post by Bucky Ball on 2017-07-12
@vasa1: Yes, there does seem to be manually installed PPAs. Please refer to post #3 in other thread linked in the first post here. ;)

---

### Post by vasa1 on 2017-07-12
> **Bucky Ball said:**
> @vasa1: Yes, there does seem to be manually installed PPAs. Please refer to post #3 in other thread linked in the first post here. ;)
Thanks!

FTR, here they are:```
Hit:5 http://ppa.launchpad.net/obsproject/obs-studio/ubuntu xenial InRelease     
Hit:6 http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu xenial InRelease  
Ign:7 https://mega.nz/linux/MEGAsync/xUbuntu_16.04 ./ InRelease
Get:8 https://mega.nz/linux/MEGAsync/xUbuntu_16.04 ./ Release [988 B]

```I included the mega.nz lines because anything not from the standard repos could be worth wondering about.

---

### Post by Alan5127 on 2017-07-12
Hi Vasa1,

> **vasa1 said:**
> Please try the following commands:```
cat /etc/*-release
cat /var/log/installer/media-info
cat /etc/debian_version
env | grep XDG_CURRENT_DESKTOP
echo $DESKTOP_SESSION
```And better not to mess with anything with "python" in the file's name!

Could you also try to recollect 
whether you've done a clean install of Ubuntu 16.04 or an upgrade from an earlier version
whether you've installed any ppa at all

Noted on not messing with Python!  I haven't, and now won't, do anything with that.

I upgraded this machine from Ubuntu 14.04LTS.  I can't remember exactly when, but I would guess around a year ago.

Outputs from the commands you requested are as follows:

```


username@machinename:/$ cat /etc/*-release

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.2 LTS"
NAME="Ubuntu"
VERSION="16.04.2 LTS (Xenial Xerus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.04.2 LTS"
VERSION_ID="16.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
VERSION_CODENAME=xenial
UBUNTU_CODENAME=xenial


```
```


username@machinename:/$ cat /var/log/installer/media-info

cat: /var/log/installer/media-info: No such file or directory


```
```


username@machinename:/$ cat /etc/debian_version

stretch/sid


```
```


username@machinename:/$ env | grep XDG_CURRENT_DESKTOP

XDG_CURRENT_DESKTOP=Unity


```
```


username@machinename:/$ echo $DESKTOP_SESSION

ubuntu


```


In terms of PPAs, I think the answer is yes.  I ran a 'sudo apt update' and got the output below showing at least three (I think), non standard, software sources.  All three are 'expected' in that I have installed osb_studio, handbrake, and megasync, but if you think they might be the cause of the issues, let me know.  I am not using obs_studio at all now, so that could certainly go, and handbrake I have probably used once in the last year, so that could go too if it is a possible issue.  I have all my photos on mega.nz so I'd prefer to keep that, but I guess we could remove it and reinstall later if necessary.

```


username@machinename:/var/lib/apt$ sudo apt update

Hit:1 http://nz.archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://nz.archive.ubuntu.com/ubuntu xenial-updates InRelease                                                                                                                                           
Hit:3 http://archive.canonical.com/ubuntu xenial InRelease                                                                                                                                                   
Get:4 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]                                                                                   
Hit:5 http://ppa.launchpad.net/obsproject/obs-studio/ubuntu xenial InRelease     
Hit:6 http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu xenial InRelease  
Ign:7 https://mega.nz/linux/MEGAsync/xUbuntu_16.04 ./ InRelease
Get:8 https://mega.nz/linux/MEGAsync/xUbuntu_16.04 ./ Release [988 B]
Fetched 103 kB in 3s (27.1 kB/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.


```


In terms of your second post, I also ran that locate command, and got this:

```


username@machinename:/$ locate distro-info

/usr/share/distro-info
/usr/share/doc/distro-info-data
/usr/share/doc/distro-info-data/README.Debian
/usr/share/doc/distro-info-data/changelog.gz
/usr/share/doc/distro-info-data/copyright
/var/lib/dpkg/info/distro-info-data.list
/var/lib/dpkg/info/distro-info-data.md5sums


```


Thanks for your help,

Alan.

---

### Post by Alan5127 on 2017-07-12
Hi SteelDriver,

> **steeldriver said:**
> The error from `find` concerning gvfs is normal

It sounds like your distro-info-data package is missing or corrupted - does

```

dpkg --audit distro-info-data

```

reveal anything?


Running that command gives no output at all.  I tried running it first as me (non admin), and then using sudo, but neither gives any output at all.

Does that indicate a problem?

Thanks,

Alan.

---

### Post by steeldriver on 2017-07-12
OK nevermind it was a bit of a long shot

Regardless, I don't think it will do any harm to re-install that package

```

sudo apt-get install --reinstall distro-info-data

```

(assuming the original error isn't blocking you from doing package operations)

---

### Post by Alan5127 on 2017-07-12
Hi SteelDriver,

> **steeldriver said:**
> OK nevermind it was a bit of a long shot

Regardless, I don't think it will do any harm to re-install that package

```

sudo apt-get install --reinstall distro-info-data

```

(assuming the original error isn't blocking you from doing package operations)

I ran the reinstall, and it all seems to have run as expected:

```


username@machinename:~$ sudo apt-get install --reinstall distro-info-data

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 4,048 B of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://nz.archive.ubuntu.com/ubuntu xenial-updates/main i386 distro-info-data all 0.28ubuntu0.3 [4,048 B]
Fetched 4,048 B in 0s (44.3 kB/s)            
(Reading database ... 248401 files and directories currently installed.)
Preparing to unpack .../distro-info-data_0.28ubuntu0.3_all.deb ...
Unpacking distro-info-data (0.28ubuntu0.3) over (0.28ubuntu0.3) ...
Setting up distro-info-data (0.28ubuntu0.3) ...


```

I then rebooted (I figured no harm), and tried 'dpkg --audit distro-info-data', but still get no response at all from that one.

 However, when I ran 'lsb_release -a' again, I now get the following result which looks to be better than before:

```


username@machinename:/var/lib/apt$ lsb_release -a

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial


```

I ran it both with and without sudo, and got the same result.

Whilst I am not sure if that is exactly what I should expect (in particular, the 'No LSB modules are available' might be right or wrong), it is way better than before :-)

For what its worth, I imagine it is all good, since it seems to match what Bucky Ball indicated I should get in the other thread:

[https://ubuntuforums.org/showthread.php?t=2365720&p=13665064#post13665064](https://ubuntuforums.org/showthread.php?t=2365720&p=13665064#post13665064)

Would you agree that this is now solved?

I don't want to waste your time, but if now fixed, could you hazard a guess as to what caused it to go wrong?  I am guessing that somehow my install of 'distro-info-data' got corrupted.  If so, then is it possible that other applications might have also been corrupted by something, and is there any way to run a mass reinstall of everything (rather than wiping and reinstalling Ubuntu entirely)?

Thanks,

Alan.

---

### Post by Alan5127 on 2017-07-13
Hi,

I am going to mark this one as 'solved', and it also appears to have solved the issue I was having with the 'failed updates' warning sign in the other thread (see my OP above), so I'll be marking that one as 'solved' too.

Thank you for all your help.

Alan.

---

