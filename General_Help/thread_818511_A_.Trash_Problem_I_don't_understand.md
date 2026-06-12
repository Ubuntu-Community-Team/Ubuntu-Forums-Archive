---
title: "A .Trash Problem I don't understand"
date: 2008-06-04
forum: General Help
---

### Post by terryj82 on 2008-06-04
...I don't have one.

I just switched to Ubuntu last week and I'm still getting my feet wet. My problem:

In the Gnome desktop environment, I have a trash icon, I can send files there, and delete them, but I don't have a .Trash folder ANYwhere on my file system. This only became a problem when I have a few files left over from an installation that refuse to be deleted, says I don't have permission. I can't manually change the permissions either.

It gets even weirder for me. Since I couldn't find a *Trash folder anywhere, I checked the location of these undeletable files and it tells me they're located in trash:///

Where on earth is that, and how do I delete these files and establish a NORMAL *Trash folder like everyone else?

Any help would be greatly appreciated, Thanks.

---

### Post by danwood76 on 2008-06-04
Try here:
~/.local/share/Trash

---

### Post by drs305 on 2008-06-04
This command will show you where your trash directories are located. You can open your file browser with *gksudo* to delete them:

```
sudo find / -type d | grep  Trash/files
```

Then edit them with:
```
gksudo nautilus
```

---

### Post by terryj82 on 2008-06-04
I love you both. :)

The other part of my problem: Why don't I have a *Trash dir like everyone else? any idea how to set things right?

---

### Post by Fixman on 2008-06-04
> **terryj82 said:**
> I love you both. :)

The other part of my problem: Why don't I have a *Trash dir like everyone else? any idea how to set things right?

Because Hardy uses a new GNOME version, where the trash is in a different place.

---

### Post by terryj82 on 2008-06-04
danwood was right, the files were there. but...

I tried deleting the files from that shared folder and they reappear right back in it with another .2 suffix.

I followed drs305's method and it pointed to that exact folder danwood pointed out to me. I ran nautilus and I can't find /terry dir. The Home is /root (I'm assuming it's because its not user specific, right?) Well, /home/terry/.local/share/Trash/files is where they are at, and Under Nautilus I can't find this dir.

Anything else that could help me, guys? Thanks.

---

### Post by ibuclaw on 2008-06-04
And the new naming conventions are all part of the new gnomevfs system.
Which is a new attempt at integrating all devices, both local and remote:
ie:
[LIST]
[*]file:/// - is your filesystem.
[*]trash:/// - is your trash folder.
[*]cdda:/// - is your cd drive.
[*]smb:/// - is a samba mount.
[*]dav:/// - is a webdav mount.
[/LIST]

We'll see where it leads up in the future, but for the most. It's all very interesting technologies indeed. :)

Regards
Iain

---

### Post by drs305 on 2008-06-04
Do you have the view hidden files option enabled? View, Show Hidden Files, checked. Any file or folder starting with a . is a hidden file. Of course, that would not explain why you can't see /home/terry  With sudo nautilus, I get to the home folder by clicking on File System, Home, then you should see the user's home folder. Also at that point you can see (one of your) root trash folders as well.

---

### Post by terryj82 on 2008-06-04
Yea, I have hidden files enabled, from .dbus to .wapi, but no .local

sigh.

---

### Post by CameO73 on 2008-06-04
Have you tried Shift-Delete (skip trash)?

Or else, in a terminal:
```

cd ~/.local/share/Trash/files
rm * -R
cd ..
cd info
rm *

```

This should clear any stuff you have in your Trash (the /files folder has the actual deleted files, the /info folder some extra information about the deleted files).

---

### Post by terryj82 on 2008-06-04
sift delete skip trash? pardon the newbness, but Im not familiar with what you're referring to.

---

### Post by drs305 on 2008-06-04
Ok, rereading from the top i'm starting to get a handle on your problem. the reason you are getting the .2 in the trash is you are just hitting the delete button to delete something that is already deleted. so ubuntu deletes it, you see it disappear momentarily while ubuntu repositions it to .... the trash folder. if you are using nautilus (or gksudo nautilus) you can *remove* those files by deleting the parent .Trash folder. Don't worry, it will reappear the next time you delete something, but it will be gone for now and will start empty the next time.


Just saw CameO73's entry. His SHIFT-DEL key combo will permanently delete without sending it to the trash. So earlier if you had used SHIFT-DEL and clicked on the files, even if they were already in the trash, they would have disappeared.

---

### Post by terryj82 on 2008-06-04
through nautilus there is no .local/ folder, which is where my Trash folder seems to be located. I can't do anything until I find that trash folder WITHIN Nautilus. Even with hidden files on, the .local/ dir  doesn't show up. it says it's located in /home/terry/.local

I'm totally at a loss here . :(

---

### Post by Het Irv on 2008-06-04
when you use sudo nautilus, you are running nautilus as root and therefor get the root home folder.  To get to your personal home folder, you need go into the filesystem and go to "/home/whatever/.local"

---

### Post by drs305 on 2008-06-04
> **terryj82 said:**
> through nautilus there is no .local/ folder, which is where my Trash folder seems to be located. I can't do anything until I find that trash folder WITHIN Nautilus. Even with hidden files on, the .local/ dir  doesn't show up. it says it's located in /home/terry/.local

I'm totally at a loss here . :(

Okay, try running this command since you said *find* was able to locate it (i.e. the computer knows the file is there):
```
gksudo nautilus /home/terry/.local
```

By the way, running CamO73's terminal commands should have deleted the files. You should still be able to see *.local* and beneath it *share*. If you delete something new, then two new subfolders, *info* and *files* should appear.

Please mark this solved once your issue is resolved.

---

### Post by terryj82 on 2008-06-04
Horray! Problem solved, looks permanently now. The files haven't come back. Thanks for dealing with me, guys, I appreciate it a lot. :)

---

### Post by Shmalignant on 2008-06-05
This thread helps me too.  Thanks people!

---

