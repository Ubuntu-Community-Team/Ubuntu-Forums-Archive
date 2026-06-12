---
title: "Software updater apparently no longer works for Lubuntu 18.04.3 LTS"
date: 2020-05-12
forum: General Help
---

### Post by AbleTassie on 2020-05-12
When the Software Updater comes up on the taskbar for a scheduled update and I click on it, I have been getting the same dialogue box listing the same software to be updated in attached Screenshot 1 for months now. I think the dysfunction my be since I recently updated to Lubuntu 18.04.3 from Lubuntu 16.04 LTS. When I click in Update, it starts to load for a second or two and then the loading dialogue box disappears. It never asks for a password.

If I attempt to manually update by going to System Tools> Software Updater, I get the dialogue box in attached Screenshot 2 indicating failure to download repository information. It says to check my internet connection, but the connection is fine.

QUESTION: Any idea what is wrong?

Thanks,

A.

[ATTACH=CONFIG]285834[/ATTACH]

[ATTACH=CONFIG]285835[/ATTACH]

---

### Post by deadflowr on 2020-05-12
Did you look at what the terminal output shows for
```
sudo apt-get update
```

---

### Post by AbleTassie on 2020-05-15
deadflowr,

**Here is the output:**

able@able-Lenovo-IdeaPad-Y510:~$ sudo apt-get update
[sudo] password for able: 
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease
Ign:2 [http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu](http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu) bionic InRelease     
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]   
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [88.7 kB]    
Err:5 [http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu](http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu) bionic Release       
  404  Not Found [IP: 2001:67c:1560:8008::15 80]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB] 
Reading package lists... Done                                                  
E: The repository 'http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

---

### Post by monkeybrain20122 on 2020-05-15
> E: The repository 'http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu bionic Release' does not have a Release file.

That ppa no longer exists. So open software & update go to the tab other software, uncheck that ppa and reload. 

( Alternatively, check if there is an entry for it in /etc/apt/sources.list, if yes, edit it out, if not, check /etc/apt/sources.list.d and delete the file for the ppa. After that run
sudo apt update in the terminal.)

---

### Post by AbleTassie on 2020-05-15
I tried to cure the problem by a Terminal Command with Method 2 here 
[https://askubuntu.com/questions/1198312/sudo-apt-get-update-and-adding-a-repository-error](https://askubuntu.com/questions/1198312/sudo-apt-get-update-and-adding-a-repository-error)

and I ran sudo apt update in the terminal after using Method 2. I get a different output. The output from Terminal is below (including the earlier output requested by deadflwr). When I try to update, I still get essentially the same list of software in my screenshot attached to my original post that needs to be downloaded and installed so it looks like that did not cure the problem. 

**Terminal output (including the earlier output requested by deadflwr):**

able@able-Lenovo-IdeaPad-Y510:~$ sudo apt-get update
[sudo] password for able: 
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease
Ign:2 [http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu](http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu) bionic InRelease     
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]   
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [88.7 kB]    
Err:5 [http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu](http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu) bionic Release       
  404  Not Found [IP: 2001:67c:1560:8008::15 80]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB] 
Reading package lists... Done                                                  
E: The repository 'http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
able@able-Lenovo-IdeaPad-Y510:~$ ^C
able@able-Lenovo-IdeaPad-Y510:~$ sudo add-apt-repository -r ppa:lubuntu-desktop/ppa
[sudo] password for able: 
 tag:launchpad.net:2008:redacted
 More info: [https://launchpad.net/~lubuntu-desktop/+archive/ubuntu/ppa](https://launchpad.net/~lubuntu-desktop/+archive/ubuntu/ppa)
Press [ENTER] to continue or Ctrl-c to cancel removing it.

able@able-Lenovo-IdeaPad-Y510:~$ sudo apt-get update
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [88.7 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]        
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB]
Fetched 252 kB in 2s (126 kB/s)                                
Reading package lists... Done
able@able-Lenovo-IdeaPad-Y510:~$

---

### Post by AbleTassie on 2020-05-15
> **monkeybrain20122 said:**
> That ppa no longer exists. So open software & update go to the tab other software, uncheck that ppa and reload. 

( Alternatively, check if there is an entry for it in /etc/apt/sources.list, if yes, edit it out, if not, check /etc/apt/sources.list.d and delete the file for the ppa. After that run
sudo apt update in the terminal.)

Hi Monkeybrain,

I looked in other software and the ppa does not seem to be listed. But I looked for the ppa after I used Method 2 in the post I made above. I do not know if that would have made a difference or not in the ppa being listed.

A.

---

### Post by deadflowr on 2020-05-15
[s]PPAs are listed in a separate directory /etc/apt/sources.list.d/[/s]
(nevermind, monkeybrain20122 already mentioned that)

Seeing that you ran the remove command and the new update output shows no errors, 
you might as well try the Software Updater and see if it works correctly now.

---

### Post by AbleTassie on 2020-05-16
> **deadflowr said:**
> [s]PPAs are listed in a separate directory /etc/apt/sources.list.d/[/s]
(nevermind, monkeybrain20122 already mentioned that)

Seeing that you ran the remove command and the new update output shows no errors, 
you might as well try the Software Updater and see if it works correctly now.

deadflwr,

When I try to use the Software Updater I keep getting the same list of software as before to be downloaded and installed. The downloading progress box looks like it is downloading for a second or so and then it disappears. Given the fact that the software list is unchanged, it appears that it is not downloading and installing the software, but is aborting the download every time soon after the download starts. I have attached two screenshots that I just took showing the list(s), which appear to be the same each time.

I tried to download and install the list in the screenshot SoftwareUpdateTrouble3. But it seemed to abort soon after starting and then I activated the Software Updater again and I got the list in the screenshot SoftwareUpdateTrouble4. Even though I may not be getting error messages, the download and updating does not seem to be working.

Any idea what I should do?

Thanks,

A.

[ATTACH=CONFIG]285892[/ATTACH]

[ATTACH=CONFIG]285893[/ATTACH]

---

### Post by deadflowr on 2020-05-16
If you try clicking on Remind Me Later,
then go and try opening Software Updater anew,
does it open up directly to the same window or does it start by running a check first?

---

### Post by ajgreeny on 2020-05-16
What happens if you update in terminal rather than using the GUI?

Try 
sudo apt update
sudo apt upgrade

---

### Post by AbleTassie on 2020-05-16
> **deadflowr said:**
> If you try clicking on Remind Me Later,
then go and try opening Software Updater anew,
does it open up directly to the same window or does it start by running a check first?

It does a check first.

A.

---

### Post by AbleTassie on 2020-05-16
> **ajgreeny said:**
> What happens if you update in terminal rather than using the GUI?

Try 
sudo apt update
sudo apt upgrade

That seemed to largely work, because MUCH software was downloaded and installed.  Now when I use the Software Updater, the Software that needs to be updated is much different than before.

But the process was aborted. I will attempt to attach the Terminal  Output as a PDF file; it is too long to paste into this reply. I tried to  paste it in and got some kind of security message. Not sure it will work as there is a ? mark over the icon. 

Thanks,

A.

Abbreviated Terminal Output Excerpt:

  	 	 	 	   Preparing to unpack .../06-systemd_237-3ubuntu10.40_amd64.deb ...
 Unpacking systemd (237-3ubuntu10.40) over (237-3ubuntu10.33) ...
 Preparing to unpack .../07-libsystemd0_237-3ubuntu10.40_amd64.deb ...
 De-configuring libsystemd0:i386 (237-3ubuntu10.33) ...
 Unpacking libsystemd0:amd64 (237-3ubuntu10.40) over (237-3ubuntu10.33) ...
  
......     .......    .......   

Processing triggers for initramfs-tools (0.130ubuntu3.9) ...
 update-initramfs: Generating /boot/initrd.img-4.15.0-99-generic
 libdvd-pkg: Checking orig.tar integrity...
 /usr/src/libdvd-pkg/libdvdcss_1.4.2.orig.tar.bz2: OK
 libdvd-pkg: `apt-get check` failed, you may have broken packages. Aborting...
 able@able-Lenovo-IdeaPad-Y510:~$ 
  

[ATTACH]285897[/ATTACH]

---

### Post by deadflowr on 2020-05-17
Have you checked if the fix-broken package command fixes it
```
sudo apt-get install -f
```

---

### Post by ajgreeny on 2020-05-17
Can you tell us if this is an OS running virtually in VirtualBox, which from your PDF is what I suspect to be the case.

I also suspect if so that you are still using an old version of VBox, 5.2.34 which I haven't seen for a very long time now; I'm using VBox 6.1.8 very successfully.

Let's also see what happens if you run command ```
sudo rm /var/cache/apt/archives/libdvd-pkg
sudo apt install --reinstall libdvd-pkg
```which appears to be the problem package as far as I can see; perhaps the downloaded package was corrupt.

---

### Post by AbleTassie on 2020-05-19
> **deadflowr said:**
> Have you checked if the fix-broken package command fixes it
```
sudo apt-get install -f
```

I ran that command, it does not look like it did anything. The Terminal output is below. I was able to update manually via the terminal command a day or two ago. And the Software Updater said the Software was up to date. Now, however, there are a couple of packages to be added for updating, and I cannot add them using the Software Updater. It is the same old thing.

There also is no longer a Lubuntu Software Center to add and remove software. I guess the Synaptic Package Manager is supposed to do this function, but I cannot get it to come up. I just get a turning time wheel for a while after I try to bring it up, but then nothing.

Thanks,

A.

v=able@able-Lenovo-IdeaPad-Y510:~$ sudo apt-get install -f
[sudo] password for able: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
able@able-Lenovo-IdeaPad-Y510:~$

---

### Post by AbleTassie on 2020-05-19
> **ajgreeny said:**
> Can you tell us if this is an OS running virtually in VirtualBox, which from your PDF is what I suspect to be the case.

I also suspect if so that you are still using an old version of VBox, 5.2.34 which I haven't seen for a very long time now; I'm using VBox 6.1.8 very successfully.

Let's also see what happens if you run command ```
sudo rm /var/cache/apt/archives/libdvd-pkg
sudo apt install --reinstall libdvd-pkg
```which appears to be the problem package as far as I can see; perhaps the downloaded package was corrupt.

AJ,

I appreciate the advice you guys are giving me. If nothing else, I can update manually now using Terminal. 

Thanks,

A.

I am running this Lubuntu OS freestanding, it is not virtualized. I do have Virtualbox with this Lubuntu OS as the host and Windows XP as the guest. But that is how I am using Virtualbox.

I tried the terminal commands you suggested, but there was an aborting. I also tried the command that Terminal suggested when I ran your commands: sudo dpkg-reconfigure libdvd-pkg, but I got a weird looking DOS screen, and I thought it looked too dangerous to mess with. 

**The output for the commands you suggested is below:**

able@able-Lenovo-IdeaPad-Y510:~$ sudo rm /var/cache/apt/archives/libdvd-pkg
[sudo] password for able: 
rm: cannot remove '/var/cache/apt/archives/libdvd-pkg': No such file or directory
able@able-Lenovo-IdeaPad-Y510:~$ sudo apt install --reinstall libdvd-pkg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 7 not upgraded.
Need to get 14.9 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/multiverse amd64 libdvd-pkg all 1.4.2-1-1 [14.9 kB]
Fetched 14.9 kB in 2s (9,701 B/s)     
Preconfiguring packages ...
(Reading database ... 232606 files and directories currently installed.)
Preparing to unpack .../libdvd-pkg_1.4.2-1-1_all.deb ...
Unpacking libdvd-pkg (1.4.2-1-1) over (1.4.2-1-1) ...
Setting up libdvd-pkg (1.4.2-1-1) ...
libdvd-pkg: dpkg database is locked. You may need to use command "sudo dpkg-reconfigure libdvd-pkg".
libdvd-pkg: Building and installation of package(s) [libdvdcss2 libdvdcss-dev] postponed till after next APT operation.
libdvd-pkg: Checking orig.tar integrity...
/usr/src/libdvd-pkg/libdvdcss_1.4.2.orig.tar.bz2: OK
libdvd-pkg: `apt-get check` failed, you may have broken packages. Aborting...

---

### Post by ajgreeny on 2020-05-19
The weird looking dos screen you saw is the needed interaction that appears as libdvd-pkg attempts to deal with installing libdvdcss, which is the reason you need libdvd-pkg in the first place.

I can not remember the full process now but allow that  dos screen to fully complete what it's  trying to do and you should get through this process and overcome your problems.

---

### Post by AbleTassie on 2020-05-21
> **ajgreeny said:**
> The weird looking dos screen you saw is the needed interaction that appears as libdvd-pkg attempts to deal with installing libdvdcss, which is the reason you need libdvd-pkg in the first place.

I can not remember the full process now but allow that  dos screen to fully complete what it's  trying to do and you should get through this process and overcome your problems.

OK I ran  the Terminal command and the Terminal output is below. It looks like it worked, but I tried running Software Updater after and it still seems stuck. I will restart the PC and see if that makes a difference.

Later: Nope, even after restart the Software Updater still is unable to download and install updates. But, I used these Terminal Commands: sudo apt update
AND  sudo apt upgrade and was able to update for now.

Thanks,

A.

able@able-Lenovo-IdeaPad-Y510:~$ sudo dpkg-reconfigure libdvd-pkg
libdvd-pkg: Checking orig.tar integrity...
/usr/src/libdvd-pkg/libdvdcss_1.4.2.orig.tar.bz2: OK
libdvd-pkg: Unpacking and configuring...
libdvd-pkg: Building the package... (it may take a while)
libdvd-pkg: Build log will be saved to /usr/src/libdvd-pkg/libdvdcss2_1.4.2-1~local_amd64.build
Current: = cap_chown,cap_dac_override,cap_dac_read_search,cap_fowner,cap_fsetid,cap_kill,cap_setgid,cap_setuid,cap_setpcap,cap_linux_immutable,cap_net_bind_service,cap_net_broadcast,cap_net_admin,cap_net_raw,cap_ipc_lock,cap_ipc_owner,cap_sys_module,cap_sys_rawio,cap_sys_chroot,cap_sys_ptrace,cap_sys_pacct,cap_sys_admin,cap_sys_boot,cap_sys_nice,cap_sys_resource,cap_sys_time,cap_sys_tty_config,cap_mknod,cap_lease,cap_audit_write,cap_audit_control,cap_setfcap,cap_mac_override,cap_mac_admin,cap_syslog,cap_wake_alarm,cap_block_suspend,cap_audit_read+ep
Bounding set =cap_chown,cap_dac_override,cap_fowner,cap_wake_alarm,cap_block_suspend,cap_audit_read
Securebits: 024/0x14/5'b10100
 secure-noroot: no (unlocked)
 secure-no-suid-fixup: yes (unlocked)
 secure-keep-caps: yes (unlocked)
uid=0(root)
gid=0(root)
groups=0(root)
libdvd-pkg: Installing...
(Reading database ... 232606 files and directories currently installed.)
Preparing to unpack .../libdvdcss-dev_1.4.2-1~local_amd64.deb ...
Unpacking libdvdcss-dev:amd64 (1.4.2-1~local) over (1.4.0-1~local) ...
Preparing to unpack .../libdvdcss2_1.4.2-1~local_amd64.deb ...
Unpacking libdvdcss2:amd64 (1.4.2-1~local) over (1.4.0-1~local) ...
Setting up libdvdcss2:amd64 (1.4.2-1~local) ...
Setting up libdvdcss-dev:amd64 (1.4.2-1~local) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
able@able-Lenovo-IdeaPad-Y510:~$

---

