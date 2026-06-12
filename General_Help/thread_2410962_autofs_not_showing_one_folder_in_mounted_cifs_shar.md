---
title: "autofs not showing one folder in mounted cifs share"
date: 2019-01-22
forum: General Help
---

### Post by konadad on 2019-01-22
I mount a CIFS share on my family's windows machine with autofs.  Had been working great for years to allow me to easily back up the family windows hard drive onto my ubuntu machine with 16.04LTS.

I just upgraded to 18.04 LTS (mythbuntu, so using xfce), and realizing that since I did, one single folder in my CIFS share is not visible when I mount it.  It happens to be the folder with my name as its name, and my name is also the name of my home directory on the ubuntu machine.  Not sure if this matters, but figured I would mention it.

The mount point is /media, and autofs mounts to /media/misc
The CIFS share mounts with the name kitchen, so /media/misc/kitchen
The missing folder is /media/misc/kitchen/brian

If I use terminal, I can cd into this /media/misc/kitchen/brian folder with no issue, and ls returns all of its contents properly.
If I ls from /media/misc/kitchen, it does not show the brian folder, but all other contents are listed properly.

From Thunar, I cannot see the brian folder, but all other folders show up.
From Thunar, if I use "Open Location" and type in /media/misc/kitchen/brian then it shows its contents properly, but if I go back up to kitchen, it once again is gone.

I have thought about changing the folder name on the Windows machine so it doesn't match my home directory name and see if that changes anything?  But don't want to mess up my backups by doing so.

Any other thoughts on what could be wrong here?  I don't see anything glaring in log files - just one entry which I can't connect to my issue from google searches:

```
automount[1519]: rmdir_path: lstat of /media/misc/.hidden failed
```

---

### Post by HermanAB on 2019-01-22
You should debug SMB/CIFS issues with smbclient.  It shows you all the error messages - google them.

That being said, your problem is likely a simple permissions issue, so check the ownerships with 'ls -al'.

It could also be an ACL issue, or an AppArmor problem, but that is unlikely - first rule out simple permissions before delving down into the special permissions.

---

### Post by konadad on 2019-01-26
No luck yet.  Using smbclient, I can access the share without error, and ls or dir commands from the smb command prompt give me a full listing of the folders on my kitchen share, including the folder named brian.

I poked around in Windows 7 a bit, but also don't see anything of concern.  From a permissions standpoint I have it set to Read access for Everyone.  I see nothing different for this one folder as compared to all of the other folders in the share that are working properly.  I also was able to browse the share from a windows laptop we have, and the brian folder is visible.

>  so check the ownerships with 'ls -al'.

Did you mean just from the main terminal command prompt or from the smb command prompt?  I get an error with this when trying it with smb.  With the main linux command prompt, I can't see the brian folder, so can't check it's permissions.

---

### Post by HermanAB on 2019-01-28
What I would do at this point, is install tcpdump or wireshark and sit and stare at the packet flow - for when things work and when things don't work.  After a while, you may spot the problem.

---

### Post by Morbius1 on 2019-01-28
I don't have your issue but you may want to post the contents of your auto.master file and your "map" file so the folks here can see how you are set up.

In the mean time you might want to run AutoFS in "diagnostic" mode:

** Make sure the share has unmounted and close Thunar.
** Then open a terminal and stop autofs:
```
sudo service autofs stop
```
** Then start it this way - [COLOR=#0000cd]and keep the terminal open[/COLOR]:
```
sudo automount -vf
```

Now open Thunar and try to access the folder and it's subfolders and see if there are any error messages in the terminal.

In my case I get a lot of "attempting to mount .... key ".hidden" not found in map source(s) ... failed to mount /xxx/yyy/.hidden" but it's followed by a "re-reading map for /xxx/yyy" and everything works as expected.

I may not be smart enough to interpret the output since I've had my own issues with Thunar and autofs in the past ( [https://forum.xfce.org/viewtopic.php?id=8943](https://forum.xfce.org/viewtopic.php?id=8943) ) but someone like ToZ in this forum may have some insight.

---

### Post by konadad on 2019-01-30
Here is what I get:

```
sudo automount -vf
Starting automounter version 5.1.2, master map /etc/auto.master
using kernel protocol version 5.02
lookup(dir): dir map /etc/auto.master.d missing or not readable
lookup(file): failed to read included master map dir:/etc/auto.master.d
lookup(file): failed to read included master map auto.master
mounted indirect on /media/misc with timeout 300, freq 75 seconds
ghosting enabled
attempting to mount entry /media/misc/.hidden
key ".hidden" not found in map source(s).
re-reading map for /media/misc
failed to mount /media/misc/.hidden
attempting to mount entry /media/misc/kitchen
mounted /media/misc/kitchen
re-reading map for /media/misc
rmdir_path: lstat of /media/misc/.hidden failed
1 remaining in /media/misc

```

My auto.master has the following un-commented lines:

```
/media/misc /etc/auto.misc --ghost
+dir:/etc/auto.master.d
+auto.master
```

and my auto.misc has the following un-commented line for the map:

```
kitchen -fstype=cifs,username=guest,password= ://192.168.0.110/KitchenWin7JDrive
```

of note is that I don't have an /etc/automaster.d directory, don't recall setting that up a few years ago when I first got this working, but I have no reason to think that line in the auto.master file changed when I did my 18.04LTS upgrade and this stopped working suddenly.

---

### Post by konadad on 2019-02-09
Progress has been made.

1) I was able to refine my problem statement to:  only the first folder alphabetically in the CIFS share does not display properly.  The "Brian" folder happened to be first alphabetically, so  I created a folder named only "A" on the kitchen drive, and this caused my "Brian" folder to re-appear through autofs.

2) I turned on debug messaging for autofs, and saw this message in my syslog:

```
No dialect specified on mount. Default has changed to a more secure dialect, SMB2.1 or later (e.g. SMB3), from CIFS (SMB1). To use the less secure SMB1 dialect to access old servers which do not support SMB3 (or SMB2.1) specify vers=1.0 on mount.
```

This caused me to read up on why SMB1 is bad, but also of course had to try it.  The issue disappears when forcing SMB version 1 in my auto.misc file.  All folders show up properly.  For now - I have unforced it again and am just keeping an extra "A" folder in my J drive that I am targeting with autofs.

Does this imply it is a Windows side issue?  Or is there possibly a bug in the implementation of the higher versions of SMB on the linux side that could be causing the issue?

---

### Post by Morbius1 on 2019-02-10
My sincere apologies for not recognizing this problem earlier.

I went through the same discovery process you did with regard to SMB1 vs SMB2: [Missing folders in windows network share mounted using samba]("https://askubuntu.com/questions/1028100/missing-folders-in-windows-network-share-mounted-using-samba/1028211#1028211")

The "solution" I offered at the time isn't much of one for a server that has disabled smbv1 like Windows 10 does. Regrettably it is not a bug in Windows but in cifs:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1572132](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1572132)
[https://bugzilla.samba.org/show_bug.cgi?id=13107](https://bugzilla.samba.org/show_bug.cgi?id=13107)

And at the moment there seems to be some issue with implementing the "fix" for this.

---

### Post by konadad on 2019-02-11
Thanks Morbius!!  That is exactly my issue, with Windows 7 being the culprit for me.  Since my target isn't a C: drive, I don't have the issue with Recycle Bin not showing up, but clearly do with the first alphabetical folder being missing.

For now, my workaround of creating the empty "A" folder is working great.  Until one of my kids deletes it by accident....

---

