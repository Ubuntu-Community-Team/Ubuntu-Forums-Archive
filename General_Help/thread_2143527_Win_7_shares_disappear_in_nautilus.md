---
title: "Win 7 shares disappear in nautilus"
date: 2013-05-09
forum: General Help
---

### Post by jonkjon1959 on 2013-05-09
After upgrading to 13.04, my win 7 shares aren't showing up in the file browser unless I restart the win 7 computer. After rebooting, the files reappear. I don't receive any error messages, the nautilus window file area is just empty. While this is problem is happening, i can run:

sudo smbclient -L computername -Uusername 

and I get the following error in the terminal:


protocol negotiation failed: NT_STATUS_INSUFFICIENT_RESOURCES

I have checked the win 7 machine for sleep or hibernate settings and they are all disabled. Again, once I reboot the windows pc, the file comes back and the error message does not display in terminal when running the smbclient command. I'm not sure how long it takes for the problem to return, I just know that it does it sometime within several hours at least, maybe less.  Thanks for any help with this.

---

### Post by VanillaMozilla on 2013-05-09
Watching this.

---

### Post by jonkjon1959 on 2013-05-10
After perusing the event manager in my windows 7 event manager, I found errors in lanman that led me to this:

[http://alan.lamielle.net/2009/09/03/windows-7-nonpaged-pool-srv-error-2017/comment-page-2#comments](http://alan.lamielle.net/2009/09/03/windows-7-nonpaged-pool-srv-error-2017/comment-page-2#comments)

This has fixed the problem of the disappearing shares for me. I hope it helps someone else.

---

