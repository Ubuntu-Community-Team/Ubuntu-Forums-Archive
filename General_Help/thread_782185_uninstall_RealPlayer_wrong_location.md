---
title: "uninstall RealPlayer wrong location"
date: 2008-05-04
forum: General Help
---

### Post by 4now on 2008-05-04
Hi I'm trying to unistall RealPlayer - because it isn't working installed in the wrong location

home/USERNAME/RealPlayer

I'm trying to uninstall it to the best of my ability

sudo apt-get remove RealPlayer 11


keep getting packages cannot be found

would love some assistance

---

### Post by warp99 on 2008-05-04
> **4now said:**
> Hi I'm trying to unistall RealPlayer - because it isn't working installed in the wrong location

home/USERNAME/RealPlayer

I'm trying to uninstall it to the best of my ability

sudo apt-get remove RealPlayer 11


keep getting packages cannot be found

would love some assistance

You installed reaplayer using the installer from realplay not from the apt-get package manager system, so you have to remove realplayer per their installer instructions.

In order to uninstall you need to download and run the the following script:

[https://player.helixcommunity.org/files/2005/downloads/uninst.sh](https://player.helixcommunity.org/files/2005/downloads/uninst.sh)

---

### Post by 4now on 2008-05-04
help please

how do I run the script :oops:

---

### Post by 4now on 2008-05-04
am I running it ???
I guess it didn't work


***@***-desktop:~$ cd ~/Desktop
***@***-desktop:~/Desktop$ chmod + uninst.sh
***@***-desktop:~/Desktop$ ./uninst.sh
./uninst.sh: 188: Syntax error: "(" unexpected (expecting "}")
***@***-desktop:~/Desktop$

---

### Post by warp99 on 2008-05-05
> **4now said:**
> am I running it ???
I guess it didn't work


***@***-desktop:~$ cd ~/Desktop
***@***-desktop:~/Desktop$ chmod + uninst.sh
***@***-desktop:~/Desktop$ ./uninst.sh
./uninst.sh: 188: Syntax error: "(" unexpected (expecting "}")
***@***-desktop:~/Desktop$

First of all the command to make the file executable is 'chmod +x uninst.sh'. Second if you type './uninst.sh -h' you'll see a list of usage instructions:

```
./uninst.sh -h

Usage: uninst [-f] [-a] [-l] [-h] [<UNINST_DIR>]
  -f: Force-remove all files including those installed to shared directories.
  -a: Guess and uninstall all found installations.
  -l: List all player installation found without actually performing uninstallation.
  -h: This help menu.
  Without specifying <UNINST_DIR>, it is taken to be the directory where
  uninst is executed from.
  <UNINST_DIR> has to be an absolute path!
  By default (without -f or -a), uninst tries to take the best course of
  action by removing shared .png only if there is no other player
  installation on the system that can use the resources.
  It always removes broken symbolic links.
```
and finally when you reinstall Realplayer please use the following instructions:

Download the bin file here:

[http://www.real.com/linux/?pageid=unagi.17735126.wrapper&pageregion=footer&src=realplayer_com&pcode=rn&opage=realplayer_com](http://www.real.com/linux/?pageid=unagi.17735126.wrapper&pageregion=footer&src=realplayer_com&pcode=rn&opage=realplayer_com)

go to the directory the file is in, then change the permissions of the file to execute:
```
chmod 775 RealPlayer11GOLD.bin
```
now execute the file as root using 'sudo':
```
sudo ./RealPlayer11GOLD.bin
```
the installer will extract and ask some questions:
```
Enter the complete path to the directory where you want
RealPlayer to be installed.  You must specify the full
pathname of the directory and have write privileges to
the chosen directory.
Directory:  [/opt/real/RealPlayer]:

```
use the directory '/usr/local/realplayer' since this is where local files are normally placed for Debian based installations:
```
You have selected the following RealPlayer configuration:

Destination:            /usr/local/realplayer

Enter [F]inish to begin copying files, or [P]revious to go
back to the previous prompts: [F]:

```
the program starts to install the files complete with menu entries. Realplayer will also find your /usr/lib/mozilla/plugins and install some web plugins. Now there is one more thing you need to do and that is place a symlink to the replayer bin file:
```
sudo ln -s /usr/local/realplayer/realplay /usr/local/bin/realplay
```
this will allow realplayer to be launched system-wide by just entering 'realplay'.

---

