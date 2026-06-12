---
title: "Accessing Windows 8.1 files (videos, music, Word docx, etc.) while in Ubuntu 14.04"
date: 2015-05-21
forum: General Help
---

### Post by drgleister on 2015-05-21
[SIZE=4][FONT=times new roman]   Twenty plus years ago I was able to use a Linux Distro (I forget which one now, maybe Fedora) to effortlessly and without any modifications whatsoever access files in my windows directories, view the vids (not many then), manipulate the pics, listen to my music, and edit .doc files. My work done in Linux was not lost upon shutdown. I was a happy camper.
   But now I have Windows 8.1 on my Acer laptop and although it seems to be adequately stable I don't like it very much. That is why I installed Ubuntu 14.04. When booted up it too, runs flawlessly. I am satisfied with each OS.
   However, unlike twenty years earlier, I cannot access anything on windows while I am in Ubuntu. I have looked for answers on the Internet but have not been too successful. One I found said to add the following:
[SIZE=3][FONT=tahoma]                      sudo mkdir /media/windows
                      sudo mount /dev/sda5 /media/windows[/FONT][/SIZE]   ed. note:  my sda is 2 and not 5. The spaces in these two lines are as the web page instructed.
   I tried this but nothing happened.
   Another site said I must be sure files sharing is allowed in Windows 8.1. So I checked what I thought were the appropriate boxes there but also, nothing.
   So here it is. How do I access my files from windows and work on them or enjoy them while on Ubuntu?
   I would be most grateful for an answer.
   Thanks.
   Harvey[/FONT][/SIZE]

---

### Post by grahammechanical on 2015-05-21
What error message do you get when you use file manager and try to access the Windows partition? Microsoft has come up with a way of speeding up the loading of Windows 8 by putting it into hibernation instead of shutting down. This prevents a Linux system from reading and writing to the Windows partition. You will have to switch off something related to fast start up or something similar.

Regards.

---

### Post by oldfred on 2015-05-22
Fast Startup off
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

But best not to directly write into Windows system partitions. The Linux NTFS driver shows all hidden files & folders that Windows normally hides. Before I started with Linux I used to turn on in Windows seeing all the hidden files & folders and created lots of issues for myself.

Better to have a separate read/write data partition formatted NTFS. And set Windows system partition as read only using fstab, so not auto mounted my Nautilus when browsing in read/write mode.

But Windows does not seem to have a way to unmount a data partition so you must have its always on hibernation or fast startup off if dual booting.

---

