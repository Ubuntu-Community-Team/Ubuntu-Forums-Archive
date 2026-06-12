---
title: "[SOLVED] /etc/apt/sources.list.d/medibuntu.list error"
date: 2008-01-21
forum: General Help
---

### Post by TimHulley on 2008-01-21
Whenever I try to open the Synaptic Package Manager or try to add/remove a program, I get the following error message:

E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I'm very new to linux, and so I'm pretty stumped.
Here is my source list file:

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

Any help would be much appreciated!

---

### Post by TimHulley on 2008-01-21
Actually, this is the file the error message is referring to:

  <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "DTD/xhtml1-strict.dtd">
                <html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
                <head>
                    <title>Medibuntu :: Multimedia, Entertainment &amp; Distractions In Ubuntu</title>
                    <meta http-equiv="Content-Type" content="text/xhtml+xml; charset=utf-8" />
                    <link rel="stylesheet" href="medibuntu.css" type="text/css" />
                </head>
                    <body>
                        <div id="header">
                            <h1><span class="hidden">Medibuntu<br />Multimedia, Entertainment &amp; Distractions In Ubuntu</span></h1>
                        </div>
                        <ul id="menu"><li><a href="index.php">Presentation</a></li>
                        <li><a href="http://help.ubuntu.com/community/Medibuntu">Repository Howto</a></li>
                        <li><a href="packages.php">Packages</a></li>
                        <li><a href="contact.php">Contact us</a></li>
                                 </ul>
        <div id="page">
              <h2>Presentation</h2>
                                <p>
                                    <strong>
                                        Medibuntu (Multimedia, Entertainment &amp; Distractions In Ubuntu) is a repository of packages that cannot be included into the Ubuntu distribution for legal reasons (copyright, license, patent, etc).
                                    </strong>
                                </p>
                                <p>
                                    Medibuntu is a packaging project dedicated to distributing software that cannot be included in Ubuntu for various reasons, related to geographical variations in legislation regarding intellectual property, security and other issues:
                                </p>
                                <ul>
                                    <li>patentability of software, algorithms, formats and other abstract creation</li>
                                    <li>legal restrictions on freedom of speech or communication</li>
                                    <li>restrictions on the use of certain types of technical solution, such as cryptography</li>
                                    <li>legal restrictions on imports of software technology, requiring for example specific permissions</li>
                                    <li>etc.</li>
                                </ul>
                                <p>
                                    A lot of excellent <a href="http://www.fsf.org/licensing/essays/free-sw.html">free software</a> and non-free software is affected by such restriction somewhere in the world, thus preventing its inclusion into Ubuntu that, for economy and simplicity, are generally identical for all countries.
                                </p>
                                <p>
                                    We refuse to resign ourselves to abandoning software that may be legally useful somewhere, and we have chosen to provide it with professional quality packaging, easily usable within the context of Ubuntu.<br />
                                    This repository provides packages for Ubuntu distribution.
                                </p>
                                <p>
                                    It is your legal responsibility to make sure that the software you are installing can be legally used in your country and for your intended purpose.
                                </p>
                                        </div>
          <div id="paypal"><form action="https://www.paypal.com/cgi-bin/webscr" method="post">
<p>
<input type="hidden" name="cmd" value="_xclick" />
<input type="hidden" name="business" value="maxenced@gmail.com" />
<input type="hidden" name="item_name" value="Medibuntu" />
<input type="hidden" name="no_shipping" value="0" />
<input type="hidden" name="no_note" value="1" />
<input type="hidden" name="currency_code" value="EUR" />
<input type="hidden" name="tax" value="0" />
<input type="hidden" name="bn" value="PP-DonationsBF" />
<input type="image" src="https://www.paypal.com/en_US/i/btn/x-click-but04.gif" name="submit" alt="Effectuez vos paiements via PayPal : une solution rapide, gratuite et sécurisée" />
<img alt="" src="https://www.paypal.com/en_US/i/scr/pixel.gif" width="1" height="1" />
</p>
</form>
          </div>
                        <div id="footer">:: designed by <a href="http://www.most-enchained.com">_Enchained</a> - logo by <a href="http://www.racoon97.net">racoon97</a> - Domain by <a href="http://flosoft.biz">Flosoft</a>  - Managed by <a href="http://www.dunnewind.net">Sp4rKy</a> ::          </div>
<!-- phpmyvisites -->
<a href="http://www.phpmyvisites.us/" title="phpMyVisites | Open source web analytics"
onclick="window.open(this.href);return(false);"><script type="text/javascript">
<!--
var a_vars = Array();
var pagename='';

var phpmyvisitesSite = 2;
var phpmyvisitesURL = "http://stats.dunnewind.net/phpmyvisites.php";
//-->
</script>
<script language="javascript" src="http://stats.dunnewind.net/phpmyvisites.js" type="text/javascript"></script>
<object><noscript><p>phpMyVisites | Open source web analytics
<img src="http://stats.dunnewind.net/phpmyvisites.php" alt="Statistics" style="border:0" />
</p></noscript></object></a>
<!-- /phpmyvisites --> 
    </body>
                </html>

---

### Post by forestpixie on 2008-01-21
open the file with gedit

```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```

select all and delete so the file is empty and save it

then do these in terminal

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get update
```

also - so that when you post big text lists there is a # button that you can use to enclose it in code tags

---

### Post by TimHulley on 2008-01-21
Thanks for the help, that fixed it. Also thanks for the tip on posting code. Obviously, I'm pretty new to this stuff.

---

### Post by forestpixie on 2008-01-21
we all were at some point - also can you mark thread solved :)

---

### Post by lurhesch on 2008-07-22
Hello

I am quiet new with this stuff and just running linux for my second day, this is my 4th install and am trying to avoid the 5th as I already took some work and time in it.
I have the same problem as described above, I am running Kubuntu 8.04 and using Kate instead to edit this file, however I seem not to have the rights to edit this file.
When I look at the properties it says the owner/user is root.

Is there another possibility to change this file, can I log in as root user? How do I do this.

I really appreciate any help. 

Thx

---

### Post by perlluver on 2008-07-22
```
kdesu kate /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by aomlives on 2008-07-22
> **lurhesch said:**
> Is there another possibility to change this file, can I log in as root user? How do I do this.

For more information about root access:

[http://ubuntuforums.org/showthread.php?t=866990](http://ubuntuforums.org/showthread.php?t=866990)

Good luck :)

---

### Post by lurhesch on 2008-07-22
Thanks al lot! Everythings works including the dvd I was trying to get play.

I used the 3 commands in the terminal but I got some error messages which really bother me.
(I do not know if I can paste such long text)

Is says something about my cd rom when using these commands. Does anyone knows how I can solve this?

'
 /etc/apt/sources.list.d/medibuntu.list
[sudo] password for peter:
--22:10:45--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 226 [text/plain]

100%[====================================>] 226           --.--K/s

22:10:45 (40.60 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [226/226]

peter@desktop:~$ wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | s
udo apt-key add - && sudo apt-get update
OK
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423) hardy Release.
gpg
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423) hardy/main Tra
nslation-en_US
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423) hardy/restrict
ed Translation-en_US
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423) hardy Release
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423) hardy/main Pac
kages
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423) hardy/restrict
ed Packages
Err cdrom://Kubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423) hardy/main Pac
kages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update can
not be used to add new CD-ROMs
Err cdrom://Kubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423) hardy/restrict
ed Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update can
not be used to add new CD-ROMs
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy Release.gpg
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy/multiverse Translation-en_US
Get:2 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy-updates Release.gpg [189B]
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy Release
Get:4 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy-updates Release [58.5kB]
Get:5 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [189B]
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Get:6 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [9335B]
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy/main Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy/restricted Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy/main Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy/restricted Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy/universe Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy/universe Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy/multiverse Sources
Get:7 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy-updates/main Packages [279kB]
Get:8 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages [6209B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [31.8kB]
Get:10 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy-updates/restricted Packages [6465B]
Get:11 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy-updates/main Sources [80.9kB]
Get:12 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages [7801B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [6465B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources [8117B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources [908B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages [23.8kB]
Get:17 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy-updates/restricted Sources [908B]
Get:18 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy-updates/universe Packages [70.8kB]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources [3318B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages [3891B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources [14B]
Get:22 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy-updates/universe Sources [16.6kB]
Get:23 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy-updates/multiverse Packages [16.1kB]
Get:24 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy-updates/multiverse Sources [2612B]
Fetched 693kB in 0s (868kB/s)
W: Failed to fetch cdrom:[Kubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]                                    /dists/hardy/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD                                    -ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Kubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]                                    /dists/hardy/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make t                                    his CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used                                     instead.
peter@desktop:~$ sudo apt-get update
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423) hardy Release.gpg
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423) hardy/main Translation-en_US
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423) hardy/restricted Translation-en_US
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423) hardy Release
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423) hardy/main Packages
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423) hardy/restricted Packages
Err cdrom://Kubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423) hardy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Kubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423) hardy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy Release.gpg
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy/main Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy/restricted Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy/main Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy/restricted Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy/universe Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy/universe Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
W: Failed to fetch cdrom:[Kubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/dists/hardy/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Kubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/dists/hardy/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.'



I did a little searching on internet and inserted the install cd and did following in the terminal : sudo apt-cdrom add 

peter@desktop:~$ sudo apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
Identifying.. [670ed85832bb27d9956d3afc4f62ec7b-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
Found label 'Kubuntu-KDE4 8.04.1 _Hardy Heron_ - Release amd64 (20080702)'
This disc is called:
'Kubuntu-KDE4 8.04.1 _Hardy Heron_ - Release amd64 (20080702)'
Copying package lists...gpgv: Signature made Wed 02 Jul 2008 02:50:21 AM CEST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Kubuntu-KDE4 8.04.1 _Hardy Heron_ - Release amd64 (20080702)]/ hardy main restricted
Unmounting CD-ROM...
Repeat this process for the rest of the CDs in your set.
peter@desktop:~$     

Could someone tell me if there is anything additional to do? I have only have 1 install cd. Is this enough?

---

### Post by aomlives on 2008-07-22
Could you use the Code tags next time plz, it makes your post a lot more readable ;)

Anyway, you have already added a lot of repositories, so you're sure to find what you want on the internet repos. You can now easily exclude the cdrom from the updating process, so you don't need it anymore every time you check. 

By doing:

```
gksudo gedit /etc/apt/sources.list
```As described in this thread: [http://ubuntuforums.org/showthread.php?t=560681](http://ubuntuforums.org/showthread.php?t=560681)

That should take care of the cdrom warning.

If you're still concerned about the other error, maybe  you'll find the answer here, but I'm not sure whether it will help you're specific case:

[https://answers.launchpad.net/ubuntu/+question/38298](https://answers.launchpad.net/ubuntu/+question/38298)

grtz :)

---

