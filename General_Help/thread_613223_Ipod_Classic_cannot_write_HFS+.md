---
title: "Ipod Classic cannot write HFS+"
date: 2007-11-14
forum: General Help
---

### Post by cybergeo3 on 2007-11-14
Hello,

I've been trying to get an 80gb ipod classic to successfully work on my feisty machine with either amarok or gtkpod, or both.  It was initially setup on a windows machine, and when i first connected it in ubuntu, the ipod could be accessed fine, I was able to copy all the songs off it, the problem is afterwards the ipod no longer thought i had any music on it.  It new it had 60 gb's of data, but no songs.

The issue is that I open gtkpod, and it cannot read the itunesDB.ext.  So I searched online and tried various recommendations on forums, nothing worked.  I factory reset it with a mac to see if that helped, it did not.  

So my current is this.  I open gtkpod and get the following window:
[I]Could not find iPod directory structure at '/media/iPod'.
If you are sure that the iPod is properly mounted at '/media/iPod', gtkpod can create the directory structure for you.
Do you want to create the directory structure now?[/I]

I click yes and it tells me 
*Error initialising iPod: Problem creating iPod directory or file: '/media/iPod/iPod_Control'.*

I assume this is because the ipod is read only.  This is what I see when I type dmesg | tail:
[ 3384.906837] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 3384.911014] sd 5:0:0:0: [sdc] 19488471 4096-byte hardware sectors (79825 MB)
[ 3384.913290] sd 5:0:0:0: [sdc] Write Protect is off
[ 3384.913295] sd 5:0:0:0: [sdc] Mode Sense: 68 00 00 08
[ 3384.913297] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 3384.913302]  sdc: [mac] sdc1 sdc2
[ 3384.949093] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[ 3384.949140] sd 5:0:0:0: Attached scsi generic sg4 type 0
[ 3385.711332] hfs: write access to a jounaled filesystem is not supported, use the force option at your own risk, mounting read-only.
[ 3448.095687] usb 4-6: USB disconnect, address 6

I attempted to add the following line to fstab, but this only resulted in the ipod no longer mounting at all, it would say the mount point /media/iPod did not exist, so i deleted it:
/dev/sdc2     /media/iPod   hfsplus     noauto,users,rw,sync,nodev,umask=0000     0 0

I literally posted this message as a last result, I know there's a ton of posts out there about this issue, but really all I want is the ipod to be able to sync with amarok or gtkpod.  I can supply more info, please just let me know.  Thank you for any help, it would be unbelievably appreciated!!

---

### Post by cybergeo3 on 2007-11-16
Does anyone have any ideas?  Has anyone successfully gotten an IPOD classic to work with ubuntu?  If you did, what did you do?  I am willing to try anything, I can reformat my IPOD in windows so if the HFS+ is a problem, that can be taken away.  Thanks.

---

### Post by mattack on 2007-11-16
There is no fix at this time...
Apple introduced a new "feature" with the latest generation of iPods. There is a new hash checked against the iPod database. It appears to prevent 3rd party apps (like Amarok or GTKPod) from writing to the database.

See the following articles for more details:
[http://apple.slashdot.org/article.pl?sid=07/09/14/1831236]("http://apple.slashdot.org/article.pl?sid=07/09/14/1831236")
[http://ipodminusitunes.blogspot.com/2007/09/apple-cuts-us-off.html]("http://ipodminusitunes.blogspot.com/2007/09/apple-cuts-us-off.html")

---

### Post by cybergeo3 on 2007-11-16
Thanks for replying, I believe there is in fact a fix, the newest builds of amarok and gtkpod appear to circumvent this hash apple built in, the problem I am having is I cannot get my ipod formatted in hfs+ to become writeable.  I followed this walkthrough [http://neoaddict.wordpress.com/2007/09/26/updating-libgpod/](http://neoaddict.wordpress.com/2007/09/26/updating-libgpod/) and got all the way to where i add the firewire id to the file, but since i can't mount with write access i get denied.  I'm going to try to reformat the ipod with a windows machine, and try again, but I know people have successfully worked around the issue, I just need to mount the ipod with read and write access.  Thanks.

---

### Post by misterwhite on 2007-11-27
Had the same trouble, and with a bit of googling, I came up with the following.

Find an OS X box and fire up a terminal. grab yourself root and:

  # diskutil disableJournal theIpodVolumeName

that should ensure that journaling is disabled on the ipod. works like a charm now.

HTH

---

### Post by Wobblybob on 2007-12-08
try this :
[[COLOR="Purple"]**http://ubuntuforums.org/showthread.php?t=619615&highlight=ipod+classic**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=619615&highlight=ipod+classic")          
I now have my iPod classic black 80GB running on my Gusty Intel PC thanks to these guys.

---

