---
title: "How are broken APT virtual packages removed?"
date: 2023-04-13
forum: General Help
---

### Post by foxsquirrel on 2023-04-13
I have done all the commands as directed by apt and deleted the .deb that is broken. Yet, it all reappears, where do I remove it from the "list".

```
root@dev1:/var/cache/apt/archives# apt purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 linux-tools-5.4.0-146 : Depends: linux-tools-common but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
root@dev1:/var/cache/apt/archives# apt-get purge linux-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'linux-tools' can't be removed
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 linux-tools-5.4.0-146 : Depends: linux-tools-common but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
root@dev1:/var/cache/apt/archives# 

```


```
root@dev1:~# sudo dpkg -r --force-remove-reinstreq linux-tools-common
dpkg: warning: ignoring request to remove linux-tools-common which isn't installed
root@dev1:~#
```

```
root@dev1:~# dpkg -r --force-remove-reinstreq linux-tools-5.4.0-146
dpkg: dependency problems prevent removal of linux-tools-5.4.0-146:
 linux-tools-5.4.0-146-generic depends on linux-tools-5.4.0-146.

dpkg: error processing package linux-tools-5.4.0-146 (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 linux-tools-5.4.0-146
root@dev1:~# 

```

---

### Post by ian-weisser on 2023-04-13
In the apt vocabulary, a "broken" package is NOT corrupted, incomplete, nor otherwise non-functional. It's not "broken" in the classic senses of a broken bicycle or broken heart.

"Broken" in apt usage simply means that the package should not be installed. Most commonly, it's simply wrong-version, so it "breaks" the logical solving of compatible dependencies.

Tip #1: Read your output twice. Here's an example of why: A whole 'nother package was revealed as a blocker. Keep going down that hole until you run out of blocking packages

```

[FONT=courier new]root@dev1:~# dpkg -r --force-remove-reinstreq linux-tools-5.4.0-146
dpkg: dependency problems prevent removal of linux-tools-5.4.0-146:
  **linux-tools-5.4.0-146-generic** depends on linux-tools-5.4.0-146.[/FONT]

```

Tip #2: You can use multiple package names with apt.

```

sudo apt remove package1 package2 package3 packageN

```

Tip #3: Be careful removing critical system packages. The system assumes that the human is competent. If you erroneously tell the system to destroy itself, it will obey you.

Tip #4: When you get frustrated, it's time for a tea break. Then go back to Tip #1. Often, after a tea break, the answer turns out to be right there within reach. And you can laugh about how, while panicked and frustrated, you though seriously about taking destructive risks. Good old tea.

---

### Post by foxsquirrel on 2023-04-13
```
root@dev1:/# apt remove linux-tools-5.4.0-146-generic linux-tools-5.4.0-146 linux-tools-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'linux-tools-common' is not installed, so not removed
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 linux-tools-generic : Depends: linux-tools-5.4.0-146-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```


Those 3 might be the problem, tried to get them out individually and in a stream. That does not work.
Is something broken with APT?, seems like all it is doing is running in a circle.


Tried to reinstall

```
root@dev1:/# apt install linux-tools-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  linux-tools-common
0 upgraded, 1 newly installed, 0 to remove and 40 not upgraded.
3 not fully installed or removed.
Need to get 214 kB of archives.
After this operation, 927 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-tools-common all 5.4.0-146.163 [214 kB]
Fetched 214 kB in 1s (297 kB/s)            
Selecting previously unselected package linux-tools-common.
(Reading database ... 320569 files and directories currently installed.)
Preparing to unpack .../linux-tools-common_5.4.0-146.163_all.deb ...
Unpacking linux-tools-common (5.4.0-146.163) ...
dpkg: error processing archive /var/cache/apt/archives/linux-tools-common_5.4.0-146.163_all.deb (--unpack
):
 trying to overwrite '/usr/bin/acpidbg', which is also in package linux-iot-tools-common 5.4.0-1013.15
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-tools-common_5.4.0-146.163_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@dev1:/# 
```

---

### Post by foxsquirrel on 2023-04-13
Got it with this```
dpkg --remove --force-remove-reinstreq linux-iot-tools-common
```

Removed that one first then was able to upgrade. Now just waiting for the massive log jam to clear and then reboot to see if its all okay.

---

