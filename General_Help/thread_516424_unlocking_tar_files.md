---
title: "unlocking tar files"
date: 2007-08-03
forum: General Help
---

### Post by doctorbrowder on 2007-08-03
Maybe if I just keep asking enough questions, I'll figure out Ubuntu eventually...

Here's another one...

I've downloaded the ClamAV file as a "tar.gz" file to my desktop. Now, how do I install it? On the download website ([http://clamtk.sourceforge.net](http://clamtk.sourceforge.net)) it gives the installation instructions as follows-
(in the terminal)
tar -xzf clamtk-2.99.tar.gz
chmod +x clamtk-2.99/clamtk
sudo mv clamtk-2.99/clamtk/usr.bin

OK, so I tried that. I opened up the terminal, and entered
tar -xzf clamtk-2.99.tar.gz
then my password, and the terminal then spit out this message-

tar: clamtk-2.99.tar.gz: cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

So, exactly how do I open up a tar.gz file correctly? What did I do wrong? If tar can't find it, then where do I put the tar file such that it can be found? Thanks!

---

### Post by 505 on 2007-08-03
first of all, where did you save the file? Navigate to that directory first, then you should be able to extract it using that command. E.g, if you saved it on the desktop, do 'cd Desktop' first.

---

### Post by forestpixie on 2007-08-03
I imagine that it's as simple as not being in the right directory - so before you follow their instructions do 

```
cd Desktop
```

in a terminal then - just to make sure your in the right place
```

dir
```

as long as your .tar shows up carry on with the instructions- check that file name you have downloaded is same as that in the command

[COLOR="Red"]clamtk-2.99.tar.gz[/COLOR]  refers to the name of the file you have on your desktop - make sure they're the same

make sure you cd to Desktop not desktop

Edit - slow again :)

---

