---
title: "Files On Server"
date: 2012-11-02
forum: General Help
---

### Post by chideock on 2012-11-02
How do I mount a connection, and have the conncetion mount every time I boot, on my Ubuntu 12.10 home computer to my folders located on a home server run by Windows?

I want to be able to access my files on my server through the open files command in software such as LibreOffice without first having to always mount the server folders.

Thanks
Tom

---

### Post by Cheesemill on 2012-11-02
You need to add the appropriate entry to your fstab file.

[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

### Post by chideock on 2012-11-02
OK thanks for your suggestion but I am looking for a GUI way to do the job - terminal commands are beyond this 61 year old.

I found out that in the 'Home Folder' tab on the desktop if I use the "connect to server" command under the 'File' tab and get the proper info inserted that it connects to my home server. Then in the open window under network I select so that the folder on my storage that I want is mounted and right click and select 'add bookmark' I get a bookmark to that server folder. I restarted the computer and found the bookmark was there and I could connect to the server.

It seems my question is actually two questions because when I open LibreOffice Calc and select the 'open' command my home server folders are still not shown and I have yet to figure out how to get them to show. Any thoughts.

Thanks
Tom

---

