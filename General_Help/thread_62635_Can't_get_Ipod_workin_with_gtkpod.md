---
title: "Can't get Ipod workin with gtkpod"
date: 2005-09-05
forum: General Help
---

### Post by HairlessHippie on 2005-09-05
I've followed all the online instructions for using this gtkpod. Now when my iPod mini is plugged in it is recongnized my Gnome but when I try to use gtkPod I get the following  message


Could not open "/media/sda2/iPod_Control/iTunes/iTunesDB.ext" for reading extended info.
Extended info will not be used.
Could not open iTunesDB "/media/sda2/iPod_Control/iTunes/iTunesDB" for reading.



Any thoughts would be appreciated

---

### Post by HaroldJohnson on 2005-09-10
[quote=HairlessHippie]I've followed all the online instructions for using this gtkpod. Now when my iPod mini is plugged in it is recongnized my Gnome but when I try to use gtkPod I get the following  message


Could not open "/media/sda2/iPod_Control/iTunes/iTunesDB.ext" for reading extended info.
Extended info will not be used.
Could not open iTunesDB "/media/sda2/iPod_Control/iTunes/iTunesDB" for reading.



Any thoughts would be appreciated[/quote]

I'm not certain this is the solution, yet perhaps it is.  This fellow posted a story on his blog regarding his failing efforts at accessing his iPod under Ubuntu, and the solution he found.  Basically, he ran a 'chmod 777' command and now all is well.  He's able to use gtkpod and everything.  Read the blog entry here:

*broken link*

Hope this helps!

---

### Post by alastair lewis on 2005-09-19
The path to iPod may be wrong.
plug in your ipod and look in /media. There should be a folder callled /IPODNAME. (Change IPODNAME to suit)

Then in gtkpod go to input/output preferences (in the file menu) and change the mount point to /media/sda2 to media/IPODNAME.

It might help.

---

### Post by meditatingfrog on 2008-04-26
> **HaroldJohnson said:**
> I'm not certain this is the solution, yet perhaps it is.  This fellow posted a story on his blog regarding his failing efforts at accessing his iPod under Ubuntu, and the solution he found.  Basically, he ran a 'chmod 777' command and now all is well.  He's able to use gtkpod and everything.  Read the blog entry here:

<broken link>

Hope this helps!



It is not the solution.  The address <broken link> isn't even a blog.

---

### Post by HaroldJohnson on 2008-04-27
> **meditatingfrog said:**
> It is not the solution.  The address <broken link> isn't even a blog.

Pardon me? Don't blame for the link no longer working; I posted the link nearly three years ago, so that's why the information is no longer active at that location.  In fact, my last visit to Ubuntu Forums was November 7 of 2006. I didn't even realize I was registered to this forum until now.

---

