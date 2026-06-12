---
title: "Compiz problem"
date: 2008-06-14
forum: General Help
---

### Post by abstractcoder on 2008-06-14
I was using Ubuntu 6.06LTS, and decided to download Ubuntu 8.04

When I try to enable effects in the appearance panel. I get the message "Could not enable effects." I opened Terminal, and ran the compiz command. 

It gave a few errors, one of which was "Nvidia not present", Which I DO have Nvidia, others were about XGL not being present..

oh btw, I have a 128MB ATI Radeon X1300 Display Adapter
 

Any ideas on how to solve this?

---

### Post by Forlong on 2008-06-14
Run this and post the output here: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by abstractcoder on 2008-06-14
I ran the check and everything checked out ok. When I run the compiz command in Terminal I get the following output:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 03:00.0 0300: 1002:7187 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0


Although I do have Nvidia, it's displaying that I don't.

---

### Post by Forlong on 2008-06-14
Again: please post the output here.

---

### Post by Forlong on 2008-06-14
Please keep the [postings]("http://ubuntuforums.org/showthread.php?p=5187012#post5187012") here.

What do you mean by saying you "do have nvidia"?
You have an ATI chip. Did you try to install a nvidia driver or anything like that?

You may want to post the content of your /etc/X11/xorg.conf

---

