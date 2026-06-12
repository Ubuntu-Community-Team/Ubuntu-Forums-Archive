---
title: "browse nfs shares with nautilus?"
date: 2007-09-28
forum: General Help
---

### Post by nix4me on 2007-09-28
Is there a way to get nautilus to browse nfs network shares?

I have not found any gui that can locate/mount nfs shares.

nix4me

---

### Post by gautada on 2007-09-28
Check out Places->Network and/or Places->Connect to Server

---

### Post by nix4me on 2007-09-28
That doesn't handle NFS as far as I can tell.

nix4me

---

### Post by jms1989 on 2007-09-28
I'm going to assume you are referring to the windows ntfs file system. First, the windows system needs to be running and connected to a network and a directory of your choice will have to be marked "shared." Next, in Ubuntu go to, Places -> Network. Now you should see the computer names or look in "Windows Network -> mshome" and you should see the computer names.


If you are wanting to access a ntfs file system under ubuntu, you'll need to mount the partition and then navigate to the directory it mounted at.


Is this what you're asking?

---

### Post by nix4me on 2007-09-28
No.  Not talking about NTFS.

NFS.  Network File System.  Other Unix/Linux shares.

If you type nfs:// in the nautilus location bar, it does not work.

If you type smb:// in the location ba, it does browse to the samba shares perfectly.

nix4me

---

### Post by Zeroedout on 2007-09-28
Hey man, i've been looking too, and it just doens't seem to exist. If you MUST have a gui on the client to connect, I think your best bet is SAMBA (not that samba's bad, i just prefer NFS), However I know how you feel, I really want a gui for NFS as well, however I think we're stuck with the command line for now. It would be sweet as hell if someone could integrate it into nautilus, but [http://live.gnome.org/GnomeVfsPlans](http://live.gnome.org/GnomeVfsPlans) doesn't even mention NFS, so i don't know how probable it is (unless I'm retarded and it already is supported, and one would think that the defacto standard for unix sharing would be! But it's unlikely)

---

### Post by SeanTater on 2007-09-28
I don't mean to sound pro-KDE but Konqueror does have an nfs:// protocol. It's at least worth a shot.. BTW: In my experience NFS shares can take a minute to mount, so it might not be the speediest connection at first..

---

### Post by nix4me on 2007-09-28
Well I hate to say this, but i will say it anyway.  PCLinuxOS has a sweet nfs admin utility.  It's part of the drakeconfig control center.

Maybe I will see about porting it from perl to python and try to get it integrated into Ubuntu.

I suck at coding, so i probably won't be successful.  Perhaps someone else who can code will read this and take some interest.

nix4me

---

### Post by SeanTater on 2007-09-28
I haven't tried that, but right-clicking the folder and sharing it from the properties isn't that bad either..

---

### Post by nix4me on 2007-09-28
Heeheheh.  Sharing a folder and browsing shares is 2 different things.

---

### Post by peos on 2007-10-03
In Nautilus all You need to do is klick on the top menu "go", select "place"
and type the adress like this:
/net/"hostname"/ and you will see all NFS-shares that You are allowed to see
from that host.

Mine is in Swedish, hope "go" and "place" is the correct english names...

Reason you need to type the adress is that the share is only mounted when you
access it, You need to know the hostname. It cannot be browsed for as far as I know.

This is dependeing on a thing called automounter (or autofs), it seems to be correctly
configured from start in the ubuntu installation I have.
If it's not You need to look for packages autofs and the configuration file /etc/auto.master
should have the line auto.net enabled.

Hope this helps.

---

