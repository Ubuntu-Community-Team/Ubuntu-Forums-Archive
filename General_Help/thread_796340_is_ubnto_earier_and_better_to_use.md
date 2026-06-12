---
title: "is ubnto earier and better to use"
date: 2008-05-16
forum: General Help
---

### Post by diablo1 on 2008-05-16
ive been using opensuse 10.3 for a month now and dont like the install and uninstall methods opensuse 10.3 uses..  i figured out how to install rpm's but tar.gz and tar.bz2 are too hard..

also when in first installed opensuse 10.3, I had to jump thru hoops to connect my wireless card netgear WG511t Atheros Communications, Inc. AR5212 pciid: 168c:0013  card.. first i had to update the kernel and kernel-source before i could install the madwifi drivers.. all had to be offline. thats a pain   

does ubunto use the same type of system or it easier to install and uninstall software in ubunto and does it have madwifi drivers already to install from first installation of the ubunto system??

any other suggestion on better linux systems?? closer  to a previous windows user
thanks

---

### Post by decoherence on 2008-05-16
You can use Ubuntu's live CD to determine whether your wireless drivers are detected.

Instead of RPMs, Ubuntu uses .DEBs. Instead of YUM or whatever it is this week, Ubuntu uses APT.

DEBs are generally acknowledged as being more rigorously documented and packaged than RPMs, allowing for better dependency handling.

APT is generally acknowledged to be so much better than YUM/Pirut/Update Manager/whatever that APT is becoming popular on RPM-based systems. (it still won't be as nice as debian or ubuntu though)

tar.gz files can be anything, but generally are source files. The methods for installing source files are often identical across distros. Software distributed as tar.gz should always be accompanied by an INSTALL or README file that contains further instruction.

Nothing to lose by booting the Live CD!

---

### Post by diablo1 on 2008-05-16
i downloaded Ubuntu 8.04 LTS Desktop Edition, its a live cd right?

so i can connect to the internet from a live distro or will my wireless just blink if it has drivers but not connect to the net??

as for tar.gz, i look at  the readme files and install file for the commands to use for the ./configure but haven't figured it out yet .  i cant find a good tutorial on the net about the ./configure . i mostly find  tutorials that just say  
tar xvf gzip-1.2.4.tar
cd gzip-1.2.4
./configure
 make
 su
 make install
nothing that explains in detail how to  or what needs to be added to the command  after the ./configure

thanks

---

### Post by housam on 2008-05-16
read this guide about installing in Ubuntu :[[COLOR="Red"]_http://monkeyblog.org/ubuntu/installing/_[/COLOR]]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by decoherence on 2008-05-16
"so i can connect to the internet from a live distro or will my wireless just blink if it has drivers but not connect to the net??"

I don't have a ton of experience with Atheros cards. If the LiveCD includes the drivers (madwifi?) it should Just Work. However, keep an eye open for pop-up messages about restricted drivers. It could be that Ubuntu will detect your card but won't have the driver in which case it will offer to download and install it for you. This of course requires a net connection, so hopefully you can do this over the wired link.

Just try the live CD, see what happens. If you can't get it working fairly easily, let us know or just try another distro. Linux Mint is based on Ubuntu and includes many extra drivers in the default install (i don't know specifically about your card, though.)

The link housam supplied has lots of good info and is definitely worth checking out. Here's a quick rundown for compiling software, which is what you're talking about when you say "make" and "configure" and all that. Just type each command in the terminal. When one finishes, type the next.

./configure -- a pre-compile script that checks out your system to determine whether the software can be compiled and if so, the best way to do it. Errors here are usually the result of missing dependencies (package y requires package x to work.) You'll have to satisfy that dependency before trying again (the purpose of APT and DEB is to spare us this 'dependency hell.') Once this is done you'll have a Makefile which is a set of instructions your compiler can use to successfully build the software.

make -- reads the Makefile and compiles the software according to its specifications. It can take a long time, depending on what you're compiling. When this is done, you'll have a binary program you can install.

sudo make install -- this is a more appropriate (for ubuntu) version of the "su; make install" command you mentioned. This part actually copies the binary to the appropriate places as determined by the Makefile.

You should now be able to run the software by typing its name. Worst case, you may need to log out or even reboot, but almost certainly not.

Note, to do all this you need a compiler and various parts of the GNU toolchain. Install Ubuntu's build-essential package to get what you need.

---

### Post by diablo1 on 2008-05-16
ok im connected with a live cd.  thanks

whats the command i can type in a terminal to see what madwifi drivers im using & the version..  how do i update it if im using an older version, where do i look?
what are some of the commands for ubunto, ive been using su to get into root for opensuse.. are they the same commands for ubunto as opensuse

thanks..

---

### Post by decoherence on 2008-05-19
to do stuff as root, start the command with sudo. for instance to find your madwifi kernel modules you can do

sudo find /lib/modules/`uname -r` -name madwifi

in this case ths sudo is actually unnecessary. also, from running that command myself, i see there are madwifi modules included with the kernel.

---

### Post by Cap'n Skyler on 2008-05-19
> **diablo1 said:**
> ok im connected with a live cd.  thanks

whats the command i can type in a terminal to see what madwifi drivers im using & the version..  how do i update it if im using an older version, where do i look?
what are some of the commands for ubunto, ive been using su to get into root for opensuse.. are they the same commands for ubunto as opensuse

thanks..
for my wireless i had synaptic add the ndiswrapper and i copied the INF file from the netgear cd.it comes with win 98, XP and millenium drivers.
my issue was getting something to open the exe file so i can copy the INF i needed.i ended up using win xp on my other comp and copy and write it to a cd then copied that over to my linux distro desktop.
Poof! it worked!
i also keep a 50 foot ethernet cable for big updates as my wireless signal is not super strong and it can be low for a big update.but otherwise is fine for a general purpose internet connection.:popcorn:

---

### Post by Cap'n Skyler on 2008-05-19
> **diablo1 said:**
> ive been using opensuse 10.3 for a month now and dont like the install and uninstall methods opensuse 10.3 uses..  i figured out how to install rpm's but tar.gz and tar.bz2 are too hard..

also when in first installed opensuse 10.3, I had to jump thru hoops to connect my wireless card netgear WG511t Atheros Communications, Inc. AR5212 pciid: 168c:0013  card.. first i had to update the kernel and kernel-source before i could install the madwifi drivers.. all had to be offline. thats a pain   

does ubunto use the same type of system or it easier to install and uninstall software in ubunto and does it have madwifi drivers already to install from first installation of the ubunto system??

any other suggestion on better linux systems?? closer  to a previous windows user
thanks

i also used an older SUSE 9.1  it was good,but i think Ubuntu is a lot better for the noob /less experienced user like me :)

---

