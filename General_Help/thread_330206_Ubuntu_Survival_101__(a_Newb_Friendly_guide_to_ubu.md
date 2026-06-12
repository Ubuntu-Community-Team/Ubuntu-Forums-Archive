---
title: "Ubuntu Survival 101  (a Newb Friendly guide to ubuntu)"
date: 2007-01-02
forum: General Help
---

### Post by fokuslee on 2007-01-02
Finally Updated : ) 

Welcome to the world of Ubuntu.  Don't be scared, linux is not that scary.  (I was dazzed when i first installed Ubuntu, But thanks to this forum and good pplz on IRC im doing ok and im starting to like ubuntu more and more)
This Guide will Attempt to give Brief introdution to Ubuntu OS and offer many useful links for those who are new to ubuntu. 

0. If you want to use and linux distro  you have to read read and read.  You also have to exercise your juicy brain, but i don't need to tell you this : )
1. Who is Ubuntu for.  Ubuntu has the BEST support community for any linux distro.   There are so many peoples on IRC and forum willing to help.  Ubuntu is powerful yet easy enough for Anyone.  
So in short Ubuntu is anyone who wants to get their feet wet with linux. (yet powerful enough for advanced users)  
2.  False Expectations:  Ubuntu is NOT Better then windows.  It is simply different.  it is more stable and vastly more customizable. But i think im safe to say that windows is a little more intuitive.  (IMOH windows make you lazy and you won't learn cool new things) 
3. Deciding the right cd.  For most peoples the ubuntu-6.10-Desktop-i386 is a good bet.  i386 is 32bit and features a graphic installation.  Note: amd64 is backward competible so you can use this version even if you have amd64. 
ubuntu-6.10-Desktop-amd64 is for ALL 64bit processors (a misconception is amd stands for AMD. not true) You must understand that if you chose to use 64bit ubuntu you can enjoy faster performance (encoding mainly) but you will have to do extra work to install 32bit firefox and java and flash and some few others.  ubuntu-6.10-Alternative-blah features a text based install but offer more option such as select Lilo instead of Grub as bootloader and give you freedom to choose which program to install.   Nonetheless with all of those install varieties you can always choose to uninstall programs you don't like with Synaptic (like add/remove in windows but better) later.
4 For people grew up on windows i recommend a dual boot.  This way you can get use to Ubuntu on your own pace and always have a familiar os to fall back on.  For a great dual boot instruction site with many walkthrough screenshots recommend this:  
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)  (if you really want to be comfortable with the installation process try to read the whole site)
5. After you finish your installation the first thing is to read the official Ubuntu guide.  This guide will briefly introduce linux answer many of your questions and make Ubuntu multimedia friendly
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html)  (Note This is a Must Read) 
6.  If you want to know more of a specific program to handle a specific task and more advanced configuration options try 
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)  (this is a wiki maintained by ubuntu users just like you!) 
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)  (this is the unofficial wiki, i personally like the layout and its succinctness better)
Number 6 is a Lengthy Reading so you can save it for latter, But DO IT  (The Benefits of Reading Number 6 are countless)  
7. For Now You want to run your system at optimal setup so you might want to install wireless cars and video driver.  
8. Wireless Cars are pretty troublesome with linux. But there are options available.  Easiest way is to install the Linux-Restricted-Module for your kernel make.  use command "uname -r" in terminal.  And install the Linux-Restricted-Modules via synaptic.  (You know how to do this because you read number 5)  If the first step does not solve your problem you have to try Ndiswrapper.  Ndiswrapper wraps around your windows drivers and make them work for linux  [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)  (ndiswrapper is not the easiest thing to install and configure, so to save you from getting frustrated with Ubuntu you might want to save it for later when your more comfortable with linux)
9 Ubuntu does come with support for your graphics card.  But it might not use the best driver for your card for compatibility reasons.  To enable 3d accelereation and all that good stuff install propreitary drivers. 
For ATI users use [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)  (i am not a ati user so if you have a better guide let me know and i will update link)  Alternatively you can use [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)  
For Nvidia users use [http://albertomilone.com/latest_nvidia_udsf_edgy.html](http://albertomilone.com/latest_nvidia_udsf_edgy.html)   This is a guide written by our talented tseliot forum mod  It features several methods including compiling from source.  Alternatively you can use [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia)  Note installing latest nvidia-glx driver will enable you to SLI and monitor both gpu's temp.  To remove the annoying Nvidia Logo on start up follow this guide: [http://gentoo-wiki.com/HOWTO_nVidia_Drivers#Removing_the_nVidia_Splash_Screen](http://gentoo-wiki.com/HOWTO_nVidia_Drivers#Removing_the_nVidia_Splash_Screen)
10.  Now We can do some basic visual customization.  Follow my guide at [http://www.ubuntuforums.org/showthread.php?t=330201](http://www.ubuntuforums.org/showthread.php?t=330201)
11.  Time for the Crazy NICE visual effects that is the world of LINUX.  Your options are Compiz or Beryl.  It is recommended to follow the official install methods for both instead of the ones posted on forum.  Since the official guide is 100% accurate and feature easy to read layout.  
Compiz [http://www.go-compiz.org/index.php?title=Ubuntu_Installation_Guide](http://www.go-compiz.org/index.php?title=Ubuntu_Installation_Guide)
Beryl  [http://www.beryl-project.org/](http://www.beryl-project.org/)
12. (optional) Compile your custom kernel for extra performance boost ( perhaps with a patch)  follow this guide here [http://doc.gwos.org/index.php/Kernel_Compilation_Dapper](http://doc.gwos.org/index.php/Kernel_Compilation_Dapper)   
13.Now to tidy things up.  In terminal run sudo apt-get dist-upgrade.  (Fix any broken packages)  then run sudo apt-get clean (cleans apt-get cache) 
14. Defrag the linux file system.  YES THE LINUX FILE SYSTEM CAN BECOME FRAGMENTED.  But no where as bad as windows.  Check out [http://www.ubuntuforums.org/showthread.php?t=169551&highlight=defrag](http://www.ubuntuforums.org/showthread.php?t=169551&highlight=defrag)
you can install the pacakge by clicking on deb.  Or if you have 64bit compile .  In terminal cd to the directory where you extracted the tar.gz.  run sudo make install.  the defrag tool will be installed in /usr/sbin  
15 To back up your LInux OS 
backing up MBR (grub 1st stage)  [http://users.bigpond.net.au/hermanzone/p13.htm#cp](http://users.bigpond.net.au/hermanzone/p13.htm#cp)
backing up ALL OF THE UBUNTU OS, i mean ALL  [http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)
16.  Read more linux good stuff. (leisure readin)
[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)
[http://linuxcommand.org/index.php](http://linuxcommand.org/index.php)
17 Look under this post for all the cool replies with cool links and be sure to share yours.  Thank you all! 


phew this took me a while i still need to address samba and mnt ntfs and maybe ntfs write support but those can be seen in number 6 so for now hehe.
Shout outs to all the user of Ubuntu.  Many thanks to  all the nice pplz on forum and IRC who helped me survive my first encounter with Ubuntu.  and remeber DO Ubuntu.  
PS yeah aptitude is better takes care of all the dependencies automatically rite? So if you want substitute where i have apt-get with aptitude.
PSS This guide is far from perfect and all encompassing.  All inputs are welcome.   : )  


Appendix.1 A list of common linux commands and brief discription so you can understand other guides on forum easier.  But when in doubt use  google.
ls /boot/vmlinuz*  #list all the different kernel versions on comp
locate  #command will search your computer for any filename you specify. It uses an index of the files on your system to work quickly: to update this index run the command updatedb. This command is run automatically each day, if you leave your computer on. 
nano -w  #nano with line wrapping off good for editing scritps
man #open manual pagees ##man -k foo will search the man files for foo. man -f foo searches only the titles of your system's man files for foo. 
startx -- :1  #Start a new X server on display :1  note :0 display is the initial display already used when starting ubuntu.  
#home directory can also be referred to by the '~' (tilde) character. So 
~  #tilda is home directory.
/home/yourname/work is the same as ~/work (when logged in as root does not work with sudo).
./  #dot forward-slash is current directory.  
pwd  #The pwd command will allow you to know in which directory you're located (pwd stands for "print working directory")
mv  #The mv command will move a file to a different location or will rename a file. ie: "mv file foo" will rename the file "file" to "foo". "mv foo ~/Desktop" will move the file "foo" to your Desktop directory but will not rename it.
df -h  #The df command displays free filesystem disk space usage for all partitions, in MB or GB.
free -m #The free command displays the amount of free and used memory in the system -m specify it in megabytes.
top  #The top command displays information on your Linux system, running processes and system resources, including CPU, RAM & swap usage and total number of tasks being run. To exit top, press "q".
uname -a  #The uname command with the -a option prints all system information, including machine name, kernel name & version, and a few other details. 
lsb_release -a  #The lsb_release command with the -a option prints version information for the Linux release you're running.
ifconfig reports on your system's network interfaces. 
grep  #allows you to find a string in a file or stream. usage: grep 'STRING' filename(or directory) It can be used with Regular expression to be more flexible at finding strings.
Regular expression
^ Denotes the beginning of a line
$ Denotes the end of a line
. Matches any one characters
* Matches 0 or more of the previous characters
.*Matches any number or type of characters
[] Matches on character for the one listed in the the Square brackets
[^]Does not match any characters listed
\<, >/ Denotes the beginning and end (respectively) of a word 
find <path> <operators>  #The path is where find will start its search. Find is a recursive command. This means that it will descend into each directory that it runs into while searching.  ##ie: find ./ -name test.txt search for a file with the name test.txt under the current directory. 
adduser newuser  #create a new general user called "newuser" on your system.
passwd newuser  #assign password to user named "newuser".
apt-get  #command-line package management.  For usage see [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/apt.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/apt.html)
 
apt-get clear  #clear the apt-get download cache @ /var/cache/apt/archives.
apt-get autoremove  #automatically remove unneeded packages. 
bash  #switch to the bash shell
ln -s  #(without -s create a hard link)create a symbolic link; work like hard links, but more functional. If you want to create a link to a directory (as opposed to a file), you must create a symlink. Symlinks are also required when linking to a file on a different disk partition or on a network.

Appendix. 2  How to Install Anything in Ubuntu  ( i just copy and paste b/c the website is down) 
[http://www.ubuntuforums.org/showthread.php?p=1960394#post1960394](http://www.ubuntuforums.org/showthread.php?p=1960394#post1960394)

---

### Post by maxamillion on 2007-01-02
[www.ubuntuguide.org](www.ubuntuguide.org) <-- link I think all new comers should be aware of, but let me please encourage the use of aptitude in place of apt-get.

---

### Post by neoflight on 2007-01-07
than you..looks like very useful info...
it would be better if you could arrange those info in a more readable mannerby using tags such as 

> this
and 
```
this
```
and
[HTML]this[/HTML]
and 
[PHP]this[/PHP]

also use paragraphs to logically group various points...
good work...:)

---

### Post by gg234 on 2007-01-08
i would suggest [this]("http://www.ubuntugeek.com") and each and every article is nicely written with screenshots so any new users can easily understand everything

---

### Post by sn0m on 2007-01-13
cool, thanks

---

### Post by haxer on 2007-01-13
This should be sticky real nice guide ;) :D

---

### Post by cfgtech on 2007-03-29
Thanx dude, will bookmark

---

