---
title: "Updated firefox with Update manager, now I can't go fullscreen on youtube videos"
date: 2008-02-09
forum: General Help
---

### Post by charlescarroll1 on 2008-02-09
Title pretty much explains it.  I just installed the updates for Ubuntu via Update Manager, one of which was for Firefox.  Now I can't go fullscreen on Youtube/flash videos (it will only go fullscreen for a fraction of a second).  Has anybody else had this issue?

---

### Post by randy78 on 2008-02-09
I cannot replicate this error...

I just went to Youtube and it worked fine for me.

Try closing Firefox and then in a terminal:
sudo apt-get remove flashplugin-nonfree
then
sudo apt-get install flashplugin-nonfree

hope this helps!

---

### Post by Quilzas on 2008-02-09
I'm having a simliar problem.  I got my flash player working again last night as it had failed after the update the other day (had to remove gnash and reinstall the nonfree player).

Now when I full screen in youtube, it'll give me a small box.  I can maximize the box so it actually fullscreens the video (but if I mixclick, like click on the bar at the top and mix the maximize button, the window will close), but the video seems choppier than it should be.  Videos play fine int he normal size.

Before the update, full screen was working fine.

---

### Post by charlescarroll1 on 2008-02-09
> **randy78 said:**
> 
Try closing Firefox and then in a terminal:
sudo apt-get remove flashplugin-nonfree
then
sudo apt-get install flashplugin-nonfree



I removed and then reinstalled the flash plugin like you suggested, but I still can't get videos to go full screen.  

Does anyone know how or if I can remove the update I installed?

---

### Post by charlescarroll1 on 2008-02-09
> **Quilzas said:**
> I'm having a simliar problem.  I got my flash player working again last night as it had failed after the update the other day (had to remove gnash and reinstall the nonfree player).

Now when I full screen in youtube, it'll give me a small box.  I can maximize the box so it actually fullscreens the video (but if I mixclick, like click on the bar at the top and mix the maximize button, the window will close), but the video seems choppier than it should be.  Videos play fine int he normal size.

Before the update, full screen was working fine.

Do you have Compiz installed?  
I had the same problem about a week ago.  In Compiz manager (Advanced Desktop Settings), go to Utility > Workarounds and unselect "Legacy Fullscreen Support".  This had solved my problem anyways.

---

### Post by charlescarroll1 on 2008-02-18
I still can't get fullscreen flash videos.

---

### Post by Curtisc on 2008-02-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/193375](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/193375) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **charlescarroll1 said:**
> Do you have Compiz installed?  
I had the same problem about a week ago.  In Compiz manager (Advanced Desktop Settings), go to Utility > Workarounds and unselect "Legacy Fullscreen Support".  This had solved my problem anyways.

Thanks, this worked for me.  I couldn't find a bug in launchpad about this issue, so I filed one.

---

### Post by amanita on 2008-03-11
Hi, I report the similar issue. When I fresh reboot I can go full screen. After approx. 5 minutes this is not possible for longer than 2 sec.

In my compiz menu (settings -> advanced desktop effects settings -> utility cannot find Workarounds either  "Legacy Fullscreen Support" 

Could you specify where I can find this option?

---

### Post by forrestcupp on 2008-03-11
> **charlescarroll1 said:**
> Do you have Compiz installed?  
I had the same problem about a week ago.  In Compiz manager (Advanced Desktop Settings), go to Utility > Workarounds and unselect "Legacy Fullscreen Support".  This had solved my problem anyways.

Thanks.  That gave me fullscreen back.  It's still a little bit choppy, though.

---

### Post by charlescarroll1 on 2008-03-13
Sometimes I can get full screen flash videos while compiz is running, and sometimes I can't.  I don't know whats up with that....

---

### Post by amanita on 2008-03-13
I switched from KDE 3 to KDE 4 and it's been working flawlessly now.

---

