---
title: "Unable to run apt-get upgrade"
date: 2015-11-25
forum: General Help
---

### Post by nate-sanders on 2015-11-25
I've been trying to research this myself but I'm stuck in one of those infinite-loops where a package can't install because of another issue, and I can't resolve the issue because of the first problem. Super exciting.

- Ubuntu 12.04 LTS, 64-bit
- Linux [removed] 3.2.0-90-generic #128-Ubuntu SMP Fri Aug 14 21:43:58 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
- cat /etc/debian_version
  wheezy/sid

Showing there are no disk issues:
```
$ df -lh
Filesystem               Size  Used Avail Use% Mounted on
/dev/mapper/rootvg-root   21G   12G  8.3G  58% /
udev                     7.9G   12K  7.9G   1% /dev
tmpfs                    1.6G  1.7M  1.6G   1% /run
none                     5.0M     0  5.0M   0% /run/lock
none                     7.9G   76K  7.9G   1% /run/shm
/dev/mapper/rootvg-tmp3   16G  182M   15G   2% /tmp
/dev/mapper/rootvg-boot  1.4G  493M  806M  38% /boot
/dev/mapper/rootvg-usr    14G   12G  1.3G  91% /usr
/dev/mapper/rootvg-var   2.9G  1.4G  1.3G  52% /var
/dev/mapper/rootvg-home  3.6T  3.0T  359G  90% /home
```

```
$ df -li
Filesystem                 Inodes   IUsed     IFree IUse% Mounted on
/dev/mapper/rootvg-root   1357376  153488   1203888   12% /
udev                      2050267     630   2049637    1% /dev
tmpfs                     2053386     654   2052732    1% /run
none                      2053386       7   2053379    1% /run/lock
none                      2053386       4   2053382    1% /run/shm
/dev/mapper/rootvg-tmp3   1048576     117   1048459    1% /tmp
/dev/mapper/rootvg-boot    355416     312    355104    1% /boot
/dev/mapper/rootvg-usr     884448  503758    380690   57% /usr
/dev/mapper/rootvg-var     186944   20609    166335   12% /var
/dev/mapper/rootvg-home 239468544 2696244 236772300    2% /home
```

apt-get update runs with no problems

```
$ apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-headers-generic : Depends: linux-headers-3.2.0-92-generic but it is not installed
 linux-headers-server : Depends: linux-headers-3.2.0-92-generic but it is not installed
 linux-server : Depends: linux-image-server (= 3.2.0.92.106) but 3.2.0.94.108 is installed
 postgresql-client-9.1 : Breaks: postgresql-9.1 (< 9.1.19-0ubuntu0.12.04) but 9.1.18-0ubuntu0.12.04 is installed
 postgresql-contrib-9.1 : Depends: postgresql-9.1 (= 9.1.19-0ubuntu0.12.04) but 9.1.18-0ubuntu0.12.04 is installed
E: Unmet dependencies. Try using -f.
```

```
$ apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-image-3.2.0-89-generic linux-headers-3.2.0-70-generic linux-headers-3.2.0-86-generic
  linux-headers-3.2.0-70 linux-headers-3.2.0-84 linux-headers-3.2.0-86 linux-headers-3.2.0-87
  linux-headers-3.2.0-88 linux-headers-3.2.0-89 linux-image-3.2.0-84-generic
  linux-headers-3.2.0-89-generic linux-image-3.2.0-87-generic linux-headers-3.2.0-84-generic foreman
  linux-headers-3.2.0-87-generic linux-image-3.2.0-88-generic linux-headers-3.2.0-88-generic
  linux-image-3.2.0-70-generic linux-image-3.2.0-86-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-generic linux-headers-server linux-server postgresql-9.1
Suggested packages:
  oidentd ident-server locales-all
The following packages will be upgraded:
  linux-headers-generic linux-headers-server linux-server postgresql-9.1
4 upgraded, 0 newly installed, 0 to remove and 81 not upgraded.
5 not fully installed or removed.
Need to get 0 B/4,324 kB of archives.
After this operation, 8,192 B of additional disk space will be used.
Do you want to continue [Y/n]? Y

Traceback (most recent call last):
  File "/usr/bin/apt-listchanges", line 237, in <module>
    main()
  File "/usr/bin/apt-listchanges", line 48, in main
    debs = apt_listchanges.read_apt_pipeline(config)
  File "/usr/share/apt-listchanges/apt_listchanges.py", line 83, in read_apt_pipeline
    return map(lambda pkg: filenames[pkg], order)
  File "/usr/share/apt-listchanges/apt_listchanges.py", line 83, in <lambda>
    return map(lambda pkg: filenames[pkg], order)
KeyError: 'linux-headers-generic'
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-3.2.0-92-generic; however:
  Package linux-headers-3.2.0-92-generic is not installed.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-server:
 linux-headers-server depends on linux-headers-3.2.0-92-generic; however:
  Package linux-headers-3.2.0-92-generic is not installed.
dpkg: error processing linux-headers-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.92.106); however:
  Version of linux-image-server on system is 3.2.0.94.108.
 linux-server depends on linux-headers-server (= 3.2.0.92.106); however:
  Package linux-headers-server is not configured yet.
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                      No apport report written because MaxReports is reached already
                                                                                    dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postgresql-9.1:
 postgresql-client-9.1 (9.1.19-0ubuntu0.12.04) breaks postgresql-9.1 (<< 9.1.19-0ubuntu0.12.04) and is installed.
  Version of postgresql-9.1 to be configured is 9.1.18-0ubuntu0.12.04.
dpkg: error processing postgresql-9.1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postgresql-contrib-9.1:
 postgresql-contrib-9.1 depends on postgresql-9.1 (= 9.1.19-0ubuntu0.12.04); however:
  Version of postgresql-9.1 on system is 9.1.18-0ubuntu0.12.04.
dpkg: error processing postgresql-contrib-9.1 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                      Errors were encountered while processing:
 linux-headers-generic
 linux-headers-server
 linux-server
 postgresql-9.1
 postgresql-contrib-9.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

So the common error above is:
```
 linux-headers-server depends on linux-headers-3.2.0-92-generic; however:
  Package linux-headers-3.2.0-92-generic is not installed.
```

So I try to install linux-headers-3.2.0-92-generic and get more errors

```
$ apt-get install linux-headers-3.2.0-92-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-server : Depends: linux-image-server (= 3.2.0.92.106) but 3.2.0.94.108 is to be installed
 postgresql-client-9.1 : Breaks: postgresql-9.1 (< 9.1.19-0ubuntu0.12.04) but 9.1.18-0ubuntu0.12.04 is to be installed
 postgresql-contrib-9.1 : Depends: postgresql-9.1 (= 9.1.19-0ubuntu0.12.04) but 9.1.18-0ubuntu0.12.04 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

Which puts me back to running -f install, which throws errors.

apt-get autoremove fails
apt-get purge linux-image-<versions> fails

Suggestions?

---

### Post by furtom on 2015-11-25
It seems the linux-headers and linux-server meta packages are depending on kernels that have been unistalled. This is odd.

try:
```
sudo dpkg --configure -a
```

If that doesn't work either, look in **/var/lib/dpkg/status** for the offending packages and remove the references to it (be very careful).

---

### Post by ajgreeny on 2015-11-25
Thread moved to the Other OSs ->Debian, which is what this seems to be.

If I'm wrong let us know.

---

### Post by nate-sanders on 2015-11-25
This is Ubuntu 12.04 as stated in my original post

$ cat /etc/motd
Welcome to Ubuntu 12.04.5 LTS (GNU/Linux 3.2.0-90-generic x86_64)

If you are confused by the output of /etc/debian_version, I'm quite surprised that should need to be explained here. Unless I'm missing something else here and my system really did get contaminated (I have no memory of doing such a thing, and apt sources show no debian repo's)

---

### Post by howefield on 2015-11-26
Thread moved back to the "*General Help*" forum and tidied up.

cat /etc/debian_version is a legitimate command/file in Ubuntu.

---

### Post by ian-weisser on 2015-11-26
df and df -i show that you don't have a disk space issue. Nor do you seem to have 'no space left on device' errors. So far, so good.

Run **sudo apt-get autoremove**, as the system is begging you to do, to clean out all those old kernel packages.

Run **sudo apt-get clean** to empty your package cache, so the system is forced to download new versions.

Decide between postgresql-client-9.1 and postgresql-9.1. They break each other, as your sytem is telling you each time; you cannot install both. Uninstall one or both - you can easily reinstall one after your package manager is working smoothly again. Run autoremove again to clean out old dependencies.

Then **sudo apt-get install --reinstall linux-headers-generic** to update the old version of that package.

That should clean up most of your issues. Then we can tackle what remains.

---

### Post by nate-sanders on 2015-11-26
so I nuked postgresql and tried your suggestions, but still I cannot use apt-get. It just fails with the same output. So I started focusing on using dpkg only (and used it to purge postresql). What did seem to get me a little further was looking back on what furtom had said:

```
$ dpkg --configure -a
dpkg: dependency problems prevent configuration of linux-headers-server:
 linux-headers-server depends on linux-headers-3.2.0-92-generic; however:
  Package linux-headers-3.2.0-92-generic is not installed.
dpkg: error processing linux-headers-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.92.106); however:
  Version of linux-image-server on system is 3.2.0.94.108.
 linux-server depends on linux-headers-server (= 3.2.0.92.106); however:
  Package linux-headers-server is not configured yet.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-3.2.0-92-generic; however:
  Package linux-headers-3.2.0-92-generic is not installed.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-server
 linux-server
 linux-headers-generic

```

So I found linux-headers-server 3.2.0.92.106 (amd64 binary) and linux-headers-3.2.0-92-generic_3.2.0-92.131 on launchpad.net 
```

$ dpkg -i linux-headers-server_3.2.0.92.106_amd64.deb linux-headers-3.2.0-92-generic_3.2.0-92.131_amd64.deb
(Reading database ... 473031 files and directories currently installed.)
Preparing to replace linux-headers-server 3.2.0.92.106 (using linux-headers-server_3.2.0.92.106_amd64.deb) ...
Unpacking replacement linux-headers-server ...
Unpacking linux-headers-3.2.0-92-generic (from linux-headers-3.2.0-92-generic_3.2.0-92.131_amd64.deb) ...
Setting up linux-headers-3.2.0-92-generic (3.2.0-92.131) ...
Examining /etc/kernel/header_postinst.d.
Setting up linux-headers-server (3.2.0.92.106) ...

```


and reran apt-get -f install, and almost..

```
KeyError: 'linux-server'
(Reading database ... 481196 files and directories currently installed.)
Preparing to replace linux-headers-server 3.2.0.92.106 (using .../linux-headers-server_3.2.0.94.108_amd64.deb) ...
Unpacking replacement linux-headers-server ...
Setting up linux-headers-generic (3.2.0.92.106) ...
Setting up linux-headers-server (3.2.0.94.108) ...
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.92.106); however:
  Version of linux-image-server on system is 3.2.0.94.108.
 linux-server depends on linux-headers-server (= 3.2.0.92.106); however:
  Version of linux-headers-server on system is 3.2.0.94.108.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

rerun dpkg --configure

```
$ dpkg --configure -a
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.92.106); however:
  Version of linux-image-server on system is 3.2.0.94.108.
 linux-server depends on linux-headers-server (= 3.2.0.92.106); however:
  Version of linux-headers-server on system is 3.2.0.94.108.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:

```

Wait, didn't I just install version .106?

```
$ dpkg -l linux-image-server
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                Version             Description
+++-===================-===================-======================================================
ii  linux-image-server  3.2.0.94.108        Linux kernel image on Server Equipment.



```

So close. Suggestions?

---

### Post by ian-weisser on 2015-11-26
First, don't download and install packages manually (just using dpkg) unless you are ready to manually resolve dependency problems. It's really tempting, but it won't actually solve your problem. Apt isn't 'stuck' like a machine that just needs a nudge - apt is blocked by a logical inconsistency that must be *solved* by you.

Second, apt's -f flag won't help you resolve this version problems. That logic mostly resolves dependencies, and you have the dependencies..

Third, your output looks very different to me now. You seem to be making progress.

Try:```

sudo apt-get update    ## Refresh the package database
sudo apt-get clean     ## Prevent re-installation of older versions
sudo apt-get install --reinstall linux-server linux-image-server linux-headers-server  ## Update to the current versions
```

---

### Post by nate-sanders on 2015-11-27
```
$ apt-get install --reinstall linux-server linux-image-server linux-headers-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-image-3.2.0-89-generic linux-headers-3.2.0-70-generic linux-headers-3.2.0-86-generic
  linux-headers-3.2.0-70 linux-headers-3.2.0-84 linux-headers-3.2.0-86 linux-headers-3.2.0-87
  linux-headers-3.2.0-88 linux-headers-3.2.0-89 linux-image-3.2.0-84-generic
  linux-headers-3.2.0-89-generic linux-image-3.2.0-87-generic linux-headers-3.2.0-84-generic foreman
  linux-headers-3.2.0-87-generic postgresql-common linux-image-3.2.0-88-generic
  postgresql-client-common linux-headers-3.2.0-88-generic linux-image-3.2.0-70-generic
  libossp-uuid16 linux-image-3.2.0-86-generic
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  linux-server
1 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 85 not upgraded.
1 not fully installed or removed.
Need to get 6,334 B of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-server amd64 3.2.0.94.108 [1,736 B]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-server amd64 3.2.0.94.108 [2,300 B]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-image-server amd64 3.2.0.94.108 [2,298 B]
Fetched 6,334 B in 0s (30.2 kB/s)
Traceback (most recent call last):
  File "/usr/bin/apt-listchanges", line 237, in <module>
    main()
  File "/usr/bin/apt-listchanges", line 48, in main
    debs = apt_listchanges.read_apt_pipeline(config)
  File "/usr/share/apt-listchanges/apt_listchanges.py", line 83, in read_apt_pipeline
    return map(lambda pkg: filenames[pkg], order)
  File "/usr/share/apt-listchanges/apt_listchanges.py", line 83, in <lambda>
    return map(lambda pkg: filenames[pkg], order)
KeyError: 'linux-server'
(Reading database ... 481196 files and directories currently installed.)
Preparing to replace linux-headers-server 3.2.0.94.108 (using .../linux-headers-server_3.2.0.94.108_amd64.deb) ...
Unpacking replacement linux-headers-server ...
Preparing to replace linux-image-server 3.2.0.94.108 (using .../linux-image-server_3.2.0.94.108_amd64.deb) ...
Unpacking replacement linux-image-server ...
Setting up linux-image-server (3.2.0.94.108) ...
Setting up linux-headers-server (3.2.0.94.108) ...
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.92.106); however:
  Version of linux-image-server on system is 3.2.0.94.108.
 linux-server depends on linux-headers-server (= 3.2.0.92.106); however:
  Version of linux-headers-server on system is 3.2.0.94.108.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
    Errors were encountered while processing:
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by ian-weisser on 2015-11-27
Did you run autoremove?

Run the --reinstall command again for linux-server. If it doesn't work, then use dpkg to upgrade it (the current version is in your /var/cache/apt/archives, and the dependencies are already upgraded.

---

### Post by nate-sanders on 2015-11-27
As I keep saying, I cant run most apt-get commands. Any time I do if just throws dependencies errors.

```
$ apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-server : Depends: linux-image-server (= 3.2.0.92.106) but 3.2.0.94.108 is installed
                Depends: linux-headers-server (= 3.2.0.92.106) but 3.2.0.94.108 is installed
E: Unmet dependencies. Try using -f.

```

---

### Post by ian-weisser on 2015-11-27
Yes, you did. The complete output, with version numbers, is very helpful.

Did you successfully upgrade linux-server using either apt or dpkg? (Post #10)

---

### Post by nate-sanders on 2015-11-27
It does not appear so. The attempt to reinstall produced the same errors

```

$ apt-get install --reinstall linux-server linux-image-server linux-headers-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-image-3.2.0-89-generic linux-headers-3.2.0-70-generic linux-headers-3.2.0-86-generic
  linux-headers-3.2.0-70 linux-headers-3.2.0-84 linux-headers-3.2.0-86 linux-headers-3.2.0-87
  linux-headers-3.2.0-88 linux-headers-3.2.0-89 linux-image-3.2.0-84-generic
  linux-headers-3.2.0-89-generic linux-image-3.2.0-87-generic linux-headers-3.2.0-84-generic foreman
  linux-headers-3.2.0-87-generic postgresql-common linux-image-3.2.0-88-generic
  postgresql-client-common linux-headers-3.2.0-88-generic linux-image-3.2.0-70-generic
  libossp-uuid16 linux-image-3.2.0-86-generic
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  linux-server
1 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 85 not upgraded.
1 not fully installed or removed.
Need to get 0 B/6,334 B of archives.
After this operation, 0 B of additional disk space will be used.
Traceback (most recent call last):
  File "/usr/bin/apt-listchanges", line 237, in <module>
    main()
  File "/usr/bin/apt-listchanges", line 48, in main
    debs = apt_listchanges.read_apt_pipeline(config)
  File "/usr/share/apt-listchanges/apt_listchanges.py", line 83, in read_apt_pipeline
    return map(lambda pkg: filenames[pkg], order)
  File "/usr/share/apt-listchanges/apt_listchanges.py", line 83, in <lambda>
    return map(lambda pkg: filenames[pkg], order)
KeyError: 'linux-server'
(Reading database ... 481196 files and directories currently installed.)
Preparing to replace linux-headers-server 3.2.0.94.108 (using .../linux-headers-server_3.2.0.94.108_amd64.deb) ...
Unpacking replacement linux-headers-server ...
Preparing to replace linux-image-server 3.2.0.94.108 (using .../linux-image-server_3.2.0.94.108_amd64.deb) ...
Unpacking replacement linux-image-server ...
Setting up linux-image-server (3.2.0.94.108) ...
Setting up linux-headers-server (3.2.0.94.108) ...
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.92.106); however:
  Version of linux-image-server on system is 3.2.0.94.108.
 linux-server depends on linux-headers-server (= 3.2.0.92.106); however:
  Version of linux-headers-server on system is 3.2.0.94.108.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)




```

I did manually rung dpkg install against the .106 versions, and it appeared they installed, yet they do not show up under dpkg -l nor does apt seem to be recognizing them.

---

### Post by ian-weisser on 2015-11-27
Not sure what you mean by 'they'. Unclear. Not sure if it's relevant.

Cease trying to reinstall linux-image-server and linux-headers-server. Those two seem to have reinstalled successfully already (twice now).

Just reinstall linux-server using either apt or dpkg.
If neither work (show us both outputs), then remove linux-server using either apt or dpkg. DON'T let the system remove any dependencies - you need those!

---

### Post by nate-sanders on 2015-11-28
Welp, we have success! I was not expecting to be able to remove linux-server, so I decided to use dpkg instead of apt, and it was successful. Now I am able run autoremove, upgrade, and so forth!

I cannot begin to thank you for your patience and assistance!!

---

### Post by ian-weisser on 2015-11-28
Remember to reinstall the new version of linux-server, so your kernel upgrades automatically.

And remember to run autoremove or occasion (perhaps monthly or so) to prevent the original problem from recurring.

---

