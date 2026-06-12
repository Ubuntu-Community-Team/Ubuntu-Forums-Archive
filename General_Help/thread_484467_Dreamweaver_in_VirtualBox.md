---
title: "Dreamweaver in VirtualBox"
date: 2007-06-25
forum: General Help
---

### Post by justtech on 2007-06-25
I have recently moved over from WinXP to Ubuntu Feisty Fawn and I love it.  I have set up the VirtualBox so I can run Photoshop, Dreamweaver, and Flash.  Only problem that I am having is that when I try and open a file in Dreamweaver, nothing happens.  Any ideas on how to fix this?

---

### Post by Medieval_Creations on 2007-06-25
I have VBox running XP and haven't had any problems running any of the appz you listed.  Did you install both XP Service packs (1 & 2)?  I have had a couple of flukey problems b-4 installing both of them (my version of XP doesn't have them preinstalled).

Aside from that I'm not sure.  I'm assuming there is no error msg.

Just for clarification you have Dreamweaver open and when trying to open the file nothing happens or you try to open a file with dreamweaver and dreamweaver doesn't launch?

---

### Post by justtech on 2007-06-25
The only version of XP that I have installed is XP SP2.  It is the only Guest OS that I have installed in VirtualBox so far.

There is not an error message.  I first had a shared folder "\media\sba5" which is a NTFS partition with all of my clients website files.  I was able to make it a viewable network drive in VirtualBox WinXP, but it was not writable.  So I installed "NTFS Configuration Tool".  That took the lock off of all the files (I'm assuming to show that they were read only).  I haven't been able to open them since.  Then I created a folder inside my user folder called documents and copy all the client's files into that and did the shared folder all over again.  Still nothing.   I have opened Dreamweaver and then went to Open and tryed that way with nothing happening.  I have also went into the network drive and right clicked on a file and told it to open with.... Dreamweaver 8.

---

### Post by Medieval_Creations on 2007-06-25
hmm... Not sure, sounds more like a read/write problem to shared foler than with Dreamweaver.  I have had the occasional problem with file transfers and access shared between VBox guest and the host, especially with larger files... I'm using MX 2004, but I don't think that is the issue.

I typically copy over the files to the Guest and then try working on them, but my sites aren't anything huge so it's not an issue for me...

---

### Post by justtech on 2007-06-25
"Typically copy over the files to the Guest"

How do you go about doing this.  I'll give it a shot.  Getting desperate.  Have a client that I was supposed to do some updates to her site Friday.  If I can't get anything soon, I'll have to install Dreamweaver on my laptop or build a second computer to work off of until I get this figured out.

---

### Post by justtech on 2007-06-26
Is the Windows File directory tucked away somewhere in all the folders of Ubuntu?  Is there a WinXP "My Documents folder that I can drag them too in my filesystem?

---

### Post by Medieval_Creations on 2007-06-26
It sounds like you've already done most of these steps, but here is how I setup my Network Drive in my XP Guest. They are local folders on my Desktop, but I would imagine that the process would be the same for a folder over a network as well, provided you have the full path to that folder.

*(Just for Clarification, this is all done in the Linux Host OS without the Virtual Machine Running)*
I made sure that I had Read/Write in your host OS to the desired folder.
```
sudo chgrp -R <folder name> <user name>
sudo chown -R <folder name> <user name>
```

Then I added the folder to the VBox.
```
 VBoxManage sharedfolder add <VBox Machine Name> -name <Share Name> -hostpath <Folder Path>
```
Example: VBoxManage sharedfolder add WinXP -name Storage_Ext3 -hostpath /mnt/Storage_Ext3

It's been a while but I think if the command is successful, it won't display a message, it will just to back to the command prompt.

*(Now boot up the Guest OS)*
In the command lilne in the XP Guest:
```
net use <Drive Letter> \\vboxsvr\<Share Name>
```
Example: net use x: \\vboxsvr\Storage_Ext3
or you could just map the drive like any other shared folder in XP using the \\vboxsvr\<Share Name>

I hope this helps, but as I mentioned it sounds like you already did most of this, but that is how I set mine up and it does work to Read/Write to the sare folder.  Although it is flake when you start transferring large amounts of data / files.

---

### Post by justtech on 2007-06-26
Man, I appreciate your time in trying to help.  Yes I had done all of that.  In fact, I just did it all again just the way you have it.  Still nothing.  It's weird because it know to Open Dreamweaver to try and edit the file but when Dreamweaver just opens up and stares at me like I'm stupid.  Maybe it's right.  So, to furthur my troubleshooting, I emailed an .html file to myself and then loged into VirtualBox WinXP and opened my email attachement and it was able to view/edit the file just fine.  Any other suggestions?

---

### Post by Medieval_Creations on 2007-06-26
No worries, I try to help when I can.  Unfortunately not to much in this case.

I'm getting pretty thin on the suggestions... One question I forgot to ask was what version of VBox are you using?  In know they just came out with a new version 1.4.0.  I think they did make some fixes to File Sharing.

Aside from that I'd have to digg in to the VBox PDF Manual & see if there are any troubleshooting steps for file sharing we could try.

Also they do have their own forum, I haven't searched it yet, but their might be some good information there as well.
[http://forums.virtualbox.org/](http://forums.virtualbox.org/)

---

### Post by RAH66 on 2007-06-26
Yeah I had the same problem its just a case of having the files inside the system of your virtual m...

meaning in windows under my documents or werever...
try getting the files into the geust OS with a flash drive or a virtual disc that you mounted... seeing as you can see the network drive you created copy all the files to my documents in the virtual machine and they should open in dreamweaver...

---

### Post by justtech on 2007-06-26
Thanks again for all the help.  I just ended up having to transfer everything into "My Documents" in the VirtualBox WinXP.  Not thrilled about it.  I don't trust Mr. Gates with years of my work.  I used a Maxtor One Touch III to back everything up but I'm still looking for a solution on that (save that for another post and hours and hours more of digging).  But once again, thanks for all the help.

---

