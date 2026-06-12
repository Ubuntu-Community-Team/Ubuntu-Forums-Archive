---
title: "Package manager is broken :("
date: 2006-10-30
forum: General Help
---

### Post by Tobster on 2006-10-30
My package manager is broken this happen when I was using Automatix :-- (

if someone could help me I be a very happy Tobster ;)

---

### Post by autocrosser on 2006-10-30
Automatix changes your /etc/apt/sources.list--when you look in the directory, you should find the backup that automatix made--as sudo, you can open the list (I use gedit) and "restore" your original sources.

---

### Post by Tobster on 2006-10-30
Thanks

If u could say but i did not understand, LOL :)  If you could say that in a less complicated way for me (Im not a bright spark! (kidding) I would be greatful

---

### Post by autocrosser on 2006-10-30
Sorry bout' that--As I said--Automatix mucks with the file that Synaptic, Apt & Aptitude all use. So I would (as root user) edit the /etc/apt/sources.list file by using the backup that automatix made--you should be able to see it--will have a date or say "backup" in the name.

If you as sudo-open both the "current" sources.list & the backup--(sudo gedit /etc/apt/sources.list in a terminal & then open another terminal and do sudo gedit /etc/apt/<whatever the name is>)--you can edit the "correct" file back to "ubuntu goodness"8)

---

### Post by meng on 2006-10-30
Try this as an alternative way of achieving what autocrosser is saying (you have to open a terminal):

cd /etc/apt
ls source*
(look for the thing that is sources.list.backup, sources.list.bak or even sources.list~, that's what you need)
sudo mv sources.list sources.list.automatix (enter your user password when prompted)
sudo mv sources.list~ [or whatever that file is called] sources.list
sudo apt-get update

And then try the package manager again.

---

### Post by autocrosser on 2006-10-30
Thank you meng--you said it better that I did:mrgreen:

---

### Post by Tobster on 2006-10-30
Hi

Thanks for helping me this is what I got so far:

toby@toby-desktop:~$ cd /etc/apt
toby@toby-desktop:/etc/apt$ ls source*
sources.list~           sources.list_backup_200610302310
sources.list.automatix  sources.list.distUpgrade

sources.list.d:
toby@toby-desktop:/etc/apt$ sudo mv sources.list sources.list.automatix
mv: cannot stat `sources.list': No such file or directory
toby@toby-desktop:/etc/apt$ sudo mv sources.list sources.list.automatix 
mv: cannot stat `sources.list': No such file or directory
toby@toby-desktop:/etc/apt$ cd /etc/apt
toby@toby-desktop:/etc/apt$ ls source*
sources.list~           sources.list_backup_200610302310
sources.list.automatix  sources.list.distUpgrade

sources.list.d:
toby@toby-desktop:/etc/apt$ sudo mv sources.list sources.list.automatix
mv: cannot stat `sources.list': No such file or directory
toby@toby-desktop:/etc/apt$

---

### Post by autocrosser on 2006-10-30
here is my sources.list---just rename & remove the .txt (can't upload files named .list)--and then in a terminal do a sudo cp ~/Desktop/sources.list /etc/apt

then do sudo apt-get update  (I assume you are on Edgy?)


Opps!!! I forgot that it is optimized for the Pacific-Northwest!!
You could use it--but I think your download speed would be bad](*,)

You can edit all the US sources with the British ones--

meng--do you have a better answer for him??

---

### Post by meng on 2006-10-30
Ok that's why your package manager isn't working, someone's deleted your sources.list. Restore it like so

cd /etc/apt
sudo mv sources.list_backup_200610302310 sources.list
sudo apt-get update

---

### Post by Tobster on 2006-10-30
I hate to say this but that someone was me woops! :)

---

### Post by Tobster on 2006-10-30
This is were im at now:

toby@toby-desktop:~$ cd /etc/apt
toby@toby-desktop:/etc/apt$ sudo mv sources.list_backup_200610302310 sources.list
toby@toby-desktop:/etc/apt$ sudo apt-get update
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_GB            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_GB
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release.gpg [191B]   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Translation-en_GB  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Translation-en_GB             
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates Release.gpg [189B]            
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates Release                          
Get: 4 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]          
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
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_GB
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages
Fetched 4B in 0s (6B/s)
Reading package lists... Done
toby@toby-desktop:/etc/apt$

---

### Post by meng on 2006-10-30
Cool, try running your package manager again now.

---

### Post by Tobster on 2006-10-30
It pops up and goes again.  Should I reboot?

Thanks

Toby

---

### Post by meng on 2006-10-30
Can't hurt to reboot, although it's not necessary for most things. Go ahead and knock yourself out. Just before you do, show us what's in the sources.list now:

cat /etc/apt/sources.list

---

### Post by Tobster on 2006-10-30
What the code again to get the source

---

### Post by meng on 2006-10-30
Just
cat /etc/apt/sources.list

(it will print the contents of the file to the screen)
Post the results here so we can check em.

---

### Post by Tobster on 2006-10-30
toby@toby-desktop:~$ cat /etc/apt/sources.list

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main


toby@toby-desktop:~$

---

### Post by meng on 2006-10-30
Looks fine to me.

---

### Post by Tobster on 2006-10-30
I click on the update icon it pops up and then disappers :confused: 

mmmm

---

### Post by Tobster on 2006-10-30
thanks for your help

I be back tomorrow if no luck as it nearly 1am

---

### Post by Tobster on 2006-10-30
toby@toby-desktop:~$ apl-get
bash: apl-get: command not found
toby@toby-desktop:~$ apt-get
apt 0.6.45ubuntu14 for linux i386 compiled on Sep 27 2006 23:43:26
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to continue if the integrity check fails
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
toby@toby-desktop:~$

---

### Post by arnieboy on 2006-10-30
> **Tobster said:**
> My package manager is broken this happen when I was using Automatix :-- (

if someone could help me I be a very happy Tobster ;)
first of all you should never try to run two package managers simultaneously (thats asking for trouble). In any case, if you are using Automatix2, there is an option on the AX main menu under **File-->Remove Automatix sources**
That will restore your original sources.list at any time. Also, AX does not "muck" with the sources.list. It merely adds whats missing from the official ubuntu repos and additional repos if and only the user wants.
IN any case **File-->Remove Automatix** repos will restore the original sources.list at any point of time. This is a feature no other package manager currently has.

---

### Post by arnieboy on 2006-10-30
also it might be possible that the update manager is broken on latest updates from edgy main.

---

### Post by autocrosser on 2006-10-31
Sorry 'bout the muck statement--In australia it is more of a "normal" word than here in the states--I do keep forgetting---

---

