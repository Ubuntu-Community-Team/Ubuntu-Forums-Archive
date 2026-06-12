---
title: "update errors when installing brave browser"
date: 2019-12-23
forum: General Help
---

### Post by robertcull1 on 2019-12-23
I am trying to install the brave browser from different instructions. I have tried using:
```

sudo apt install snapd
sudo snap install brave
```

The browser freezes. I uninstalled with:

```
sudo snap remove brave

```
I tried installing with the instructions here:

[https://www.tecrobust.com/install-brave-web-browser-linux-ubuntu-fedora-rhel-debian-latest/](https://www.tecrobust.com/install-brave-web-browser-linux-ubuntu-fedora-rhel-debian-latest/)

```
sudo apt install apt-transport-https curl

curl -s [https://brave-browser-apt-release.s3.brave.com/brave-core.asc](https://brave-browser-apt-release.s3.brave.com/brave-core.asc) | sudo apt-key --keyring /etc/apt/trusted.gpg.d/brave-browser-release.gpg add -

```
source /etc/os-release

```
echo "deb [arch=amd64] [https://brave-browser-apt-release.s3.brave.com/](https://brave-browser-apt-release.s3.brave.com/) $UBUNTU_CODENAME main" | sudo tee /etc/apt/sources.list.d/brave-browser-release-${UBUNTU_CODENAME}.list

```
but when I try:

sudo apt update

I get the following output:

```
Get:1 [http://dl.winehq.org/wine-builds/ubuntu](http://dl.winehq.org/wine-builds/ubuntu) bionic InRelease [6,259 B]
Hit:3 [https://brave-browser-apt-release.s3.brave.com](https://brave-browser-apt-release.s3.brave.com) bionic InRelease
Hit:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease
Ign:5 [https://dl.bintray.com/aluxian/deb](https://dl.bintray.com/aluxian/deb) beta InRelease
Err:6 [https://dl.bintray.com/aluxian/deb](https://dl.bintray.com/aluxian/deb) beta Release
  404  Not Found [IP: 34.214.69.171 443]
Err:1 [http://dl.winehq.org/wine-builds/ubuntu](http://dl.winehq.org/wine-builds/ubuntu) bionic InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F
Err:2 [http://www.getdeb.net/ubuntu](http://www.getdeb.net/ubuntu) bionic-getdeb InRelease                                                           
  403  Forbidden [IP: 143.95.32.90 80]
Hit:7 [https://s3-us-west-2.amazonaws.com/brave-apt](https://s3-us-west-2.amazonaws.com/brave-apt) xenial InRelease                       
Hit:8 [http://ppa.launchpad.net/audio-recorder/ppa/ubuntu](http://ppa.launchpad.net/audio-recorder/ppa/ubuntu) bionic InRelease
Hit:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease                                          
Hit:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease                                 
Hit:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease                               
Hit:12 [http://ppa.launchpad.net/deadsnakes/ppa/ubuntu](http://ppa.launchpad.net/deadsnakes/ppa/ubuntu) bionic InRelease   
Hit:13 [http://ppa.launchpad.net/git-core/ppa/ubuntu](http://ppa.launchpad.net/git-core/ppa/ubuntu) bionic InRelease          
Ign:14 [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) bionic InRelease      
Hit:15 [http://ppa.launchpad.net/ubuntuhandbook1/avidemux/ubuntu](http://ppa.launchpad.net/ubuntuhandbook1/avidemux/ubuntu) bionic InRelease
Err:16 [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) bionic Release          
  404  Not Found [IP: 91.189.95.83 80]
Reading package lists... Done                                                  
E: The repository 'https://dl.bintray.com/aluxian/deb beta Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: [http://dl.winehq.org/wine-builds/ubuntu](http://dl.winehq.org/wine-builds/ubuntu) bionic InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F
E: The repository 'http://dl.winehq.org/wine-builds/ubuntu bionic InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/bionic-getdeb/InRelease](http://archive.getdeb.net/ubuntu/dists/bionic-getdeb/InRelease)  403  Forbidden [IP: 143.95.32.90 80]
E: The repository 'http://archive.getdeb.net/ubuntu bionic-getdeb InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:54
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:54
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:54
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:54
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:54
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:54
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:54
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:54
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:54
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:54
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:54
W: Target Packages (apps/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target Packages (apps/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target Packages (apps/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target Translations (apps/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target Translations (apps/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target DEP-11 (apps/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target DEP-11 (apps/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target DEP-11-icons-small (apps/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target DEP-11-icons (apps/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target CNF (apps/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target CNF (apps/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2

```
It's all greek to me. Can anyone offer any suggestions?

---

### Post by Holger_Gehrke on 2019-12-24
The problem isn't with the brave repository at all but with several old repositories you've got in your sources that either don't exist any more ([www.getdeb.net]("http://www.getdeb.net") and possibly dl.bintray.com/aluxian), don't have any packages for your version of Ubuntu since they haven't been updated in a very long time (the ubuntu-wine ppa) or have changed their key since you installed them (dl.winehq.org).
The procedure for fixing the key for dl.winehq.org is described in this [post on the winehq forum]("https://forum.winehq.org/viewtopic.php?t=31621").
For removing the three broken repositories you've got three option:
[LIST]
[*]There should be a graphical tool for doing this. On Xubuntu - which I am using - it's found in settings and is called 'Software & Updates'. The actual program this runs is 'software-properties-gtk'. This - or something similar - should be available on all flavours of Ubuntu. It gives you a list of all sources for packages and gives you the option to activate, deactivate or edit them. 
[*]You can use 'sudo add-apt-repository --remove' with the repository as a parameter to remove a repository. 
[*]You can remove configuration fragments from /etc/apt/sources.list.d/ (getdeb seems to be installed as such a fragment; 'sudo rm /etc/apt/sources.list.d/getdeb.list' should get rid of this problem) or edit /etc/apt/sources.list ('sudoedit /etc/apt/sources.list' is probably the best way to do this) and either remove the lines which define the broken sources or mark them as comments (which stops apt from using these sources) by putting a '#' at the beginning of the line. 
[/LIST]

Holger

---

### Post by robertcull1 on 2019-12-24
I have found out that I can keep it from freezing by turning off the hardware acceleration under settings.

Thanks!

---

