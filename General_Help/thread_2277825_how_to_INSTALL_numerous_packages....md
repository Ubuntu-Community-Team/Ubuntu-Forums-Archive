---
title: "how to INSTALL numerous packages..."
date: 2015-05-11
forum: General Help
---

### Post by brian52 on 2015-05-11
Hi,

I want to install lot of packages, but I am really tired of writing one by one, I just spend the whole day doing it.. and looking to reformat the computer !

```
sudo apt-get install apache2-mpm-worker
sudo apt-get install apache2
sudo apt-get install apache2.2-common
sudo apt-get install apache2-suexec
sudo apt-get install apache2-utils
sudo apt-get install awstats
sudo apt-get install bash
sudo apt-get install bind9
sudo apt-get install bzip2
sudo apt-get install chkrootkit
sudo apt-get install courier-authdaemon
sudo apt-get install courier-base
sudo apt-get install courier-imap
sudo apt-get install courier-maildrop
sudo apt-get install courier-pop
sudo apt-get install diffutils
sudo apt-get install dnsutils
sudo apt-get install gcc
sudo apt-get install gzip
sudo apt-get install iptables
sudo apt-get install ispell
sudo apt-get install libapache2-mod-fastcgi
sudo apt-get install libapache2-mod-fcgid
sudo apt-get install libberkeleydb-perl
sudo apt-get install libc6-dev
sudo apt-get install libcrypt-blowfish-perl
sudo apt-get install libcrypt-cbc-perl
sudo apt-get install libcrypt-passwdmd5-perl
sudo apt-get install libdate-calc-perl
sudo apt-get install libdate-manip-perl
sudo apt-get install libdatetime-perl
sudo apt-get install libdatetime-timezone-perl
sudo apt-get install libdigest-md5-perl
sudo apt-get install libdbd-mysql-perl
sudo apt-get install libdbi-perl
sudo apt-get install libfile-copy-recursive-perl
sudo apt-get install libfile-mimeinfo-perl
sudo apt-get install libio-stringy-perl
sudo apt-get install libmail-sendmail-perl
sudo apt-get install libmailtools-perl
sudo apt-get install libhtml-parser-perl
sudo apt-get install libmcrypt4
sudo apt-get install libmime-perl
sudo apt-get install libnet-dns-perl
sudo apt-get install libnet-libidn-perl
sudo apt-get install libnet-netmask-perl
sudo apt-get install libnet-smtp-server-perl
sudo apt-get install libperl5.10
sudo apt-get install libsasl2-2
sudo apt-get install libsasl2-modules
sudo apt-get install libsnmp-session-perl
sudo apt-get install libterm-readkey-perl
sudo apt-get install libterm-readpassword-perl
sudo apt-get install libtimedate-perl
sudo apt-get install libmysqlclient16
sudo apt-get install locales
sudo apt-get install lsb-base
sudo apt-get install lynx
sudo apt-get install lzma
sudo apt-get install make
sudo apt-get install mysql-client
sudo apt-get install mysql-common
sudo apt-get install mysql-server
sudo apt-get install original-awk
sudo apt-get install patch
sudo apt-get install perl
sudo apt-get install perl-base
sudo apt-get install perl-modules
sudo apt-get install php-pear
sudo apt-get install php5
sudo apt-get install php5-adodb
sudo apt-get install php5-cgi
sudo apt-get install php5-cli
sudo apt-get install php5-common
sudo apt-get install php5-gd
sudo apt-get install php5-mcrypt
sudo apt-get install php5-mysql
sudo apt-get install policyd-weight
sudo apt-get install postfix
sudo apt-get install postgrey
sudo apt-get install procmail
sudo apt-get install proftpd-basic
sudo apt-get install proftpd-mod-mysql
sudo apt-get install rkhunter
sudo apt-get install sasl2-bin
sudo apt-get install ssh
sudo apt-get install tar
sudo apt-get install wget
```

Is there a way to make it doing automatically without me having to type one line by line ...

I am a newbie in ubuntu, as you can see, so please detail me the intructions instead of telling me what to do because I don't know how.... Especially the Syntax...

Isn't there a way like to put all those packages into a document and run through it?

Thanks

---

### Post by cariboo on 2015-05-11
you could all the packages in one command:

```
sudo apt-get install package1 package2 package3
```

You seem to be trying to install the dependencies that should be installed when a package is installed.

Use:

```
apt-cache showpkg apache2
```

will show you the depends, as well as reverse depends. the part of the output you are interested in is at the bottom od the output:

```
Dependencies: 
2.4.10-9ubuntu1 - lsb-base (0 (null)) procps (0 (null)) perl (0 (null)) mime-support (0 (null)) apache2-bin (5 2.4.10-9ubuntu1) apache2-utils (2 2.4) apache2-data (5 2.4.10-9ubuntu1) dpkg (2 1.17.14) www-browser (0 (null)) apache2-doc (0 (null)) apache2-suexec-pristine (16 (null)) apache2-suexec-custom (0 (null)) ufw (0 (null)) ssl-cert (0 (null)) apache2.2-common (3 2.3~) apache2.2-common:i386 (3 2.3~) apache2.2-common (0 (null)) apache2.2-common:i386 (0 (null)) apache2:i386 (0 (null)) 
Provides: 
2.4.10-9ubuntu1 - httpd-cgi httpd 
```

---

### Post by Portaro on 2015-05-11
I think that can use the dpkg --get-selections '*' >your.text ; to save as text and then install with 
dpkg --set-selections <your.text

---

### Post by brian52 on 2015-05-11
Here is the thing, i want to install ispcp, but in instructions:

> 3. Install the required modules   First update your system:
	# sudo aptitude update && aptitude upgrade
	# sudo aptitude install lsb-release
	# sudo aptitude install $(cat ./docs/Ubuntu/ubuntu-packages-`lsb_release -cs`)


   Make sure you have added multiverse into your /etc/apt/sources.list

Then we have the packages in my post #1.

thing is i copied paste exactly those lines of commands but doesnt work.. I dont even understand what multiverse stands for, i believe in the softwares sources , there is already a checked box for something multiverse...

----------------------

commands didnt work.. I tried [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install package1 package2 package3 and also [/FONT][/COLOR][COLOR=#000000]dpkg --set-selections <your.text[/COLOR]

---

### Post by wildmanne39 on 2015-05-11
When you ran:
```
 sudo apt-get install package1 package2 package3
```
did you change the package1, package2 and package3 to the actual names of the packages that you want to install?
Thanks

---

### Post by cariboo on 2015-05-11
For one thing ispcp isn't available in the repositories. Looking at the source file on Sourceforge, you have to compile the program in order to use it. This may beyond a beginners abilities.

I'd suggest you install Webmin, easy to understand instructions here:

[http://www.unixmen.com/install-webmin-ubuntu-14-04/](http://www.unixmen.com/install-webmin-ubuntu-14-04/)

or you could do a compleete install of Zentyal Server:

[http://www.zentyal.org/](http://www.zentyal.org/)

---

### Post by brian52 on 2015-05-11
> **Wild Man said:**
> When you ran:
```
 sudo apt-get install package1 package2 package3
```
did you change the package1, package2 and package3 to the actual names of the packages that you want to install?
Thanks

yep. I tried it before even posting here, but I was impressed with so much great help I got.

Here is the result:

> sudo apt-get install apache2-mpm-worker apache2 apache2.2-common apache2-suexec apache2-utils awstats bash bind9 bzip2 chkrootkit courier-authdaemon courier-base courier-imap courier-maildrop courier-pop diffutils dnsutils gcc gzip iptables ispell libapache2-mod-fastcgi libapache2-mod-fcgid libberkeleydb-perl libc6-dev libcrypt-blowfish-perl libcrypt-cbc-perl libcrypt-passwdmd5-perl libdate-calc-perl libdate-manip-perl libdatetime-perl libdatetime-timezone-perl libdigest-md5-perl libdbd-mysql-perl libdbi-perl libfile-copy-recursive-perl libfile-mimeinfo-perl libio-stringy-perl libmail-sendmail-perl libmailtools-perl libhtml-parser-perl libmcrypt4 libmime-perl libnet-dns-perl libnet-libidn-perl libnet-netmask-perl libnet-smtp-server-perl libperl5.10 libsasl2-2 libsasl2-modules libsnmp-session-perl libterm-readkey-perl libterm-readpassword-perl libtimedate-perl libmysqlclient16 locales lsb-base lynx lzma make mysql-client mysql-common mysql-server original-awk patch perl perl-base perl-modules php-pear php5 php5-adodb php5-cgi php5-cli php5-common php5-gd php5-mcrypt php5-mysql policyd-weight postfix postgrey procmail proftpd-basic proftpd-mod-mysql rkhunter sasl2-bin ssh tar wgetReading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'perl' instead of 'libdigest-md5-perl'
Note, selecting 'libmime-tools-perl' instead of 'libmime-perl'
Package apache2.2-common is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However, the following packages replace it:
  apache2-bin:i386 apache2:i386 apache2-data apache2-bin apache2


E: Package 'apache2.2-common' has no installation candidate
E: Unable to locate package libperl5.10
E: Couldn't find any package by regex 'libperl5.10'
E: Unable to locate package libmysqlclient16

I am not sure why it's not working, any syntax problem?

---

### Post by brian52 on 2015-05-11
> **brian52 said:**
> yep. I tried it before even posting here, but I was impressed with so much great help I got.

Here is the result:



I am not sure why it's not working, any syntax problem?

anyways i remove those packages with errors and i think it now works..

however, installation fail. oh well

---

### Post by CantankRus on 2015-05-12
You may want to back up a bit and explain exactly what your trying to achieve 
so someone can point you in the right direction.

---

### Post by brian52 on 2015-05-12
> **CantankRus said:**
> You may want to back up a bit and explain exactly what your trying to achieve 
so someone can point you in the right direction.

you're right.

I am trying to install ispcp, and now it looks like it can be successfully installed. However, I am unable to access any of it, especially the most important: the index.php of ispcp..

I am sure something is wrong.

Here is the situation.

My vps provider will let me choose: use ubuntu 10 (very old) with nothing compatible anymore or install ubuntu 14 for me, without any software installed.

The old ubuntu 10 had those programs preinstalled:

[COLOR=#000000][FONT=Verdana]- NX 4.5[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]- ISPCP/phpmyadmin/View bandwith user --> for webhosting[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]- gFTP[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]- Subsonic Media Streammer[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]- torrent[/FONT][/COLOR]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#000000]- PBX (I wonder if incredible PBX - asterisk works)[/COLOR][/SIZE][/FONT]

[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#000000]So once he will reformat to ubuntu 14, I will have to install all these programs myself. My linux is beyond terrible, yet I already begged him to install NX for me, because he told me only ssh could be used...[/COLOR][/SIZE][/FONT]

[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#000000]Anyhow, I decide to install ubuntu 14 in one of my spare computer, and try to replicate those ubuntu 10 preinstalled programs. So far, I was able to install everything but ISPCP and Subsonic media and PBX.[/COLOR][/SIZE][/FONT]

[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#000000]Well I already give up on pbx. Subsonic looks cool, but never used it, so not too important while ispcp is useful for me to create several website under this VPS/static ip.[/COLOR][/SIZE][/FONT]

===============================

When trying to install ispcp, it asked me those questions that I do not know how to answer (because I am installing ispcp into a local computer without any domain.... IP address of the computer is 192.168.1.111 through a router..) :

> SERVER_HOSTNAME = 192.168.1.111.zazeen   (MUST BE A FULLY QUALIFIED HOSTNAME)

BASE_SERVER_IP = 192.168.1.111


BASE_SERVER_VHOST = admin.zazeen


BASE_SERVER_VHOST_PREFIX = http://

At the end of installation: it says success, please access to ispcp control panel at [http://admin.zazeen](http://admin.zazeen)

Obviously, [http://admin.zazeen](http://admin.zazeen) gives me page can not be reached (no such thing!)

So I have no idea what is a fully qualified hostname... and what to put in** IP **(computer IP?? or external IP?? I have lot of computers under the same external ip ie router)

**BASE_SERVER_VHOST** should be the domain name where ispcp omega should run on.

I guess I just have no idea what to put as IP or BASE_SERVER_VHOST when it's for a local setup...  I tried 192.168.1.111, localhost , 127.0.0.1... doesn't work. It also looks like the BASE_SERVER_VHOST doesn't allow me to enter any IP address ....

---

### Post by mastablasta on 2015-05-12
have you tried reaching it on 192.168.1.111 ? if not check what port it listent to and then [http://192.168.1.111:port](http://192.168.1.111:port)

also as others mentioned you might find it easier to install something like Webmin, Zentyal or Ajenti. 

LS PCP had last update in 2012. I hope it is well maintained.

as others said there are metapackages available (for example for PHP, apache...). if you installed ubuntu server it would ask you what kind of server you want and oyu can already install packages there, another option is to use tasksell which is for installing only. it has meta packages like LAMP server and similar.

SSH is not an issue if you install a nice webGUI to server.

make sure you protect it properly. the attacked mine within hours of opening the port.

---

### Post by brian52 on 2015-05-12
> **mastablasta said:**
> have you tried reaching it on 192.168.1.111 ? if not check what port it listent to and then [http://192.168.1.111:port](http://192.168.1.111:port)

also as others mentioned you might find it easier to install something like Webmin, Zentyal or Ajenti. 

LS PCP had last update in 2012. I hope it is well maintained.

as others said there are metapackages available (for example for PHP, apache...). if you installed ubuntu server it would ask you what kind of server you want and oyu can already install packages there, another option is to use tasksell which is for installing only. it has meta packages like LAMP server and similar.

SSH is not an issue if you install a nice webGUI to server.

make sure you protect it properly. the attacked mine within hours of opening the port.

not sure how to secure anything lol

so ubuntu has been installed.

However, the screen looks very hard to read especially in the system terminal for example, i tried different sreen display but doesn't work.

Here is a pic, I can barely read what it says in the terminal, it's choppy, but it's also like this in real life. Any idea how I can make it more clear to read?

[IMG]http://i60.tinypic.com/11v73hl.jpg[/IMG]

---

### Post by Keith_Helms on 2015-05-13
I don't know if it will help, but I have multiple systems running Ubuntu and I get tired of installing a bunch of packages every time I install a new release on one of them.   I wrote a little script to read a text file containing a list of package names and install them.

```
#!/bin/bash

install_package () {
    apt-get -myq install $package || true
}

if [ $# -ne 1 ]
then
    echo "Usage: install_packages.sh package_list_file"
    exit
fi

if [ ! -e "$1" ]
then
  echo "$1 package list file not found"
  exit
fi

IFS=$'\n' 
read -d '' -r -a lines < "$1"

limit=${#lines[@]}
echo "Starting install of $limit packages"
for ((i=0;i<$limit;i++))
do
    package=${lines[$i]}
    echo "installing package $package"
    install_package
done
```

I run the script with sudo and pass it the name of the text file, an excerpt from which is:

```
abcde
aisleriot
argyll
audacious
build-essential
chromium-browser
cvs
default-jdk
dosbox
eclipse
exiftool
eyed3
flac
flashplugin-installer
gedit
geeqie
gnome-games
...

```

This may not be the best or optimal way to setup a system, but it allows me to keep multiple canned lists of packages for various target systems - Xubuntu laptop, Xubuntu desktop, Ubuntu laptop, Xubuntu desktop running MythTV, etc.

---

### Post by brian52 on 2015-05-13
> **Keith_Helms said:**
> I don't know if it will help, but I have multiple systems running Ubuntu and I get tired of installing a bunch of packages every time I install a new release on one of them.   I wrote a little script to read a text file containing a list of package names and install them.

```
#!/bin/bash

install_package () {
    apt-get -myq install $package || true
}

if [ $# -ne 1 ]
then
    echo "Usage: install_packages.sh package_list_file"
    exit
fi

if [ ! -e "$1" ]
then
  echo "$1 package list file not found"
  exit
fi

IFS=$'\n' 
read -d '' -r -a lines < "$1"

limit=${#lines[@]}
echo "Starting install of $limit packages"
for ((i=0;i<$limit;i++))
do
    package=${lines[$i]}
    echo "installing package $package"
    install_package
done
```

I run the script with sudo and pass it the name of the text file, an excerpt from which is:

```
abcde
aisleriot
argyll
audacious
build-essential
chromium-browser
cvs
default-jdk
dosbox
eclipse
exiftool
eyed3
flac
flashplugin-installer
gedit
geeqie
gnome-games
...

```

This may not be the best or optimal way to setup a system, but it allows me to keep multiple canned lists of packages for various target systems - Xubuntu laptop, Xubuntu desktop, Ubuntu laptop, Xubuntu desktop running MythTV, etc.

cool , how do you run a script in ubuntu?

---

### Post by Keith_Helms on 2015-05-13
Your previous posts show that you have been running "apt-get install" commands, so you are apparently familiar with using the terminal window and running commands.  The terminal window actually is running a program called a shell, which in Ubuntu defaults to a program named "bash".  A shell script consists of instructions that bash recognizes that have been saved in a text file.  That script is usually named something descriptive and given a suffix of .sh so that you can recognize it when you see it again.  On my system, the script I listed above is stored under the name **install_packages.sh**, but you could call it what you want.  Once you paste the code into a text editor and save the file, you will need to mark it as executable with the following command:

```
chmod +x *scriptname*.sh
```

The script also needs to be somewhere that the command prompt in the terminal window can find it.  There are 3 ways (that I can think of <g>) to do that.

1. The script can be in a directory that has been added to what is known as the PATH variable.  If you either have, or create a subdirectory under your home directory named bin, then whatever you put in that directory should be found with the PATH variable and you can just type the name of the script to run it - **myscript.sh** for example.
NOTE: If that bin directory did not exist and you create it, you might need to logout and back in in order for it to be found by the system.  If you want to see where PATH is looking for stuff, type **echo $PATH** at the command prompt and hit enter.
2. You can explicitly type the full path to the script, such as **/home/myuserid/myscript.sh** or **/home/myuserid/bin/myscript.sh** depending on where you stored it.
3. You can cd into the directory containing the script and then run it by putting a dot and a slash in front of the script name, such as **./myscript.sh**.

---

### Post by mastablasta on 2015-05-13
> **brian52 said:**
> 
However, the screen looks very hard to read especially in the system terminal for example, i tried different sreen display but doesn't work.

Here is a pic, I can barely read what it says in the terminal, it's choppy, but it's also like this in real life. Any idea how I can make it more clear to read?



this is a different issue. post into another thread in appropriate forum. make sure you leave some PC specs. 

and read this before you do it: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

Ubuntu hardening guide.: [http://hardenubuntu.com/](http://hardenubuntu.com/)

---

### Post by brian52 on 2015-05-14
So here is the source of problem of not loading...

> * Reloading web server apache2                                                                                                                                                                               *  * The apache2 configtest failed. Not doing anything.
Output of config test was:
AH00526: Syntax error on line 55 of /etc/apache2/sites-enabled/00_master.conf:
Either all Options must start with + or -, or no Option may.
Action 'configtest' failed.


In 00_master.conf line 55 in bold

>     <Directory /var/www/ispcp/gui>[B] 
       Options -Indexes Includes FollowSymLinks MultiViews[/B]
        AllowOverride None
        Order allow,deny
        Allow from all

I don't understand, what is wrong and how to fix?

---

### Post by Keith_Helms on 2015-05-14
Without knowing anything about that particular config file, I read the messages as saying you should put a + in front of each of Includes FollowSymLinks MultiViews and see what happens. :KS   I read it as saying either all options should be preceded by a + or a - or none of them should have either.

---

### Post by brian52 on 2015-05-14
> **Keith_Helms said:**
> Without knowing anything about that particular config file, I read the messages as saying you should put a + in front of each of Includes FollowSymLinks MultiViews and see what happens. :KS   I read it as saying either all options should be preceded by a + or a - or none of them should have either.

You're right!!

Do you know what those terms stand for and what does + do and - do?

---

### Post by brian52 on 2015-05-14
I did some researches...

And found this which explains my previous question: [http://httpd.apache.org/docs/2.2/mod/core.html#options](http://httpd.apache.org/docs/2.2/mod/core.html#options)

But I don't understand a thing!!!

Can someone tells me in some newbie language? Is it important or not? I am am looking for ispcp to get some webhosting, ftp. (does apache has anything to do with FTP?)

---

