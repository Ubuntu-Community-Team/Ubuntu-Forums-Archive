---
title: "Syncing Multiple Linux OS"
date: 2013-03-27
forum: General Help
---

### Post by Arkenbrien on 2013-03-27
Greetings once again, my fellow 'buntus. 

I'll make this quick:

I multi-boot my computer. I have a few Linux distros, including, of course, Ubuntu. Is there a way to sync programs across these distros directly? I've looked around, but my search-fu was inadequate. I don't want to use my internet connection, so Ubuntu One can't be used, even if it could, because my data usage is a little limited. The goal of this is to eliminate the need to re-install everysingle program that I download on Ubuntu.

Thank you for your time.

---

### Post by Dragonbite on 2013-03-27
If you don't want to use the Internet, then Dropbox (which is cross-platform and cross-Distro) isn't going to suffice.

If you can "see" the files in the other distros (are they on the same machine?) then you can use **rsync** (command-line) or **grsync** (a gui-front end for rsync) or even easier is [FreeFileSync]("http://sourceforge.net/projects/freefilesync/").

If they are separate machines you will need to do some configuring to get rsync to work over the network, though with FreeFileSync I think you only need to mount the samba drive to be able to synchronize them.

Another benefit of FreeFileSync (which ultimately uses rsync in the background) is that you can set the sync to work a couple of ways including "Mirror" (files will be copied from source to destination and any files in destination are removed if not in the source), "Update" (only move over files from source if they are not present in destination, regardless of what else is in the destination) and "Sync" (merges and makes the two drives identical).  FreeFileSync also comes with "real sync" which like Ubuntu One and Dropbox it monitors a folder for changes and when detected will automatically run whatever FreeFileSync batch job you created.

For for example, I may use the "Update" to copy digitial pictures I import on my laptop into a central computer (desktop, server, etc.) while my Documents are "Sync" so if I make a change to a document on my laptop then sit down at the desktop, it will be the version I just saved on the laptop.

Unfortunately to use it on non-Ubuntu systems you'll need to download the source.  On the other hand, it only needs to be working on one computer; that computer will manage watching for changes and copy things to/from as necessary.

For example I use this at work where I am not allowed to install any programs on the server, but am given GB of space to store and backup my system. So I installed FreeFileSync on my laptop and it is the only version running.  When I make a change on the laptop, it will Sync with the server. If I make a change to the server version, then when the laptop is connected it will look for changes and download the changes on the server version (it's newer than the version on my laptop).  If there is a conflict (both changed) then I can elect to go into the program and tell it which one to keep.

So, that should be enough shooting in the dark. Can you describe your setup better (how many computers, dual-boot, networked, etc.)

---

### Post by Arkenbrien on 2013-03-27
Sorry for not making myself very clear.

I have a single computer, that has multiple partitions and OSs. What I want to do is to sync apps throughout the Linux distros on that single computer. That way, if I don't have to re-download say like Blender3D on each and every distro.

Thanks

---

### Post by cioma on 2013-03-27
List of installed distros would help.
But in general I don't think it's possible to do that in any reliable way.

---

### Post by Dragonbite on 2013-03-27
Synchronizing apps?  If they are all Ubuntu-based and same version you may be able to share .DEB files from the repository or generic .deb files.  Same things if you have multiple RPM-based distros (Fedora, Red Hat, CentOS or openSUSE based).

I thought you meant files.  

Now if you are planning on installing from source, then after downloading you may be able to install on each one individually but that means you'll have to do the legwork to getting each installed for each distro.

Portable apps may be more flexible but again, you will have to do the leg work for that too.

---

