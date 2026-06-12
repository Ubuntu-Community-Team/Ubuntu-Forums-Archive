---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2014-06-03
forum: General Help
---

### Post by James_Brough on 2014-06-03
I am unable to install/uninstall anything via the Software Center because I keep getting an error saying I have a problem with the software currently installed. I have an option to cancel or repair. I read some other threads and keep coming to a command "sudo apt-get -f install" and then I get this error at the bottom line

E: Sub-process /usr/bin/dpkg returned an error code (1)

Just wondering if anyone can point me in the right direction here. I am kind of stuck.

And I almost forgot, this is my first post on here even though I have been reading through the forum for about a year or so. 

Greetings from East Tennessee!!! ):P

---

### Post by plucky on 2014-06-03
> I read some other threads and keep coming to a command "sudo apt-get -f install" and then I get this error at the bottom line

E: Sub-process /usr/bin/dpkg returned an error code (1)

Just wondering if anyone can point me in the right direction here. I am kind of stuck.

Welcome to the forum @James_Brough

Can you copy and paste the complete result of the "sudo apt-get -f install" command.

Use [noparse]```
 Your Text[
```[/noparse] blocks around the text.

This should show the package that is casing the error.

Good Luck

---

### Post by James_Brough on 2014-06-07
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libavformat53 libebml3 libgroupsock0 liblivemedia7 libmatroska5
  libusageenvironment0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libebml4
The following NEW packages will be installed:
  libebml4
0 upgraded, 1 newly installed, 0 to remove and 90 not upgraded.
5 not fully installed or removed.
Need to get 0 B/51.7 kB of archives.
After this operation, 178 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 188154 files and directories currently installed.)
Preparing to unpack .../libebml4_1.3.0-2_amd64.deb ...
Unpacking libebml4:amd64 (1.3.0-2) ...
dpkg: error processing archive /var/cache/apt/archives/libebml4_1.3.0-2_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libebml.so.4', which is also in package libebml3:amd64 1.3.0-0~ppa0
Errors were encountered while processing:
 /var/cache/apt/archives/libebml4_1.3.0-2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by James_Brough on 2014-06-07
Also just so you know I found another thread on another forum with exact same problem. I followed the instructions listed in this thread and still have trouble. This might help you see more details about my problem....



[https://answers.launchpad.net/ubuntu/+question/249219](https://answers.launchpad.net/ubuntu/+question/249219)


If you view that other thread you will see what I get down to post #12. I get the exact same thing....

---

### Post by plucky on 2014-06-08
> dpkg: error processing archive /var/cache/apt/archives/libebml4_1.3.0-2_amd64.deb (--unpack):
trying to overwrite '/usr/lib/x86_64-linux-gnu/libebml.so.4', which is also in package libebml3:amd64 1.3.0-0~ppa0

But above that > The following packages were automatically installed and are no longer required:
libavformat53 **libebml3** libgroupsock0 liblivemedia7 libmatroska5
libusageenvironment0
Use 'apt-get autoremove' to remove them.

Try running ```
sudo apt-get autoremove
``` and then ```
sudo apt-get install -f
``` and see if that fixes the problem.

Good Luck

---

### Post by James_Brough on 2014-06-10
results from "sudo apt-get autoremove"

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libmatroska6 : Depends: libebml4 but it is not installed
 vlc-nox : Depends: libebml4 but it is not installed
           Recommends: libdvdcss2 but it is not installable
E: Unmet dependencies. Try using -f.


results from "sudo apt-get install -f"

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libavformat53 libebml3 libgroupsock0 liblivemedia7 libmatroska5
  libusageenvironment0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libebml4
The following NEW packages will be installed:
  libebml4
0 upgraded, 1 newly installed, 0 to remove and 90 not upgraded.
5 not fully installed or removed.
Need to get 0 B/51.7 kB of archives.
After this operation, 178 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 188154 files and directories currently installed.)
Preparing to unpack .../libebml4_1.3.0-2_amd64.deb ...
Unpacking libebml4:amd64 (1.3.0-2) ...
dpkg: error processing archive /var/cache/apt/archives/libebml4_1.3.0-2_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libebml.so.4', which is also in package libebml3:amd64 1.3.0-0~ppa0
Errors were encountered while processing:
 /var/cache/apt/archives/libebml4_1.3.0-2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by plucky on 2014-06-10
Found [This Bug Report](https://bugs.launchpad.net/ubuntu/+source/libebml/+bug/1279357)

See post #8 might work for you.

Good Luck

---

