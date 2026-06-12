---
title: "Package manager conflict: libcups2"
date: 2014-09-11
forum: General Help
---

### Post by sippycup2 on 2014-09-11
Hey all,

Running Ubuntu 12.04 for about 1.5-2 years now. Software Center is angry with me and tells me I have BrokenCount > 0. Source seems to be a conflict between versions of libcups2 i386 and libcups2 amd64. Not sure how this might have come about.

Found this thread: [http://askubuntu.com/questions/462185/libcups2amd64-cannot-be-configured-because-libcups2i386-is-in-a-different-ver](http://askubuntu.com/questions/462185/libcups2amd64-cannot-be-configured-because-libcups2i386-is-in-a-different-ver)

Performed all advice except editing the text file. Removing the libcups2 entry basically would tell apt-get / dpkg / software manager that it's no longer installed, right? In theory then I could reinstall it, which might fix the issue but doesn't seem to be getting at the root cause (version mismatch).

Any ideas? Thanks!

```
sippy@sippyDESK:~$ sudo apt-get install -fReading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-65-generic linux-headers-3.2.0-52-generic
  linux-headers-3.2.0-29 linux-headers-3.2.0-51 linux-headers-3.2.0-52
  linux-headers-3.2.0-53 linux-headers-3.2.0-54 linux-headers-3.2.0-60
  linux-headers-3.2.0-55 linux-headers-3.2.0-61 linux-headers-3.2.0-56
  linux-headers-3.2.0-57 linux-headers-3.2.0-63 linux-headers-3.2.0-58
  linux-headers-3.2.0-64 linux-headers-3.2.0-59 linux-headers-3.2.0-65 g++-4.6
  linux-headers-3.2.0-29-generic linux-headers-3.2.0-60-generic
  linux-headers-3.2.0-55-generic g++ linux-headers-3.2.0-63-generic
  linux-headers-3.2.0-58-generic linux-headers-3.2.0-53-generic
  libstdc++6-4.6-dev linux-headers-3.2.0-61-generic
  linux-headers-3.2.0-56-generic language-pack-kde-en kde-l10n-engb
  linux-headers-3.2.0-64-generic linux-headers-3.2.0-59-generic
  linux-headers-3.2.0-51-generic linux-headers-3.2.0-54-generic
  language-pack-kde-en-base linux-headers-3.2.0-57-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libcups2
The following packages will be upgraded:
  libcups2
1 upgraded, 0 newly installed, 0 to remove and 38 not upgraded.
2 not fully installed or removed.
Need to get 0 B/168 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing libcups2 (--configure):
 libcups2:amd64 1.5.3-0ubuntu8.4 cannot be configured because libcups2:i386 is in a different version (1.5.3-0ubuntu8.5)
dpkg: error processing libcups2:i386 (--configure):
 libcups2:i386 1.5.3-0ubuntu8.5 cannot be configured because libcups2:amd64 is in a different version (1.5.3-0ubuntu8.4)
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libcups2
 libcups2:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
sippy@sippyDESK:~$ 



```

---

### Post by deadflowr on 2014-09-11
I would have run
```
sudo apt-get update
```
first, before trying any other command.
In general I would try these in order
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install -f
```

The first command will refresh the package list available.
This is where things normally can get solved, because sometimes the packages you have listed in your lists are out dated and a simply refresh will fix it.

The second and third commands updates the packages on the system. The first updates existing packages only, where as the second one will install new version of existing packages. Might not make a lot of sense...

And then the last command, which you should already know, is to fix broken packages.
If anything odd to you shows up, or more errors occur , post them.


For the record both libcups2 packages should both be 1.5.3-0ubuntu8.5

---

### Post by sippycup2 on 2014-09-13
Hey deadflowr, thanks for your response. I ran the commands you suggested and they all generated about the same errors: namely that libcups2 is the wrong version and it can't configure it. 

Hmmm... well. Should I delete their entries from [FONT=Ubuntu Mono]/var/lib/dpkg/status?

Thanks,
Eric [/FONT]

---

### Post by deadflowr on 2014-09-13
Try the solutions found here
[http://ubuntuforums.org/showthread.php?t=1642173](http://ubuntuforums.org/showthread.php?t=1642173)

---

### Post by sippycup2 on 2014-09-14
deadflowr,

I reckon I'm going to play this one like Windows and just upgrade to 14.04 when I get some free time. Thanks for the suggestions tho!

Eric

---

