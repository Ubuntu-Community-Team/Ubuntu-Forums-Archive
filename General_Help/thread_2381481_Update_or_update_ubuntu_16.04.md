---
title: "Update or update ubuntu 16.04"
date: 2018-01-01
forum: General Help
---

### Post by up4cyber on 2018-01-01
I think something is broken or messed up Ubuntu repo management wise.  I too have the same errors when I try to update a 16.04.2 LTS system.  

It appears that some of the repos pointed to in the sources files are either new or taken offline.  This results in an incomplete update command execution and thus the upgrade command fails as the packages list is not updates/complete/valid.

I have tried changing the sources from the UK to US, FR, IN, GR, DE so its not a individual repo problem - it's bigger than that.  But until this is fixed the systems will not update - why there maybe so many threads on cron updates not working too.

The back end of another failing "# apt-get update" command:

```
Err:20 http://security.ubuntu.com/ubuntu xenial-security/main Sources
  Connection failed [IP: 91.189.88.152 80]
Ign:30 http://security.ubuntu.com/ubuntu xenial-security/restricted Sources
Ign:32 http://security.ubuntu.com/ubuntu xenial-security/universe Sources
Ign:41 http://security.ubuntu.com/ubuntu xenial-security/multiverse Sources
Ign:51 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
Ign:53 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages
Ign:61 http://security.ubuntu.com/ubuntu xenial-security/main all Packages
Ign:69 http://security.ubuntu.com/ubuntu xenial-security/main Translation-en_GB
Ign:71 http://security.ubuntu.com/ubuntu xenial-security/main Translation-en
Ign:79 http://security.ubuntu.com/ubuntu xenial-security/restricted amd64 Packages
Ign:87 http://security.ubuntu.com/ubuntu xenial-security/restricted i386 Packages
Reading package lists... Done                         
W: The repository 'http://archive.ubuntu.com/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://archive.ubuntu.com/ubuntu xenial-updates Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://archive.ubuntu.com/ubuntu xenial-backports Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://archive.canonical.com/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://security.ubuntu.com/ubuntu xenial-security Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial/main/source/Sources  Connection failed [IP: 91.189.88.152 80]
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial-updates/main/source/Sources  Connection failed [IP: 91.189.88.152 80]
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial-backports/main/source/Sources  Connection failed [IP: 91.189.88.152 80]
E: Failed to fetch http://archive.canonical.com/ubuntu/dists/xenial/partner/source/Sources  Connection failed [IP: 91.189.92.150 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/dists/xenial-security/main/source/Sources  Connection failed [IP: 91.189.88.152 80]
[COLOR=#000000][FONT=Menlo]E: Some index files failed to download. They have been ignored, or old ones used instead.
[/FONT][/COLOR]
```

Grateful for any clues, but I have been playing with this problem for 4 days :-(

Also it's not a DNS or proxy issue - I have been around those and conducted multiple look-ups from various parts of the internet.

Cheers

---

### Post by howefield on 2018-01-01
Post moved to own thread.

---

### Post by #&amp;thj^% on 2018-01-01
> **up4cyber said:**
> I think something is broken or messed up Ubuntu repo management wise.  I too have the same errors when I try to update a 16.04.2 LTS system.  

It appears that some of the repos pointed to in the sources files are either new or taken offline.  This results in an incomplete update command execution and thus the upgrade command fails as the packages list is not updates/complete/valid.

I have tried changing the sources from the UK to US, FR, IN, GR, DE so its not a individual repo problem - it's bigger than that.  But until this is fixed the systems will not update - why there maybe so many threads on cron updates not working too.

The back end of another failing "# apt-get update" command:

```
Err:20 http://security.ubuntu.com/ubuntu xenial-security/main Sources
  Connection failed [IP: 91.189.88.152 80]
Ign:30 http://security.ubuntu.com/ubuntu xenial-security/restricted Sources
Ign:32 http://security.ubuntu.com/ubuntu xenial-security/universe Sources
Ign:41 http://security.ubuntu.com/ubuntu xenial-security/multiverse Sources
Ign:51 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
Ign:53 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages
Ign:61 http://security.ubuntu.com/ubuntu xenial-security/main all Packages
Ign:69 http://security.ubuntu.com/ubuntu xenial-security/main Translation-en_GB
Ign:71 http://security.ubuntu.com/ubuntu xenial-security/main Translation-en
Ign:79 http://security.ubuntu.com/ubuntu xenial-security/restricted amd64 Packages
Ign:87 http://security.ubuntu.com/ubuntu xenial-security/restricted i386 Packages
Reading package lists... Done                         
W: The repository 'http://archive.ubuntu.com/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://archive.ubuntu.com/ubuntu xenial-updates Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://archive.ubuntu.com/ubuntu xenial-backports Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://archive.canonical.com/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://security.ubuntu.com/ubuntu xenial-security Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial/main/source/Sources  Connection failed [IP: 91.189.88.152 80]
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial-updates/main/source/Sources  Connection failed [IP: 91.189.88.152 80]
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial-backports/main/source/Sources  Connection failed [IP: 91.189.88.152 80]
E: Failed to fetch http://archive.canonical.com/ubuntu/dists/xenial/partner/source/Sources  Connection failed [IP: 91.189.92.150 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/dists/xenial-security/main/source/Sources  Connection failed [IP: 91.189.88.152 80]
[COLOR=#000000][FONT=Menlo]E: Some index files failed to download. They have been ignored, or old ones used instead.
[/FONT][/COLOR]
```

Grateful for any clues, but I have been playing with this problem for 4 days :-(

Also it's not a DNS or proxy issue - I have been around those and conducted multiple look-ups from various parts of the internet.

Cheers

Have you run:
```
sudo apt-get clean
sudo apt-get update
```
show us any errors from the update command
EDIT: If the above dose not clear things up to "upgrade" then give this a try:
```
cd /etc/apt
sudo mv sources.list sources.list.original

```
And proceed to run your update again:
```
sudo apt-get update
sudo apt-get upgrade
```
Let us know and Good Luck.

---

### Post by up4cyber on 2018-01-01
Thanks for the pointers, I have had about 10 diff sources from around the planet, none have worked.  Here is the output from the latest commands (I cut the stuff from further in the update putput as it was error free)

```
Err:21 http://security.ubuntu.com/ubuntu xenial-security/main Sources
  Connection failed [IP: 91.189.88.162 80]
Ign:23 http://security.ubuntu.com/ubuntu xenial-security/restricted Sources
Ign:32 http://security.ubuntu.com/ubuntu xenial-security/universe Sources
Ign:42 http://security.ubuntu.com/ubuntu xenial-security/multiverse Sources
Ign:44 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
Ign:54 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages
Ign:62 http://security.ubuntu.com/ubuntu xenial-security/main all Packages
Ign:65 http://security.ubuntu.com/ubuntu xenial-security/main Translation-en_GB
Ign:73 http://security.ubuntu.com/ubuntu xenial-security/main Translation-en
Ign:81 http://security.ubuntu.com/ubuntu xenial-security/restricted amd64 Packages
Ign:82 http://security.ubuntu.com/ubuntu xenial-security/restricted i386 Packages
Reading package lists... Done
W: The repository 'http://archive.ubuntu.com/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://archive.ubuntu.com/ubuntu xenial-updates Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://archive.ubuntu.com/ubuntu xenial-backports Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://security.ubuntu.com/ubuntu xenial-security Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://archive.canonical.com/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial/main/source/Sources  Connection failed [IP: 91.189.88.162 80]
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial-updates/main/source/Sources  Connection failed [IP: 91.189.88.162 80]
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial-backports/main/source/Sources  Connection failed [IP: 91.189.88.162 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/dists/xenial-security/main/source/Sources  Connection failed [IP: 91.189.88.162 80]
E: Failed to fetch http://archive.canonical.com/ubuntu/dists/xenial/partner/source/Sources  Connection failed [IP: 91.189.92.150 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.
root@support:/home/support# mv /etc/apt/sources.list /etc/apt/sources.list-old
root@support:/home/support# apt-get update
Reading package lists... Done
root@support:/home/support# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
[COLOR=#000000][FONT=Menlo]0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.[/FONT][/COLOR]
```

Same errors as before :-(

I know this box needs updates and I cannot install anything as this point eg:
```
root@support:/home/support# apt install nmap
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nmap
root@support:/home/support# apt-get install htop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=#000000][FONT=Menlo]E: Unable to locate package htop[/FONT][/COLOR]
```

---

### Post by #&amp;thj^% on 2018-01-02
> **up4cyber said:**
> Thanks for the pointers, I have had about 10 diff sources from around the planet, none have worked.  
Same errors as before :-(

I know this box needs updates and I cannot install anything as this point eg:

Well what you have tried in the past would be a unknown for me, as there is nothing in your posts that actually state what you have tried. :D (Outside of changing the sources from the UK to US, FR, IN, GR, D)
Now this will be a tedious effort to try to solve this issue. (Just a heads up)
I have seen a handful of box's here iin UF with similar problems. (in 16.04)
I don't see any added PPA's that you may have added that could also result with this problem at hand.
Can you show me this please:
```
cd /etc/apt
ls
```
Please run the code one line at a time and paste back here.

---

### Post by up4cyber on 2018-01-02
What I did.
[LIST=1]
[*]I checked the DNS response for the erroring hostname on multiple servers on the internet to ensure I wasn't getting a stale response.
[*]I went here : [https://repogen.simplylinux.ch/](https://repogen.simplylinux.ch/)   and tried to get new sources from different countries to see if the repo I was using was corrupt somehow.  For each I remarked or removed the old contents and then added the new contents.
[*]I tried to connect to the identified servers to see if they were indeed Ubuntu servers - while they were all ubuntu servers several had default apache pages and the ones generated the errors didn't have the necessary folders or files.
[*]I did try to write all this in the post last night but the forum would not allow me to add or update any threads
[/LIST]

I followed your instructions here is the output of an ls command in the /etc/apt directory.

```
[COLOR=#000000][FONT=Menlo]root@support:/etc/apt# ls -las[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]total 44[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] 4 drwxr-xr-x  6 root root  4096 Jan  2 21:14 [COLOR=#5230E1]**.**[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] 4 drwxr-xr-x 92 root root  4096 Dec 31 04:40 [COLOR=#5230E1]**..**[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] 4 drwxr-xr-x  2 root root  4096 Dec 30 14:01 [COLOR=#5230E1]**apt.conf.d**[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] 0 -rw-r--r--  1 root root     0 Dec 30 14:26 gpg_keys.txt[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] 4 drwxr-xr-x  2 root root  4096 Apr 14  2016 [COLOR=#5230E1]**preferences.d**[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] 4 -rw-r--r--  1 root root  2967 Dec 31 04:07 sources.list[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] 4 drwxr-xr-x  2 root root  4096 Dec 31 04:15 [COLOR=#5230E1]**sources.list.d**[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] 4 -rw-r--r--  1 root root  1215 Dec 31 04:13 sources.list.save[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]12 -rw-r--r--  1 root root 12255 Apr 20  2016 trusted.gpg[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] 4 drwxr-xr-x  2 root root  4096 Dec 31 04:13 [/FONT][/COLOR][COLOR=#5230E1][FONT=Menlo][B]trusted.gpg.d
[/B][/FONT][/COLOR]
```

Here is the contents of the /etc/apt/sources.list:
```
[COLOR=#000000][FONT=Menlo]root@support:/etc/apt# cat /etc/apt/sources.list[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# deb cdrom:[Ubuntu-Studio 16.04 LTS _Xenial Xerus_ - Alpha amd64 (20151225)]/ xenial main multiverse restricted universe[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# newer versions of the distribution.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb http://archive.ubuntu.com/ubuntu/ xenial main restricted[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb-src http://archive.ubuntu.com/ubuntu/ xenial main restricted[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## Major bug fix updates produced after the final release of the[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## distribution.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb http://archive.ubuntu.com/ubuntu/ xenial-updates main restricted[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb-src http://archive.ubuntu.com/ubuntu/ xenial-updates main restricted[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## team, and may not be under a free licence. Please satisfy yourself as to[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## your rights to use the software. Also, please note that software in[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## universe WILL NOT receive any review or updates from the Ubuntu security[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## team.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb http://archive.ubuntu.com/ubuntu/ xenial universe[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb-src http://archive.ubuntu.com/ubuntu/ xenial universe[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb http://archive.ubuntu.com/ubuntu/ xenial-updates universe[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb-src http://archive.ubuntu.com/ubuntu/ xenial-updates universe[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## team, and may not be under a free licence. Please satisfy yourself as to [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## your rights to use the software. Also, please note that software in [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## multiverse WILL NOT receive any review or updates from the Ubuntu[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## security team.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb http://archive.ubuntu.com/ubuntu/ xenial multiverse[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb-src http://archive.ubuntu.com/ubuntu/ xenial multiverse[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb http://archive.ubuntu.com/ubuntu/ xenial-updates multiverse[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb-src http://archive.ubuntu.com/ubuntu/ xenial-updates multiverse[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## N.B. software from this repository may not have been tested as[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## extensively as that contained in the main release, although it includes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## newer versions of some applications which may provide useful features.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## Also, please note that software in backports WILL NOT receive any review[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## or updates from the Ubuntu security team.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb http://archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb-src http://archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## Uncomment the following two lines to add software from Canonical's[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## 'partner' repository.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## This software is not part of Ubuntu, but is offered by Canonical and the[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## respective vendors as a service to Ubuntu users.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb http://archive.canonical.com/ubuntu xenial partner[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb-src http://archive.canonical.com/ubuntu xenial partner[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb http://security.ubuntu.com/ubuntu xenial-security main restricted[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb http://security.ubuntu.com/ubuntu xenial-security universe[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb-src http://security.ubuntu.com/ubuntu xenial-security universe[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb http://security.ubuntu.com/ubuntu xenial-security multiverse[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
[/FONT][/COLOR]
```

for completeness here is the full output:

[https://pastebin.ubuntu.com/26308979/](https://pastebin.ubuntu.com/26308979/)

Grateful for any pointers 

Thanks!

---

### Post by #&amp;thj^% on 2018-01-02
> **up4cyber said:**
> What I did.
[LIST=1]
[*]I checked the DNS response for the erroring hostname on multiple servers on the internet to ensure I wasn't getting a stale response.
[*]I went here : [https://repogen.simplylinux.ch/](https://repogen.simplylinux.ch/)   and tried to get new sources from different countries to see if the repo I was using was corrupt somehow.  For each I remarked or removed the old contents and then added the new contents.
[*]I tried to connect to the identified servers to see if they were indeed Ubuntu servers - while they were all ubuntu servers several had default apache pages and the ones generated the errors didn't have the necessary folders or files.
[*]I did try to write all this in the post last night but the forum would not allow me to add or update any threads
[/LIST]

I followed your instructions here is the output of an ls command in the /etc/apt directory.

```
[COLOR=#000000][FONT=Menlo]root@support:/etc/apt# ls -las[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]total 44[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] 4 drwxr-xr-x  6 root root  4096 Jan  2 21:14 [COLOR=#5230E1]**.**[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] 4 drwxr-xr-x 92 root root  4096 Dec 31 04:40 [COLOR=#5230E1]**..**[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] 4 drwxr-xr-x  2 root root  4096 Dec 30 14:01 [COLOR=#5230E1]**apt.conf.d**[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] 0 -rw-r--r--  1 root root     0 Dec 30 14:26 gpg_keys.txt[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] 4 drwxr-xr-x  2 root root  4096 Apr 14  2016 [COLOR=#5230E1]**preferences.d**[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] 4 -rw-r--r--  1 root root  2967 Dec 31 04:07 sources.list[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] 4 drwxr-xr-x  2 root root  4096 Dec 31 04:15 [COLOR=#5230E1]**sources.list.d**[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] 4 -rw-r--r--  1 root root  1215 Dec 31 04:13 sources.list.save[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]12 -rw-r--r--  1 root root 12255 Apr 20  2016 trusted.gpg[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] 4 drwxr-xr-x  2 root root  4096 Dec 31 04:13 [/FONT][/COLOR][COLOR=#5230E1][FONT=Menlo][B]trusted.gpg.d
[/B][/FONT][/COLOR]
```

Here is the contents of the /etc/apt/sources.list:
```
[COLOR=#000000][FONT=Menlo]root@support:/etc/apt# cat /etc/apt/sources.list[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# deb cdrom:[Ubuntu-Studio 16.04 LTS _Xenial Xerus_ - Alpha amd64 (20151225)]/ xenial main multiverse restricted universe[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# newer versions of the distribution.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb http://archive.ubuntu.com/ubuntu/ xenial main restricted[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb-src http://archive.ubuntu.com/ubuntu/ xenial main restricted[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## Major bug fix updates produced after the final release of the[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## distribution.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb http://archive.ubuntu.com/ubuntu/ xenial-updates main restricted[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb-src http://archive.ubuntu.com/ubuntu/ xenial-updates main restricted[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## team, and may not be under a free licence. Please satisfy yourself as to[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## your rights to use the software. Also, please note that software in[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## universe WILL NOT receive any review or updates from the Ubuntu security[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## team.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb http://archive.ubuntu.com/ubuntu/ xenial universe[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb-src http://archive.ubuntu.com/ubuntu/ xenial universe[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb http://archive.ubuntu.com/ubuntu/ xenial-updates universe[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb-src http://archive.ubuntu.com/ubuntu/ xenial-updates universe[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## team, and may not be under a free licence. Please satisfy yourself as to [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## your rights to use the software. Also, please note that software in [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## multiverse WILL NOT receive any review or updates from the Ubuntu[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## security team.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb http://archive.ubuntu.com/ubuntu/ xenial multiverse[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb-src http://archive.ubuntu.com/ubuntu/ xenial multiverse[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb http://archive.ubuntu.com/ubuntu/ xenial-updates multiverse[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb-src http://archive.ubuntu.com/ubuntu/ xenial-updates multiverse[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## N.B. software from this repository may not have been tested as[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## extensively as that contained in the main release, although it includes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## newer versions of some applications which may provide useful features.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## Also, please note that software in backports WILL NOT receive any review[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## or updates from the Ubuntu security team.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb http://archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb-src http://archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## Uncomment the following two lines to add software from Canonical's[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## 'partner' repository.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## This software is not part of Ubuntu, but is offered by Canonical and the[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## respective vendors as a service to Ubuntu users.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb http://archive.canonical.com/ubuntu xenial partner[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb-src http://archive.canonical.com/ubuntu xenial partner[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb http://security.ubuntu.com/ubuntu xenial-security main restricted[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb http://security.ubuntu.com/ubuntu xenial-security universe[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb-src http://security.ubuntu.com/ubuntu xenial-security universe[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb http://security.ubuntu.com/ubuntu xenial-security multiverse[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
[/FONT][/COLOR]
```

for completeness here is the full output:

[https://pastebin.ubuntu.com/26308979/](https://pastebin.ubuntu.com/26308979/)

Grateful for any pointers 

Thanks!

Thanks for all your Great Information>>>Helpful! ;)
Now would you run this:
```
sudo apt-key update
```
Post any errors.Then run:
```
sudo apt update
```
paste that back here.

---

### Post by westie457 on 2018-01-02
Hi, can please post he output of these commands ```
uname -r
lsb_release -a
```

---

### Post by up4cyber on 2018-01-02
Cheers,

```
root@support:~# sudo apt-key update
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 4

gpg:              unchanged: 4

```

```
root@support:~# sudo apt update
Ign:1 http://archive.ubuntu.com/ubuntu xenial InRelease
Ign:2 http://security.ubuntu.com/ubuntu xenial-security InRelease            
Ign:3 http://archive.ubuntu.com/ubuntu xenial-updates InRelease              
Ign:4 http://archive.ubuntu.com/ubuntu xenial-backports InRelease                                         
Err:5 http://archive.ubuntu.com/ubuntu xenial Release                                                     
  Connection failed [IP: 91.189.88.162 80]
Err:6 http://archive.ubuntu.com/ubuntu xenial-updates Release                                             
  Connection failed [IP: 91.189.88.161 80]
Err:7 http://archive.ubuntu.com/ubuntu xenial-backports Release                                           
  Connection failed [IP: 91.189.88.162 80]
Ign:8 http://archive.canonical.com/ubuntu xenial InRelease                                                 
Err:9 http://security.ubuntu.com/ubuntu xenial-security Release                                            
  Connection failed [IP: 91.189.88.149 80]
Err:10 http://archive.canonical.com/ubuntu xenial Release
  Connection failed [IP: 91.189.91.15 80]
Reading package lists... Done                          
E: The repository 'http://archive.ubuntu.com/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu xenial-updates Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu xenial-backports Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://security.ubuntu.com/ubuntu xenial-security Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.canonical.com/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
[COLOR=#000000][FONT=Menlo]root@support:~#[/FONT][/COLOR][COLOR=#000000][FONT=Menlo] 
[/FONT][/COLOR]
```

```
root@support:~# uname -r
4.4.0-72-generic
[COLOR=#000000][FONT=Menlo]root@support:~#[/FONT][/COLOR][COLOR=#000000][FONT=Menlo] 
[/FONT][/COLOR]
```

```
root@support:~# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial
[COLOR=#000000][FONT=Menlo]root@support:~#[/FONT][/COLOR][COLOR=#000000][FONT=Menlo] 
[/FONT][/COLOR]
```

Thanks for your time

---

### Post by westie457 on 2018-01-02
Forgot this one. post the result please ```
ls -al /boot
```

---

### Post by up4cyber on 2018-01-02
Here you go:
```
root@support:~# ls -al /boot
total 143670
drwxr-xr-x  4 root root     3072 Apr 23  2017 **.**
drwxr-xr-x 23 root root     4096 Apr  4  2017 **..**
-rw-r--r--  1 root root  1239577 Apr 18  2016 abi-4.4.0-21-generic
-rw-r--r--  1 root root  1245659 Mar 24  2017 abi-4.4.0-71-generic
-rw-r--r--  1 root root  1245659 Mar 31  2017 abi-4.4.0-72-generic
-rw-r--r--  1 root root   189412 Apr 18  2016 config-4.4.0-21-generic
-rw-r--r--  1 root root   190236 Mar 24  2017 config-4.4.0-71-generic
-rw-r--r--  1 root root   190236 Mar 31  2017 config-4.4.0-72-generic
drwxr-xr-x  5 root root     1024 Apr 23  2017 **grub**
-rw-r--r--  1 root root 35685773 Feb 14  2017 initrd.img-4.4.0-21-generic
-rw-r--r--  1 root root 36221541 Mar 30  2017 initrd.img-4.4.0-71-generic
-rw-r--r--  1 root root 37494257 Apr 23  2017 initrd.img-4.4.0-72-generic
drwx------  2 root root    12288 Feb 14  2017 **lost+found**
-rw-------  1 root root  3853719 Apr 18  2016 System.map-4.4.0-21-generic
-rw-------  1 root root  3882277 Mar 24  2017 System.map-4.4.0-71-generic
-rw-------  1 root root  3882277 Mar 31  2017 System.map-4.4.0-72-generic
-rw-------  1 root root  7013968 Apr 18  2016 vmlinuz-4.4.0-21-generic
-rw-------  1 root root  7083344 Mar 24  2017 vmlinuz-4.4.0-71-generic
-rw-------  1 root root  7083248 Mar 31  2017 vmlinuz-4.4.0-72-generic
[COLOR=#000000][FONT=Menlo]root@support:~#[/FONT][/COLOR][COLOR=#000000][FONT=Menlo] [/FONT][/COLOR]
```

---

### Post by westie457 on 2018-01-02
Not sure if you missed the point when 16.04.2 became 16.04.3. if that is the case read this. [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

The following command is a simulation of what will likely be installed and removed, no changes to your system will happen ```
sudo apt -s install --install-recommends linux-generic-hwe-16.04 xserver-xorg-hwe-16.04
```

If you are happy with what is shown run the command again leaving out the '-s' then try ```
sudo apt update
sudo apt upgrade
```

Let us know the result.

---

### Post by up4cyber on 2018-01-03
Thanks for your time on this.  

The response is not good:
```
root@support:/home/cprsupport# apt -s install --install-recommends linux-generic-hwe-16.04 xserver-xorg-hwe-16.04
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-generic-hwe-16.04
E: Couldn't find any package by glob 'linux-generic-hwe-16.04'
E: Couldn't find any package by regex 'linux-generic-hwe-16.04'
E: Unable to locate package xserver-xorg-hwe-16.04
E: Couldn't find any package by glob 'xserver-xorg-hwe-16.04'
E: Couldn't find any package by regex 'xserver-xorg-hwe-16.04'
root@support:/home/cprsupport# apt -s install --install-recommends
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=#000000][FONT=Menlo]0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.[/FONT][/COLOR]
```

With a broken sources.list I cannot update anything on the system. 

 Annoyingly I built another system at the same time and it too has exactly the same problem - it cannot be updated.

:-9

---

### Post by westie457 on 2018-01-03
Are we trying to fix this issue purely in the terminal or do you have access to a desktop environment (GUI)?

I prefer sometimes  to use point and click apps. This will be difficult for me if you have only terminal access.

---

### Post by up4cyber on 2018-01-03
Sorry its a server there is no GUI and I cant install one either with the current problems.

---

### Post by westie457 on 2018-01-03
At the moment the only thing I can suggest is looking at this page to see if it gives you any ideas. [https://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-an-old-unsupported-release](https://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-an-old-unsupported-release)

Unfortunately my knowledge of the terminal is very nearly exhausted where servers are concerned, I wish you good luck if the page is helpful.

If it is not helpful it may be quicker to clean install from a newer iso.

---

### Post by up4cyber on 2018-01-07
Thanks for your help.    I think it's sad that a stock build can get borked like this.   I won't be rebuildings this box as a Ubuntu, I think RHEL maybe a better plan.  Cheers

---

### Post by dragonfly41 on 2018-01-07
Before you jump Ubuntu ship you could try installing webmin on server to do remote configuration.

---

### Post by up4cyber on 2018-01-08
> **dragonfly41 said:**
> Before you jump Ubuntu ship you could try installing webmin on server to do remote configuration.  I would love to but with a broken apt capability, I can't install anything (unless I use individual deb files) so flattening it seems the fastest fix.

---

