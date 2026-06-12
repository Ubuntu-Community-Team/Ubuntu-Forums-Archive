---
title: "unable to perform security update"
date: 2018-05-08
forum: General Help
---

### Post by chopra on 2018-05-08
Hi All,
I am running Ubuntu 16.04, and was prompted to install security updates regarding cups printing.  The updating failed, multiple times with the same error message.
I then tried:
sudo apt dist-upgrade
and got the following message:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  cups-browsed
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/92.9 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 369589 files and directories currently installed.)
Preparing to unpack .../cups-browsed_1.8.3-2ubuntu3.4_amd64.deb ...
Failed to stop cups-browsed.service: Unit cups-browsed.service not loaded.
invoke-rc.d: initscript cups-browsed, action "stop" failed.
dpkg: warning: subprocess old pre-removal script returned error exit status 5
dpkg: trying script from the new package instead ...
Failed to stop cups-browsed.service: Unit cups-browsed.service not loaded.
invoke-rc.d: initscript cups-browsed, action "stop" failed.
dpkg: error processing archive /var/cache/apt/archives/cups-browsed_1.8.3-2ubuntu3.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 5
Errors were encountered while processing:
 /var/cache/apt/archives/cups-browsed_1.8.3-2ubuntu3.4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

This is the same error I got when trying to install the security update from the GUI. I have not printed anything from this machine in a year or so, but have never had any problems.

Thanks, Chopra

---

### Post by Xian on 2018-05-08
This is a puzzler. Let's try a series of commands:
```
sudo service cups stop
sudo service cups-browsed stop
sudo apt-get update
sudo apt-get install -f
sudo apt-get upgrade
sudo service cups start
sudo service cups-browsed start
```
Any change?

---

### Post by chopra on 2018-05-09
Hi Xian,
I tried the commands, and the second one gave me this message:
Failed to stop cups-browsed.service: Unit cups-browsed.service not loaded.

```
sudo apt-get update leads to:
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
Hit:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease              
Hit:3 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Ign:4 [http://dl.google.com/linux/talkplugin/deb](http://dl.google.com/linux/talkplugin/deb) stable InRelease               
Hit:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease             
Hit:6 [http://dl.google.com/linux/talkplugin/deb](http://dl.google.com/linux/talkplugin/deb) stable Release                 
Hit:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease
Reading package lists... Done

sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.

sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic linux-signed-generic
  linux-signed-image-generic
The following packages will be upgraded:
  cups-browsed distro-info-data flashplugin-installer linux-libc-dev wget
5 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Need to get 1,159 kB/1,252 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue? [Y/n] y

so after hitting yes, I get the same error message.

Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 distro-info-data all 0.28ubuntu0.8 [4,502 B]
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 wget amd64 1.17.1-1ubuntu1.4 [299 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 flashplugin-installer amd64 29.0.0.171ubuntu0.16.04.1 [6,818 B]
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 linux-libc-dev amd64 4.4.0-124.148 [849 kB]
Fetched 1,159 kB in 0s (2,501 kB/s)     
Preconfiguring packages ...
(Reading database ... 369589 files and directories currently installed.)
Preparing to unpack .../distro-info-data_0.28ubuntu0.8_all.deb ...
Unpacking distro-info-data (0.28ubuntu0.8) over (0.28ubuntu0.7) ...
Preparing to unpack .../wget_1.17.1-1ubuntu1.4_amd64.deb ...
Unpacking wget (1.17.1-1ubuntu1.4) over (1.17.1-1ubuntu1.3) ...
Preparing to unpack .../cups-browsed_1.8.3-2ubuntu3.4_amd64.deb ...
Failed to stop cups-browsed.service: Unit cups-browsed.service not loaded.
invoke-rc.d: initscript cups-browsed, action "stop" failed.
dpkg: warning: subprocess old pre-removal script returned error exit status 5
dpkg: trying script from the new package instead ...
Failed to stop cups-browsed.service: Unit cups-browsed.service not loaded.
invoke-rc.d: initscript cups-browsed, action "stop" failed.
dpkg: error processing archive /var/cache/apt/archives/cups-browsed_1.8.3-2ubuntu3.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 5
Preparing to unpack .../flashplugin-installer_29.0.0.171ubuntu0.16.04.1_amd64.deb ...
Unpacking flashplugin-installer (29.0.0.171ubuntu0.16.04.1) over (29.0.0.140ubuntu0.16.04.1) ...
Preparing to unpack .../linux-libc-dev_4.4.0-124.148_amd64.deb ...
Unpacking linux-libc-dev:amd64 (4.4.0-124.148) over (4.4.0-122.146) ...
Processing triggers for install-info (6.1.0.dfsg.1-5) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for update-notifier-common (3.168.8) ...
flashplugin-installer: processing...
flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20180508.1.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20180508.1.orig.tar.gz)
Get:1 [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20180508.1.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20180508.1.orig.tar.gz) [30.5 MB]
Fetched 30.5 MB in 3s (10.1 MB/s)                                              
Installing from local file /var/lib/update-notifier/package-data-downloads/partial/adobe-flashplugin_20180508.1.orig.tar.gz
Flash Plugin installed.
Errors were encountered while processing:
 /var/cache/apt/archives/cups-browsed_1.8.3-2ubuntu3.4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

In addition, the very last command you have gives:
Failed to start cups-browsed.service: Unit cups-browsed.service is not loaded properly: Invalid argument.
See system logs and 'systemctl status cups-browsed.service' for details.

So I did systemctl status cups-browsed.service and got this message:
&#9679; cups-browsed.service - Make remote CUPS printers available locally
   Loaded: error (Reason: Invalid argument)
   Active: inactive (dead)

May 09 11:57:03 Satellite-E45-B systemd[1]: cups-browsed.service: Service lacks 
May 09 11:57:04 Satellite-E45-B systemd[1]: cups-browsed.service: Service lacks
```

---

### Post by Xian on 2018-05-09
Let's try:

```
sudo dpkg-reconfigure cups
sudo dpkg-reconfigure cups-browsed
```

Now check running services:

```
service cups-browsed status
service cups status
```

If both show active (running) then good.
If not try to start them:

```
sudo service cups start
sudo service cups-browsed start
```

Check again to see if services now running:

```
service cups-browsed status
service cups status
```

If not then:

```
sudo apt-get install --reinstall cups cups-browsed cups-client cups-common cups-daemon cups-server-common hplip
```
```
sudo systemctl daemon-reload
```

```
sudo service cups start
sudo service cups-browsed start
```

Check again:

```
service cups-browsed status
service cups status
```

Now .... where do things stand?

---

### Post by chopra on 2018-05-10
Hi,
Thanks for the reply.  So, the first command led me to a screen that asked me to choose a communication backend, giving me options
lpd
socket
usb
snmp
dnssd

I chose the first on the list, and it exited. Second command lead to:
```
sudo dpkg-reconfigure cups-browsed 
```
```
Failed to stop cups-browsed.service: Unit cups-browsed.service not loaded.
```

Service cups status showed a message:
```
service cups status
```
```

&#9679; cups.service - CUPS Scheduler
   Loaded: loaded (/lib/systemd/system/cups.service; enabled; vendor preset: ena
   Active: active (running) since Thu 2018-05-10 10:21:27 EDT; 1min 47s ago
     Docs: man:cupsd(8)
 Main PID: 3731 (cupsd)
   CGroup: /system.slice/cups.service
           &#9492;&#9472;3731 /usr/sbin/cupsd -l

```
but, service, cups-browsed status showed:
```
service cups-browsed status
```
```

&#9679; cups-browsed.service - Make remote CUPS printers available locally
   Loaded: error (Reason: Invalid argument)
   Active: inactive (dead)

```
```
sudo service cups-browsed start
```
```

Failed to start cups-browsed.service: Unit cups-browsed.service is not loaded properly: Invalid argument.
See system logs and 'systemctl status cups-browsed.service' for details.

```
Here's the output from the last command:
```
sudo apt-get install --reinstall cups cups-browsed cups-client cups-common cups-daemon cups-server-common hplip
```

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-121 linux-headers-4.4.0-121-generic
  linux-image-4.4.0-121-generic linux-image-extra-4.4.0-121-generic
  linux-signed-image-4.4.0-121-generic
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  cups-browsed
1 upgraded, 0 newly installed, 6 reinstalled, 0 to remove and 0 not upgraded.
Need to get 1,320 kB/1,413 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 cups-daemon amd64 2.1.3-4ubuntu0.4 [302 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 cups-server-common all 2.1.3-4ubuntu0.4 [494 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 cups-client amd64 2.1.3-4ubuntu0.4 [133 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 cups amd64 2.1.3-4ubuntu0.4 [192 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 cups-common all 2.1.3-4ubuntu0.4 [134 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 hplip amd64 3.16.3+repack0-1 [65.6 kB]
Fetched 1,320 kB in 0s (2,781 kB/s)
Preconfiguring packages ...
(Reading database ... 401992 files and directories currently installed.)
Preparing to unpack .../cups-browsed_1.8.3-2ubuntu3.4_amd64.deb ...
Failed to stop cups-browsed.service: Unit cups-browsed.service not loaded.
invoke-rc.d: initscript cups-browsed, action "stop" failed.
dpkg: warning: subprocess old pre-removal script returned error exit status 5
dpkg: trying script from the new package instead ...
Failed to stop cups-browsed.service: Unit cups-browsed.service not loaded.
invoke-rc.d: initscript cups-browsed, action "stop" failed.
dpkg: error processing archive /var/cache/apt/archives/cups-browsed_1.8.3-2ubuntu3.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 5
Preparing to unpack .../cups-daemon_2.1.3-4ubuntu0.4_amd64.deb ...
Warning: Stopping cups.service, but it can still be activated by:
  cups.socket
Unpacking cups-daemon (2.1.3-4ubuntu0.4) over (2.1.3-4ubuntu0.4) ...
Preparing to unpack .../cups-server-common_2.1.3-4ubuntu0.4_all.deb ...
Unpacking cups-server-common (2.1.3-4ubuntu0.4) over (2.1.3-4ubuntu0.4) ...
Preparing to unpack .../cups-client_2.1.3-4ubuntu0.4_amd64.deb ...
Unpacking cups-client (2.1.3-4ubuntu0.4) over (2.1.3-4ubuntu0.4) ...
Preparing to unpack .../cups_2.1.3-4ubuntu0.4_amd64.deb ...
Unpacking cups (2.1.3-4ubuntu0.4) over (2.1.3-4ubuntu0.4) ...
Preparing to unpack .../cups-common_2.1.3-4ubuntu0.4_all.deb ...
Unpacking cups-common (2.1.3-4ubuntu0.4) over (2.1.3-4ubuntu0.4) ...
Preparing to unpack .../hplip_3.16.3+repack0-1_amd64.deb ...
Unpacking hplip (3.16.3+repack0-1) over (3.16.3+repack0-1) ...
Processing triggers for ufw (0.35-0ubuntu2) ...
Processing triggers for systemd (229-4ubuntu21.2) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for doc-base (0.10.7) ...
Processing 1 changed doc-base file...
Processing triggers for dbus (1.10.6-1ubuntu3.3) ...
Errors were encountered while processing:
 /var/cache/apt/archives/cups-browsed_1.8.3-2ubuntu3.4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Similar to before.  However, performing that exact same command a second time gives a shorter error:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-121 linux-headers-4.4.0-121-generic linux-image-4.4.0-121-generic linux-image-extra-4.4.0-121-generic linux-signed-image-4.4.0-121-generic
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  cups-browsed
1 upgraded, 0 newly installed, 6 reinstalled, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0 B/92.9 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
E: Internal Error, No file name for cups-daemon:amd64

```

Chopra

---

### Post by Xian on 2018-05-10
Making progress ... 

Just for documentation post any errors from the command below.
Looking for output that mentions partially configured packages.
```
sudo dpkg --audit
```

If you do get a hit then enter this terminal command:
```
sudo dpkg --configure --pending
```

Now run your apt-get dist-upgrade command. 

```
sudo apt-get dist-upgrade
```

Any change?

If still errors let's move on to the next steps.

```
sudo dpkg -i /var/cache/apt/archives/*.deb
sudo dpkg --configure -a
sudo apt-get install -f
```

Reboot your computer. Try the apt-get dist-upgrade command again. 


```
sudo apt-get dist-upgrade
```


Post back with results.

---

### Post by chopra on 2018-05-10
Okay, so the dpkg --audit command gave me the following output:
```

The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 cups                 Common UNIX Printing System(tm) - PPD/driver support, web
 cups-client          Common UNIX Printing System(tm) - client programs (SysV)
 cups-common          Common UNIX Printing System(tm) - common files
 cups-daemon          Common UNIX Printing System(tm) - daemon
 cups-server-common   Common UNIX Printing System(tm) - server common files
 hplip                HP Linux Printing and Imaging System (HPLIP)

```

next, the --configure --pending gave me:
```

Setting up cups-server-common (2.1.3-4ubuntu0.4) ...
Setting up cups-common (2.1.3-4ubuntu0.4) ...
Setting up cups-daemon (2.1.3-4ubuntu0.4) ...
Setting up cups-client (2.1.3-4ubuntu0.4) ...
Setting up cups (2.1.3-4ubuntu0.4) ...
Updating PPD files for cups ...
Setting up hplip (3.16.3+repack0-1) ...
Creating/updating hplip user account...

```

The dist-upgrade gave me the same error, so I went down to the next command:
sudo dpkg -i /var/cache/apt/archives/*.deb

and got a whole bunch of output, which I didn't paste all of, but it was laced with similar errors.  It ended with:
Errors were encountered while processing:
 /var/cache/apt/archives/cups-browsed_1.8.3-2ubuntu3.4_amd64.deb


I still followed the remaining directions, rebooted, and did the dist-upgrade again, and got the familiar error:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-121 linux-headers-4.4.0-121-generic
  linux-image-4.4.0-121-generic linux-image-extra-4.4.0-121-generic
  linux-signed-image-4.4.0-121-generic
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  cups-browsed libpulse-mainloop-glib0 libpulse0 libpulsedsp pulseaudio
  pulseaudio-esound-compat pulseaudio-module-x11 pulseaudio-utils
8 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,241 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 401992 files and directories currently installed.)
Preparing to unpack .../cups-browsed_1.8.3-2ubuntu3.4_amd64.deb ...
Failed to stop cups-browsed.service: Unit cups-browsed.service not loaded.
invoke-rc.d: initscript cups-browsed, action "stop" failed.
dpkg: warning: subprocess old pre-removal script returned error exit status 5
dpkg: trying script from the new package instead ...
Failed to stop cups-browsed.service: Unit cups-browsed.service not loaded.
invoke-rc.d: initscript cups-browsed, action "stop" failed.
dpkg: error processing archive /var/cache/apt/archives/cups-browsed_1.8.3-2ubuntu3.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 5
Preparing to unpack .../pulseaudio-esound-compat_1%3a8.0-0ubuntu3.10_amd64.deb ...
Unpacking pulseaudio-esound-compat (1:8.0-0ubuntu3.10) over (1:8.0-0ubuntu3.9) ...
Preparing to unpack .../libpulsedsp_1%3a8.0-0ubuntu3.10_amd64.deb ...
Unpacking libpulsedsp:amd64 (1:8.0-0ubuntu3.10) over (1:8.0-0ubuntu3.9) ...
Preparing to unpack .../pulseaudio-utils_1%3a8.0-0ubuntu3.10_amd64.deb ...
Unpacking pulseaudio-utils (1:8.0-0ubuntu3.10) over (1:8.0-0ubuntu3.9) ...
Preparing to unpack .../pulseaudio-module-x11_1%3a8.0-0ubuntu3.10_amd64.deb ...
Unpacking pulseaudio-module-x11 (1:8.0-0ubuntu3.10) over (1:8.0-0ubuntu3.9) ...
Preparing to unpack .../pulseaudio_1%3a8.0-0ubuntu3.10_amd64.deb ...
Unpacking pulseaudio (1:8.0-0ubuntu3.10) over (1:8.0-0ubuntu3.9) ...
Preparing to unpack .../libpulse-mainloop-glib0_1%3a8.0-0ubuntu3.10_amd64.deb ...
Unpacking libpulse-mainloop-glib0:amd64 (1:8.0-0ubuntu3.10) over (1:8.0-0ubuntu3.9) ...
Preparing to unpack .../libpulse0_1%3a8.0-0ubuntu3.10_amd64.deb ...
Unpacking libpulse0:amd64 (1:8.0-0ubuntu3.10) over (1:8.0-0ubuntu3.9) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for dbus (1.10.6-1ubuntu3.3) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Errors were encountered while processing:
 /var/cache/apt/archives/cups-browsed_1.8.3-2ubuntu3.4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Chopra

---

### Post by Xian on 2018-05-11
Now we need to focus on the single offending package: cups-browsed. 

Let's see if we can actually get that package correctly installed.

```
sudo apt-get clean
sudo apt-get install --reinstall cups-browsed
sudo dpkg-reconfigure cups-browsed
```

If this fails to install the package move on to:

```
sudo apt-get purge cups-browsed 
sudo apt-get install cups-browsed
```

If either of these works --- great. Reboot & run a dist-upgrade command.

If both fail then:

```
cd
sudo apt-get download cups-browsed
sudo dpkg --force-all -i cups-browsed
```

---

### Post by chopra on 2018-05-12
Okay, so I tried everything, and still got the same errors.
The apt-get download first gave me an error:

```
sudo apt-get download cups-browsed
```

```

Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 cups-browsed amd64 1.8.3-2ubuntu3.4 [92.9 kB]
Fetched 92.9 kB in 0s (241 kB/s)      

W: Can't drop privileges for downloading as file '/home/chopra/cups-browsed_1.8.3-2ubuntu3.4_amd64.deb' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)

```
I'm used to seeing similar errors with adobe and the permissions of the pseudo-user _apt, but I ran it again, and no errors.

Then the very last command on your list:
```
 sudo dpkg --force-all -i cups-browsed 
```
```

dpkg: error processing archive cups-browsed (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 cups-browsed

```

The auto complete was trying to get me to type the full package name, so that's what I tried next:
```
sudo dpkg --force-all -i cups-browsed_1.8.3-2ubuntu3.4_amd64.deb
```

This gave me the error:
```

(Reading database ... 401991 files and directories currently installed.)
Preparing to unpack cups-browsed_1.8.3-2ubuntu3.4_amd64.deb ...
Failed to stop cups-browsed.service: Unit cups-browsed.service not loaded.
invoke-rc.d: initscript cups-browsed, action "stop" failed.
dpkg: warning: subprocess old pre-removal script returned error exit status 5
dpkg: trying script from the new package instead ...
Failed to stop cups-browsed.service: Unit cups-browsed.service not loaded.
invoke-rc.d: initscript cups-browsed, action "stop" failed.
dpkg: error processing archive cups-browsed_1.8.3-2ubuntu3.4_amd64.deb (--install):
 subprocess new pre-removal script returned error exit status 5
Errors were encountered while processing:
 cups-browsed_1.8.3-2ubuntu3.4_amd64.deb

```

---

### Post by chopra on 2018-05-16
just another update:

I tried again running the commands, and after entering the command 
```
 sudo dpkg --force-all -i cups-browsed 
```

I got the message:
```

dpkg: error processing archive cups-browsed (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 cups-browsed

```

I'm not sure why I got a different output earlier, perhaps I copied and pasted wrong, but I maybe this might shed some light on the issue.

Chopra

---

### Post by chopra on 2018-05-21
Hi Guys,
I seem to have fixed the problem, thanks to this stack exhchange post.
[https://serverfault.com/questions/894878/subprocess-installed-pre-removal-script-returned-error-exit-status-5/894951#894951?newreg=0150ea1eee3b4d4998f05b76864219b7](https://serverfault.com/questions/894878/subprocess-installed-pre-removal-script-returned-error-exit-status-5/894951#894951?newreg=0150ea1eee3b4d4998f05b76864219b7)

```

sudo vi /var/lib/dpkg/info/cups-browsed.prerm

```

Editing the file, and replacing the line
```
invoke-rc.d cups-browsed stop || exit $?
```

with
```
invoke-rc.d cups-browsed stop || echo $? #exit $?
```

Then performing the commands:
```

sudo apt-get remove cups-browsed

sudo apt-get update

sudo apt-get clean

sudo apt-get install --reinstall cups-browsed

sudo apt-get dist-upgrade

sudo service cups-browsed start

```
The output of the command 

```
service cups-browsed status
```

Gives:

```

&#9679; cups-browsed.service - Make remote CUPS printers available locally
   Loaded: loaded (/lib/systemd/system/cups-browsed.service; enabled; vendor pre
   Active: active (running) since Mon 2018-05-21 19:00:32 EDT; 3s ago
 Main PID: 12090 (cups-browsed)
   CGroup: /system.slice/cups-browsed.service
           &#9492;&#9472;12090 /usr/sbin/cups-browsed

```

And the security update whose failure prompted this whole thread seems to have been done in the process. The update manager isn't asking me to do it, but I don't know how else to check if it was done.

However, the file I edited also seems to have reverted back to its old self in the process.

Chopra

---

### Post by oldos2er on 2018-05-21
Would you please mark your thread 'Solved' under Thread Tools at the top of the page? It'll help others who may be having the same problem.

Thanks.

---

### Post by #&amp;thj^% on 2018-05-21
Thanks that's very kind and helpful to others.
Now if you would mark it as Solved it will help even more people. :)
Good Work chopra ;)
Kind Regards
Ninja'd by oldos2er :)

---

### Post by chopra on 2018-05-22
Yes, and thanks to Xian for getting the ball rolling as well.
The only reason I waited to mark it as solved was that I was waiting to make sure the update request didn't re-appear later, just to be on the safe side.

---

