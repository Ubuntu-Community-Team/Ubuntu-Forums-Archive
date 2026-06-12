---
title: "Usb stick entered in fstab does not mount automagicaly."
date: 2008-03-13
forum: General Help
---

### Post by sneax on 2008-03-13
Hello, I have a usb stick that I would like to mount permanently into my computer. It's used to store a user's home directory so I thought it would be a good idea to put the mount line in fstab so it gets mounted at boot.

The reason is because this user will hold sensitive information, like this the usb stick can be removed easely in case of emergency.

This is the line in fstab:
UUID=d096014a-182a-4c4c-bf71-0da773c8d876 /home/matt auto defaults,errors=remount-ro 0 0

UUID is definately correct (found with 'blkid' command). When the login screen appears I can not log in with user matt (from usb stick) because it is not mounted (for some reason I don't know). When I login as another user existing on the system and through that user I mount the usb disk to /home/matt it mounts without error. I logout and login in matt without problem.

Why does it not automount? Can you help me troubleshoot? Thank you.

---

### Post by kuja on 2008-03-13
Try putting something like "mount -a" in one of the /etc/init.d/..... scripts that you know is going to run, preferably something related, or create another one. This should at least work around it.

---

### Post by FuturePilot on 2008-03-13
If it has a FAT filesystem it will not work as a /home partition.

---

### Post by sneax on 2008-03-13
It is formatted as ext3.

For the workaround, thanks for the idea, I'll google how those init scripts work.

 I just wish I knew why this is happening, is there no way I can find what error it spits out when it runs over that fstab entry?

---

### Post by bodhi.zazen on 2008-03-13
I would move your /home directory to the USB drive , like this:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Note: you can not just "yank" the usb drive out without the possibility of data loss, it has to be unmounted. This it true of both Windows and Linux.

---

### Post by sneax on 2008-03-13
> **bodhi.zazen said:**
> Note: you can not just "yank" the usb drive out without the possibility of data loss, it has to be unmounted. This it true of both Windows and Linux.

Yes, it will only be removed when pc is turned off.

Also, in case of emergency, it's ok if the data might be lost when pulling it out, as long as nobody unauthorised can view the data, it is ok if it's lost.

Also thanks for the link regarding putting the whole /home directory on the stick.

---

### Post by bodhi.zazen on 2008-03-13
From your description you might want to look at encryption.

---

### Post by sneax on 2008-03-16
The solution that I went for is simply installing the whole of ubuntu on an external hard drive, stupid that I didn't thought of this before. Thanks for help, and I'll surely look into how to encrypting that hard disk for extra security!

---

### Post by kuja on 2008-03-16
> **sneax said:**
> The solution that I went for is simply installing the whole of ubuntu on an external hard drive, stupid that I didn't thought of this before. Thanks for help, and I'll surely look into how to encrypting that hard disk for extra security!

Not really optimal ...... It's much easier to encrypt things when your disk is blank, seeing as to encrypt you're going to be erasing everything and overwriting it with random data! You might want to consider doing it now before your drive is loaded up with important things to miss if possible, if it's not already too late for that. With regards to doing the encryption, the easiest way will be to install ubuntu with the alternate cd or the dvd (text mode install option). When you get to the partitioning phase, you can either opt to do it guided (sub-optimal, but it should work), or to do it manually (Takes a little more time plus getting used to the interface, but it's a good idea so you can put /home on a different partition (which I would highly recommend)). I think to do it manually it runs something like this (with a blank disk): create a partition, choose the size you want (/ (root) I'd say about 8-15GiB) , probably about 1GiB for swap (when doing the swap, still set the type to encrypted, but change the one option from passphrase to random),  home could probably be the rest of it if it's not a server, and the type should be encrypted somethingrather (there's only one option with encrypted in the name, and it'd be it). Then, in the main partitioning menu, there should be a set up encrypted partitions option, do it next. It could take a long time to run, maybe even hours. When it's done randomizing the disk and setting up the blocks, you'll create the actual partitions inside the new encrypted devices, of which there should be 3 (root, swap, home). From here it's manual partitioning as usual. (create partitions in each, of the pseudo devices, default would be ext3 for / and /home, though xfs/jfs/ext2/reiserfs3 can also be used. Swap you just choose swap for the type and voila, done)

Note: whenever it lets you choose your passphrase(s), you should choose a [strong password](http://www.google.com/search?client=opera&rls=en&q=wikipedia+choosing+a+strong+password%7Cpassphrase&sourceid=opera&ie=utf-8&oe=utf-8)

---

