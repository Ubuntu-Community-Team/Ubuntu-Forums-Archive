---
title: "Unmet dependencies - g15 i think."
date: 2013-08-09
forum: General Help
---

### Post by anotherssodisabledname on 2013-08-09
Hello;

for some reason during a recent update my xubuntu laptop has decided it has unmet dependencies.  The error is posted below:

```
The following packages have unmet dependencies. lcdproc-extra-drivers : Depends: libg15daemon-client1 but it is not installed
E: Unmet dependencies. Try using -f.

```

I have tried apt-get -f install and the following is the result:

```
Do you want to continue [Y/n]? y(Reading database ... 347718 files and directories currently installed.)
Unpacking libg15daemon-client1 (from .../libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libg15daemon_client.so.1.0.2', which is also in package libg15daemon-client 1.9.5.4-0~svn529gnome15
Processing triggers for man-db ...


Errors were encountered while processing:
 /var/cache/apt/archives/libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I am not sure what sparked this off, but it is annoying me to try and fix it.  

I have tried the following things as well:

sudo apt-get autoclean

sudo apt-get clean

sudo apt-get autoremove
Any help greatly received with this problem, I remember spending months a few years ago trying to fix broken dependencies and never really understanding the process.

Andy

---

### Post by slickymaster on 2013-08-09
Try the following:```
sudo dpkg --configure -a
```If that doesn't work, try:```
sudo dpkg -i /var/cache/apt/archives/libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb
```

---

### Post by ian-weisser on 2013-08-09
> **Andy_hawkes said:**
> ```
The following packages have unmet dependencies.[COLOR=#ff0000] lcdproc-extra-drivers[/COLOR] : Depends: libg15daemon-client1 but it is not installed
[...]
dpkg: error processing /var/cache/apt/archives/libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libg15daemon_client.so.1.0.2', which is also in package libg15daemon-client 1.9.5.4-0~svn529gnome15

```

Looks like you added a PPA or otherwise manually updated the lcdproc package (and it's dependencies).

The non-Ubuntu package you are trying to install is trying to duplicate a package that is already installed. The naming schemes are different (libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb vs libg15daemon-client 1.9.5.4-0~svn529gnome15) , apt cannot tell which one it should use.

The easiest way to fix the issue is usually to disable the PPA.

---

### Post by anotherssodisabledname on 2013-08-10
Thanks for the replies, so dpkg --configure -a gives this:

```
dpkg: dependency problems prevent configuration of lcdproc-extra-drivers: lcdproc-extra-drivers depends on libg15daemon-client1; however:
  Package libg15daemon-client1 is not installed.


dpkg: error processing lcdproc-extra-drivers (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 lcdproc-extra-drivers

```

```

sudo dpkg -i /var/cache/apt/archives/libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb
(Reading database ... 347718 files and directories currently installed.)
Unpacking libg15daemon-client1 (from .../libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb (--install):
 trying to overwrite '/usr/lib/libg15daemon_client.so.1.0.2', which is also in package libg15daemon-client 1.9.5.4-0~svn529gnome15
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb

```

How can i tell which PPA to disable from my list?

---

### Post by ian-weisser on 2013-08-10
If you remember which PPA you added that is causing the problem (for example, banshee), then disable that one.

If you don't know which PPA requires lcdproc, then disable them ALL.
Then reenable each -one at a time- and update/upgrade after each until you find the one that causes the breakage. Disable that one permanently.

Remember to report the problem to the broken PPA maintainer. They won't know unless you tell them.

---

### Post by anotherssodisabledname on 2013-08-10
Thanks.  It might actually be banshee as that was a recent install! If not i will disable all and then try one by one as you suggest.  Thanks for the help!

---

### Post by anotherssodisabledname on 2013-08-12
Ok so i have missed something.  I disabled all the sources in Ubuntu software center software sources,  did an apt get update / upgrade and still had the same errors. Where else should I disable the sources? Thanks

---

### Post by slickymaster on 2013-08-12
> **Andy_hawkes said:**
> Thanks for the replies, so dpkg --configure -a gives this:

```
[COLOR=#ff0000]dpkg: dependency problems prevent configuration of lcdproc-extra-drivers: lcdproc-extra-drivers depends on libg15daemon-client1; however:
  Package libg15daemon-client1 is not installed.[/COLOR]


dpkg: error processing lcdproc-extra-drivers (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 lcdproc-extra-drivers

```

```

sudo dpkg -i /var/cache/apt/archives/libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb
(Reading database ... 347718 files and directories currently installed.)
Unpacking libg15daemon-client1 (from .../libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb (--install):
 trying to overwrite '/usr/lib/libg15daemon_client.so.1.0.2', which is also in package libg15daemon-client 1.9.5.4-0~svn529gnome15
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb

```

How can i tell which PPA to disable from my list?

Install libg15daemon-client1:```
sudo apt-get install libg15daemon-client1
```then run:```
sudo dpkg --configure -a
```

---

### Post by anotherssodisabledname on 2013-08-12
I tried that, i have even downloaded the package and tried to run it manually but end up with the following error code:

```

Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  libg15daemon-client1
0 upgraded, 1 newly installed, 0 to remove and 175 not upgraded.
1 not fully installed or removed.
Need to get 0 B/12.8 kB of archives.
After this operation, 62.5 kB of additional disk space will be used.
(Reading database ... 347718 files and directories currently installed.)
Unpacking libg15daemon-client1 (from .../libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libg15daemon_client.so.1.0.2', which is also in package libg15daemon-client 1.9.5.4-0~svn529gnome15
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by slickymaster on 2013-08-12
Can you please post the output of:```
sudo dpkg --audit
```

---

### Post by anotherssodisabledname on 2013-08-13
```

The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 lcdproc-extra-drivers extra drivers for the LCD display driver daemon

```

Is the output of dpgk --audit.

---

### Post by slickymaster on 2013-08-13
Run the following```
sudo dpkg --configure lcdproc-extra-drivers
```

---

### Post by anotherssodisabledname on 2013-08-13
```

dpkg: dependency problems prevent configuration of lcdproc-extra-drivers:
 lcdproc-extra-drivers depends on libg15daemon-client1; however:
  Package libg15daemon-client1 is not installed.


dpkg: error processing lcdproc-extra-drivers (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 lcdproc-extra-drivers

```

Was the next output. Thanks for your help so far

---

### Post by slickymaster on 2013-08-13
Don't give up on it just yet.

Can you please post the output of:```
apt-cache policy libg15daemon-client1
```
If it's something like```
libg15daemon-client1:
  [COLOR=#ff0000]Installed: (none)[/COLOR]
  Candidate: 1.9.5.3-8.2ubuntu2
  Version table:
     1.9.5.3-8.2ubuntu2 0
        500 http://pt.archive.ubuntu.com/ubuntu/ saucy/universe i386 Packages

```then let's try with dpkg and not with apt-get```
[COLOR=#333333][FONT=Ubuntu]sudo dpkg -i /var/cache/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]apt/archives/[/FONT][/COLOR]libg15daemon-client1
```

---

### Post by anotherssodisabledname on 2013-08-14
Ok in order, apt-cache policy gives:
```

libg15daemon-client1:
  Installed: (none)
  Candidate: 1.9.5.3-8.2ubuntu2
  Version table:
     1.9.5.3-8.2ubuntu2 0
        500 http://ubuntu.mirrors.isu.net.sa/ubuntu/ raring/universe amd64 Packages

```

the dpkg without apt didnt work as the file wasnt there, i did tab out the following file though: libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.debso figured why not try and install that, the following was the output:
```

(Reading database ... 347718 files and directories currently installed.)
Unpacking libg15daemon-client1 (from .../libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb (--install):
 trying to overwrite '/usr/lib/libg15daemon_client.so.1.0.2', which is also in package libg15daemon-client 1.9.5.4-0~svn529gnome15
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb

```

---

### Post by geekyhawkes on 2013-08-14
At least I have my sso user name faff sorted now!

---

### Post by slickymaster on 2013-08-14
Ok, let's try it differently. Open a terminal and run the following:
```
cd ~
wget -c [http://ubuntu.mirrors.isu.net.sa/ubuntu//pool/universe/g/g15daemon/libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb](http://ubuntu.mirrors.isu.net.sa/ubuntu//pool/universe/g/g15daemon/libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb)
sudo dpkg -i ~/libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb
sudo cp -v ~/libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb /var/cache/apt/archives/
rm ~/libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb
sudo dpkg --configure -a
```

---

### Post by geekyhawkes on 2013-08-15
SO the wget worked ok, but when i tried the dpkg -i I got the following error:

```

(Reading database ... 347718 files and directories currently installed.)
Unpacking libg15daemon-client1 (from .../libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb) ...
dpkg: error processing /home/geeky/libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb (--install):
 trying to overwrite '/usr/lib/libg15daemon_client.so.1.0.2', which is also in package libg15daemon-client 1.9.5.4-0~svn529gnome15
Processing triggers for man-db ...
Errors were encountered while processing:
 /home/geeky/libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb

```

---

### Post by slickymaster on 2013-08-16
It's seems to me that problem could had been caused by the fact that some of the installation scripts were aborted due to problems with g15daemon itself, during those updates you mentioned on your OP. So what you can try is to purge g15daemon, thus removing it and its config files and reinstall it again.
To do it, you'll have to run the following commands, one at a time:```
sudo apt-get purge g15daemon
cd ~
wget -c http://ubuntu.mirrors.isu.net.sa/ubuntu//pool/universe/g/g15daemon/g15daemon_1.9.5.3-8.2ubuntu2_amd64.deb
sudo dpkg -i ~/g15daemon_1.9.5.3-8.2ubuntu2_amd64.deb
sudo cp -v ~/g15daemon_1.9.5.3-8.2ubuntu2_amd64.deb /var/cache/apt/archives/
rm ~/g15daemon_1.9.5.3-8.2ubuntu2_amd64.deb
sudo dpkg --configure -a
```
Then, if everything runs without errors, try:```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by geekyhawkes on 2013-08-20
```

Package 'g15daemon' is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 lcdproc-extra-drivers : Depends: libg15daemon-client1 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
geeky@Taylor:~$ wget -c http://ubuntu.mirrors.isu.net.sa/ubuntu//pool/universe/g/g15daemon/g15daemon_1.9.5.3-8.2ubuntu2_amd64.deb
--2013-08-20 20:06:16--  http://ubuntu.mirrors.isu.net.sa/ubuntu//pool/universe/g/g15daemon/g15daemon_1.9.5.3-8.2ubuntu2_amd64.deb
Resolving ubuntu.mirrors.isu.net.sa (ubuntu.mirrors.isu.net.sa)... 212.26.18.8
Connecting to ubuntu.mirrors.isu.net.sa (ubuntu.mirrors.isu.net.sa)|212.26.18.8|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 35790 (35K) [text/plain]
Saving to: &#8216;g15daemon_1.9.5.3-8.2ubuntu2_amd64.deb&#8217;

100%[======================================>] 35,790      33.5KB/s   in 1.0s   

2013-08-20 20:06:21 (33.5 KB/s) - &#8216;g15daemon_1.9.5.3-8.2ubuntu2_amd64.deb&#8217; saved [35790/35790]

geeky@Taylor:~$ sudo dpkg -i ~/g15daemon_1.9.5.3-8.2ubuntu2_amd64.deb
(Reading database ... 347718 files and directories currently installed.)
Unpacking g15daemon (from .../g15daemon_1.9.5.3-8.2ubuntu2_amd64.deb) ...
dpkg: dependency problems prevent configuration of g15daemon:
 g15daemon depends on libg15daemon-client1 (= 1.9.5.3-8.2ubuntu2); however:
  Package libg15daemon-client1 is not installed.

dpkg: error processing g15daemon (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Errors were encountered while processing:
 g15daemon

```

this was the output this time.

---

### Post by slickymaster on 2013-08-21
Hmm, back to square one, again.

Let's try another approach. First remove any cached packages which may be causing problems:```
sudo rm -f /var/cache/apt/archives/*
```update your repositories```
sudo apt-get update
```try to reinstall any pending installations```
sudo dpkg --configure -a
```force the installation of pending installations```
sudo apt-get -f install
```and finally upgrade the system```
sudo apt-get upgrade -y
```

---

### Post by geekyhawkes on 2013-08-21
sudo dpkg --configure -a gave the following:

```

dpkg: dependency problems prevent configuration of g15daemon:
 g15daemon depends on libg15daemon-client1 (= 1.9.5.3-8.2ubuntu2); however:
  Package libg15daemon-client1 is not installed.

dpkg: error processing g15daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lcdproc-extra-drivers:
 lcdproc-extra-drivers depends on libg15daemon-client1; however:
  Package libg15daemon-client1 is not installed.

dpkg: error processing lcdproc-extra-drivers (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 g15daemon
 lcdproc-extra-drivers

```

This is driving me crazy!  I reinstalled last time this happened on my old machine, but that seems bit extreme.

---

### Post by slickymaster on 2013-08-21
Before moving into drastic measures, such as reinstalling, there's still something you could try, which is to reinstall using this command:```
sudo apt-get install --reinstall --no-install-recommends libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb g15daemon lcdproc-extra-drivers
```

---

### Post by geekyhawkes on 2013-08-23
```

E: Unable to locate package libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb
E: Couldn't find any package by regex 'libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb'

```

I have both of these files locally, is there a way i can force the install to use the locally downloaded versions?

EDIT: I also tried copying the files to /var/cache/apt but got the same error

---

### Post by geekyhawkes on 2013-08-27
Anyone able to keep trying to help me with this problem?  I seem to be going around in circles!

---

### Post by ian-weisser on 2013-08-27
> **anotherssodisabledname said:**
> 
```
Do you want to continue [Y/n]? y(Reading database ... 347718 files and directories currently installed.)
Unpacking libg15daemon-client1 (from .../libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/[COLOR=#ff0000]libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb[/COLOR] (--unpack):
 trying to overwrite '/usr/lib/libg15daemon_client.so.1.0.2', which is also in package [COLOR=#ff0000]libg15daemon-client 1.9.5.4-0~svn529gnome15[/COLOR]

```



1) Try removing the Gnome package. 
```
sudo dpkg --remove [COLOR=#ff0000]libg15daemon-client[/COLOR]
```

2) If that works, then try installing the Ubuntu package.
```
sudo apt-get install libg15daemon-client1
```


You still have not figured out what you added that pulled in the Gnome package?
We really cannot figure that out for you. You must use the **apt-cache rdepends** command and work your way up the chain of dependencies until you recognize a change you made. (Hey! I remember installing that.)

Since you don't know where you got the Gnome package from, there is no assurance you won't erroneously reinstall it.
There is also no assurance that other strange packages are not lurking in your system, waiting to break your system again.
Tip: Don't use PPAs or third-party repositories, and keep your repo list clean.

---

### Post by geekyhawkes on 2013-08-29
Thanks for the reply.  Getting rid of the package is causing me some problems:

```

dpkg: dependency problems prevent removal of libg15daemon-client:
 libg15daemon-client-dev depends on libg15daemon-client (= 1.9.5.4-0~svn529gnome15).

dpkg: error processing libg15daemon-client (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 libg15daemon-client

```

---

### Post by ian-weisser on 2013-08-29
Try looking for all the dependencies. Try the following command, which WON'T actually remove anything.

```
sudo apt-get remove --simulate libg15daemon-client
```

Look carefully at the list of everything removed.
If none of your favorite applications are on the list, then run the command for real (do it omitting the --simulate flag). 
Test your package manager with **sudo apt-get update** and **sudo apt-get upgrade**. If it works, then your problem is fixed.

If any of your favorite applications are on the list, or if the list is very long, then show us the list before running the command for real.

---

### Post by geekyhawkes on 2013-08-30
Thanks for the reply, i am getting the same circular error as earlier in the post, cant do anything as dependancy not met, cant fix dependancy as its broken! 

```

You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 g15daemon : Depends: libg15daemon-client1 (= 1.9.5.3-8.2ubuntu2) but it is not going to be installed
 lcdproc-extra-drivers : Depends: libg15daemon-client1 but it is not going to be installed
 libg15daemon-client-dev : Depends: libg15daemon-client (= 1.9.5.4-0~svn529gnome15) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by ian-weisser on 2013-08-30
Seems like time to drag out the heavier, more dangerous tools.
If possible, back up your data.

Try:
```
sudo dpkg --force-depends --remove libg15daemon-client
```
The --force-depends flag overrides the dpkg dependency error that failed the previous try, converting the errors into warnings. Errors fail, warnings succeed. Look at the output carefully to see what happens.


If that works, then:
```
sudo apt-get install libg15daemon-client1
```

---

### Post by geekyhawkes on 2013-08-30
```

dpkg: libg15daemon-client: dependency problems, but removing anyway as you requested:
 libg15daemon-client-dev depends on libg15daemon-client (= 1.9.5.4-0~svn529gnome15).

(Reading database ... 347740 files and directories currently installed.)
Removing libg15daemon-client ...
geeky@Taylor:~$ sudo apt-get install libg15daemon-client1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 libg15daemon-client-dev : Depends: libg15daemon-client (= 1.9.5.4-0~svn529gnome15) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
geeky@Taylor:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libg15daemon-client1
The following packages will be REMOVED
  libg15daemon-client-dev
The following NEW packages will be installed
  libg15daemon-client1
0 upgraded, 1 newly installed, 1 to remove and 201 not upgraded.
2 not fully installed or removed.
Need to get 12.8 kB of archives.
After this operation, 4,096 B of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libg15daemon-client1
Install these packages without verification [y/N]? y
Get:1 http://ubuntu.mirrors.isu.net.sa/ubuntu/ raring/universe libg15daemon-client1 amd64 1.9.5.3-8.2ubuntu2 [12.8 kB]
Fetched 12.8 kB in 2s (5,273 B/s)             
(Reading database ... 347735 files and directories currently installed.)
Unpacking libg15daemon-client1 (from .../libg15daemon-client1_1.9.5.3-8.2ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
(Reading database ... 347744 files and directories currently installed.)
Removing libg15daemon-client-dev ...
Setting up libg15daemon-client1 (1.9.5.3-8.2ubuntu2) ...
Setting up g15daemon (1.9.5.3-8.2ubuntu2) ...
Starting g15daemon: .../dev/input/uinput not found ...invoke-rc.d: initscript g15daemon, action "start" failed.
dpkg: error processing g15daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up lcdproc-extra-drivers (0.5.5-2) ...
No apport report written because MaxReports has already been reached
                                                                    Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 g15daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Not sure where this leaves me....

---

### Post by ian-weisser on 2013-08-30
You have discovered a separate bug, unrelated to your original problem: [https://bugs.launchpad.net/ubuntu/+source/g15daemon/+bug/570245](https://bugs.launchpad.net/ubuntu/+source/g15daemon/+bug/570245) . But we need to fix it, too.
Your original problem of an incompatible-architecture library is solved.

You have two options:
1) We can try the workaround in the bug report to install g15daemon. Once it installs properly, your package manager should start working properly again.

2) We can uninstall g15daemon to get your package manager working again. Then we can install g15daemon and play with the workaround.

I recommend #2, unless you really need g15daemon for some hardware interface. Getting your package manager working properly again is very important.

The workaround in the bug report is to edit the file /etc/init.d/g15daemon (using sudo).
Around lines 63 and 95, edit the strings "/dev/input/uinput" to "/dev/uinput"

Which option will you feel more comfortable doing?

---

### Post by geekyhawkes on 2013-09-09
So i tried editing the /etc/init.d/g15daemon file without removing g15daemon, but i am still having some of the same issues.  Do i need to remove it and then try again?  Is it a full purge removal or just apt-get remove i need to do? 

Thanks for the help, and great spot on the bug!

---

