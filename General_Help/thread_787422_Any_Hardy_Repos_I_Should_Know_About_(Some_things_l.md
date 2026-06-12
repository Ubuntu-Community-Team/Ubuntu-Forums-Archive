---
title: "Any Hardy Repos I Should Know About? (Some things like VMware Server Don't Exist!)"
date: 2008-05-08
forum: General Help
---

### Post by OzzyFrank on 2008-05-08
I'm having a hell of a time with vmware-server vs ia32-libs in Hardy:

[http://ubuntuforums.org/showthread.php?p=4915208#post4915208](http://ubuntuforums.org/showthread.php?p=4915208#post4915208)

and after removing Gutsy repos, vmware-server apparently doesn't exist anymore! It no longer shows up in Synaptic, though 2 vmware-server-kernel packages do. So are there some repos I am missing that will fix this??

Tried adding:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy-commercial main

but it seems it doesn't exist. Any suggestions for more repos?

---

### Post by garyedwardjohnston on 2008-05-08
I use virtualbox.  Much easier.

Switch your server to the main server and see if that helps.  If it doesn't it means it isnt supported.  Ubuntu and Qemu are getting along nicly, though I havent tried it yet.  Still prefer Virtualbox.

---

### Post by OzzyFrank on 2008-05-15
Yeah, seems VMware and Ubuntu aren't getting along, and so there is no version for Hardy in the repos. There are guides to getting vmware-server happening in Hardy, but it involves a few steps and a patch to be applied. I decided to give Virtualbox a go, so downloaded it (I think you can get the OSE version through Synaptic, but getting the .deb from the site was easy enough). I have to say, it is pretty good. In vmware-server I could never configure the sharing of folders/drives between Ubuntu and Windows, even after getting little apps that are supposed to make the Samba connections easy, etc. And forget USB... I would have to rely on sharing stuff via CD. In Virtualbox, it was so easy to set up a couple of shared folders in Ubuntu and then share them with the virtual Windows. In fact, one of the shared folders is the actual NTFS partition that houses my real Windows XP installation, which makes getting some Windows files/settings into the virtual one a breeze! I recommend Virtualbox - it's great!

---

