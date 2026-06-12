---
title: "excessive time to log out, why?"
date: 2013-10-28
forum: General Help
---

### Post by Coder88 on 2013-10-28
I just installed xubuntu 13.10 and when I click the desktop menu and choose to log off, it takes perhaps 60 seconds before the choices appear on the gui desktop to log out, shutdown, or suspend; that is an unacceptable time. I had this happen recently on another xubunt install and i have no clue what i did to have that go away on that xubuntu install (now the logout/shutdown/suspend choices appear in about a second as it should). Both installs as 13.10 AMD64. Just wondering if anybody has a clue what process or package could be causing such a long delay before seeing the logout screen?

---

### Post by philinux on 2013-10-28
> **Coder88 said:**
> I just installed xubuntu 13.10 and when I click the desktop menu and choose to log off, it takes perhaps 60 seconds before the choices appear on the gui desktop to log out, shutdown, or suspend; that is an unacceptable time. I had this happen recently on another xubunt install and i have no clue what i did to have that go away on that xubuntu install (now the logout/shutdown/suspend choices appear in about a second as it should). Both installs as 13.10 AMD64. Just wondering if anybody has a clue what process or package could be causing such a long delay before seeing the logout screen?

You could try this from a terminal and observe any error messages or other.

```
xfce4-session-logout
``` or it might be just xfce without the 4. Can't remember.

---

### Post by Coder88 on 2013-10-28
> **philinux said:**
> You could try this from a terminal and observe any error messages or other.

Tried that, no error messages.
Okay so then I did a reinstall of xubuntu but with the option for the reinstall to keep as many apps and user systems as possible. Same issue after that except that this time when I chose to Logout from the xfce4 menu, again waiting almost a full minute, a popup error window appeared with this:

Error
(-) Received error while trying to log out
Did not receive a reply . Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken. 
[Close]

---

### Post by Coder88 on 2013-10-28
I have a great xubuntu 13.10 AMD64 on an SSD drive on my desktop PC, it logs out just fine (quick). The xubuntu giving me issues now is the second install on an external USB drive. What would happen if I made a tarball of "/" from my good install and then used that to overwrite "/" on the funky xubuntu?

---

### Post by Coder88 on 2013-10-28
So I just did fresh install on that external usb drive. Same issue, no different. Both before and after the fresh install asked to do xubuntu base and security updates (just a few files). Same issue, no different. No additional apps installed, just the basic install.  I wonder if the external usb drive hardware might be an issue, it is an old drive, an old toshiba external pocket usb drive, maybe five years old, had a lot of use. I might go buy a new external usb drive tomorrow and see if that changes anything. i am out of sata ports on my motherboard, even though I have extra sata drives I have nowhere to install them so I have to go with an external usb drive.

---

### Post by Coder88 on 2013-10-30
Well i have up on any chance of a fix because i think the problem is inherent to the distro version. I tried a fresh install of xubuntu 13.10 AMD64 to a clearn sata hard drive, basic install, not additional packages, and still had the super long (1 minute) delay trying to log out.

I decided to just install Ubuntu 12.04LTS to the same clearn sata hard drive and logout happens immediately as it should.

Still have my Xubuntu 13.10 for my main linux on an SSD, instant logout, but I am going with Ubuntu 12 for the custom linux build i am working on to then make a live DVD.

---

