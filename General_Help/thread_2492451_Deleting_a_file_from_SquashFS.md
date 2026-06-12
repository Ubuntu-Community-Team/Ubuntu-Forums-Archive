---
title: "Deleting a file from SquashFS"
date: 2023-11-11
forum: General Help
---

### Post by surmi on 2023-11-11
Please tell me how best I can delete the file that is located at the path: /snap/gtk-common-themes/1535/share/icons/Papirus-Dark-Maia/16x16/places/folder.svg. I tried to change the permissions, but not It turns out that the system has read and execute rights. I have Linux Ubuntu 22.04. I found one way, do you think it works and is safe? If there is a way to do it quickly, please tell me about it. The method itself:
#Unzipping SquashFS
unsquashfs folder.squashfs

# Deleting a file
rm extracted_fs/path/to/folder.svg

# Recompress SquashFS
mksquashfs extracted_fs new_folder.squashfs

---

### Post by Rubi1200 on 2023-11-11
I'm curious...why do you want to do this?

---

### Post by MAFoElffen on 2023-11-11
??? But that "there' is not persistent, nor it is really where that exists. When it is first started, that gets decompressed to there to run from, but that is not where it was downloaded to / installed to.

I know how to change and edit those... Just like you would to edit or change any other image files that get decompressed and mounted to a system... But you know that in the next update, that will be copied over and all those changes will be lost, right?

This goes back to the last post, where he asked you "why" you think you need to???

---

### Post by surmi on 2023-11-12
> **Rubi1200 said:**
> I'm curious...why do you want to do this?
The photo I want to delete (there are more than 100 of them) remains from the deleted browser. I want to reinstall the browser and there will be even more such photos in the system, firstly, I don’t like that there will be unnecessary photos, and secondly, I want to gain experience in deleting such files in the SquashFS system

---

### Post by surmi on 2023-11-12
> **MAFoElffen said:**
> ??? But that "there' is not persistent, nor it is really where that exists. When it is first started, that gets decompressed to there to run from, but that is not where it was downloaded to / installed to.

I know how to change and edit those... Just like you would to edit or change any other image files that get decompressed and mounted to a system... But you know that in the next update, that will be copied over and all those changes will be lost, right?

This goes back to the last post, where he asked you "why" you think you need to???
I'm new to Linux and don't know how saving works on SquashFS system, I just want to delete photos. As I understand from your message, even if I delete the photos, they will be restored? But I deleted the browser (the browser installed these photos) and it turns out the photos should disappear forever.

---

### Post by MAFoElffen on 2023-11-12
Look at this:
```

s-name="SnapNameHere"
s-version=$(snap list | grep 's-name' | awk '{print $3}')
ls -lah /var/lib/snapd/snaps/$s-name_$s-version.snap
sudo systemctl stop "snap-$s-name-$s-name.mount".
sudo /usr/lib/snapd/snap-discard-ns $s-name
mkdir /tmp/modifying-snap-dir && cd /tmp/modifying-snap-dir
sudo chmod o+r '/var/lib/snapd/snaps/$s-name_$s-version.snap'
unsquashfs -d snap '/var/lib/snapd/snaps/$s-name_$s-version.snap'
## Do your modifications! All the Snap's files will be located in the directory you created.
sudo rm -f '/var/lib/snapd/snaps/$s-name_$s-version.snap'
sudo mksquashfs snap '/var/lib/snapd/snaps/$s-name_$s-version.snap' -noappend -comp lzo -no-fragments.
sudo systemctl start "snap-$s-name-@s-version.mount".
rmdir /tmp/modifying-snap-dir

```
But... every 2 weeks or so, the FireFox Snap get's updated and triggers an update. When the update downloads and installs, it gets installed to a new directory, with the version changed in that path, and a symlink gets changed poining to it, then it copies the old data, ito the persistent storage of the new Snap.

So every two weeks, if you wanted that change, you would have to redo all that work again. It doesn't make sense to me for somethng that gets updated that often. 

When a Snap extracts and mounts, it goes to a loop device. That loop device is in memory, not actual disk space. A Snap application includes all dependencies it needs for itself... Which means that some things are going to be there, duplicated. This has been brought up as seeming to be "something"... But Canonical seems to think that that the many advantages outweigh a few things that don't seem to... Well. That's the way it is right now.

---

### Post by surmi on 2023-11-12
> **MAFoElffen said:**
> Look at this:
```

s-name="SnapNameHere"
s-version=$(snap list | grep 's-name' | awk '{print $3}')
ls -lah /var/lib/snapd/snaps/$s-name_$s-version.snap
sudo systemctl stop "snap-$s-name-$s-name.mount".
sudo /usr/lib/snapd/snap-discard-ns $s-name
mkdir /tmp/modifying-snap-dir && cd /tmp/modifying-snap-dir
sudo chmod o+r '/var/lib/snapd/snaps/$s-name_$s-version.snap'
unsquashfs -d snap '/var/lib/snapd/snaps/$s-name_$s-version.snap'
## Do your modifications! All the Snap's files will be located in the directory you created.
sudo rm -f '/var/lib/snapd/snaps/$s-name_$s-version.snap'
sudo mksquashfs snap '/var/lib/snapd/snaps/$s-name_$s-version.snap' -noappend -comp lzo -no-fragments.
sudo systemctl start "snap-$s-name-@s-version.mount".
rmdir /tmp/modifying-snap-dir

```
But... every 2 weeks or so, the FireFox Snap get's updated and triggers an update. When the update downloads and installs, it gets installed to a new directory, with the version changed in that path, and a symlink gets changed poining to it, then it copies the old data, ito the persistent storage of the new Snap.

So every two weeks, if you wanted that change, you would have to redo all that work again. It doesn't make sense to me for somethng that gets updated that often. 

When a Snap extracts and mounts, it goes to a loop device. That loop device is in memory, not actual disk space. A Snap application includes all dependencies it needs for itself... Which means that some things are going to be there, duplicated. This has been brought up as seeming to be "something"... But Canonical seems to think that that the many advantages outweigh a few things that don't seem to... Well. That's the way it is right now.
thanks for the help:).
But even if the photos are restored, I want to know a way to delete them.

---

### Post by MAFoElffen on 2023-11-12
The thing about Snaps pulling in all their own dependencies, the Snap app itself point to those resources within it's own sandbox. In that way, it is sort of like a container. So even though things are duplicated in other places of the system, that Snap app only sees the resources it is pointed to, not what is outside that sandbox. So if you do delete it, that Snap app is going to get a file-not-found error, because that is no longer there, in the location it expects it...

I told you "how" to do that... But: "*Just because something is possible, doesn't make it a good idea.*"

You now "know a way to delete it"... _But I would recommend against that._ Go ahead if you are dead-set on doing that. If it has an error (which I believe it will), remove it and then reinstall it. But what you do is on you.

---

### Post by surmi on 2023-11-12
> **MAFoElffen said:**
> The thing about Snaps pulling in all their own dependencies, the Snap app itself point to those resources within it's own sandbox. In that way, it is sort of like a container. So even though things are duplicated in other places of the system, that Snap app only sees the resources it is pointed to, not what is outside that sandbox. So if you do delete it, that Snap app is going to get a file-not-found error, because that is no longer there, in the location it expects it...

I told you "how" to do that... But: "*Just because something is possible, doesn't make it a good idea.*"

You now "know a way to delete it"... _But I would recommend against that._ Go ahead if you are dead-set on doing that. If it has an error (which I believe it will), remove it and then reinstall it. But what you do is on you.
[h=2]Thanks a bunch;)[/h]

---

### Post by MAFoElffen on 2023-11-12
You are welcome. If your question is answered, you can mark your thread as "Solved", by Selecting the "Thread Tools" link in the upper right of this page.

---

