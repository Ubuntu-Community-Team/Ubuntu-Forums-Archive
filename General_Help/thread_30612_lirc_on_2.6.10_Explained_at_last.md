---
title: "lirc on 2.6.10 Explained at last"
date: 2005-04-29
forum: General Help
---

### Post by CompEngr on 2005-04-29
I have been struggling to install lirc for some time now.  I just recently got further than ever before and thought I'd share my comments with everyone else so that I can get heckled for my spelling and possibly get some support to finish the job I've started.  (Incidently if anyone gets a serial transmitter working alongside of a TV card, please post the configuration and steps you took!)

Most of the howto's on these forums have been to use the lirc-modules-source. However I haven't been able to coax out a module with the '.ko' extension that I so desperately needed so I downloaded the tarball from lirc and compiled it, but I get ahead of myself.

1.  Download the kernel source:
      $uname -r
        2.6.10-5-386
       (Use your own kernel version here)
      $sudo apt-get source kernel-source-2.6.10
        (This places kernel-source-2.6.10.tar.bz2 in /usr/src.)

2.  Download the gcc compiler:
      $sudo apt-get install build-essential

3.  Change to the directory /usr/src:
      $cd /usr/src

4.  Uncompress the kernel source:
      $sudo tar xvjf linux-source-2.6.10.tar.bz2

5.  Make a link called linux from the new source directory:
      $sudo ln -s /usr/src/linux-source-2.6.10 /usr/src/linux

6.  We need the source directory to contain certain files (version.h, configuration files) for lirc to compile so:
      $cd linux
      $sudo make oldconfig      --This should make the config file
      $sudo make menuconfig     --This I think does the same thing, but it is here just in case it does more
      $sudo make include/linux/version.h   --This creates the version.h file
      $sudo make modules        --This I think creates /usr/src/linux/include/asm/param.h
WARNING:  I may have missed a command here.  You will know when you run make on lirc and it fails.  If it does I'll try to help you fix it...

Now we need the lirc package, I used lirc-0.7.1pre4.tar.bz2.  It might be a better idea to get the non-"pre" version, but to each his own.
7.  Download lirc:
      $cd /usr/src
      $sudo wget [http://lirc.sourceforge.net/software/snapshots/lirc-0.7.1pre4.tar.bz2](http://lirc.sourceforge.net/software/snapshots/lirc-0.7.1pre4.tar.bz2)

8.  Uncompress lirc
      $sudo tar xvjf lirc-0.7.1pre4.tar.bz2

Now you should have a directory called lirc-0.7.1pre4.

9.  Now the magic step to make this all work.  It was given by Martin Lohmeier in the newsgroups. (Abra Kadabra...)
      $sudo touch /usr/src/linux/Rules.make 
      (I would have paid soooo much if someone could have told me this 2 weeks ago.  Man!)
      This creates a file that allows lirc to understand that you do indeed have a woking source directory.

10.  Now go to the lirc directory:
      $cd lirc-0.7.1pre4

11.  Run the setup:
      $./setup.sh

11a. I choose to compile the Haupauge TV card because I have a PVR250.  You choose your own poison.
11b. Select Option 3 "Save configuration & run configure"
     If you have problems here, it can be caused by the kernel source directory. (Solutions vary.)
If this works, HOORAY!  Take note of the module it mentions it is going to compile and install.  It usually looks like "lirc_serial" or "lirc_i2c", you get the idea.  You'll need this info for later when try to load the module.  Onward...

12.  Make lirc:
       $make

13.  If it made without errors:
       $sudo make install

This actually installs in the right directory which for me was /lib/modules/2.6.10-3-386/misc/ rather than creating a directory 2.6.10 and putting them there.

14.  Allright, my knowledge begins to break down here... But here are somethings to try...
        -Think before doing this next line
         $sudo apt-get install lirc lirc-x
        -In theory, it adds all of the necessary configuration files namely /etc/modutils/lirc, I am not convinced this is needed,  do not do this step, and come back to it if needed.  "make install" may have already done everything, not sure at this point.

15.  Update the modules file, dependency file, and try to modprobe them in...
        $sudo update-modules
        $sudo depmod -ae
        $sudo modprobe lirc_i2c  (Substitute the module you made above here instead of lirc_i2c)

With any luck, it worked!

16.  I checked the make install text and noticed that it installed an appropriate remote control file for me (/etc/lircd.conf) with Hauppaug codes in it. (Now that's service!!!!) So next, start the daemon and the lirc test program:
         $lircd
         $irw

You should now be looking at a blank line... Point your remote at your sensor and push a button... (Praying at this point is not unheard of)  If everything worked right, you should see something like this:
         00000000000017e1 00 Ch- hauppauge_pvr
         00000000000017e1 01 Ch- hauppauge_pvr

VICTORY!!!!!!

Now I need to determine my configuration files necessary to load the lirc_serial, disable the current serial port (something like setserial /dev/uart0 off), making sure this setup survives a reboot, and get my Dish network codes in the lircd.conf file.  Something I'll add later maybe.

Please add your experiences.

Best of luck!

---

### Post by dilmah on 2005-05-02
An excellent thread!

After many hours of trying to get this happening under ubuntu I finally managed to do it with the help of this guide. :grin:

For the record, I have the following:
Ubuntu Hoary 5.10 x86 (with current patches & followed the ubuntuguide.org guide)
Leadtek Winfast TV2000/XP
Onboard NVidia NForce 3 250 Sound Card

I had this same hardware working in Gentoo before, so I knew it wasn't a hardware/linux issue. I had tried compiling lirc from source and so on under Ubuntu in an attempt to get this to work, but had the dreaded module problem (.o instead of .ko), compile errors, etc.

Anyway, I followed this guide to the letter all the way and finally got it working.
A few notes:
#9 aahhh... so that's what I was missing?!  ](*,) 
#16 Before running this I had to:

```
sudo chmod go+w /dev/lirc
``` and instead of running lircd (or maybe that should be "sudo lircd"), I started the lirc daemon by doing:
```
sudo /etc/init.d/lirc start
```

After I was happy it was working, I customised the .lircrc file for my remote control (from the lirc source) and added irexec to my startup programs (System -> Preferences -> Sessions -> Startup Programs) & rebooted to make sure it survived.

Whohoo! Now I can control the Radio, XMMS, MPlayer, Xine and tvtime all with the touch of a few buttons.
If anyone wants my (pretty heavily customised) .lircrc config file I can post it somewhere.

Thanks again!   :razz:

EDIT: I needed to change that entry in startup programs to 'irexec -d' to start it in daemon mode otherwise it didn't work properly

---

### Post by danbee on 2005-05-02
Am I just going mad?

```
# apt-get source kernel-source-2.6.10
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for kernel-source-2.6.10
```

I'm trying to do it with the kernel-headers, as it appears I can get hold of those...

---

### Post by danbee on 2005-05-02
Ok, it all worked for me using the kernel-headers instead.

For those having problems getting hold of the kernel-sources, substitute kernel-headers instead :)

---

### Post by kidcharles on 2005-05-08
I can confirm that this worked for me for my Hauppauge PVR-350 on Debian Sarge (2.6.8 kernel).  Thanks for this guide!

EDIT:  I get the proper response when running irw, but I don't have irxeventd which I think needs to be running so I can get MythTV to respond to the remote.

---

### Post by dilmah on 2005-05-08
If you can't find irxevent or get it working, you can also try using something like irexec and set up the .lircrc and .mythtv/lircrc files appropriately. There are many examples on the web which you can modify, and yours is a pretty popular card so you shouldn't have too many problems in that respect.

---

### Post by kidcharles on 2005-05-08
I figured out that the command was 'irxevent &' and not 'irxeventd &'.  I saw a reference to the latter somewhere, though it doesn't exist, and it got me off track.  Now I'm trying to get the whole thing to start up automatically at boot, though at least I know everything is working.

---

### Post by Rumo on 2005-06-05
I have the same problem I had before (I posted it somewhere in this forum):

After I ran "make install" and "apt-get install lirc" everything worked fine. But after a reboot I got this message by irw: "connect: Connection refused". The modules are still there and load properly (as far as I can see). I also set the rights of /dev/lirc* to 777 ("chmod 777 /dev/lirc*").

I have absolutely no idea what went wrong. The funny thing is, that I can make the remote work by typing: '/usr/src/lirc-whatever/make install && modprobe lirc_i2c && /etc/init.d/lirc start', But I have to run this after each reboot!

---

### Post by dilmah on 2005-06-05
You shouldn't have to "make install" after every reboot. What may be the problem though is that the lirc_i2c module isn't getting loaded automatically at boot for some reason. Try adding lirc_i2c to the /etc/modules file and reboot to see if it works.

---

### Post by Rumo on 2005-06-06
[QUOTE=dilmah]You shouldn't have to "make install" after every reboot. What may be the problem though is that the lirc_i2c module isn't getting loaded automatically at boot for some reason. Try adding lirc_i2c to the /etc/modules file and reboot to see if it works.[/QUOTE]
 lirc_i2c is loaded. I've also tried to load it manually, that means "rmmod lirc_i2c && rmmod lirc_dev && modprobe lirc_i2c" (and of course '/etc/init.d/lirc restart'). I get no error message and lsmod lists lirc_i2c and lirc_dev. Nonetheless my remote doesn't work.

Btw I've got a WinTV PCI FM (if that helps). 

P.S.: It was so easy to install lirc under kanotix/debian. Just an "apt-get install lirc" and everything was done. Why is this so much more difficult under ubuntu when it is also based on debian???

---

### Post by DrKayBee on 2005-06-06
I have run into a couple problems. 
First, at step 12, LIRC gave errors, complaining that it needs "module unloading" in the kernel. So I changed the .config in /usr/src/linux and changed MODULE_UNLOAD to y (it was 'not set' previously. Did a successful make on /usr/src/linux and also on /usr/src/lirc-0.7.1/ 

Then modprobing lirc_i2c gave me the following error

WARNING: Error inserting lirc_dev (/lib/modules/2.6.10-5-k7/misc/lirc_dev.ko): Invalid module format
FATAL: Error inserting lirc_i2c (/lib/modules/2.6.10-5-k7/misc/lirc_i2c.ko): Invalid module format


What should I do now?

---

### Post by dilmah on 2005-06-06
I agree, it is all too difficult, and it doesn't "just work" :(

I can only hope that some smart person out there can make a working lirc deb package and submit it. It should be just as easy as going apt-get install lirc, answer a couple of questions like what card you have and be done with it!

I'm probably a bit out of my depth now without anymore information. Perhaps try looking for error messages relating to lirc in dmesg, /var/log/messages and /var/log/lircd. Also check that the devices exist in /dev/lirc /dev/lircd ,etc.

I recently discovered that on the occasional reboot on my machine that instead of getting a device called /dev/lirc I would get one called /dev/lirc0, which of course caused lircd to die as soon as irexec (or irw, etc.) was launched. I can't explain why this was happening, but managed to work around the problem by adding a line to /etc/udev/udev.rules to create a permanent symlink (i.e. recreated on every reboot) from /dev/lirc to /dev/lirc0. Hopefully this will fix my problem. Time will tell.

---

### Post by Rumo on 2005-06-07
[QUOTE=dilmah]
I recently discovered that on the occasional reboot on my machine that instead of getting a device called /dev/lirc I would get one called /dev/lirc0, which of course caused lircd to die as soon as irexec (or irw, etc.) was launched. 
[/QUOTE]
I've checked this and it seems that I've got exactly this problem, too. Thanks a lot! At least I know now what went wrong.
> 
I can't explain why this was happening, but managed to work around the problem by adding a line to /etc/udev/udev.rules to create a permanent symlink (i.e. recreated on every reboot) from /dev/lirc to /dev/lirc0. Hopefully this will fix my problem. Time will tell.
I've already set a symlink to /dev/lirc0 and that works. Can you tell me the line you added to udev.rules? I could add an 'ln -s ...' to a boot-script but I think that would be even uglier than your work around ;-)

Again, I'm very grateful for your help!

---

### Post by Botsinge on 2005-06-07
[QUOTE=Rumo]I've already set a symlink to /dev/lirc0 and that works. Can you tell me the line you added to udev.rules? I could add an 'ln -s ...' to a boot-script but I think that would be even uglier than your work around ;-)[/QUOTE]I also had the problem of getting "connect: Connection refused" when trying to run irw, and I also could get it to work by doing a "make install" for lirc and restart of /etc/init.d/ircd.

As pointed out, it seems that the one thing missing, which made /etc/init.d/lirc fail (which in turn made irw fail) was the device /dev/lirc. So I also added a symlink in udev.rules to lirc0:

/etc/udev/udev.rules
```
...
KERNEL="lirc0", SYMLINK="lirc"
```But that wasn't enough, it seems that if it's left up to /etc/init.d/lircd to load the modules (lirc_i2c and lirc_dev in my case) the symlink for lirc is added to late which make /etc/init.d/lircd fail silently, so I also had to add the line:

/etc/modules
```
...
lirc_i2c
```But after that everything seems to be loaded and initialized in order.

---

### Post by dilmah on 2005-06-07
Thanks Botsinge, that's the line you need in /etc/udev/udev.rules I didn't have access to my box when I posted that message.

---

### Post by abarbaccia on 2005-06-16
I have done just about everything I can think of to get lircd running at boot.  My status is:

lirc installed
/dev/lirc0  -- ir device
/dev/lirc   -- link to /dev/lirc0 created in udev
modules load at boottime
lirc_i2c is in /etc/modules
lircd startup script is run at S19 (tried 99 as well)

For some reason, lircd is killed in bootup.  Once i'm booted up I can simply sudo lircd, and everything works perfectly!!  Someone please help me out.

--Andrew

---

### Post by GameGod on 2005-06-19
[QUOTE=DrKayBee]I have run into a couple problems. 
First, at step 12, LIRC gave errors, complaining that it needs "module unloading" in the kernel. So I changed the .config in /usr/src/linux and changed MODULE_UNLOAD to y (it was 'not set' previously. Did a successful make on /usr/src/linux and also on /usr/src/lirc-0.7.1/ 

Then modprobing lirc_i2c gave me the following error

WARNING: Error inserting lirc_dev (/lib/modules/2.6.10-5-k7/misc/lirc_dev.ko): Invalid module format
FATAL: Error inserting lirc_i2c (/lib/modules/2.6.10-5-k7/misc/lirc_i2c.ko): Invalid module format


What should I do now?[/QUOTE]

I just ran into that problem and have been banging my head against the wall all night.

I read on the MythTV mailing list that this has something to do with the modules being compiled for the wrong kernel version... so that got me thinking, and this is what I ended up with...

[SIZE=4]Solution:[/SIZE]
- Uninstalled linux-source and all the linux-headers packages I had installed with synaptic.
- Deleted **/usr/src/linux-source-2.6.10-5** (the source) because removing the package for this just gets rid of the .tar.bz2 file.
- Deleted the /usr/src/linux symlink.
- (Re)installed **linux-headers-2.6.10-5** AND **linux-headers-2.6.10-5-386**.
- Created the /usr/src/linux symlink to /usr/src/linux-headers-2.6.10-5-386 as so:
**ln -s /usr/src/linux-headers-2.6.10-5-386 /usr/src/linux**
- Went to my lirc-0.7.1 source directory, did a "make clean", "make uninstall", and also made sure all the lirc packages were uninstalled through synaptic.

Now, I simply recompiled and installed LIRC like in the original few posts, and she modprobes fine.

Hopefully this will help someone, I found lots of people through Google with the same problem, but no fix...

---

### Post by dilmah on 2005-06-20
[QUOTE=abarbaccia]I have done just about everything I can think of to get lircd running at boot.  My status is:

lirc installed
/dev/lirc0  -- ir device
/dev/lirc   -- link to /dev/lirc0 created in udev
modules load at boottime
lirc_i2c is in /etc/modules
lircd startup script is run at S19 (tried 99 as well)

For some reason, lircd is killed in bootup.  Once i'm booted up I can simply sudo lircd, and everything works perfectly!!  Someone please help me out.

--Andrew[/QUOTE]

Looks like you've tried basically everything outlined in here. A few things to try:
Run:
```
$sudo /etc/init.d/lircd stop
$sudo /etc/init.d/lircd start
```

if the remote still doesn't work, check the logs now /var/log/lirc*; dmesg; /var/log/messages, etc.
Perhaps that will give you some clue as to why it's not working. Looks like you've got the modules in there okay, but i think "sudo /etc/init.d/lircd start" is different from "sudo lircd" in the way it does things internaly

---

### Post by tristan on 2005-07-06
This thread has been unbelievably useful in getting lirc up and running on my box, I don't know how many other versions I tried to no success!

I also had the problem where lirc worked fine after the make install, but no after reboot.

In the end I did a couple of things which got it working for me.

1 - create the symlink to /dev/lirc

2 - disable  lirc from my startup (using rcconf)

3 - create my own startup script (startup.sh) in /etc/init.d :

[B]modprobe lirc_dev
modprobe lirc_gpio 
lircd
lircmd[/B]

The exact lirc modules will differ depending on the remote - I use a Leadtek Winfast2000XP remote

4 - Activate startup.sh to start at boot using rcconf

5 - add irexec to the gnome session

Voila - now I can use my AV streamer to transmit my remote signals to the computer in the other room, and control the videos (totem) streaming from the computer to the TV. 

This may not be the prettiest workaround to the problem but who cares :)

---

### Post by harm on 2005-07-13
Thank you so much guys!!! After days of trying I got LIRC to work. I only had to do
$sudo setserial /dev/ttyS0 uart none 
to free the serial port (got 'device or resource busy' while loading lirc_serial) and I was set. 
I love this!

---

### Post by teknomaniac on 2005-07-23
Hi.i have this problem when want to install lirc

root@ubuntu:/usr/src/lirc-0.7.1pre4 # make
make  all-recursive
make[1]: Wej&#347;cie do katalogu `/usr/src/lirc-0.7.1pre4'
Making all in drivers
make[2]: Wej&#347;cie do katalogu `/usr/src/lirc-0.7.1pre4/drivers'
Making all in lirc_dev
make[3]: Wej&#347;cie do katalogu `/usr/src/lirc-0.7.1pre4/drivers/lirc_dev'
Makefile:8: **************************************************
Makefile:8: *** Makefile trick not undone, trying to recover *
Makefile:8: **************************************************
mv Makefile.automake Makefile
make all
make[4]: Wej&#347;cie do katalogu `/usr/src/lirc-0.7.1pre4/drivers/lirc_dev'
mv Makefile Makefile.automake
cp ../Makefile.kernel Makefile
make -C /usr/src/linux/ SUBDIRS=/usr/src/lirc-0.7.1pre4/drivers/lirc_dev modules
 \
        KBUILD_VERBOSE=1
make[5]: Wej&#347;cie do katalogu `/usr/src/kernel-source-2.6.10'
mkdir -p /usr/src/lirc-0.7.1pre4/drivers/lirc_dev/.tmp_versions
make -f scripts/Makefile.build obj=/usr/src/lirc-0.7.1pre4/drivers/lirc_dev
  gcc -Wp,-MD,/usr/src/lirc-0.7.1pre4/drivers/lirc_dev/.lirc_dev.o.d -nostdinc -
iwithprefix include -D__KERNEL__ -Iinclude  -Wall -Wstrict-prototypes -Wno-trigr
aphs -fno-strict-aliasing -fno-common -Os     -fomit-frame-pointer -pipe -msoft-
float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i386 -Iinclude/asm                                        -i386/mach-default -Wdeclaration-after-statement -DIRCTL_DEV_MAJOR=61 -DEXPORT_S                                        YMTAB -DHAVE_CONFIG_H -I. -I. -I../.. -I /usr/src/lirc-0.7.1pre4/drivers/lirc_de                                        v/../.. -I /usr/src/linux//include/  -DMODULE -DKBUILD_BASENAME=lirc_dev -DKBUIL                                        D_MODNAME=lirc_dev -c -o /usr/src/lirc-0.7.1pre4/drivers/lirc_dev/.tmp_lirc_dev.                                        o /usr/src/lirc-0.7.1pre4/drivers/lirc_dev/lirc_dev.c
In file included from /usr/src/lirc-0.7.1pre4/drivers/lirc_dev/../../drivers/kco                                        mpat.h:167,
                 from /usr/src/lirc-0.7.1pre4/drivers/lirc_dev/lirc_dev.c:61:
include/linux/i2c.h:58: error: array type has incomplete element type
include/linux/i2c.h:197: error: array type has incomplete element type
make[6]: *** [/usr/src/lirc-0.7.1pre4/drivers/lirc_dev/lirc_dev.o] error 1
make[5]: *** [_module_/usr/src/lirc-0.7.1pre4/drivers/lirc_dev] error 2
make[5]: leaving directory `/usr/src/kernel-source-2.6.10'
make[4]: *** [lirc_dev.o] erroe 2
make[4]:leaving directory `/usr/src/lirc-0.7.1pre4/drivers/lirc_dev'
make[3]: *** [all] error 2
make[3]: leaving directory `/usr/src/lirc-0.7.1pre4/drivers/lirc_dev'
make[2]: *** [all-recursive] error 1
make[2]: leaving directory `/usr/src/lirc-0.7.1pre4/drivers'
make[1]: *** [all-recursive] error 1
make[1]: leaving directory `/usr/src/lirc-0.7.1pre4'
make: *** [all] error 2

i'm newbie and i don't know what i shoul'd do.
please help.

---

### Post by fl_QuelTos on 2005-07-23
@ reboot-problem.. maybe a cleaner solution:
there were 2 things i had to do to make lirc work after reboot:
/etc/lirc/hardware.conf:
DEVICE="/dev/lirc0"
MODULES="lirc_dev lirc_gpio"
(the MODULES-entry "lirc_dev lirc_serial" was a wrong one for me)

and then i had to fix the init script
/etc/init.d/lirc:
all path-entries for lircd and lircmd have been wrong. in my case i had to replace all paths /usr/sbin/lircd and /usr/sbin/lircmd by /usr/local/sbin/lircd and /usr/local/sbin/lircmd

now it works fine
no symlinks, no extra-module-loading, no own init-script ;)

think that are pretty easy-to-avoid-problems.. hope the ppl from lirc will fix that for better usability

@teknomaniac
try to follow the first post step by step and if u have any problems.. go on to the next posts and look out for posts describing the same problem u have.
your lines look like problems with linux-source/headers
if it doesnt compile with linux-source installed (and /usr/src/linux correctly linked) try using the headers instead (already described in this thread)

---

### Post by teknomaniac on 2005-07-24
succes  i have lirc_gpio and lirc_dev but when i try to add then :

root@ubuntu:/dev # modprobe lirc_gpio
FATAL: Module lirc_gpio not found.

root@ubuntu:/lib/modules/2.6.10-5-386/misc # modprobe /lib/modules/2.6.10-5-386/misc/lirc_gpio.o
FATAL: Module /lib/modules/2.6.10_5_386/misc/lirc_gpio.o not found.

after reboot i don't have /dev/lirc and /dev/lircd so i try dpkg-reconfigure lirc and lird is in /dev/ but after reboot lirc disapered.i don't know whats happend.


please help .

---

### Post by remmelt on 2005-08-11
[QUOTE=GameGod]
[SIZE=4]Solution:[/SIZE]
- Uninstalled linux-source and all the linux-headers packages I had installed with synaptic.
- Deleted **/usr/src/linux-source-2.6.10-5** (the source) because removing the package for this just gets rid of the .tar.bz2 file.
- Deleted the /usr/src/linux symlink.
- (Re)installed **linux-headers-2.6.10-5** AND **linux-headers-2.6.10-5-386**.
- Created the /usr/src/linux symlink to /usr/src/linux-headers-2.6.10-5-386 as so:
**ln -s /usr/src/linux-headers-2.6.10-5-386 /usr/src/linux**
- Went to my lirc-0.7.1 source directory, did a "make clean", "make uninstall", and also made sure all the lirc packages were uninstalled through synaptic.

Now, I simply recompiled and installed LIRC like in the original few posts, and she modprobes fine.

Hopefully this will help someone, I found lots of people through Google with the same problem, but no fix...[/QUOTE]


HURRAY! Thank you! That did the trick!

I found out I didn't have to do the "sudo make modules" from the first post in this thread.
After getting it all set up, I installed "apt-get install lirc lirc-x" so all the startup scripts and conf files are in the right place. 
If you are running KDE and want to control it with a RC, install the kdelirc package and start irkick instead of irexec. Then go into K-menu, Control Center, Peripherals, Remote Controls (or just right-click the little remote icon in the systray and go Configure).

If anyone is still having trouble, do post!

---

### Post by wilho on 2005-09-27
note: You'll have to do "make modules_install" after "make modules".

I got microsoft media center remote to work. You'll need to copy 
/usr/share/doc/lirc/remotes/mceusb/lircd.conf.mceusb
to overwrite
/etc/lirc/lircd.conf

I haven't read this thread thorougly, but I think it's unmentioned that proper way to get lirc to load on boot is through a /etc/init.d/lirc -script, which requires /etc/lirc/hardware.conf to be configured to load proper modules. In my case I had to edit modules -line to look like this:

MODULES="lirc_dev lirc_mceusb2"

And thats about it. Now I'll have to get the mythtv to work with lirc... 
:cool:

---

### Post by treegezer on 2005-10-13
Well I got lirc to work with my AST remote thanks to this thread. However, when I try to use a serial port other then /dev/ttyS0 I get ```
 treegezer@box:~$ irw
connect: Connection refused

```
any idea? Permissions on ttyS0 and the others are the same. 
The reason I want to verify my other ports is that I would like to get two serial irblasters plus the remote working on the same machine. I cannot seem to find any information on how this would be done. If someone could point me in the right direction, I would appreciate it.
Thanks in advance,
Stuart Hemm

---

### Post by dilmah on 2005-10-16
Okay, anyone got any ideas how to make this work on breezy?

I've got as far as downloading the kernel source for the kernel used in breezy (2.6.12-9), apt-getting gcc-3.4 (apparently needed to compile the kernel stuff in step #6), following the rest of the stuff as listed.

However, when trying to insert the lirc kernel modules, I get errors:
$ sudo modprobe lirc_gpio
WARNING: Error inserting lirc_dev (/lib/modules/2.6.12-9-k7/misc/lirc_dev.ko): Invalid module format
FATAL: Error inserting lirc_gpio (/lib/modules/2.6.12-9-k7/misc/lirc_gpio.ko): Invalid module format

This may have something to do with breezy using gcc-4.0 to compile the shipped kernel, and me having to use gcc-3.4 to compile the custom kernel modules in step #6.

Please, anyone who may have an idea, please share your experiences.
There's also a related thread here on [whether to use gcc-3.4 or gcc-4.x to compile custom kernel modules]("http://ubuntuforums.org/showthread.php?t=75651")

Dilmah.

---

### Post by dilmah on 2005-10-16
Aah, I fixed it myself.

Because I upgraded from hoary to breezy, I used the existing source directory that I had there from last time.

Going into the lirc source directory and doing a make clean fixed it.
Here's what I did:
cd /usr/src/lirc-0.7.1pre4
make clean
CC=gcc-3.4
export CC
./setup.sh
sudo make && sudo make install

Ubuntu rocks again! :)

---

### Post by piedamaro on 2005-10-18
For me there was no need to compile the kernel. I just untarred linux-source, made the link, ant then ran ./setup.sh in lirc source tree, it's explained here: [http://www.ubuntuforums.org/showthread.php?t=39125&highlight=lirc](http://www.ubuntuforums.org/showthread.php?t=39125&highlight=lirc)

---

### Post by eschvoca on 2005-10-19
My kernel modules were not loaded on reboot so I also had to edit /etc/udev/devfs.rules and add:

KERNEL=="lirc0",                SYMLINK="lirc"

and also add to /etc/udev/permissions.rules:

KERNEL=="lirc[0-9dm]*", MODE="0660", GROUP="lirc"

I added the "lirc" group and made myself belong to it (in /etc/group):

lirc:x:118:eschvoca

And add "lirc_i2c" to /etc/modules

Then it all works but once "lirc_dev" was taking 99% CPU for some reason.

Hope that helps some people who can't connect to lirc and having boot problems.

---

### Post by xinman on 2005-10-22
I've followed this guide and the one front slash32.com for the mythtv setup.  Now it all seems to work through most of this howto (mythtv is working great, except for the remote) how do i get lirc to interface with mythtv to make it do anything.

If I try running irexec it brings back:
```
irexec: could not open config files /home/xinman/.lircrc and /etc/lircrc
irexec: No such file or directory
```

What needs to go in this config file, where am I messing up.

Configuration:
Happauge PVR-250 running it on Breezy 386 kernel

Please help this is driving me insane, and my girlfriend is getting pissed that she can't change the channel without me doing it on the computer.

TIA,
XinMan    <--- ](*,)

---

### Post by tigrez on 2005-10-27
[QUOTE=dilmah]Okay, anyone got any ideas how to make this work on breezy?

I've got as far as downloading the kernel source for the kernel used in breezy (2.6.12-9), apt-getting gcc-3.4 (apparently needed to compile the kernel stuff in step #6), following the rest of the stuff as listed.

However, when trying to insert the lirc kernel modules, I get errors:
$ sudo modprobe lirc_gpio
WARNING: Error inserting lirc_dev (/lib/modules/2.6.12-9-k7/misc/lirc_dev.ko): Invalid module format
FATAL: Error inserting lirc_gpio (/lib/modules/2.6.12-9-k7/misc/lirc_gpio.ko): Invalid module format

This may have something to do with breezy using gcc-4.0 to compile the shipped kernel, and me having to use gcc-3.4 to compile the custom kernel modules in step #6.

Please, anyone who may have an idea, please share your experiences.
There's also a related thread here on [whether to use gcc-3.4 or gcc-4.x to compile custom kernel modules]("http://ubuntuforums.org/showthread.php?t=75651")

Dilmah.[/QUOTE]

I've solved this error installing gcc-3.4 
$ sudo apt-get install gcc-3.4*
$ cd /usr/src/linux 
$ make clean
$ make menuconfig 
etc...
My kernel is 2.6.12-9-386 and I'm using microfott media center remote.

Anyway thanks!

---

### Post by apollyonis on 2005-11-29
In case anyone's having trouble with changing the remote type mid-stream and rerunning ./setup.sh, make sure that you do a ```
sudo killall lircd
```
before running make;make install again, otherwise it will leave the old config file under /etc/lircd.conf - just in case you could always do ```
sudo cp /etc/lirc/lircd.conf /etc/lircd.conf
```

That solved my problem of trying different remote configs and restarting the server each time. :)

---

### Post by apollyonis on 2005-11-30
For those few who have set up lirc with an RC-6 MCE remote, I have included the lircrc file to put under ~/.lircrc and ~/.mythtv so that the remote will have correctly functioning buttons. Decompress and copy the file to both ~/.lircrc and ~/.mythtv  .

---

### Post by oblib on 2005-12-03
[QUOTE=Botsinge]
As pointed out, it seems that the one thing missing, which made /etc/init.d/lirc fail (which in turn made irw fail) was the device /dev/lirc. So I also added a symlink in udev.rules to lirc0:

/etc/udev/udev.rules
```
...
KERNEL="lirc0", SYMLINK="lirc"
```But that wasn't enough, it seems that if it's left up to /etc/init.d/lircd to load the modules (lirc_i2c and lirc_dev in my case) the symlink for lirc is added to late which make /etc/init.d/lircd fail silently, so I also had to add the line:

/etc/modules
```
...
lirc_i2c
```But after that everything seems to be loaded and initialized in order.[/QUOTE]

For those having a problem with /dev/lirc0 being made instead of /dev/lirc, another solution, as mentioned on the lirc homepage is to create this file /etc/udev/rules.d/lirc.rules, and use the following contents:
```

KERNEL="lirc[0-9]*",    NAME="lirc", MODE="0666"

```
That actually renames lirc0 to lirc, and opens it up to the world (use MODE="0660" if your user is in the right group). I really don't know much about so use at your own risk.

---

### Post by crouton on 2006-01-08
If you get the lirc_i2c module loaded but irw refuses to connect, try running 'sudo mode2' and pressing buttons on the remote.  This works for me.

---

### Post by _rob_ on 2006-01-30
Is there a thread or forum group for LIRC on Breezy?  

I got lirc to run fine following the "InstallMythOnUbuntu" wiki.  But now I'm having trouble getting lirc to work.  [I screwed it up trying to get it to auto start at boot up.]  Now after I get lircd daemon running and start irw to test, lircd daemon dies (mythfrontend will also kill it).

Any ideas?

-Rob

Here is /var/log/lirc:
…
Jan 29 20:21:47 ClosetBox lircd 0.7.3pre1: lircd(hauppauge) ready
Jan 29 20:21:47 ClosetBox lircd 0.7.3pre1: accepted new client on /dev/lircd
Jan 29 20:21:47 ClosetBox lircd 0.7.3pre1: could not get file information for /dev/lirc
Jan 29 20:21:47 ClosetBox lircd 0.7.3pre1: default_init(): No such file or directory
Jan 29 20:21:47 ClosetBox lircd 0.7.3pre1: caught signal

---

### Post by Sonic-NKT on 2006-02-17
Hi,
im trying to get lirc working right now... but i have some problems.
i have a igor usb ir receiver that works great (atleast in windows) now it wanted to get it working under linux. configured lirc and then compiled it. everything worked without errors. 
But what to do now? i dont have a lircd.conf cause i use a old remotecontrol that was lying around in the basement... 
what do do know?
i tried running mode2 and if i press a button on the remotecontrol the program recognizes it, so the ir receiver is working right?
but how can i make a new config file for my remote control?

EDIT1:
hmm found the app irrecord.. but now im faced with the problem that it only receives one code, for every button i press...
so its unusable :(
argh ok next try then i think

---

### Post by Sonic-NKT on 2006-02-19
sooo...
lirc is working now perfect, exepct that the /dev/lirc device dissapears after reboot and i have to do a make install again...
how can i fix this?

---

### Post by dilmah on 2006-02-19
Make sure that you've inserted the required modules for your setup into the modules file in /etc (can't remember the exact filename right now, but step #15 in the original post).

HTH.
Dilmah

---

### Post by i-mehl on 2006-02-28
i always get this while compiling:
Sorry, this dri ver needs bttv version 0.7.45 or higher. If you are using the bttv package, copy it to the kernel 

what can i do?

---

### Post by d0d0 on 2006-05-08
same here, anyone please ?

---

### Post by [Yatta] on 2006-05-18
WHY??
When i do:
```
sudo make include/linux/version.h
sudo make modules
```
I end up getting this error:
```
/usr/src/linux# make modules
  CHK     include/linux/version.h
  SPLIT   include/linux/autoconf.h -> include/config/*
make[1]: *** No rule to make target `arch/i386/kernel/msr.c', needed by `arch/i386/kernel/msr.o'.  Stop.
make: *** [arch/i386/kernel] Error 2
root@minime:/usr/src/linux#
```

Any help would be greatly appreciated....  ](*,) 

```
lirc_dev: IR Remote Control driver registered, at major 61 
lirc_serial: no version for "lirc_unregister_plugin" found: kernel tainted.
```
BTW i'm using Breezy and PVR-150

***Edit***
I think i found my problem... will update if i do rectify it

---

### Post by [Yatta] on 2006-05-21
i recompiled my kernel 2.6.16-10ck ... working fine.
to a point. 
 when i use 
```
mode2
```
i see gibberish when i press keys on my remote, btw which is a One-for-All URC-8910. When i use 
```
irw
```
Nada ](*,) .... I know that is sorta good :cool:. If i remember correctly i jsut need to find lircd.conf file for my 8910.
Any help would be greatly appreciated.

---

### Post by [Yatta] on 2006-05-27
It's working now

---

### Post by z0r on 2006-06-05
[QUOTE=i-mehl]i always get this while compiling:
Sorry, this dri ver needs bttv version 0.7.45 or higher. If you are using the bttv package, copy it to the kernel[/QUOTE]

Here's how I built LIRC for Ubuntu Dapper, running Linux 2.6.15:

Follow instructions here [http://www.mythtv.org/wiki/index.php/Ubuntu_Installation#LIRC]("http://www.mythtv.org/wiki/index.php/Ubuntu_Installation#LIRC") to build the kernel modules. I had to disable a couple of modules which refused to build.

Get LIRC 0.8.0 from [http://www.lirc.org/]("http://www.lirc.org/"). Unpack it wherever you like, and change into the new directory.
```
tar jxvf lirc-0.8.0.tar.bz2
cd lirc-0.8.0
```

Run setup.sh. After configuring it for your receiver, choose "Save configuration & run configure".
```
./setup.sh
```

Run make.
```
make
```

At this point it complained about missing include files. To fix this, I created a link to the kernel source:
```
ln -s /usr/src/linux/drivers/ drivers/drivers
```
That assumes that your kernel source is available under /usr/src/linux.

Now it should build fine:
```
make
```

Before installing it, remove the Ubuntu LIRC packages to prevent conflicts:
```
sudo apt-get remove lirc lirc-x
```

Then install:
```
sudo make install
```

The code should have installed to /usr/local. Follow the rest of the guide (above) to finish setting it up.

I have an AverMedia card with the bt878 chipset. My /etc/modules contains this line:
```
lirc-gpio gpio_mask=0xf00f0 gpio_lock_mask=0x20 gpio_xor_mask=0xf00f0 soft_gap=0 sample_rate=10
```
My /etc/lircd.conf looks like this:
```
begin remote

  name  lirc_test.txt
  bits            8
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          199946
  toggle_bit      0


      begin codes
          source                   0x7D
          teletext                 0xBD
          power                    0xFD
          1                        0x75
          2                        0xB5
          3                        0x35
          4                        0x6D
          5                        0xAD
          6                        0x2D
          7                        0x65
          8                        0xA5
          9                        0x25
          0-enter                  0x5D
          audio                    0xED
          fullscreen               0xE5
          display                  0x9D
          loop                     0x1D
          preview                  0xDD
          backward                 0x55
          forward                  0x95
          capture                  0x15
          mute                     0xD5
          record                   0x4D
          pause                    0x8D
          stop                     0x0D
          play                     0xCD
          red                      0x45
          green                    0x79
          volume-                  0x85
          volume+                  0x05
          ok/yellow                0xC5
          previous                 0xB9
          next                     0x39
          cancel/blue              0xF9
      end codes

end remote
```

Good luck!
Alex

---

### Post by silent_scream on 2006-08-29
it seems tha the installation and the setup succefeed with your way z0r ,
but what should i do next?
I have a winfast 2000 PVR, so the line in my /etc/modules what should be?
id there anything else that i should do???
your instructions were great!

---

### Post by christooss on 2006-08-30
Does any body know why lirc isn't suported by default?

It would be great if simply apt-get install lirc would work.

---

### Post by z0r on 2006-08-31
Hi silent scream,

Glad to hear that the instructions worked! I think all you need to do is to get the right line for /etc/modules. I found mine by searching the net: look for your card name, lirc and /etc/modules. Unfortunately I do not know how to derive the contents of the line. It is probably complicated.

Sorry about that. Good luck!

---

### Post by silent_scream on 2006-09-17
well i have a leadtek winfast pvr 2000, but i can't find something usefull
to  add in /etc/modules ...

it uses the same chipset bt878...
if you have any information just shoot!

edit: ok i managed to install lirc and  configure it.
but every time i reboot i must do this from the beginning :-? ](*,) 
i have to configure make make install modprobe etc...

any idea to fix this??

---

### Post by mirceade on 2007-07-09
> **'[Yatta] said:**
> i recompiled my kernel 2.6.16-10ck ... working fine.
to a point. 
 when i use 
```
mode2
```
i see gibberish when i press keys on my remote, btw which is a One-for-All URC-8910. When i use 
```
irw
```
Nada ](*,) .... I know that is sorta good :cool:. If i remember correctly i jsut need to find lircd.conf file for my 8910.
Any help would be greatly appreciated.

Same problemo here. How'd you get it to work?

---

