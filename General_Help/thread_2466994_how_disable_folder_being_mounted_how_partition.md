---
title: "how disable folder being mounted how partition ?"
date: 2021-09-12
forum: General Help
---

### Post by aug7744 on 2021-09-12
When starting the OS has a folder being mounted among with others ( / , /home , /tmp ).
The folder is /run/user/1000/doc/ being totally empty.
How disable that folder being mounted when the system is being started ?
Not programs are using that folder.

---

### Post by vanadium on 2021-09-13
Leave this folder mounted. It will not harm you. Have some trust in the linux developpers. It will be mounted for a reason.

---

### Post by TheFu on 2021-09-13
What do you mean "mounted"?  
if you run 
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```
does it show up?  If not, then it isn't a "real" mount.

Typically, things under /run/ are pseudo-file systems created for use by the OS.  Since almost everything on Unix-based systems are files, the way that the OS interacts with hardware, directories, devices, and ... er ... files ... is by treating all of them as files.  Yes, directories are files too.  It makes for a simple, elegant, OS, yes?

---

### Post by aug7744 on 2021-09-14
@TheFu

"It makes for a simple, elegant, OS, yes?"
Yes.

The folder /run/user/1000/doc/ not is listed if using the command 
df -hT -x squashfs -x tmpfs -x devtmpfs

The folder is only displayed among others /sda folder mounted in Double Commander in mounted list icon.

I want remove it. Well trying figure a solution.

---

### Post by deadflowr on 2021-09-14
I believe the location relates to fuse.portal, which is what allows you to access your files in flatpak and maybe snap programs.
+1 to leave it be.

Edit: Your issue is with Double Commander.
Try using it's Drive Blacklist feature to hide it; 
see: [https://doublecmd.github.io/doc/en/help.html#mnu_config]("https://doublecmd.github.io/doc/en/help.html#mnu_config")

---

### Post by aug7744 on 2021-09-14
"I believe the location relates to fuse.portal, which is what allows  you to access your files in flatpak and maybe snap programs."
I current installed OS never was used flatpak or snap.

@deadflowr

I not see if is or not related with Double Commander.
Thanks for your reply.

---

### Post by ajgreeny on 2021-09-14
You may not have installed any flatpack or snap packages but I think all the Ubuntu family of OSs have snapd installed by default even if no snaps are installed; my Xubuntu 20.04 certainly did, though I have now removed all snap related packages including snapd.

I know nothing about flatpacks as I've never used any, but to see your current snap situation run command **snap list** which will show you all.

---

### Post by TheFu on 2021-09-14
> **aug7744 said:**
>  
The folder /run/user/1000/doc/ not is listed if using the command 
df -hT -x squashfs -x tmpfs -x devtmpfs

Then it isn't a real mount. Nothing to be concerned about at all.  Some other program has created a pseudo-location to talk to the OS. It has nothing to do with storage.  I suppose you could figure out the program that created it and perhaps try to do something about it, but it is NOT Linux or core Ubuntu.  

**None of my systems shows this location**, so I'd assume it is something extra that you've installed.  When I look at /run/user/1000/, I see a few named pipes into some system processes.  Named pipes are a way for other processes to communicate with each other.  The formal term is "interprocess communication" - often shortened to IPC.  I wouldn't just remove stuff there.  You need to find the program using it.  Perhaps searching through **lsof** output will provide a hint?
**For example**, /run/user/1000/[COLOR="#FF0000"]pk-debconf-socket[/COLOR]= is a named pipe on my system.
Running
```
$ sudo lsof |grep  [COLOR="#FF0000"]pk-debconf-socket[/COLOR]
```
tells me that systemd (the userid) and lightdm (the process), are reading from /run/user/1000/pk-debconf-socket.   The '=' at the end of the name is added by my ls display settings.  '=' means named pipe.  **ls -F** will show the type of file.

---

### Post by aug7744 on 2021-09-14
sudo lsof |grep  pk-debconf-socket

lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/1000/gvfs
      Output information may be incomplete.
systemd   1159                         augusto   32u     unix 0xffff9cd601d9c000      0t0      27795 /run/user/1000/pk-debconf-socket type=STREAM

---

### Post by TheFu on 2021-09-14
> **aug7744 said:**
> sudo lsof |grep  pk-debconf-socket

lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/1000/gvfs
      Output information may be incomplete.
systemd   1159                         augusto   32u     unix 0xffff9cd601d9c000      0t0      27795 /run/user/1000/pk-debconf-socket type=STREAM

Sorry, but why would you search for pk-debconf-socket when you are interested in a completely different directory?
Please don't copy/paste commands.  Look up what each does first, understand, then run.

---

### Post by vanadium on 2021-09-15
That mount indeed appears related to flatpak: [https://docs.flatpak.org/en/latest/flatpak-command-reference.html#flatpak-document-export](https://docs.flatpak.org/en/latest/flatpak-command-reference.html#flatpak-document-export)

---

### Post by aug7744 on 2021-09-21
Flatpak not is installed.
I only want to not display the folder in Double Commander, but in moment is better disable that folder being displayed in Double Commander.
Thanks for all replies.

---

