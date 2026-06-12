---
title: "close file dialog takes few seconds to appear"
date: 2019-11-28
forum: General Help
---

### Post by bkbrd on 2019-11-28
I have a problem on two machines running Ubuntu 19.10 with gnome shell 3.34.1: the "close without saving / save /cancel" dialog takes few seconds to appear. 
Say, I open `gedit`, type something, press alt+F4 - the window starts to fade to grey slowly, then with noticeable delay the dialog appaers

It does not look like a rendering problem - other window animations look smooth. Also the close dialog appears quicker if invoked for the second time.
However if I switch to some other application and then back to gedit and try to close it - it is slow again. 

If I create a new user, however, in that user it seems to work OK. 
So it might be something with my current user's setup, but I tried disabling all gnome extensions, stopping all file syncing services etc - it is still slow. 
More importantly, it clearly worked fine before upgrading from 19.04, it also appeared on another machine I installed from scratch, with similar set of applications etc - so it looks like some systematic issue. 

It feels like it has something to do with file system access, though I made sure don't have any slow e.g. network file systems mounted, my drives are SSD (though encrypted with LUKS, / and /home on a separate drive. 
Can it be because the current user simply has more files and it takes time to decrypt or something like that? Any ideas on where else to look? 

My HW is AMD Ryzen 5 2600X / MSI MS-7B89 mobo,
home drive is WD Black NVMe PCIe M.2 1TB, root drive is Transcend M.2 512GB SATA stick.
currently kernel 5.3.0 but seems to not depend on kernel version

another machine is Ryzen 5 3600 / ROG Strix B450-I with two M.2 sticks as well, even newer ones

---

