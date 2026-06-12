---
title: "[SOLVED] OpenOffice m118 buggy"
date: 2005-07-27
forum: General Help
---

### Post by manicka on 2005-07-27
I was wondering how other people are finding m118. I've found it quite buggy with random erros and crashes/lockups (yes, I reported them all).

For now I've gone back to m113 and will see what the next build is like. Is anyone else finding 118 less stable than 113?

---

### Post by wbiggers on 2005-07-29
I installed m118 on my WindowsXP machine at work yesterday and today I'm finding the same thing.

I just installed Ubuntu on my home system but the latest OOo2 that I could find on the ubuntu packages was very old.  I would like to get m113 but don't know where to get it.  Can you help?

Thanks-

---

### Post by manicka on 2005-07-29
[QUOTE=wbiggers]I installed m118 on my WindowsXP machine at work yesterday and today I'm finding the same thing.

I just installed Ubuntu on my home system but the latest OOo2 that I could find on the ubuntu packages was very old.  I would like to get m113 but don't know where to get it.  Can you help?

Thanks-[/QUOTE]
 Copy the script below into a text file. Save it as evolutioncolt_oo2.sh 113, then in the files properties (right click-->Properties) make it executable by changing the permissions.
Before you start make a directory called openoffice2 in your home directory and save the atttached tar.gz file (OOo2MenuItems.tar.gz) into it. 
Then in a terminal change to the directory where the script is saved and run the command
```
./evolutioncolt_oo2.sh 113
```

The script

```
Installation Script for OpenOffice.org 2 Beta (1.9.xxx)
#
# Contact spayne@sebpayne.com with any problems
#
# This script is copyright Evolution Colt 2005.
#
# Modified by zerohalo:
# Accepts OOo2-beta snapshot number as parameter passed to the script.
# Works with modified menu items that point to /opt/openoffice.org1.9.
# Installs OOo2-beta in /opt/openoffice.org1.9
# 
#

echo
echo "Welcome to the Evolution Colt Script for Installing OpenOffice 2 Beta. This has been officaly tested by us on Ubuntu Linux Hoary Hedgehog 5.04. Please Note: If you are promopted with 'Password:', enter your password. This is the NON-JAVA version which assumes you have the Sun JRE installed. If you do, this could destroy you setup. You should cancel it now (Ctrl+C) and run the Java version evolutioncolt_oo2_java.sh as this will install the JRE. You have been warned...."
echo
sleep 10

# Stage 1: Get the Files

echo
echo "***Downloading the Installation File**"
echo
sleep 2

mkdir ~/openoffice2
cd ~/openoffice2
wget http://www.mirror.ac.uk/mirror/sunsite.dk/openoffice/developer/680_m$1/OOo_1.9.$1_LinuxIntel_install.tar.gz

# Stage 2: Covert the Files to Debian Packages and Installation

echo
echo "***Converting the Packages to the Debian Format***"
echo
sleep 2

tar zxvf OOo_1.9.$1_LinuxIntel_install.tar.gz
cd SRC680_m$1_native_packed-1_en-US.8930/RPMS
rm openofficeorg-testtool-1.9.$1-1.i586.rpm
rm -r desktop-integration
sudo alien -d *.rpm
rm *.rpm
sudo dpkg -i *.deb
sudo chmod 555 /opt/openoffice.org1.9.$1/program/soffice
sudo mv -f /opt/openoffice.org1.9.$1 /opt/openoffice.org1.9

# Stage 3: Copying the Menu Links

echo
echo "***Menu Links***"
echo
echo "Make sure you've downloaded OOoMenuItems.tar.gz and placed"
echo "it in your ~/openoffice2 folder. If you haven't, open"
echo "another terminal and do so now before continuing."
echo
echo "If OOo2MenuItems.tar.gz is in place, press enter."
echo
read

cd ~/openoffice2
tar zxvf OOo2MenuItems.tar.gz
sudo cp menu/* /usr/share/applications/

# Stage 4: Copying the Icons

echo
echo "***Moving the Icons to the Right Place***"
echo
sleep 1

sudo cp 16x16/* /usr/share/icons/hicolor/16x16/apps/
sudo cp 32x32/* /usr/share/icons/hicolor/32x32/apps/
sudo cp 48x48/* /usr/share/icons/hicolor/48x48/apps/

echo
echo "***Finished! You can now start OpenOffice2.org from the Applications menu***"
echo
sleep 2
```

Note that this will not install 118. Try here for a script that will install 118 and hopefully later versions.

[http://www.ubuntuforums.org/showpost.php?p=267226&postcount=233](http://www.ubuntuforums.org/showpost.php?p=267226&postcount=233)

HTH :D

---

### Post by wbiggers on 2005-07-30
Thanks for the script, etc.  It didn't quite work as expected.  First, I got and error when trying to download the file.  Apparently the wild-card characters that were supposed to read 1.9.113 didn't work.  I just edited the script so the download happened as expected by explicitely stating the file to be downloaded.

Second, the download apparently wasn't in the location where the script expected - so I just manually walked through the commands in the script instead of using the automated format.

Still - I've FINALLY got 1.9.113!!  :smile: 

By the way, before I got my office XP system downgraded to 113, I also had a crash in 118 with Impress.  Never had that in 113.  I think you are right on when you state 118 has quirks/bugs.

Thanks again!

---

### Post by manicka on 2005-07-30
Just curious.  :-k 

did you run the script with the command 

./evolutioncolt_oo2.sh 113    or just       ./evolutioncolt_oo2.sh

It won't download or process the files properly without the version number that you are downloading tacked onto the end.

There is also a wiki now that you may find useful for future installations

[https://wiki.ubuntu.com/OpenOffice2Beta](https://wiki.ubuntu.com/OpenOffice2Beta)

---

### Post by wbiggers on 2005-08-03
Not sure what I did to prevent the script from working - I'm still new to the scripting world.  I ended up just editing the commands so they explicitely stated release 113 instead of using the variable/input method.

I noticed m122 is now out but the release notes don't say anything about the problems with 118.  I wonder if the issues with 118 were fixed.

---

