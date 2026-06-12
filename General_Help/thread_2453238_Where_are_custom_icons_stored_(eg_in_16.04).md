---
title: "Where are custom icons stored (eg in 16.04)"
date: 2020-11-05
forum: General Help
---

### Post by col48 on 2020-11-05
Running in 16.04... I want to change the icon (in Nautilus/Nemo, on desktop) which identifies a particular file.  This is independent of the mime type.

Up to about two years ago, I could do this by pulling up the Properties, clicking on the image of the icon shown there, navigating to the desired png file and clicking Open.  It is still possible to go through the motions but it now has no effect on the icon displayed there or that used when listing files in nautilus or nemo.  Furthermore the custom icons I had set more than two years ago were lost as far as nautilus/nemo are concerned.

On another site, I recently came across this Terminal command which purports to do what I want
```
gvfs-set-attribute -t string <path to target file> metadata::custom-icon file: <path to desired icon>
```
but it doesn't do the job for me.  To run it at all I have to run it with sudo (that's unexpected?) and it then says that custom-icon is unsupported.

Another fragment of evidence:
I have an old 12.04 bootable partition on the same HDD.
I used to change icons in 12.04 with no problem, so I logged into 12.04, and was able to look at the 16.04 file and change its icon (using a png stored on the 16.04 file system).
But that change is only visible in the 12.04 environment.  I'm not surprised that when I rebooted into 16.04 it was using the old icon once more.  Just sad.

So why can't I change the icons in 16.04?  Where should the association be stored?  Is there an obscure permissions issue?  Can I learn anything useful from the 12.04 experience?

---

### Post by col48 on 2020-11-06
Well, well!
This turns out to be very simple to solve - although I don't know why the it happened.

I did not have read or write permission to ~/.local/share/gvfs-metadata/home 
This 'home' file is a Text file (mainly not human readable), nothing to do with the home folder which sits above the users' home folders
All the other files in the gvfs-metadata folder were owned by me and in the group with my username.
Once I made 'home' conform to this, the problem disappeared - and files which had not been changed over the last couple of years suddenly also got their custom icons back.

**So this is where Nautilus/Nemo finds which *_custom_* icon to show for a file, if there is one.**
Since there has never been a problem with the icons in a panel on the desktop, the mechanism for this must be different.

There is only one user on my machine, so that's works for me, but perhaps there is some more general mechanism to cover files shared between a number of users, who may not be in the same user group.

PS: I haven't tried the Terminal command since changing the ownership - I no longer need to!

---

