---
title: "Program Removal"
date: 2016-09-03
forum: General Help
---

### Post by stockpimp on 2016-09-03
I'm running into an issue removing CGMiner 4.9.2 from my new install of Ubuntu Mate on Raspberry Pi 3.  4.9.2 will not work with my Zeus miner so I'm trying to go back to an older version and it wont allow me to as 4.9.2 is the current one.  I have access to the Pi through ssh terminal but my terminal skills are close to zero to be honest.  I manged to delete the directory in the hopes that this would allow the new install but no luck and I have tried to run apt-get install etc but again.... lacking in skills in this area.  Any help remeoving 4.9.2 and installing 4.3.5 would be greatly appreciated!

---

### Post by egeezer on 2016-09-03
You might try the following:
```
sudo apt-get remove --purge <the official name of the program>
```
If that doesn't work, you could use the root account by running
```
sudo -i
```
followed by your password.  CAUTION: once you do that, you are the boss - what you type will be done, right or wrong!  The prompt will change from $ to a #, and you can use:
```
dpkg --purge <the official name of the program>
```
 When that completes, you'll be left with the terminal with root privilege active, so type
```
exit
```
and you will see the $ return at the prompt (user mode)

That should really clean out the old stuff, so you can look for a source of the new program.

---

### Post by stockpimp on 2016-09-06
Thank-you for the response.  I tried this out today and it didn't work?  when I go to the new folder 4.3.5 to try and run that it still runs 4.9.2?  I tried re-booting and same result and i even tried to remove 4.3.5 but it can't "find" it.  The directory is there.... i can see it when i hit "ls" in my downloads section but still can't seem to remove it.  I'm wondering if I need to start again and reflash the Ubu Mate image and the re-load 4.3.5?  Seems extreme but....

---

### Post by egeezer on 2016-09-06
I'm afraid I can't help further - my  personal experience with this sort of thing doesn't go beyond the straight dpkg --purge.  You might try again and add --force-help, but I've never tried that.

---

### Post by howefield on 2016-09-06
> **stockpimp said:**
> I tried this out today and it didn't work?

"it didn't work" doesn't help others to help you. It would be better if others could see the command that you used and the output, so copy/paste the terminal text back here between code tags.

What is the output of the terminal command..

```
apt-cache policy cgminer
```

---

### Post by stockpimp on 2016-09-06
> **howefield said:**
> "it didn't work" doesn't help others to help you. It would be better if others could see the command that you used and the output, so copy/paste the terminal text back here between code tags.

What is the output of the terminal command..

```
apt-cache policy cgminer
```

```
cgminer:
  Installed: 4.9.2-1build1
  Candidate: 4.9.2-1build1
  Version table:
 *** 4.9.2-1build1 500
        500 http://ports.ubuntu.com xenial/universe armhf Packages
        100 /var/lib/dpkg/status
```

Sorry tried to be as descriptive as pos.  I just figured out how to use cut and paste in SSH terminal mode... not at all used to using this one.

---

### Post by howefield on 2016-09-06
> **stockpimp said:**
> Sorry tried to be as descriptive as pos.  I just figured out how to use cut and paste in SSH terminal mode... not at all used to using this one.

Congrats on learning something new :)

And post back the info from..

```
sudo apt-get purge cgminer
```

---

### Post by stockpimp on 2016-09-06
```
dj@DJPi:/$ sudo apt-get purge cgminer[sudo] password for dj: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following package was automatically installed and is no longer required:
  libjansson4
Use 'sudo apt autoremove' to remove it.
The following packages will be REMOVED:
  cgminer*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 857 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 171002 files and directories currently installed.)
Removing cgminer (4.9.2-1build1) ...
Processing triggers for man-db (2.7.5-1) ...

```

looks like that may have worked

---

### Post by howefield on 2016-09-06
OK, there may be some configuration files left in your /home folder that I don't think will be a problem but you can have a look and keep or remove them. To see the hidden files in your home folder, use the command 

```
ls -al ~/
```

Or open the File Manager and press the Ctrl + H keys which will toggle the show hidden files switch.

Now you can go find the version that you want to install that will work with your operating system. And if installed with a deb file, you can use

```
sudo apt-mark hold cgminer
```

to stop it being upgraded to the version included with your operating system repositories, ie version 4.9.2

---

### Post by stockpimp on 2016-09-07
Now when I type Sudo apt insatll cgminer in terminal it re-installs 4.9.2?  Sorry to be such a pain with this but I can't seem to get away from this one version?  Thanx again!

---

### Post by howefield on 2016-09-08
> **stockpimp said:**
> Now when I type Sudo apt insatll cgminer in terminal it re-installs 4.9.2?  Sorry to be such a pain with this but I can't seem to get away from this one version?  Thanx again!

So presumably you have obtained a copy of the version you desire, yes ? Might be helpful if you mentioned where you got it and the file name.

Assuming that you have, and that it is downloaded to your ~/Downloads folder, you can use apt to install it with..

```
sudo apt install ~/Downloads/cgminer_4.3.5_amd64.deb
```

That isn't likely to be the name of the file, I am only guessing at the name for illustration.

Then use the apt-mark hold command to prevent it from upgrading to the repository version (4.9.2)

---

### Post by stockpimp on 2016-09-08
> **howefield said:**
> So presumably you have obtained a copy of the version you desire, yes ? Might be helpful if you mentioned where you got it and the file name.

Assuming that you have, and that it is downloaded to your ~/Downloads folder, you can use apt to install it with..

```
sudo apt install ~/Downloads/cgminer_4.3.5_amd64.deb
```

That isn't likely to be the name of the file, I am only guessing at the name for illustration.

Then use the apt-mark hold command to prevent it from upgrading to the repository version (4.9.2)

The file is not a .deb file.  It's a "zip" file 

```
 dj@DJPi:~$ cd /home/dj/Downloadsdj@DJPi:~/Downloads$ ls
cgminer-master    cgminer-master.zip
dj@DJPi:~/Downloads$ 

```

which looks like this.... 
```
 01-cgminer.rules       driver-minion.c
A1-board-selector-CCD.c    driver-modminer.c
A1-board-selector-CCR.c    driver-SPI-bitmine-A1.c
A1-board-selector.h       driver-spondoolies.c
A1-common.h           driver-spondoolies.h
A1-desk-board-selector.c   driver-zeus.c
A1-trimpot-mcp4x.c       driver-zeus.h
A1-trimpot-mcp4x.h       elist.h
api.c               example.conf
API.class           FPGA-README
api-example.c           fpgautils.c
api-example.php           fpgautils.h
api-example.py           hexdump.c
api-example.rb           hf_protocol_be.h
API.java           hf_protocol.h
API-README           i2c-context.c
arg-nonnull.h           i2c-context.h
ASIC-README           klist.c
AUTHORS               klist.h
autogen.sh           lib
bench_block.h           libbitfury.c
bitforce-firmware-flash.c  libbitfury.h
bitstreams           LICENSE
ccan               linux-usb-cgminer
c++defs.h           logging.c
cgminer.c           logging.h
ChangeLog           m4
compat               Makefile.am
compat.h           MCast.class
configure.ac           MCast.java
COPYING               mcp2210.c
crc16.c               mcp2210.h
crc.h               mg_proto_parser.c
driver-avalon2.c       mg_proto_parser.h
driver-avalon2.h       miner.h
driver-avalon.c           miner.php
driver-avalon.h           mknsis.sh
driver-bab.c           NEWS
driver-bflsc.c           noncedup.c
driver-bflsc.h           README
driver-bitforce.c       README.md
driver-bitfury.c       scrypt.c
driver-bitfury.h       scrypt.h
driver-bitmain.c       sha2.c
driver-bitmain.h       sha2.h
driver-cointerra.c       spi-context.c
driver-cointerra.h       spi-context.h
driver-drillbit.c       usbtest.py
driver-drillbit.h       usbutils.c
driver-gridseed.c       usbutils.h
driver-gridseed.h       uthash.h
driver-hashfast.c       util.c
driver-hashfast.h       util.h
driver-icarus.c           warn-on-use.h
driver-klondike.c       windows-build.txt
driver-knc-spi-fpga.c
dj@DJPi:~/Downloads/cgminer-master$ 

```

Thank-you again for the help!

---

### Post by stockpimp on 2016-09-11
Anyone have any ideas on this one?  Thank-you again for your help... lost on this stuff.

---

### Post by deadflowr on 2016-09-11
Do either of the two README files (README and README.md.) give you any clues as to what you need to do in order to install it?

---

### Post by howefield on 2016-09-11
The installation instructions are in the README file, there are also mentions of support avenues that you might like to try.

---

### Post by Keith_Helms on 2016-09-11
Is there any reason you think the 4.3.5 version will work?  Unless you're up for compiling it from source, it would be easier to install a package file.  You can get the 4.7.0 version from here:

[https://packages.debian.org/jessie/amd64/cgminer/download](https://packages.debian.org/jessie/amd64/cgminer/download)

The Ubuntu repositories seem to have either 4.9.2 or 3.11.0:

[http://packages.ubuntu.com/search?suite=all&searchon=names&keywords=cgminer](http://packages.ubuntu.com/search?suite=all&searchon=names&keywords=cgminer)

There's no guarantee all the install dependencies will be met for an older version, but you can give it a shot.

---

### Post by stockpimp on 2016-09-11
I found this version as it is supposed to be set up for the zeus miner where as the 4.9.2 isn't.  I have read the "read-me" file.... but unfortunately it was / is not exceptionally helpfully or at least for me.  As I say, complete noob on this stuff.  I will go back to the windows version.

---

