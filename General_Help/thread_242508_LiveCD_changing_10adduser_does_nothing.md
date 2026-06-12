---
title: "LiveCD: changing 10adduser does nothing?"
date: 2006-08-23
forum: General Help
---

### Post by ferret on 2006-08-23
I was customizing my LiveCD by [this guide](https://help.ubuntu.com/community/LiveCDCustomization/6.06) and everything seemed to be working perfectly. I squashed and mkisofsed up the CD and burned it without error.  But I made modifications to the usr/share/initramfs-tools/scripts/casper-bottom/10adduser file, to untar a tarball of useful files into the user's new home directory, and to change the USERNAME from ubuntu to "synx".  None of those modifications showed up in the resulting CD, and I even changed the "Adding LiveCD user" message to "Adding LiveCD synx" and still no change. It's as if I never modified the script at all, or if I was using an old disk image somehow.  Other files though, such as the loading screen and the desktop background, did remain changed and persisted all the way to the disk image.

I'm going to make 100% sure my squashfs filesystem is deleted, my cd ISO is deleted, and then recreate the whole thing yet again, but my computer is a 1.2GHz/800FSB with not much RAM, and a slow hard disk, so it takes half the day to complete the operation.  If this time the changes I made to 10adduser do indeed result in a liveCD untarring the files I need during startup into the user's directory, I will report it here. If anyone sees anything in this report that I'm doing horribly wrong though, please let me know.

In 10adduser I added something like this:
```
chroot /root tar xzf /root/skeleton.tar.gz -C /home/$USERNAME/
```

---

### Post by ferret on 2006-08-25
I'm sorry to say that even after deleting the squashfs file, even after deleting the CD ISO file, even after making sure that usr/share/initramfs-tools/scripts/casper-bottom/10adduser was changed to "Adding LiveCD synx", and then making the squashfs, the md5s, and the CD ISO, it _still_ displayed "Adding LiveCD user..." when I tried it in qemu, not "Adding LiveCD synx".  ](*,)

Any ideas anyone?  :confused: Where the heck is it getting the text "Adding LiveCD user" at all?  Why is it when I modify the 10adduser script, then do the CD creation process, it remains unchanged?  The only thing I can think at this point is that the "Adding LiveCD user" message is somehow internationalized and is hiding in a .po file somewhere, but I don't want to waste another CD just to see whether my silent commands are working, if my noisy commands refuse to change the LiveCD message.

---

### Post by ferret on 2006-08-25
Okay, after combing through files I found the 10adduser script embedded in initrd.gz.  In the tutorial I mentioned above, I noticed it say:> mkinitrdfs -o /initrd.gzI hadn't read that before. :oops:  So I'll just go see about getting mkinitrdfs... hmm, on my system it's mkinitrd that's not a good sign.  Oh no, I'm supposed to use mkinitramfs now.  And... undocumented support to specify the non-active kernel version as a command line parameter... yay it worked! I'm creating the ISO now, but I won't be able to test it until I get to my home computer. I'm not cruel enough to try to run qemu over a VNC. Well...maybe I am... no! Bad ferret!

---

### Post by ferret on 2006-08-25
Yes!  Success!  After running mkinitramfs chrooted into the working directory for the LiveCD, it finally showed the modified initialization. Everything worked perfectly on qemu! Now all I have to do is wait until tonight to test it out on a real CD.  Thanks so much for your help everyone. :cry: I don't know what I would have done without you.

---

