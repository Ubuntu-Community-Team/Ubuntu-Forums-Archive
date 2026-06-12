---
title: "Command line, connect to a Windows Share"
date: 2007-04-27
forum: General Help
---

### Post by bstan2 on 2007-04-27
Hello all,

I am a new Ubuntu user.  I have used Redhat/Fedora for many years and I personally find that Ubuntu is much easier to use and setup.

One thing that I have not been able to figure out is how to connect to a Windows share via a terminal window.  I do not have smbmount nor do I seem to have CIFS.

Can someone tell me what I need to do?

Thanks!

---

### Post by bstan2 on 2007-04-27
BTW, I am using Feisty Fawn

---

### Post by bAdSkAtEr on 2007-06-13
From back in the day I always mount my SMB shares with a script, which basically calls the command line programs you might be trying to use:

mount -t cifs //server/share /mnt/share -o ro,user=joe,password=XXXXXXXX,uid=joe,gid=joe

I also found this did not work at first.  I wish I had kept notes about what I had to do to get this to work.  The key is package smbclient, available via "apt-get install smbclient".  I am guessing Samba was already installed, but in case it was not either the above command will automatically find samba-common as a requirement, or  you can easily install it via "apt-get install samba-common"

After that, the above mount script worked fine.  (Note, it is part of a script I have been using for years now, updated only to switch from smbfs to cifs a few years back)

The problem I have found is that I cannot get the system to unmount the shares prior to or at a proper time during shutdown.  This was never a problem with RedHat/Fedora, but in Ubuntu (7.04) it hangs the shutdown for about a minute.  Not a big deal, but is a small blemish in an otherwise very nice experience with Ubuntu.

---

### Post by bAdSkAtEr on 2007-06-13
I really should have taken notes...

The smbfs package is the key.  To be sure, I think samba-common, smbclient, and smbfs are all required (maybe not?) but I think smbfs is what got me through: apt-get install smbfs.

---

