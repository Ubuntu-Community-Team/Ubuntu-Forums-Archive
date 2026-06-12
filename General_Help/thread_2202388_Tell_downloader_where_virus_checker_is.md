---
title: "Tell downloader where virus checker is"
date: 2014-01-28
forum: General Help
---

### Post by OldGrampa on 2014-01-28
How do I tell my downloader, where my virus checker is?
I use clamTK.
I am somewhat new to Ubuntu, and don't know where the command file is.

Tx

---

### Post by claracc on 2014-01-29
I suposse you want to scan the files you download.

First, your browser will download the files to a determined folder, for example folder Downloads which use to be in /home/your_user_name/ (my firefox downloads files to /home/clara/Desktop), you will have to specify it in your browser.

Then you can scan the downloaded file with command line. For entering command line you will launch a xterm:
```
CTRL+alt+T
```

Then you can use the command to scan:
```
clamscan -r /home/your_user_name/Downloads
```

For more information about using and updating clamav antivirus, please see: [https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

In this link, it is also said how to use the gui for clamav: ClamTK to scan your downloaded files.

---

