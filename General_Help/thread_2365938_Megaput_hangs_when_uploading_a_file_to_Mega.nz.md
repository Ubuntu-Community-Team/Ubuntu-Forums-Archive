---
title: "Megaput hangs when uploading a file to Mega.nz"
date: 2017-07-12
forum: General Help
---

### Post by Rooster2000 on 2017-07-12
I have difficulties to upload files to Mega file storage service with *megatools*. When I try to upload a file with *megaput*, it gets stuck at some point during the transfer (10MB, 71,9MB, 150MB) without showing any error message. If I stop the command execution and try again, the transfer hangs right in the beginning, after only 32kB.

```
$ megaput --config=".megarc" --reload test-file
test-file: 0% - 32,0 KiB of 300,0 MiB
```

Have tried without any options, with and without specified destination folder (/Root, /Root/backup) and config file, but still no luck. *Megacopy* does not work either, but hangs similarly. *Megaget* does not work either after this hangup occurs, but stops the download right in the beginning. Using only *Megaget* does not cause this hangup though. *Megals* works fine in any situation. Reboot does not fix the problem, although it does disappear by itself after some time.

What could cause this, or where I could get some hint of what is going on? No error messages are found at /var/log/syslog, also the debug output of --debug=api,cache,fs displays nothing that would clearly explain it to me. Up- and download via web browser to my Mega account works fine.

* Megatools* version is 1.9.97, installed from Ubuntu repositories.

[SIZE=1]**Edit 2017-07-13:** Chagnged the topic, updates based on latest test results + small clarifications.[/SIZE]

---

### Post by Rooster2000 on 2017-07-13
After *megaput* hangs, I am unable to connect some online sites, like ubuntuforums.org and amazon.com. However, via tor I am able to connect them. This would suggest that the problem lies on my OS or some restrictions at my ISP, especially as I think they disappear when I turn off my modem for a while and acquire a new IP address. It is a bit strange though that these restrictions wouldn't get triggered on when using *megaget* or browser transfers, and do not block the latter ones either.

---

### Post by Rooster2000 on 2017-07-14
I contacted my ISP, and they stated a strong view that the problem would be rather in my devices (or software) than their connection.

One solution for this seems to be Tor connection, more precisely *torify*, with *megaput* command too (**Edit 2017-07-27:** It turned out that this didn't solve the problem after all):

```
$ torify megaput --config=".megarc" --reload test-file
```

It is naturally a bit slower, and I guess Tor network is not suggested to be used in large file transfers. But I could live with it, as I am doing these transfers so rarely.

Would be curious to know what is behind this, is this a bug in *Megatools* or some fault in my OS or modem. Let's see if I am motivated enough to find out.

---

### Post by Rooster2000 on 2017-07-27
I tested the upload with another modem, and it seems my current modem is guilty for these problems. With another modem upload seems to work fluently.

---

