---
title: "Ubuntu gone from list after formatting windows xp"
date: 2007-10-06
forum: General Help
---

### Post by chroncile on 2007-10-06
I just formatted my windows xp which is on a different partition, and now I don't have an option of booting up ubuntu any more :(
You know that list that you get at the begining when you boot up your computer and it gives you 10 seconds to choose a operating system, ubuntu would be first and windows xp would be last.
That list is now gone, I can't choose to start ubuntu any more, what should I do :(

---

### Post by taurus on 2007-10-06
When you reinstall Windows, it will overwrite GRUB from MBR so you can't boot Ubuntu anymore.  Therefore, you need to reinstall GRUB to MBR again.

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

---

### Post by HermanAB on 2007-10-06
Hmm, I can feel your pain.  Windows doesn't play nice in groups and will always try to grab the whole machine for itself.  The trouble is that you destroyed the master boot record on the boot drive, which is the one Windows is on.  That MBR probably chain loaded the the boot code on the other drive.

The good news is that you can do a system recovery from the Ubuntu CD to get Ubuntu to boot up again.  It will take some experimentation to get it right.

You can find lots of howto guides on recovering from this rather common catastrophe with Google:
[http://www.google.ca/search?q=Linux+windows+repair+MBR](http://www.google.ca/search?q=Linux+windows+repair+MBR)

Also search these forums, since are a few threads discussing this very same permanent issue.  Once you have it sorted out again, be sure to send a personal thank-you letter to Bill Gates and Steve Balmer.

The 21st Century solution to this mess is virtualization.  Once you have Ubuntu working again, install Virtualbox or VMware and then install Windows in a virtual machine where it will be completely sandboxed with Windows running in a window.  The advantage of this approach, is that you can then run Linux and Windows simultaneously and drag and drop files between the two systems.  That will put the evil empire firmly under your thumb, where it belongs.

Cheers,

Herman

---

### Post by d_xtremw on 2007-10-06
I'm interested in the VMware idea that u brought up. Ive been thinking about it all week and coincidentally just read your post (my idea of fate).  Does it require any extra space to be used?? and can i use it like a normal windows environment as well( running .exe files and such) ??

thanx in advance

---

