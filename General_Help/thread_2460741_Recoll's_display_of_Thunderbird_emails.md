---
title: "Recoll's display of Thunderbird emails"
date: 2021-04-17
forum: General Help
---

### Post by Robbyx on 2021-04-17
I use Thunderbird ("TB") pop3 for emails, and Recoll for indexing my files including mbox files created by TB.

When I do a search in Recoll and then choose to have the message opened from within Recoll I get the the detailed content of the headers of the message, every line is numbered and control characters such as =0D  are also shown in the display window.

What changes should I make to allow  TB emails to be properly displayed by Recoll?

---

### Post by walts48 on 2021-04-17
Changes to Recoil or to Thunderbird?

Can't help, just curious.

---

### Post by Robbyx on 2021-04-17
I don't know, but it looks like the message is not being opened by TB.  To me it seems as if a text editor is doing it instead.

---

### Post by ajgreeny on 2021-04-17
Unfortunately even if you ask the system to open a mailbox file in TB it will not show you the mailbox as TB normally shows it, but will simply create a new message with the mailbox file added as an attachment.

I do not know of a way to view mailbox files in anything other than a text editor though you could rename the mailbox file, eg, giving it a suffix number and then add it to your current TB configuration folder in the MAIL subfolder, however, this will still not answer your recoll problem.

It's a long time since I have looked at recoll and I can not remember what the configuration options are for its use, though it does ask you if you want to open a file or simply preview it if I remember correctly; is there any difference between the two views?  I will have to leave you to answer that yourself as I do not wish to install it and allow it to waste space with a database of files which used to be huge; is that still the case?

---

### Post by TheFu on 2021-04-17
I use recoll extensively, but not for email. Sorry.  My IMAP email server has fantastic search capability (added by Yahoo!), so all searching happens on the server, never the client.  It is self-hosted, but more complicated than 95% of Linux people should attempt. Any email that gets copied locally can be wiped completely thanks to IMAP.

As for the size of recoll DBs, 
```
$ du -shc recoll-index
2.1G    recoll-index
2.1G    total
```
So - 2.1G for 
```
$ inxi -Dx
Drives:    HDD Total Size: **32326.3GB** (72.2% used)
           ID-1: USB /dev/sda  size: 8001.6GB temp: 0C
           ID-2: USB /dev/sdb  size: 8001.6GB temp: 0C
           ID-3: /dev/sdc size: 4000.8GB temp: 34C
           ID-4: /dev/sdd size: 320.1GB temp: 38C
           ID-5: /dev/sde size: 4000.8GB temp: 36C
           ID-6: /dev/sdf size: 4000.8GB temp: 37C
           ID-7: /dev/sdg size: 4000.8GB temp: 39C
```
about 32TB.

**inxi** amazes me with some new summary all the time.  Most of those files are media, so only the metadata gets indexed. I don't use the Recoll GUI to search. Rather, I use a little shell script to perform the search and display just the parts I want.

I'm curious. Just installed it on a desktop where I run Thunderbird for email. It uses Qt - yuck. It is doing the indexing for my HOME now. Shouldn't take too long, as there's only a few GB there.  I'll add more if I see it.

Update1: It is still indexing. .... this seems like a very long time, considering there's only 6.4G in the index directory I specified.

Update2: It doesn't appear to find any thunderbird email. Haven't figured out why not yet.

---

### Post by TheFu on 2021-04-18
This morning, after an automatic recoll update scan, I searched for some messages that were displayed inside Thunderbird.  Tried searching by both the "subject" and for words inside the message body.  Neither returned ANY results.

Doing some other searches based on filenames and content, I do see lots of expected results, just nothing from Thunderbird.  I'll look over my exclusions and inclusions lists again. I did specifically include ~/.thunderbird, but I exclude ~/.[0-Z]* because I have thousands of tiny files from Ruby and Perl libraries in local subdirs.

---

