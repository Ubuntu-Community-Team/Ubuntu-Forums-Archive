---
title: "curlftpfs unmount questions"
date: 2020-07-04
forum: General Help
---

### Post by sdjcsdw on 2020-07-04
Good morning,


I'm trying to use Ubuntu and this system is a nightmare for a novice user.
My big unknown is the situation in which I installed something via curlftpfs and I don't know if I can delete it.


I don't know what will happen if my files from the FTP server are deleted or the mount link for curlftpfs is deleted?


The system is unintuitive and the lack of an interface to manage many things is a nightmare.


I did not find anything in the curlftpfs documentation to unmount the ftp folder I installed.


In addition, it is very annoying that practically every activity should be performed in the console, even seemingly simple and easy things.


The same applies to storage space. In Windows, it is a very convenient tool to manage storage space, which presents the condition of the disks in a simple and clear way.


The mdadm utility does not have any interface that could facilitate volume management.


I have been using Ubuntu for 3 months and I still encounter a wall, this system will never be popular if it does not change.


Many programs are not available in the Ubuntu store and must be installed separately.


AnyDesk I use also does not work well, has graphic artifacts and does not work with dark mode.


rsync, which is supposed to be so perfect, does not have any sensible synchronization management tool.


I think I will have to go back to Windows because this system is not suitable for everyday use ...

---

### Post by tea for one on 2020-07-04
> **grzegrze said:**
> I'm trying to use Ubuntu and this system is a nightmare for a novice user.
My big unknown is the situation in which I installed something via curlftpfs and I don't know if I can delete it.

Go on, give us a clue, what is this **something** that you installed?

A file, a program, some firmware for a device or is it a secret?

You never know, somebody may be able to help?

---

### Post by sdjcsdw on 2020-07-04
I installed the FTP directory using curlftpfs and I don't know what will happen if I delete it ... Will the FTP files start to be deleted? Do I need to unmount curlftpfs somehow? There is no information how it works ...

---

### Post by tea for one on 2020-07-04
I do not use **curlftpfs** but I had a quick search and found this page about unmounting:-

[https://wiki.gentoo.org/wiki/CurlFtpFS#Unmounting](https://wiki.gentoo.org/wiki/CurlFtpFS#Unmounting)

Does it provide a clue for your problem?

---

### Post by sdjcsdw on 2020-07-04
[FONT=arial]Did not work...This is my mounted catalog:
I use command [/FONT]curlftpfs ftp-user:ftp-pass@my-ftp-location.local /mnt/my_ftp/[FONT=arial]

[/FONT][IMG]https://i.ibb.co/G0QKL5S/Screenshot-from-2020-07-04-22-32-18.png[/IMG]


[FONT=arial]
[/FONT][FONT=arial]What happens when I delete it?After entering this directory, I connect to the FTP server ...[/FONT][FONT=arial]

[/FONT]

---

### Post by tea for one on 2020-07-04
As I mentioned previously, I do not use **curlftpfs**, I was simply trying to find a link to help you.

---

### Post by sdjcsdw on 2020-07-04
I copied the entire FTP server (1 hour of your time)


And then I used sudo rm -rf and deleted the directory, nothing happened, the directory itself was deleted ...


The tool is bad

---

### Post by tea for one on 2020-07-04
> **grzegrze said:**
> The tool is bad

Therefore, you should consider alternatives.

**sftp** or possibly **sshfs**

---

### Post by sdjcsdw on 2020-07-04
Subject to close, a multitude of things on Ubuntu introduces chaos in the absence of adequate support for the user,

---

