---
title: "Widespread file corruption garbling on Samba shared gvfs-fuse volume"
date: 2013-10-31
forum: General Help
---

### Post by tetsuo29 on 2013-10-31
I'm running 12.04 as a file server in a small office environment- approx. 12 users. I use gvfs-fuse to mount a volume that came from the previous Fedora install. This volume is shared to Windows desktop clients via Samba and also SSH (they use Filezilla or Cyberduck to connect and sync folders when working remotely).

Yesterday, it was discovered that widespread and random file corruption was happening. A user would save an Excel, Word, or PDF file on the shared drive and within minutes, the file would become unreadable. File size, date & time stamps, filename, etc. all remained unchanged. If you open the Word or Excel files in a text editor, instead of seeing the XML data, you would just get a bunch of garbled data like this:

[IMG]http://i.imgur.com/vQ7fWA6.png[/IMG]

I've rebooted the server. I ran hardware checks, including memory checks. I ran chkrootkit and rkhunter- nothing unusual and no known rootkits detected. I checked the file systems and they were clean. Now, that the server has been rebooted, the problem seems to have stopped- at least for the spreadsheet I've created and been editing.

Does anyone out there have any ideas why this happened? Is there any way to determine if it was gvfs-fuse-daemon or Samba?

Does anyone have any ideas if the corrupt files are recoverable in any way? The amount of data has not changed? Maybe gvfs or Samba left the files in a temp or encoded format and there's a way to decode them?

Help! I'm a little panicked and confused about why this happened. Nine years of running a Linux file server for this office and nothing like this has ever happened before. (You can laugh at me, but my backups of the shared volume are rsynced to a remote machine and so many of the corrupted files have been syncing to the remote backup each night.)

---

### Post by daitau on 2013-11-01
Not sure if it really matters, but xlsx or any modern MS Office files are actually XML files within a zip file, so you may want to rename the file to .zip and open in archiver instead of opening it directly with a text editor. Does this corruption happen to plain text files as well?

Also for corruption of files I had an experience previously where the security software on the Windows desktop (that encrypts files on the fly) got confused and corrupted files randomly. Just something to look out for in case you are using those software.

---

### Post by nativehound on 2013-11-01
Better examine all the Windows PC's for Cryptolocker! There has been reports on the internet of this thing encrypting Network Shares and/or NAS boxes that Windows machines have write access to. If you never heard Cryptolocker you better start googling. If it is Cryptolocker, the infected Windows PC will have a countdown timer on it and a statement that it that it will cost you 300USD to get your files back and no i'm not joking.

---

### Post by tetsuo29 on 2013-11-01
You called it. They brought in a laptop and didn't tell me about it, connected it to the shared volume, and this laptop had no anti-malware software installed on it and got infected with Cryptolocker. They ended up paying $300 in ransom in order to get their files decrypted. In fact, it's still working on decrypting the files on the shared drive as I type this.

---

### Post by tetsuo29 on 2013-11-01
Thanks for the reply. Turns out it was malware called Cryptolocker on an unsecured laptop that they connected to the shared drive. Was an expensive lesson for them and i'm working on implementing a rolling set of backups with rsync rather than just a nightly sync of everything.

---

### Post by nativehound on 2013-11-01
Wow, that sux. Better beef up samba security as well.

---

