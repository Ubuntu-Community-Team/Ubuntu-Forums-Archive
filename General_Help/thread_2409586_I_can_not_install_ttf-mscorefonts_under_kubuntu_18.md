---
title: "I can not install ttf-mscorefonts under kubuntu 18"
date: 2019-01-04
forum: General Help
---

### Post by ivancsvetkov on 2019-01-04
Hello,
I try to install microsoft fonts as it is written here [https://www.ostechnix.com/install-microsoft-windows-fonts-ubuntu-16-04/](https://www.ostechnix.com/install-microsoft-windows-fonts-ubuntu-16-04/)

```
sudo apt install ttf-mscorefonts-installer
```

and 
```
sudo fc-cache -f -v
```

and even restarted the OS
I thought that is all.

and I see this package installed : [https://imgur.com/a/s65iG1M](https://imgur.com/a/s65iG1M)

But I do not see any additive fonts like Times, Courier in Settings->Font management or Libre Office in font selection.

I found directory [/usr/share/fonts/truetype/msttcorefonts]("file:///usr/share/fonts/truetype/msttcorefonts"), but it is empty.

Did I miss some steps ?

My system :
```
$ uname -a
Linux serge 4.15.0-43-generic #46-Ubuntu SMP Thu Dec 6 14:45:28 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
$ lsb_release -d; uname -r; uname -i
Description:    Ubuntu 18.04.1 LTS
4.15.0-43-generic
x86_64

```
Checking installed packages :
```
$ apt list *mscorefonts*
Listing... Done
ttf-mscorefonts-installer/bionic,bionic,now 3.6ubuntu2 all [installed]

$ apt list *cabextract*
Listing... Done
cabextract/bionic,now 1.6-1.1 amd64 [installed,automatic]

$ apt list *debconf*
Listing... Done
cdebconf/bionic 0.213ubuntu1 amd64
cdebconf-gtk/bionic 0.213ubuntu1 amd64
debaux-debconf/bionic,bionic 0.1.12-1 all
debconf/bionic,bionic,now 1.5.66 all [installed]
debconf-doc/bionic,bionic 1.5.66 all
debconf-i18n/bionic,bionic,now 1.5.66 all [installed]
debconf-kde-data/bionic,bionic,now 1.0.3-0ubuntu1 all [installed]
debconf-kde-dbg/bionic 1.0.3-0ubuntu1 amd64
debconf-kde-helper/bionic 1.0.3-0ubuntu1 amd64
debconf-utils/bionic,bionic 1.5.66 all
fusiondirectory-plugin-debconf/bionic-updates,bionic-updates 1.0.19-1ubuntu0.18.04.1 all
fusiondirectory-plugin-debconf-schema/bionic-updates,bionic-updates 1.0.19-1ubuntu0.18.04.1 all
gkdebconf/bionic 2.0.3 amd64
libdebconf-kde-dev/bionic 1.0.3-0ubuntu1 amd64
libdebconf-kde1/bionic,now 1.0.3-0ubuntu1 amd64 [installed]
libdebconfclient0/bionic,now 0.213ubuntu1 amd64 [installed]
libdebconfclient0-dev/bionic 0.213ubuntu1 amd64
oem-config-debconf/bionic-updates,bionic-updates 18.04.14.9 all
po-debconf/bionic,bionic,now 1.0.20 all [installed,automatic]
python-debconf/bionic,bionic 1.5.66 all
python3-debconf/bionic,bionic,now 1.5.66 all [installed,automatic]
ubiquity-frontend-debconf/bionic-updates 18.04.14.9 amd64

$ apt list *debfonf*
Listing... Done

$ apt list *update-notifier-common*
Listing... Done
update-notifier-common/bionic-updates,bionic-updates,now 3.192.1.4 all [installed]
N: There is 1 additional version. Please use the '-a' switch to see it

$ apt list *xfonts-utils*
Listing... Done
xfonts-utils/bionic,now 1:7.7+6 amd64 [installed]

```

How to add these fonts ?

Thanks!

---

### Post by howefield on 2019-01-04
Looks like there is a problem with the server failing to download the fonts to you. Have a look in your /var/log/apt/term.log file for a clue. If you can see such an error as below or similar there is a way around it.

```
tail -n 20 /var/log/apt/term.log 
Unpacking ttf-mscorefonts-installer (3.7ubuntu4~really3.6ubuntu3) ...
Processing triggers for update-notifier-common (3.192.7) ...
ttf-mscorefonts-installer: processing...
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/andale32.exe
Get:1 http://downloads.sourceforge.net/corefonts/andale32.exe [198 kB]
Fetched 198 kB in 1s (207 kB/s)                                                          
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/arial32.exe
Err:1 http://downloads.sourceforge.net/corefonts/arial32.exe
  Could not wait for server fd - select (11: Resource temporarily unavailable) [IP: 5.10.152.194 443]
E: Failed to fetch https://vorboss.dl.sourceforge.net/project/corefonts/the fonts/final/arial32.exe  Could not wait for server fd - select (11: Resource temporarily unavailable) [IP: 5.10.152.194 443]
E: Download Failed
Setting up ttf-mscorefonts-installer (3.7ubuntu4~really3.6ubuntu3) ...
Processing triggers for fontconfig (2.13.0-5ubuntu3) ...
Log ended: 2019-01-04  09:55:06
```

---

### Post by ivancsvetkov on 2019-01-04
Yes, I found error:
> Err:1 [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe)
  Redirection from https to 'http://downloads.sourceforge.net/mirrorproblem?failedmirror=netix.dl.sourceforge.net' is forbidden [IP: 87.121.121.2 443]

How to fix it ?

---

### Post by clementc on 2019-01-04
Hi [**[COLOR=#000000]ivancsvetkov[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115460"),

Can you please try running the following commands in Terminal:

```
sudo apt purge ttf-mscorefonts-installer
wget http://ftp.de.debian.org/debian/pool/contrib/m/msttcorefonts/ttf-mscorefonts-installer_3.7_all.deb -P ~/Downloads
sudo apt install ~/Downloads/ttf-mscorefonts-installer_3.7_all.deb
sudo apt-mark hold ttf-mscorefonts-installer
```

---

### Post by howefield on 2019-01-04
> **ivancsvetkov said:**
> Yes, I found error:..

You could create a folder in ~/home called mscorefonts, download the fonts from : 

```
https://sourceforge.net/projects/corefonts/files/the%20fonts/final/
```

and store them in the /home/$USER/mscorefonts folder that you created earlier, then run..

```
sudo dpkg-reconfigure ttf-mscorefonts-installer
```

You should be prompted to give the path for the downloaded files and the rest should be self explanatory.

Having said that, I installed a couple of hours ago and the server appeared to be back up and running so 

```
sudo apt-get install --reinstall ttf-mscorefonts-installer
```

might work.

---

### Post by ivancsvetkov on 2019-01-05
Thank you, that was helpful! I did not find where Salved button? Seems, I have  to push it?

---

### Post by QIII on 2019-01-05
Hello!

Click ***Thread Tools*** and then ***Mark this thread as solved***.

Cheers!

---

