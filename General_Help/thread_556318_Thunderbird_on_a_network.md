---
title: "Thunderbird on a network"
date: 2007-09-21
forum: General Help
---

### Post by rpn on 2007-09-21
As of yesterday both primary machines on my network are Ubuntu 7.04 :) However it means I need to get Thunderbird to work on them and I've hit a problem. Both downloaded and installed Thunderbird 1.5 without any problems. But I cannot get them to look to the mail folder on the server running Win2000Server. 

With XP this is easy (they run 2.0 but it worked fine with older versions too). Install Thunderbird with basic account. Open accound settings, change the server settings and 'local folder' file locations. Job done. I don't run any extensions with Thunderbird and only one account as the mailserver aggregates everything to the one account Thunderbird references on it. So this approach 'just works' without fiddling with profiles etc. (The mail server on the W2000S box does have webmail but it is slower, the interface isn't as attractive and practical and its junk handling is pretty poor in comparison to Thunderbird but it is free and it does work very well ignoring the webmail so it is staying. But I am playing with SME server with a view to switching to it longer term)

On the Ubuntu boxes though while they have absolutely no problem accessing the folder and the connection made registers in Nautilus but when I try to change location Thunderbirds file navigator does not show the network links like Nautilus does. If I type smb://server name/ thereafter it clearly is 'seeing' something in producing a drop down with the right content so I can navigate on but it doesn't stick. Unlike XP I can't type direct into the box either. There does seem problem with Thunderbird seeing the network but at the same time neither install allows any direct edit of the location either so that's two issues perhaps or one underlying one leading to them.

I appreciate I could install Samba on one of the Linux boxes and share the folder from there but the two primary machines are three floors apart and while one is generally on it isn't always. The server is the one machine that is on 24/365 so I would really rather leave the mail folder there and until its W2000S install dies I'm in no hurry to switch it to something else as 'if it ain't broke don't fix it' sort of person with core things.

So, anyone have any ideas why I cannot 1) edit the boxes 2) access the folder on the remote windows server? And I am a relative newbie with Linux so I may have missed something obvious :)

Richard.

---

### Post by Spam Banjo on 2007-09-21
I had a similar problem using Dreamweaver over a network.

I had to use Pyneighborhood (I think that the spelling). It's in the add/remove section.

You can use Pyneighborhood to map network drives... they then show up in the '/mnt/lan' folder.

They are then considered as local folders to all your applications.

Hope this helps.

---

### Post by rpn on 2007-09-21
Thank you.

Unfortunately that suggests a deeper problem. Pyneighborhood sees the network shares but it will not mount any of the the servers shares. Tried an XP box that is running and visible but the share on it won't mount either. Yet I can connect using 'connect to server' fine and such connections show up in the file manager. They do not show in the TB file navigation window but as I said if I type smb://server name/ then the applet is clearly seeing the folder to produce dropdowns. 

What beats me is that I can use Nautilus etc and go to these folders. Open Office sees them fine. TB though seems to A) not like the locations being edited and B) have a problem seeing an SMB share. Yet possibly that isn't TB's fault as Phneighborhood won't mount them either. Note I do not have Samba installed. Only the client and smbfs. Can't see why it would need to be anyway.

Richard.

---

### Post by rpn on 2007-09-21
Resolved.

I checked with Pyneighborhoods site to find a link to a Grumpymole article on Samba browsing using it in Xubuntu. Pointed out two permission issues. One is where you mount the share (change to your home directory being an obvious choice) and give root level permission to Phnieghborhood to do the SMB mount/umount. After that it worked fine and Thunderbird is reaching the mail folder fine.

Many thanks for putting me on the right track.

Richard.

---

### Post by Spam Banjo on 2007-09-21
Yeah sorry... should have mentioned the root permissions.

Once set up, it should work like a charm. I've been using it seamlessly for months now.

Glad to hear it worked. I think that's the first solution I've offered!

I love this community... nice to finally give something back!!

---

