---
title: "Ghost Icon of Flash Disk can't be removed from Desktop"
date: 2008-04-30
forum: General Help
---

### Post by Amurko on 2008-04-30
I've got the icon for a flash disk stuck on my desktop.  If I insert the actual disk again, a second icon corresponding to the disk appears.  If no disk is inserted and I try to delete the disk, it says I must unmount it.  But when I try to unmount it, it says no disk exists.  How do I manually remove it using the command line?

---

### Post by kpkeerthi on 2008-04-30
Reboot?

---

### Post by chunchengch on 2008-04-30
Press Alt-F2 ,input command [COLOR="Red"]gconf-editor[/COLOR] and then click [Run], this will open a window, go to apps > nautilus > desktop, uncheck [volumes_visible] to see if the problem is solved.

---

### Post by playinpearls on 2008-06-21
I just had this problem and was able to get rid of it by connecting the media back to the computer, and then restarting the computer. It didn't work if the media wasn't connected. I guess it just takes that icon once it restarts and doesn't add the one it created when you plug it in the second time. This was for my ipod, which i disconnected without hitting eject....not recommended;):mrgreen:

yes, this is an old thread...just incase..

---

