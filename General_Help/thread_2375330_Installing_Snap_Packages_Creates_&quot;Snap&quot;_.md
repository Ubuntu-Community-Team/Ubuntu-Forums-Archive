---
title: "Installing Snap Packages Creates &quot;Snap&quot; Folder in Home Directory: Hide? 17.10"
date: 2017-10-23
forum: General Help
---

### Post by MrKevin1a on 2017-10-23
I recently installed 17.10 Ubuntu with the Budgie desktop after being on Mint since Unity became a thing.  It's like returning to a place you once lived, and I'd be lying if I said I wasn't a little thrilled to see what has been done with the place.  I'm pretty happy with some of the new features and annoyed at some of the old Ubuntu quirks, but it's nice to be back.

I installed Discord and Brackets via snaps rather than PPA as I would have in the past, but now I have an annoying folder in my home directory called "snap".  Is there any benefit to having this folder named "snap" rather than ".snap"?  I deleted it thinking that maybe it was left over files from the installation, but then I had to log into Discord again because something screwed up.  I assume that also means I can't rename it. :(

My question is: What is this folder used for, and is there a way for me to hide it or move it so it's not in the middle of all my personal files?  Every other folder that get's put in my home directory that relates to functionality rather than my files is already hidden: .mozilla .local .gnome .whatever

---

### Post by again? on 2017-10-23
Use a ~/.hidden file.
Using terminal...
```
echo "snap" >> ~/.hidden
```

You can place one file or directory per line.
The .hidden file only works with files/folders in the same diectory so you don't use full paths in the .hidden file.

eg my ~/.hidden file
```
**glen@GU17:~$ cat ~/.hidden**
operatransfers
libpeerconnection.log
GNUstep
id.txt
ardesia
VirtualBox VMs
Templates
py
LGP-IraCharts
stopwatch
tmp
Examples
bin
#conky-manager
gPodder
football
hwe-support-status
Audio
Steam
src
betty
skel-links
pytut
Todo
FreeFileSync
test.txt
dreamteam
git
Sounds
pytut
snap
```
The files/folders in ~/.hidden can be viewed in the file browser using ctrl+h, like other hidden files.

You can also install the nautilus extension **nautilus-hide**, that utilises the .hidden file and adds options to the right-click menu to hide or unhide files.

---

