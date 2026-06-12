---
title: "Deleting Old Linux Headers?"
date: 2014-05-01
forum: General Help
---

### Post by RealisticDave on 2014-05-01
I have 12.04 installed using WUBI, on a laptop with Win XP. Everything has been running fine for a year or so. Recently I tried to install some updates, and I received an error---/usr/src/linux headers 3.8.0-39 can't be installed because of a disk full error. (My /usr is 99% used.) I've looked through a number of posts, and I've seen some indications that if you remove all of the previous linux headers from the /src folder---EXCEPT for the previous update, in my case it would be 3.0.0-38 and 3.8.0-38-generic---that it will free up the needed space. Some posts state that this is just 'good housekeeping,' and should be done regularly.

But---I don't want to do this if the previous downloads are still needed.  My thinking is that each download is 'stand-alone,' and replaces all the previous---but I don't know for certain. Can anyone tell me for sure?  Other posts say that it's possible to use GPARTED to repartition or rearrange things.  But, I'm not sure I'd be all that comfortable doing so. I'd appreciate any information about removing previous linux headers, or suggestions about a solution.  Thanks!

---

### Post by tgalati4 on 2014-05-01
It's generally safe to remove old headers.  You would only need to keep them to preserve a build environment for a program that you compiled with a specific version--a custom kernel for instance.  Since you are out of space, it doesn't really matter.  Your system will not function without freeing up space, so you have to start dumping.  Old headers, even older, compiled kernels can go.  Keep at least one older kernel for a backup.

Since you are running through XP, chances are high that your Windows partition will take a dump before Ubuntu balls up, so you might as well do some house cleaning and prepare for a dual-boot installation.

---

### Post by papibe on 2014-05-01
Hi RealisticDave.

Been there: [Bug #1089195]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1089195").

I would gladly help you. The idea is delete/uninstall as much as possible, but keeping at least a couple of old kernels and headers.

Could you open a terminal, run these commands and post back the output (you can copy/paste the text)?
```
df -h

df -i

dpkg -l | grep linux-image | awk '{print $2}'
```
Regards.

---

### Post by RealisticDave on 2014-05-02
Thanks, had a busy day so I couldn't get back right away.
df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0      3.8G  1.8G  1.9G  48% /
udev            929M  4.0K  929M   1% /dev
tmpfs           188M  816K  187M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            938M  152K  938M   1% /run/shm
/dev/sda3        45G   14G   31G  32% /host
/dev/loop1      3.8G  288M  3.4G   8% /home
/dev/loop2      3.8G  2.7G  923M  75% /usr

df -i
Filesystem     Inodes  IUsed  IFree IUse% Mounted on
/dev/loop0     256000  41369 214631   17% /
udev           237651    502 237149    1% /dev
tmpfs          240043    420 239623    1% /run
none           240043      3 240040    1% /run/lock
none           240043      7 240036    1% /run/shm
/dev/sda3           0      0      0     - /host
/dev/loop1     256000   3950 252050    2% /home
/dev/loop2     256000 251090   4910   99% /usr

dpkg -l | grep linux-image | awk '{print $2}'
linux-image-3.8.0-29-generic
linux-image-3.8.0-35-generic
linux-image-3.8.0-36-generic
linux-image-3.8.0-37-generic
linux-image-3.8.0-38-generic
linux-image-3.8.0-39-generic
linux-image-generic-lts-raring

As near as I can tell, Update Manager gets hung up at trying to install the 'second-half' of "39"---if that's the correct terminology? Do you think that if I trashed everything except 3.8.0-38 and 3.8.0-38 generic, that would do the trick?  I appreciate your input. Thanks.

---

### Post by papibe on 2014-05-02
Thanks.

So the latest kernel and headers are from 3.8.0-39. That's is the one you are using right now and it shouldn't be removed.

Also, I'd keep the previous one as safety practice (3.8.0-38).

Then run this command:
```
sudo apt-get purge linux-image-3.8.0-29-generic linux-image-3.8.0-35-generic linux-image-3.8.0-36-generic linux-image-3.8.0-37-generic
```
Now the the kernels those kernel are out of the picture, you can remove their headers:
```
sudo apt-get purge linux-headers-3.8.0-29 linux-headers-3.8.0-35 linux-headers-3.8.0-36 linux-headers-3.8.0-37
```
Let us know how it goes.
Regards.

---

### Post by RealisticDave on 2014-05-02
Hello again, I tried to do the command to purge the kernels, and I received the following reply.  I did the suggested command (I'd done that many times yesterday), and I received the same error message that I saw yesterday.  I'll paste the messages below, but I had one question. Is there a way to go directly into the folder where these are located and remove them manually?  I don't think that I can simply pull them to trash because it needs a higher permission, and I don't know how to "sudo" when I'm trying to do something manually.  Anyway, I'd appreciate your comments, and I may not be staying online much more today, but I'll be back on Saturday. (I spent about 8 hours today doing yard work for a couple charities, and the Arkansas sun has just about done me in, so I'll be heading to bed soon!)  Thanks.

sudo apt-get purge linux-image-3.8.0-29-generic linux-image-3.8.0-35-generic linux-image-3.8.0-36-generic linux-image-3.8.0-37-generic
[sudo] password for daveandjan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-generic-lts-raring : Depends: linux-headers-3.8.0-39-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
daveandjan@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gir1.2-ubuntuoneui-3.0 libubuntuoneui-3.0-1 thunderbird-globalmenu
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.8.0-39-generic
The following NEW packages will be installed:
  linux-headers-3.8.0-39-generic
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
2 not fully installed or removed.
Need to get 0 B/1,012 kB of archives.
After this operation, 12.0 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 278450 files and directories currently installed.)
Unpacking linux-headers-3.8.0-39-generic (from .../linux-headers-3.8.0-39-generic_3.8.0-39.57~precise1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.8.0-39-generic_3.8.0-39.57~precise1_amd64.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.8.0-39-generic/include/config/scsi/pm8001.h.dpkg-new' (while processing `./usr/src/linux-headers-3.8.0-39-generic/include/config/scsi/pm8001.h'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.8.0-39-generic_3.8.0-39.57~precise1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by papibe on 2014-05-02
I've experience that. There's no space even to delete stuff (inodes actually).

To make enough space you will have to go to the directory where one of the header packages we are trying to delete, and delete by hand.

Removing one set of headers should suffice. For instance:
```
rm -rf /usr/src/linux-headers-3.2.0-29*
```
Then try again purging the kernels and the headers.

Regards.

---

### Post by RealisticDave on 2014-05-02
I ran the command, and I've now deleted all of the kernels and headers except for 38.  I tried to install the header for 39 through Update Manager, but it wouldn't do so.  So, I did it with the apt-get install -f command, and it worked fine.  I now have both kernel and header for 38 and 39.  As part of 'good housekeeping,' I should always delete old kernels and headers whenever Update Manager shows that their are new ones, correct?

Thanks for your assistance.  I learned some new things through this process, and I appreciate your help.  Have a nice weekend, and just to see what effect this had on inodes, I re-ran the commands again and I've pasted them below, showing that it cleared out quite a bit.  I'm going to mark this thread as solved!
df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0      3.8G  1.8G  1.9G  49% /
udev            929M  4.0K  929M   1% /dev
tmpfs           188M  820K  187M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            938M  156K  938M   1% /run/shm
/dev/sda3        45G   14G   31G  32% /host
/dev/loop1      3.8G  342M  3.3G  10% /home
/dev/loop2      3.8G  2.4G  1.3G  65% /usr
daveandjan@ubuntu:~$ df -i
Filesystem     Inodes  IUsed  IFree IUse% Mounted on
/dev/loop0     256000  41372 214628   17% /
udev           237651    502 237149    1% /dev
tmpfs          240043    420 239623    1% /run
none           240043      3 240040    1% /run/lock
none           240043      7 240036    1% /run/shm
/dev/sda3           0      0      0     - /host
/dev/loop1     256000   5215 250785    3% /home
/dev/loop2     256000 165353  90647   65% /usr

---

