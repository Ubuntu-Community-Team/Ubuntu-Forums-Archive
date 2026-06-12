---
title: "Problem in installing MS TrueType fonts"
date: 2012-12-06
forum: General Help
---

### Post by pwabrahams on 2012-12-06
I'm running Kubuntu 12.10, and I'm trying to reinstall the MS TrueType fonts.  I had the package **ttf-mscorefonts-installer** already installed, but since I was getting error messages I reinstalled it. The reinstallation produced these error messages, which were like the ones I had seen before:
```
pa@morchella:~$ sudo apt-get install --reinstall ttf-mscorefonts-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 234 not upgraded.
Need to get 27.4 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ quantal/multiverse ttf-mscorefonts-installer all 3.4ubuntu3 [27.4 kB]
Fetched 27.4 kB in 0s (38.7 kB/s)                  
Preconfiguring packages ...
(Reading database ... 267773 files and directories currently installed.)
Preparing to replace ttf-mscorefonts-installer 3.4ubuntu3 (using .../ttf-mscorefonts-installer_3.4ubuntu3_all.deb) ...
mscorefonts-eula license has already been accepted
Unpacking replacement ttf-mscorefonts-installer ...
Processing triggers for fontconfig ...
Processing triggers for update-notifier-common ...
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/andale32.exe
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
  File "/usr/lib/python2.7/httplib.py", line 958, in endheaders
    self._send_output(message_body)
  File "/usr/lib/python2.7/httplib.py", line 818, in _send_output
    self.send(msg)
  File "/usr/lib/python2.7/httplib.py", line 780, in send
    self.connect()
  File "/usr/lib/python2.7/httplib.py", line 761, in connect
    self.timeout, self.source_address)
  File "/usr/lib/python2.7/socket.py", line 553, in create_connection
    for res in getaddrinfo(host, port, 0, SOCK_STREAM):
IOError: [Errno socket error] [Errno 2] No such file or directory
Setting up ttf-mscorefonts-installer (3.4ubuntu3) ...

```

Does anyone know what the problem might be?

---

### Post by Kirk Schnable on 2012-12-09
I am versed in several programming languages, but not Python. 

What this looks like on the surface to me, is either something is wrong with your Python installation, or a Python library needed to download files is absent...

The error reads in such a way that it might mean your computer can't contact downloads.sourceforge.net as well.... Can you contact that address?

---

### Post by pwabrahams on 2012-12-09
```
pa@morchella:~$ ping downloads.sourceforge.net
PING downloads.sourceforge.net (216.34.181.59) 56(84) bytes of data.
64 bytes from downloads.sourceforge.net (216.34.181.59): icmp_req=1 ttl=245 time=41.2 ms
64 bytes from downloads.sourceforge.net (216.34.181.59): icmp_req=2 ttl=245 time=44.2 ms
64 bytes from downloads.sourceforge.net (216.34.181.59): icmp_req=3 ttl=245 time=41.4 ms

```

Well, I don't know Python either.  But I doubt if knowledge of Python would help, given the nature of the socket error on the last line of the traceback.

This kind of error is very frustrating.  I've gotten communication-related errors with several other unrelated programs such as **launchpad-getkeys** as well.  I'm not using a proxy server (**System Settings** confirms that) and I'm not using a firewall either (**ufw** confirms that).

---

### Post by HermanAB on 2012-12-09
You should rather install the Liberation Fonts package. It was designed as a drop in replacement and is in the repos: [https://www.redhat.com/promo/fonts/](https://www.redhat.com/promo/fonts/)

---

### Post by bra|10n on 2012-12-09
```
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 234 not upgraded.
```It seems you have applied only a partial upgrade.
You might try purging flashplugin-installer and ttf-mscorefonts and **upgrading your system** first.
Then install flash and the fonts you want afterwards.

---

### Post by Kirk Schnable on 2012-12-09
> **bra|10n said:**
> ```
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 234 not upgraded.
```It seems you have applied only a partial upgrade.
You might try purging flashplugin-installer and ttf-mscorefonts and **upgrading your system** first.
Then install flash and the fonts you want afterwards.

If there is an issue with an older version of Python for some reason, following this advice might help resolve the issue.

---

