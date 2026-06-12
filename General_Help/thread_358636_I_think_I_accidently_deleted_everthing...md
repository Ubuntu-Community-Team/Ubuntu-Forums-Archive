---
title: "I think I accidently deleted everthing.."
date: 2007-02-11
forum: General Help
---

### Post by norty32 on 2007-02-11
I had 2 partitions on a 140 gig hd. 1 partition was for windows xp and it was 10 gigs, the rest was for all my data. I decided to install unbuntu so I used gparted live cd to resize the 130 gig into 1 10 gig for which I mounted the root file system of unbuntu and another 4 gig that i used for the swap partition. Everything installed fine but when I went back to into xp I can only see my 1 10 gig partition, I cannot get to my now 125 gig partition with all my data on it! How do I get it back?!

edit - I found out that the parition with all my data on it is in linux-swap format...

---

### Post by mykalreborn on 2007-02-11
it most certainly is not in linux swap format. maybe ext2/3 or reiserfs, but not linux swap. also it's not worth having a 4 gig swap partition. 
i think you should read this:[http://tldp.org/HOWTO/Partition/](http://tldp.org/HOWTO/Partition/)

---

### Post by norty32 on 2007-02-11
how do i get my data back though?

---

### Post by mykalreborn on 2007-02-11
can you still see it in linux?

---

### Post by kevinf311 on 2007-02-11
Wowser, do you remember what you chose from the drop down menus in gparted?

It sounds like you took the partition with your data on it and formatted it to become your new root partition for Ubuntu. If that is the case then yes, you have deleted your data. If you installed Ubuntu to another partition than the one that had your data on it, then it should be there somewhere, pending you did not format the partition.

If the partition was formatted then you may have to find a program/shop that can recover lost data from formatted drives. I think that when a drive is formatted from software, the original data is not so much lost as written over. I had a friend who borked his system a while back and found a way to recover the data. If I see him, I'll ask him what it was he used.

There is a program called [FS-Driver]("http://www.fs-driver.org/") that allows windows to read/write to ext2 partitions. ext3 (and 2 as well, I think) are file systems that are available for use when installing Ubuntu from the CD. ext3 is like ext2, but with a journaling system incorporated to guard against data errors. My preferred partition setup is as follows:

[-windows_ntfs-][----/home_ext3------][-Linux_ext3][swap]

With this setup and FS-Driver, you can store all of your data/media/documents in the /home partition and access them from both windows and Linux. In the event that your system goes south, you can re-install (electing not to format the /home partition, but defining it as /home in the install) without loosing your data or program settings. I have had to do this once, and am glad I set it up this way.

Did you back up any of your data before you started the process? If you have a fairly recent backup and aren't loosing any vital files, I'd say just start from scratch (leaving your windows installation as is of course). 

Good luck in recovering your data and I will post back if I happen to find something else or get in touch with my friend.

---

### Post by norty32 on 2007-02-11
nope I didn't back anything up.. i know it was stupid.. but is there any hope of getting it back?

---

### Post by kvonb on 2007-02-11
You could run the qparted CD again and look at the partition sizes.

If as you believe the NTFS was changed to a Linux swap, all you should have to do is change it back to NTFS.

I say "should" because if it was formatted at install time, (which from memory the swap IS formatted by default), then you might be in trouble.

There are several progs available that I have used to recover deleted data, but they are commercial.

Ones that spring to mind are: "recover my files", "active partition recovery", "getback NT".

Just remember, any change you make further decreases the chances of a successful recovery!

Good luck, Kev :)

---

### Post by kevinf311 on 2007-02-11
Well, I looked a little online and found some Data recovery programs. Two of them are commercial, and one claims to be freeware.

[R-Studio Data Recovery]("http://www.data-recovery-software.net/") ($80 USD)

[Recover My Files]("http://www.recovermyfiles.com/") ($70 USD)

[PC Inspector File Recovery 4.x]("http://www.pcinspector.de/file_recovery/uk/welcome.htm") (freeware)

I cannot vouch for any of these programs, but they seem the least sketchy from my search.

If you used ext2/3, try FS-Driver and see if you can find your data from your XP installation. if it does not show up anywhere, then it's been formatted and your only course of action is to try a data recovery resource. Software is probably cheaper than taking it to a lab, but may not have as high a chance of retrieving your data. It sucks that this happened, but you gotta ask yourself; "how much are those files worth?"

Best of luck.

[edit] PS I'm going to sleep, as it is 5 am here and I've yet to call it a night. I'll check back with y'all tomorrow...er, later today. G'night

---

### Post by dexter on 2007-02-11
Can you see the partitions in windows disk manager ? Control Panel -> Administration -> Computer Management (or something like that) -> Disk Management. You should see them there, regardless of the file system they are using.

---

### Post by norty32 on 2007-02-11
im trying to get things back using ubuntu. I mounted the NTFS partition to a folder on my desktop but i get access to see the files in the folder, so right now im trying to copy all the files over. so i know they are there, they haven't been deleted or anything

---

### Post by norty32 on 2007-02-11
ok so this is an update:

I mounted the partition with all my data on it, lets call it partition D, in linux to a folder (folder1) on the desktop. When I tried to access the files in that folder it said I didnt have permission. I used the commands: chmod and chown to try to get permission but it still says I don't have permission. Next think I did was copy all the files in folder1 to another folder (folder2) on the desktop. I then again used the same commands chmod and chown to gain permission to that folder, which worked. My problem is, the amount of data in partition D is about 120 gigs, and the partition in which linux is on is only 10 gigs. So I could only copy over 10 gigs of the data from partition D. Now, I was trying to think of ways to get my data off my computer, so that I could just wipe the disk and start over. I was thinking of trying to have it copy the 10 gigs, then have me move those 10 gigs to another computer, and then delete them, and have it copy the next 10 gigs, and so on and so forth. But I don't really know how to do that.. Any help with that method?  Also another method I was thinking was have it copy from folder1 directly to another computer with more space so that ?I could copy the whole 120 gigs. Im not really sure how to do that either. I was thinking I could just put my harddrive into the other computer and mount the partition D, but then I thought, maybe I could mount it anyways on my own computer but I can't, it doesn't let me. 

So im kind of stuck here, any help at all would be greatly appreciated..

---

### Post by kevinf311 on 2007-02-11
This may not be needed now, but it's good to know anyways. RAV TUX just posted a thread with this link: 

[http://servers.linux.com/article.pl?sid=06/08/21/1558230&from=rss](http://servers.linux.com/article.pl?sid=06/08/21/1558230&from=rss)

It's for data recovery from a wiped hard drive.

When I redid my computer (in the configuration posted last page) I moved all of my music/data over to my roommates computer via the local network. I have also moved data from one hard drive to another by hooking the data drive up to the host computer.

Network (you must be a member of the host workgroup):
In Windows: On the computer being used as temporary storage create a folder and share it. Allow users to change the files. From the computer with the data on it, map to the shared folder. 
In ubuntu: go Places >> Connect to Server >> Service Type: Windows Share; Server: name of other computer; Share: name of shared folder. This will create an icon on your desktop "Folder on Server," double click on it to open, move "Folder1" into the shared folder. 120GB will take a while, and if possible it might be a good idea to bread it up into chunks. After your data is safely on the other computer, get your partitions set up right, install again if necessary, re-mount the shared folder as described above, copy files back to the desired location (probably /home).

If you only have another ubuntu computer to copy to, then create a shared folder in there and follow steps to give permissions and go that way.

Directly transfer files:
Remove your drive that has the data. Plug it into the other computer as slave. After turning it on, see if it has found the hard drive. If the other computer is windows (do not attempt if it is XP Home, I borked my sisters activation because I did this with her husbands hard drive), use FS-Driver to access the Linux partition (assuming the file system is ext2/3, if FAT then windows will recognize it, if reiserfs, I don't know what program to use). After finding the folder with your data, copy it to a folder on the main drive of the other computer. After the data is safely on the other hard drive, turn off, remove your drive, reinstall it into your computer, set up the partitions, install again.
You can either do the network method, or remove your drive again and reverse the flow of data from the other computer to a folder on your newly created storage partition.

This should work, I've done it with my computer and my brother in laws computer with decent success (only the XP Home activation detracted from it :rolleyes: )

Let us know if you need any more instruction, or if you hit a snag somewhere.

---

