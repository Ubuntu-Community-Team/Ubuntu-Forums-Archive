---
title: "Two questions: editing files and headphones"
date: 2008-04-29
forum: General Help
---

### Post by FerociaCoutoura on 2008-04-29
1) Every ubuntu advice forum I go to mentions obscure instructions about finding certain lines of code or files and editing or adding to them.  I would imagine this is similar to the "run" function in Windows or making text files, saving them with a certain extension and running them.  Please tell me how to do this in ubuntu.

2) Headphone issue.  Sound comes out through my speakers and continues to do so when I plug headphones in.  Any ideas?

---

### Post by olejorgen on 2008-04-30
1) I'm not sure what you're asking here?
2) [http://ubuntuforums.org/showthread.php?t=773207](http://ubuntuforums.org/showthread.php?t=773207) (might solve it)

---

### Post by ryanhaigh on 2008-04-30
For the most part you are probably editing configuration files rather than code. To edit a file you simply navigate to where that file is and double click to open it in the text editor.  Often though especially if you are editing important files you need to open them as root (basically admin) as they are protected by permissions. To make this easier you could install a package called nautilus-gksu have a look for it in synaptic under system>admin>synaptic. Just search and you should find it.

Also a lot of the instructions are given for the terminal because the terminal always acts the same way, in Linux people can have a vast array of different configurations so its not always as easy as "press the start button, press control panel", instead the terminal is the universal tool and configurations are stored in flat files many of which have associated documentation. After a while you may grow to appreciate the simplicity and flexibility of this approach as I do. It can be a little daunting at first but if you know someone with a little experience just ask for some help or as always you can post in these forums.

---

### Post by bergersau on 2008-04-30
The Alt+F2 key combination is the Linux equivalent of the run option in the Windows menu.

(Try using Alt+F2 then typing gedit and hitting enter to see it in use.)

You can open a Terminal window or 'xterm' by typing the name of the terminal you wish to run eg: Alt+F2 xterm   Then press enter.

Or you can open an xterm from the gnome or KDE menu.

Or you can use Ctrl+Alt+F1..F6 to open one or more 'virtual terminals'
Ctrl+Alt+F7 will return you to your graphical desktop. 

These are functionally the same as an xterm in most respects.

All of these options place you in a Command Line Interface (BASH by default).  
The most basic commands are:
ls - to list a directory contents
cd - to change to a new directory
pwd - print the name of the current directory
cp - to copy a file
rm - to delete a file
sudo - to gain administrator privileges for this command
man - to get a manual page

Bash essentially is the same on any distro.
There a many BASH tutorials out there so Google to your heart's content.

The other thing you'll want is to find a text editor you are comfortable with on the command line.
Have a look at nano, pico,or jed for simple choices, or if your feeling more adventurous you can try vi (or vim) or emacs. Then you can enter into the vi/emacs debate  that's been raging for decades.

A good text editor on the command line can be a real benefit under Linux as every configuration file is a text file. One day you may not have a graphical environment if you manage to break your x server settings somehow.

---

### Post by FerociaCoutoura on 2008-05-02
Thanks guys!  I'm understanding better.  But...how might I execute the following script in order to get my headphones to work?

#!/bin/sh

# This script will recompile the ALSA drivers for Ubuntu
# This procedure was gotten from
# [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
#
# Authored by Bob Nelson  [email]admin@stchman.com[/email]
#
# This script updated 9/6/2007


script_name="alsa_setup.sh"

# Script must run as root 
if [ $USER != "root" ]; then
	echo "You need to run this script as root."
	echo "Use 'sudo ./$script_name' then enter your password when prompted."
	exit 1
fi

# Install the required tools
sudo apt-get -y install build-essential ncurses-dev gettext

# Install your kernel headers
sudo apt-get -y install linux-headers-`uname -r`

# Change to users home folder
cd ~

# Get the files from [www.stchman.com](www.stchman.com)
wget [http://www.stchman.com/tools/alsa/alsa-driver-1.0.16.tar.bz2](http://www.stchman.com/tools/alsa/alsa-driver-1.0.16.tar.bz2)
wget [http://www.stchman.com/tools/alsa/alsa-lib-1.0.16.tar.bz2](http://www.stchman.com/tools/alsa/alsa-lib-1.0.16.tar.bz2)
wget [http://www.stchman.com/tools/alsa/alsa-utils-1.0.16.tar.bz2](http://www.stchman.com/tools/alsa/alsa-utils-1.0.16.tar.bz2)

# make a new folder 
sudo mkdir -p /usr/src/alsa

# Change to that folder
cd /usr/src/alsa

# Copy the downloaded files to the newly made folder
sudo cp ~/alsa* .

# Unpack the tar archive files
sudo tar xjf alsa-driver*
sudo tar xjf alsa-lib*
sudo tar xjf alsa-utils*

#Compile and install alsa-driver
cd alsa-driver*
sudo ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)
sudo make
sudo make install

# Compile and install alsa-lib
cd ../alsa-lib*
sudo ./configure
sudo make
sudo make install

# Compile and install alsa-utils
cd ../alsa-utils*
sudo ./configure
sudo make
sudo make install

# Remove the archives as they are no longer needed
rm -f ~/alsa-driver*
rm -f ~/alsa-lib*
rm -f ~/alsa-utils*

# Add the following line to the file, replacing '3stack' with your model
sudo echo -e '\n' >> /etc/modprobe.d/alsa-base
sudo echo "options snd-hda-intel model=3stack" >> /etc/modprobe.d/alsa-base

# Reboot the computer
sudo reboot

---

### Post by bergersau on 2008-05-02
You'll need to make the script executable first.

Open an xterm (See my previous post)

cd to the directory the script is in
(Note that Bash is case sensitive so for example: Fred.sh is different to fred.sh)

then
chmod +x alsa_setup.sh 

This will make the script executable. You may need to use sudo depending on the location and file ownership of the script.

Then you can execute it with

sudo ./alsa_setup.sh  

(I was just reading the script and it requires you to run with sudo )

Hope this helps.

---

