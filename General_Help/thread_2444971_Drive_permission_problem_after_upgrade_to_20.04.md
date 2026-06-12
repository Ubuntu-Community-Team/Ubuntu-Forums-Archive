---
title: "Drive permission problem after upgrade to 20.04"
date: 2020-06-07
forum: General Help
---

### Post by judykerr3d on 2020-06-07
[COLOR=#242729][FONT=Arial]I have a secondary internal drive that I use for storing old files. After upgrading to 20.04 a week or so ago, I can access this drive fine using the "Files" application - I can read, write, rename or delete its files and folders - but if I try to access it via other applications I get Permission Denied. For example, I can't upload a file from this disk using a browser, or open an image file from it with GIMP. Copying the files to my home directory using "Files" and accessing them from there works, but it's annoying to have to do that. I didn't have this problem before the upgrade, and I've not changed anything to do with the disk's definitions or its permissions. 
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I've had a look at the disk's entry in fstab, and it looks fine to me:
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]/dev/sda5 /media/Loft ntfs defaults,umask=000,uid=1000,gid=1000,auto,rw 0 0
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The uid of 1000 is the correct one for my user id.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The entry in smb.conf also looks OK:
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][Loft][/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]path = /media/Loft[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]available = yes[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]valid users = ZZZZZ (where ZZZZZ is my correct user id)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]browsable = yes[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]public = yes[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]writable = yes[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
When I use the Brave browser to try to navigate to the file I want to upload, I get a list of directories that includes /media (but not /media/Loft), and if I try to open /media I get: 
Could not read the contents of media Error opening directory '/media'permission denied
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]/media is owned by root but has r-x permissions for rest-of-the-world. I can open a terminal and cd into /media with no trouble.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Loft is owned by my userid, and has rwxrwxrwx permissions so I would expect Brave under my userid to be able to open /media to get into Loft, and from there to be able to read a file for upload 


I'm wondering if this problem might be to do with apparmor, as I found these messages in the syslog just after a failed attempt to upload a file using Brave.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Jun 6 11:03:43 xxxxxx kernel: [ 4975.486583] audit: type=1400 audit(1591437823.332:91): apparmor="DENIED" operation="open" profile="snap.brave.brave" name="/media/" pid=3656 comm="pool" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Unfortunately I know nothing about apparmor, so I don't know whether it is an apparmor setting that is causing this, or whether it's the fact that I'm not getting the full path (/media/Loft) coming up when I try to navigate to the file I want to upload.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Does anyone have any ideas?

UPDATE:
I've installed the latest version of Firefox, and I don't have any issues uploading files from /media/Loft using this. The navigation page I get when using Firefox shows Loft as a directory on its own and when I select that, it works OK. I also went back and had a look at GIMP again, and I now see that the navigation window in that includes both paths - /media and /media/Loft. I missed that the last time. Selecting /media/Loft works. 

So it looks as though something does not like apps directly accessing the root-owned /media... perhaps? I still have the problem uploading with Brave, but I'm not sure whether it's Brave that constructs the list of available directories in the navigation window, or whether it's Ubuntu passing them across differently. I presume that Brave should be showing either Loft or /media/Loft as a directory for the access to be granted. I'll raise this issue on the Brave forum, but if anyone here can explain why the list of paths and directories varies according to which app you use, I'd be very interested to find out. 
[/FONT][/COLOR]

---

### Post by CatKiller on 2020-06-07
> **judykerr3d said:**
> if I try to access it via other applications I get Permission Denied. For example, I can't upload a file from this disk using a browser, or open an image file from it with GIMP. Copying the files to my home directory using "Files" and accessing them from there works, but it's annoying to have to do that.

Are you using snaps? They need you to allow them access to files outside your home directory, because they're sandboxed.

---

### Post by judykerr3d on 2020-06-07
> **CatKiller said:**
> Are you using snaps? They need you to allow them access to files outside your home directory, because they're sandboxed.

Hi! Thanks for the answer, but I've no idea what counts as a snap. I've just updated my post, as I installed Firefox and tried with that, and I don't get the problem. I didn't give Firefox any special access.

---

### Post by CatKiller on 2020-06-07
> **judykerr3d said:**
> Hi! Thanks for the answer, but I've no idea what counts as a snap. I've just updated my post, as I installed Firefox and tried with that, and I don't get the problem. I didn't give Firefox any special access.

Well, you have installed Brave as a snap:
```
profile="snap.brave.brave"
```

Snaps are containerised applications independent of the system they're installed on, and access into and out of the sandbox can only happen through defined interfaces. There's an interface for access to removable media, but it's not enabled by default. 

I understand that you can set permissions for your snaps through the software centre, but I don't use snaps and I haven't upgraded to 20.04 yet, so I couldn't tell you exactly where.

An alternative to allowing the access is to remove the snap and install a traditional package. Both are available through the software centre.

There's more information about snaps [here](https://snapcraft.io/docs/getting-started).

---

### Post by judykerr3d on 2020-06-07
> **CatKiller said:**
> Well, you have installed Brave as a snap:
```
profile="snap.brave.brave"
```

Snaps are containerised applications independent of the system they're installed on, and access into and out of the sandbox can only happen through defined interfaces. There's an interface for access to removable media, but it's not enabled by default. 

I understand that you can set permissions for your snaps through the software centre, but I don't use snaps and I haven't upgraded to 20.04 yet, so I couldn't tell you exactly where.

An alternative to allowing the access is to remove the snap and install a traditional package. Both are available through the software centre.

There's more information about snaps [here]("https://snapcraft.io/docs/getting-started").


Thanks for that. I've had a look, and I've definitely never visited the snap store. I've had Brave on Ubuntu for at least 3 years now, and I can't remember how I installed it, but it would probably have been via Software Centre. I suppose I might have selected the snap version instead of the traditional package by mistake, though. So I guess I now need either to uninstall it and replace it as a traditional package, or find out how to set permissions for it. Should keep me busy for a while.  :-(

Much appreciate your help, that's given me a direction to head in.

---

### Post by CelticWarrior on 2020-06-07
Just search for it in the software store app and you'll see a "permission" button. Enable read/write to mass storage devices. There's also a command for that.

---

