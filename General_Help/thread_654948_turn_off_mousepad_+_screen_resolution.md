---
title: "turn off mousepad + screen resolution"
date: 2007-12-31
forum: General Help
---

### Post by NadeMaster on 2007-12-31
I am going to install 7.04 of ubuntu on this laptop of mine and i know when i was running debian on here the mouse would click things just by touching it and i hated it.  How can i turn off the mousepad?


Also i remember with the screen resolution, i did something to raise it to a higher resolution.  I think i used some xorg.conf or somehi9ng like that.  Can someone remind me what to do?  Thanks.

---

### Post by overdrank on 2007-12-31
> **NadeMaster said:**
> I am going to install 7.04 of ubuntu on this laptop of mine and i know when i was running debian on here the mouse would click things just by touching it and i hated it.  How can i turn off the mousepad?


Also i remember with the screen resolution, i did something to raise it to a higher resolution.  I think i used some xorg.conf or somehi9ng like that.  Can someone remind me what to do?  Thanks.

Hi and I believe you are speaking of the command ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by thomasaaron on 2007-12-31
You can turn off the mousepad by going to a terminal and entering this command:
sudo modprobe -r psmouse
You can re-start it with:
sudo modprobe psmouse

There might also be settings in...
 System > Preferences > Touchpad 
...or...
System > Preferences > Mouse
...for adjusting the sensitivity.


For the screen resolution, you should try going to...
System > Preferences > Screen Resolution
...to select a higher resolution.

---

### Post by NadeMaster on 2007-12-31
with the screen resolution it didnt work, i remember using some kind of horz and vert refresh rate and height and stuff like that.

---

### Post by overdrank on 2007-12-31
> **NadeMaster said:**
> with the screen resolution it didnt work, i remember using some kind of horz and vert refresh rate and height and stuff like that.

HI and maybe this link will help
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

