---
title: "GVFS, Nautilus, and other programs"
date: 2008-04-29
forum: General Help
---

### Post by AusIV4 on 2008-04-29
I've been excited about the Hardy release for a while, primarily because of GVFS. I thought that since GVFS was going to use FUSE to make remote file systems available to non-gnome applications, that meant Nautilus would successfully open files in the appropriate programs.

This turns out not to be the case. I use Nautilus' sftp:// protocol to mount my desktop's file system from my laptop. I try to play a song in Amarok, and get the same old complaint about no support for that protocol.

If I go to ~/.gvfs/ I can find the files, but I can't play them for very long before I start getting transmission errors.

Is there any hope that this will be remedied in the near future?

---

### Post by encompass on 2008-04-29
nope... fuse doesn't have the integration ability that gnome demands.
You can just have you location mounted at boot.  And if you can't do that... for example if your wireless will not start until login, you can make a script to do it for you too. :)
But yeah, I understand your feeling.  But there are still a lot of improvements over the old way, so I am happy to greet it in this version of ubuntu.

---

### Post by AusIV4 on 2008-04-29
It seems like it should be simple enough for Nautilus to point other applications to the .gvfs location instead of locations using odd protocols.

But even going through the .gvfs folder, the connection crashes until I restart gnome, making that feature completely worthless.

---

### Post by Endolith on 2008-04-30
When I first did Places --> Connect to Server... it worked perfectly.  It created a bookmark, and clicking the bookmark opens Nautilus with the sftp:// URL for my other machine.  Then I can alt+drag from there into my ~/Music directory and create a link, which, when you look in Properties, is actually to the ~/.gvfs location.  This worked great until I rebooted, and the connection is forgotten.  Even if I reconnect manually by clicking the bookmark, there is no .gvfs folder anymore.

---

