---
title: "USB mount point name- Darktable sync on two PCs"
date: 2016-03-24
forum: General Help
---

### Post by vector on 2016-03-24
Hi all,
I use Darktable at two PC locations id like to keep everything in sync across both machines. (rsync)

syncing the .config files works except for the naming of the path to the HD where the images are kept.

PC2 is looking for the images in the wrong folder path.
on PC 1 the path is media/Photos. The hd is an internal drive that i have setup fstab to auto mount on power up.

PC2 uses an external HD to USB docking port (often changed for different jobs)

its path is media/username/Photos.

I tired a few relabel tricks and symlinks but cant get them to work. Not holding my tongue right I guess ;( it either wont let me relabel because its already mounted or the symlink wont create because it dosen't exist.
Obviously I dont know what im doing... 

What is the best procedure?

when I plug the usb drive on Id like it to mount to /media rather than /media/username

running 14.04 on both pcs. Darktable 2.0.2

---

### Post by papibe on 2016-03-26
Hi vector.

There's no perfect solution, but here's a few ideas:

[LIST]
[*]You could create one level of abstraction using symlinks or mount-binds, so that the configuration would be identical on both machines. Foe example, the photo library would be a directory in your home directory which in PC1 would point to /media/Photos, and in PC2 to /media/username/Photos
[*]Another idea: you can specify where a well-know USB disk would mount. Get the UUID and create an entry in /etc/fstab. For instance:
```
# WD My Book external 1TB USB drive
UUID="02D0852FD08529CD" /media/Photos    ext4    noauto 0 0

```
The noauto option will skip mounting the disk at boot in order to  avoid a slow boot when the disk is not connected.
[/LIST]
Hope it helps. Let us know how if that helps.
Regards.

---

### Post by vector on 2016-03-29
Hi papbie,
sorry for the late reply, Easter break and all that.
small problem with a solution I tried using Pictures\Photos as the common symlink point.. 
Darktable is using the entire path when looking for folders_marksymold
.
on PC1 it expects to find image1 for example now via  a symlink in
/home/username/Pictures/Photos which points to media/Photos

When I apply the same trick to PC2
/home/username/Pictures/Photos symlink points to media/username/Photos all should be well

But the username on both machines is not the same so DT for example
PC1 is looking at /home/Bill/Pictures/Photos
but on PC2 there is no Bill only Fred so it cant find the symlink.

I can either change the usernames? to match
or find a spot outside of the user areas  as per your suggestion.

reverting back to the old path where PC1 used the direct /media/Photos
On PC2 I created a symlink in /media called /media/Photos to point to /media/username/Photos
and this works.
One small issue. 
When I use the DT import feature the symlink does not appear in the Places or Devices list. (Of course the USB drive does  but its path is /media/username/Photos)
I have to go to Devices/Computer/media/ where my symlink(Photos) appears.
Is there anyway to get the Symlink to appear in either Places or Devices list on a typical  file folder viewer?
Haven't tried the fstab idea yet. will try that next

---

### Post by vector on 2016-03-29
I tried the fstab approach, works as far as mounting to the /media/Photos2
UUID=123456789 /media/Photos    ntfs    noauto 0 0
then ran mount -a to refresh fstab
plugged in USB drive

BTW the UUID should not be in quotes :)
(I used Photos2 to avoid any confusion with the possibility of it mounting the USB drive as well as my fstab mount)
I expected and found two mount points for the USB drive /media/Photos2 and the /media/username/Photos Of course only the /media/username/Photos appears on the nautilus devices list.
I modified fstab to Photos rather than Photos2 expecting maybe a conflict(but it does seem to be smart enough to overrule the mount on plugin rules) ;)
mount -a to refresh fstab
plugged in USB

All ok I now have /media/Photos and nothing in /media/username/
The Devices list in nautilus and DT folder view selects the wanted path /media/Photos

I think we have a solution. Ill do some more testing and get back
awesome!! :)

---

### Post by vector on 2016-03-29
ahh one last problem
I have two or maybe more(as image capacity expands) USB HDs on PC2, Both hd are labelled Photos and contain the same folder structure as the internal drive on PC1 except that the folders  are split. Lets say folders A-J are on disk 1 and k-Z are on disk2
The internal drive on PC1 is 1TB the two USB drives used on PC2 are 500gb. Folders are image project or event related so I occasionally swap drives.
Thinking I could simply create two UUIDs for the same mount point

UUID=123456789 /media/Photos ntfs noauto 0 0
UUID=987654321 /media/Photos ntfs noauto 0 0

But no, Looks like the system reserves /media/Photos for the first UUID it sees in the fstab
after removing ID 1234.. or even rebooting with ID 9876..  as soon as you click on Photos in devices it errors with cant find UUID 1234..
Its not allowing 987.. to mount at all

So close ;(

any ideas?


What I currently have that seems to work is
sudo ln -s /media/username/Photos/ /media/Photos

Both drives mount on plugin to /media/username/Photos and thus symlink. Dt simply sees /media/Photos and is happy

To get around the no listing on the folders view, I created a  bookmark. I can click that to read a  new folder rather than tunnel down thru Computer/media/

Not sure if this symlink will break or disappear under various conditions.
Its not a clean solution as the the link can break. Is there anyway better?

---

