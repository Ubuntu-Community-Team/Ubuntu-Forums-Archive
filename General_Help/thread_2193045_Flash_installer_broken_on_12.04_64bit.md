---
title: "Flash installer broken on 12.04 64bit"
date: 2013-12-10
forum: General Help
---

### Post by BigBaka on 2013-12-10
This morning I updated software on my newly installed Ubuntu 12.04 64 bit desktop system, and flashplugin-installer is now broken. I've noticed that people have been having this problem, but couldn't seem to find a solution apart from downloading google chrome. Following one of those posts I purged and then tried to re-install flash, but it seems that the link to the download is broken or something. See the readout below. Has anyone been able to find a solution to this ongoing problem yet.

```
glenn@GRdesktop:~/Downloads$ sudo apt-get install flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-filesystem1.46.1 libboost-graph-parallel1.46.1 libboost-system1.46.1
  libboost-python1.46.1 libboost-signals1.46.1 libboost-program-options1.46.1
  libboost-test1.46.1 libboost-iostreams1.46.1 libboost-wave1.46.1 libboost-graph1.46.1
  libboost-thread1.46.1 libboost-mpi1.46.1 libcmis-0.2-0 libreoffice-emailmerge
  libboost-math1.46.1 libboost-regex1.46.1 libboost-random1.46.1
Use 'apt-get autoremove' to remove them.
Suggested packages:
  x-ttcidfont-conf ttf-mscorefonts-installer ttf-bitstream-vera ttf-dejavu
  ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/6,932 B of archives.
After this operation, 139 kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously unselected package flashplugin-installer.
(Reading database ... 256644 files and directories currently installed.)
Unpacking flashplugin-installer (from .../flashplugin-installer_11.2.202.332ubuntu0.12.04.1_amd64.deb) ...
Processing triggers for update-notifier-common ...
flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.332.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.332.orig.tar.gz)
Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 234, in process_download_requests
    dest_file = urllib.urlretrieve(files[i])[0]
  File "/usr/lib/python2.7/urllib.py", line 93, in urlretrieve
    return _urlopener.retrieve(url, filename, reporthook, data)
  File "/usr/lib/python2.7/urllib.py", line 239, in retrieve
    fp = self.open(url, data)
  File "/usr/lib/python2.7/urllib.py", line 207, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 344, in open_http
    h.endheaders(data)
  File "/usr/lib/python2.7/httplib.py", line 954, in endheaders
    self._send_output(message_body)
  File "/usr/lib/python2.7/httplib.py", line 814, in _send_output
    self.send(msg)
  File "/usr/lib/python2.7/httplib.py", line 776, in send
    self.connect()
  File "/usr/lib/python2.7/httplib.py", line 757, in connect
    self.timeout, self.source_address)
  File "/usr/lib/python2.7/socket.py", line 571, in create_connection
    raise err
IOError: [Errno socket error] [Errno 101] Network is unreachable
Setting up flashplugin-installer (11.2.202.332ubuntu0.12.04.1) ...
```

---

### Post by mattrochman on 2013-12-13
Bump... Me too! Anyone know what the issue is?

---

### Post by cetag on 2013-12-19
Me too. 
 
Flash stopped working in Firefox, Ubuntu 12.04.3 LTS, so I performed this; 
  ```
sudo apt-get remove flashplugin-installer 
  sudo apt-get purge  flashplugin-installer 
  sudo apt-get install flashplugin-installer 
```

That got it working perfectly. Suddenly, a day later, Flash not working in Firefox again. 
So I peform the same operation as above, and get a bad link error during the install. 
I wonder why Flash in Firefox suddenly failed, and why re-install fails too. 
Here was error message; 
 
```
aa@aa:~$ sudo apt-get install flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  x-ttcidfont-conf xfs
The following NEW packages will be installed:
  flashplugin-installer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/6,936 B of archives.
After this operation, 139 kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously unselected package flashplugin-installer.
(Reading database ... 412876 files and directories currently installed.)
Unpacking flashplugin-installer (from .../flashplugin-installer_11.2.202.332ubuntu0.12.04.1_i386.deb) ...
Processing triggers for update-notifier-common ...
flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.332.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.332.orig.tar.gz)
Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 234, in process_download_requests
    dest_file = urllib.urlretrieve(files[i])[0]
  File "/usr/lib/python2.7/urllib.py", line 93, in urlretrieve
    return _urlopener.retrieve(url, filename, reporthook, data)
  File "/usr/lib/python2.7/urllib.py", line 239, in retrieve
    fp = self.open(url, data)
  File "/usr/lib/python2.7/urllib.py", line 207, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 344, in open_http
    h.endheaders(data)
  File "/usr/lib/python2.7/httplib.py", line 954, in endheaders
    self._send_output(message_body)
  File "/usr/lib/python2.7/httplib.py", line 814, in _send_output
    self.send(msg)
  File "/usr/lib/python2.7/httplib.py", line 776, in send
    self.connect()
  File "/usr/lib/python2.7/httplib.py", line 757, in connect
    self.timeout, self.source_address)
  File "/usr/lib/python2.7/socket.py", line 571, in create_connection
    raise err
IOError: [Errno socket error] [Errno 101] Network is unreachable
Setting up flashplugin-installer (11.2.202.332ubuntu0.12.04.1) ...
aa@aa:~$
```

---

### Post by efflandt on 2013-12-19
I have been running 64-bit 12.04 for some time and reinstalled 12.04.3 after replacing a failing hard drive (in July?) and have not had any problems with it. I watch Hulu regularly and YouTube videos fairly frequently in Firefox and have not had any flash issues.```
efflandt@xps8100-1204:~$ dpkg-query -l flash* | grep ii
ii  flashplugin-installer                  11.2.202.332ubuntu0.12.04.1             Adobe Flash Player plugin installer
```Curious that both of you who listed install error messages have the same error:
IOError: [Errno socket error] [Errno 101] Network is unreachable

Can you: **tracepath archive.canonical.com**
which for me ends up in London at kudan.canonical.com

Also do you update your system using **Update Manager** or manually? I see many people using **sudo apt-get update** and then **sudo apt-get update**, which might skip some packages that would be included with smarter **sudo apt-get dist-upgrade** (see: man apt-get).

---

### Post by cetag on 2013-12-19
Yes, tracepath ends in London, 
```
...
16:  ae-59-224.csw2.London1.Level3.net                   318.450ms asymm 17 
17:  ae-2-52.edge5.London1.Level3.net                    319.188ms asymm 16 
18:  SOURCE-MANA.edge5.London1.Level3.net                318.824ms asymm 17 
19:  archive.canonical.com                               366.051ms reached
     Resume: pmtu 1492 hops 19 back 42 
aa@aa:~$ 
```


I was using apt-get install. When that failed I tried synaptic, each time with 'apt-get purge flashplugin-installer' beforehand. 
Using synpatic failed with the same 'Network is unavailable' error message.


I just now ran   
    ```
$ sudo apt-get upgrade
```
and then ran install as below. This time it appears to have completed. 

```
aa@aa:~$ sudo apt-get install flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  x-ttcidfont-conf xfs
The following packages will be REMOVED:
  adobe-flash-properties-gtk adobe-flashplugin
The following NEW packages will be installed:
  flashplugin-installer
0 upgraded, 1 newly installed, 2 to remove and 3 not upgraded.
Need to get 0 B/6,936 B of archives.
After this operation, 17.9 MB disk space will be freed.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 412902 files and directories currently installed.)
Removing adobe-flash-properties-gtk ...
Removing adobe-flashplugin ...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Selecting previously unselected package flashplugin-installer.
(Reading database ... 412876 files and directories currently installed.)
Unpacking flashplugin-installer (from .../flashplugin-installer_11.2.202.332ubuntu0.12.04.1_i386.deb) ...
Processing triggers for update-notifier-common ...
flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.332.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.332.orig.tar.gz)
Installing from local file /tmp/tmppFu_9m.gz
Flash Plugin installed.
Setting up flashplugin-installer (11.2.202.332ubuntu0.12.04.1) ...

```
Presently it seems sometimes the network/file is simply unavailable, and other times it is available. 
For now I doubt the 'apt-get update' has anything to do with it.


And no fix, despite 'apt-get install flashplugin-installer' completing without error.

---

### Post by QIII on 2013-12-19
Please use code tags, folks.  See my signature for how.

Thanks.

---

### Post by cetag on 2013-12-20
OK. While this may not apply to the 64-bit system of the OP, it has got FLash working in Firefox for me again. 

After the apt-get install business mentioned above, using 'find' I searched for all flash libraries. There were two, of different sizes and dates. 

```
$ ll /usr/lib/flashplugin-installer/libflashplayer.so
-rw-r--r-- 1 root root 17422820 Dec 20 15:14 /usr/lib/flashplugin-installer/libflashplayer.so

$ ll /usr/lib/mozilla/plugins/libflashplayer.so
-rw-r--r-- 1 root root 17047372 Nov 17 21:24 /usr/lib/mozilla/plugins/libflashplayer.so

```

Replacing the earlier one in the 2nd location above, with the Dec20 version, didn't get Flash going.
Replacing the later one in the 1st location above, with the earlier Nov17 version, did get Flash going. 
Presently both these locations now contain the same Nov17 version. 

While this may not be a fix for anyone else, the process of seeing which version libraries are where, can be informative. 
```
find / -name "libflashplayer.so"
```
I guess my problem is perhaps, a legacy library fouling the purge/install process.

---

### Post by mörgæs on 2013-12-20
If everything else fails installing Chrome is an option.

---

