---
title: "lubuntu 16.10 - Can't run Steam: &quot;Steam needs to be online to update&quot;"
date: 2016-11-05
forum: General Help
---

### Post by jimmyvh on 2016-11-05
I recently reinstalled lubuntu on my intel NUC, running KODI as frontend. Before I reinstalled I could run steam just fine. 

On my new lubuntu installation, I simply installed steam through apt-get, then try to run it. When I do, I get the following output:

```
jimmy@media:~$ DISPLAY=:0 steam
ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
[2016-11-05 11:13:07] Startup - updater built Mar 29 2016 17:40:06
[2016-11-05 11:13:08] Verifying installation...
[2016-11-05 11:13:08] Unable to read and verify install manifest /home/jimmy/.steam/package/steam_client_ubuntu12.installed
[2016-11-05 11:13:08] Verification complete
[2016-11-05 11:13:08] Downloading Update...
[2016-11-05 11:13:08] Checking for available update...
[2016-11-05 11:13:09] Download failed: http error 0
[2016-11-05 11:13:09] Download failed: http error 0
[2016-11-05 11:13:09] failed to load manifest from buffer.
[2016-11-05 11:13:09] Failed to load manifest
[2016-11-05 11:13:09] Error: Download failed: http error 0
[2016-11-05 11:13:09] Error: Steam needs to be online to update.         Please confirm your network connection and try again.

```
Steam shows the error message on the UI with a "close" button. After I click "close", the program exits with the following output:
```
[2016-11-05 11:30:48] Shutdownthreadtools.cpp (3193) : Assertion Failed: Illegal termination of worker thread 'Thread(0x0x5779bbf8/0x0xf696bb'
tar: Dit ziet er niet uit als een tar-archief (translation: This doesn't look like a tar archive)
xz: (stdin): Bestandtype niet herkend (translation: file type not recognised)
tar: Child returned status 1
tar: Error is not recoverable: exiting now
find: &#8216;/home/jimmy/.steam/ubuntu12_32/steam-runtime&#8217;: Bestand of map bestaat niet (translation: file or directory doesn't exist)
```

I tried a full reinstall (with apt-get remove and purge), but the result is the same every time.
Every time I try to start steam, it creates *~/.steam/ubuntu12_32/steam-runtime.tar.xz*, that has a size of zero bytes. Deleting the file and starting steam again will create the same zero size file again, so I guess this is the file steam wants to download when giving the http error.

Everything points towards a network error, but my network works just fine, and I can also ping the steam servers without a problem. I've had this problem for several days now, and I seem to be alone with this problem, so the steam servers don't seem to be the issue. Does anyone have an idea what I can do?

---

### Post by jimmyvh on 2016-11-05
I found the solution. I have configured a static IP address, but I didn't specify a DNS server. An oversight on my part that I didn't realise sooner because every other application has no problem with doing DNS lookups (not sure how/why. Ubuntu uses a fallback DNS server for when it doesn't have that info?). Steam however, is helpless when you don't have one specified with a static IP configuration.

Filled in my nameserver settings, rebooted and steam started updating. Problem solved.

---

### Post by oldos2er on 2016-11-05
Hello, would you please use Thread Tools at the top of the page to mark your thread 'Solved'? It'll help others to find this solution. Thanks!

---

