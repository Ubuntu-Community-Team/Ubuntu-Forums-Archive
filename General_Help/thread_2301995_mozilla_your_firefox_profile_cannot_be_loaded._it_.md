---
title: "mozilla your firefox profile cannot be loaded. it may be missing or inaccessible"
date: 2015-11-06
forum: General Help
---

### Post by XnP on 2015-11-06
Ubuntu Version 14.04
Skills: low
Issue: after trying updating torbrowser, it didn't update, and as result, unless I start MF as root, gives back the message "mozilla your firefox profile cannot be loaded. it may be missing or inaccessible"
Tried already:
delete .mozilla : didn't work
deleted profile through profile manager: didn't work
change access permissions through "sudo chown -R $USER:$USER ~/.mozilla": didn't work
uninstalled through purge and reinstalled MF: didn't work
recovered from backup: didn't work

I am out of options...
Thanks.

---

### Post by matsuzine on 2015-11-06
Hey, the problem might be the cache. Make sure the mozilla cache directory has the correct permissions since it will give the same error message.

```

# check the permissions
ls -l ~/.cache | grep mozilla

# fix the permissions
sudo chown -R $USER:$USER ~/.cache/mozilla

```

** Edit: added the -R flag to make the command recurse.

---

### Post by efflandt on 2015-11-07
You should **never** run firefox using sudo, because that can give files in your home directory incorrect permissions for root only.

---

### Post by XnP on 2015-11-07
Results:
drwx------ 3 root      root       4096 Aug 20  2014 mozilla
After running:
sudo chown $USER:$USER ~/.cache/mozilla
I had the same results.... Even if I closed FF and ran the command.

Efflandt:
I know :(, unfortunately is the only way I have to start it, and for instance, get to this forum.
Is not by choice...

---

### Post by matsuzine on 2015-11-07
I know this is frustrating. Permissions can be surprising. But I'm pretty sure we're still on the right path. From what I can tell, there are only two directories in local user space:

```
~/.mozilla
~/.cache/mozilla
```

The permissions for those two directories and all subdirectories and files need to be for your local user. So let's try this:

```
sudo chown -R $USER:$USER ~/.mozilla
sudo chown -R $USER:$USER ~/.cache/mozilla
```

I just realized that I forgot to use the -R flag in the command I posted yesterday, which tells chown to change ownership recursively. Try doing both directories at once and let me know the result. Be sure to close the browser before you do it, and don't open it with sudo (which would recreate the directories with the root permissions).

---

### Post by matsuzine on 2015-11-12
Just curious, did you give this lasted answer a try? Did you get it working?

---

### Post by hnoor0044 on 2016-03-08
thinks for sharing information



______________________
NOOR

---

### Post by XnP on 2016-03-20
Thanks matsuzine and all for the help.
Sorry for the late reply. 
To be quite honest, I have a vague reminiscence of whether it fixed or not.. It is so long.
If I recall correctly, after your post, adding the R, it did work.
I now have the latest version of Torrent, and happily using it.
I know, I should have been better at keeping track of it..

Cheers,

Xn.

---

