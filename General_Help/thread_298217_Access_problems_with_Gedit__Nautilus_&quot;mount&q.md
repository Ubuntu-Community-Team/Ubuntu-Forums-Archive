---
title: "Access problems with Gedit / Nautilus &quot;mount&quot;, Read-Only"
date: 2006-11-12
forum: General Help
---

### Post by kaylus on 2006-11-12
I've "mounted" an ftp location with the Nautilus (File->Connect to Server), and all works well, I can browse just fine, I copy files to and from the "mount", but I have a problem with using GEdit.

The file opens up properly but opens up as "[Read Only]", and does not allow me to save it. I thought it might be permissions based so I copied a file from, deleted it off the "mount" and replaced it just fine. There seems to be no permissions problem, I also ssh'd in and made sure I was the owner (just in case!).

I would really like to use GEdit for what I am doing with it (alot of text editing) and it works just fine for what I do. I don't mind looking at things similar to GEdit (basic text editors w/syntax highlighting and tabs).

Does anyone have any advice on this, wondered if it was a bug on the system or a bug in the user ;) 

Kaylus

---

### Post by kaylus on 2006-11-12
-sorry- I was browsing back and double-posted :/ Please forgive my sins.

---

### Post by kaylus on 2006-11-12
Alright, for anyone that wishes to know. I've solved this.

GEdit doesn't allow FTP saving by default. To fix this:

Launch (run) gconf-editor
Browse to this: /apps/gedit-2/preferences/editor/save
Double-click on the key: writable_vfs_schemes
Click "add" and add the word "ftp"
Click "ok"

Voila. Gedit saving FTP.

---

### Post by joncheyne on 2006-12-19
> **kaylus said:**
> Alright, for anyone that wishes to know. I've solved this.

GEdit doesn't allow FTP saving by default. To fix this:

Launch (run) gconf-editor
Browse to this: /apps/gedit-2/preferences/editor/save
Double-click on the key: writable_vfs_schemes
Click "add" and add the word "ftp"
Click "ok"

Voila. Gedit saving FTP.

Gets rid of the read only display but when I go to save, it says file not found. And sure enough it has deleted the file on the ftp server, I assume prior to "saving" the new one. ](*,)

---

### Post by PA28 on 2008-01-31
I can confirm that kaylus' gconf-editor trick works. Just make sure that you run gconf-editor without root privilages.

Hopefully that may save some other users some trouble, and wasted time. ;)

---

### Post by kesman on 2008-01-31
You should add "solved" to the topic now since this really is solved :)

---

### Post by undoIT on 2008-02-28
This is exactly what I was looking for and will save a lot of time. I should have looked this up a long time ago. My love for Linux and Ubuntu continues to grow :D

---

### Post by ArrantSquid on 2008-03-18
Dude! You so rock! This was exactly what I needed.

---

### Post by shaffe on 2008-04-24
How can I change 666 default persmissions to 644 when uploading file on FTP servers whith gedit ?

---

### Post by undoIT on 2008-04-24
> **shaffe said:**
> How can I change 666 default persmissions to 644 when uploading file on FTP servers whith gedit ?

I am assuming you mean uploading a file with FTP using Nautilus. You need to know what the numbers mean. To change permissions you would right-click the file, go to the permissions tab and select:

Owner:
Access: Read and write

Group:
Access: Read-only

Others
Access: Read-only

---

### Post by kaylus on 2008-04-27
> **undoIT said:**
> This is exactly what I was looking for and will save a lot of time. I should have looked this up a long time ago. My love for Linux and Ubuntu continues to grow :D

Glad I could help some people out! :) Adding [SOLVED] to the subject, so that it can help others in the future.

---

