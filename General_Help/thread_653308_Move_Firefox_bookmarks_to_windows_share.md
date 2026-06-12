---
title: "Move Firefox bookmarks to windows share"
date: 2007-12-29
forum: General Help
---

### Post by domiflichi on 2007-12-29
Hello,

I have a Windows network with several windows clients and a Windows 2000 Server server. I also currently use Firefox on my Windows PCs with my bookmarks located centrally on the Win2K server so that all my client PC&#347; Firefox&#347; can share bookmarks.

My question is how do I reference my Firefox (ver 2) in Ubuntu 7.04 to my Windows 2000 Server? I tried the same similar procedure found on Mozilla&#347; website as far as editing about:config and also trying to add a user.js file in my profile folder.  All to no avail. The location I have been trying to point to has been like this:

smb://winservername//sharename//foldername//bookmarks.html

and I have tried this:

smb:\\winservername\\sharename\\foldername\\bookmarks.html

(Note: i know it is showing a space between the a and the r above, but I do not have it that way)

I am guessing that it is my syntax. I have tried navigating to that location through the GUI and I can access and open that file, so I do not think that it is a permission problem.

Thanks.

---

### Post by SOULRiDER on 2007-12-29
I was gonna suggest exporting them but its not good enough. I suggest you browse the mozilla addons page, theres probably an addon that will do this for you.

---

### Post by SOULRiDER on 2007-12-29
Check out these two, I hope theya re useful.
[https://addons.mozilla.org/en-US/firefox/addon/5525](https://addons.mozilla.org/en-US/firefox/addon/5525)
[https://addons.mozilla.org/en-US/firefox/addon/4496](https://addons.mozilla.org/en-US/firefox/addon/4496)

About the samba issues, i dont really know, im a total newb at samba.

---

### Post by domiflichi on 2007-12-29
Soulrider, thank you for your suggestions. I may end up using one of them. However, I was hoping to do this without a third-party add-on. And I would also like to learn more about Ubuntu/Linux.

I was experimenting with using smbmount to mount the shared drives that I need access to (including the one that has my bookmarks), and then pointing to that (i.e. mnt/winshared) and that worked. However, after I reboot, that mount place is gone.

So I have 2 other options here:

1. Either still use the long smb path that I was originally trying...which I would like to use, because I would like to learn the syntax for that, and it seems like the easiest way...or 

2. Learn how to have those shares mounted automatically upon startup of my computer. Which I would also like to learn how to do.

So if anyone can help me with 1 or more of these, I'd be grateful.

---

### Post by SOULRiDER on 2007-12-30
For #2, i believe you can add your samba share to your fstab. Check this out:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://lists.samba.org/archive/samba/2004-February/080086.html](http://lists.samba.org/archive/samba/2004-February/080086.html)
[http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/](http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/)

Good luck, and ask if you dont understand anything although as I said before, i know very very little about samba.

---

### Post by domiflichi on 2007-12-30
Soulrider,

Thanks for those links for help with #2. I tried out using fstab to mount a share on startup, and it worked! However, I do have 1 small problem with it. It seems to mount them as root, because when I try to delete any file off of that share, it won't let me. And when I right-click on any of the files in that share, it says the owner is root. I can read and modify files just fine though. 

Do you know why that might be?

Also, anybody out there that knows about Firefox and Samba...for my #1 method?

thanks.

---

