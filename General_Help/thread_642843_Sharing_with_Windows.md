---
title: "Sharing with Windows"
date: 2007-12-17
forum: General Help
---

### Post by PaulClarke on 2007-12-17
Hello

I have a problem with sharing a disk on a windows machine.  When setting up the shared drive I called it "Fon Willie" (Willie is our dog).  I then put the line in fstab to mount this disk on my Ubuntu machine but it would not mount.  After playing around a while I found our that the problem was the space in the shared disk name.  I went back to the Windows machine and it would not let me change the name.  I can get other folders on the windows C drive to mount.

does anyone one have any idea how I can either get Ubuntu to mount this drive or get Windows to change the name.  The Windows box is XP Home.

Regards

Paul

---

### Post by SteveHillier on 2007-12-17
This might help, but don't kick me if it doesn't.
Is your XP machines set up for simple file sharing?
XP Home by default uses this simple file sharing which offers you very little control over what it does.
Try the following

Open Windows Explorer (Click My Computer)
Click 'Tools' from menu bar.
Select 'Folder Options'.
Click on the 'View' tab
Scroll to bottom
Remove tick from the 'Use Simple File Sharing (Recommended) option.
Then close explorer

Now when you go to share folders and devices you should get a much more comprehensive list of things to do.  In particular you can now explicitly set permissions at a user level.  
If the resource you are trying to share looks restricted then add a new user ('everyone' might be good here) and set permissions as you want.

Good luck

Just one point of clarity from your post.  Are you trying to share a drive or a folder?

---

### Post by PaulClarke on 2007-12-17
Hello,

It all worked till the unticking the "simple sharing" option.  There was no such option available.

Thank you for your reply.  If you have any other ideas please let me know

Paul

---

