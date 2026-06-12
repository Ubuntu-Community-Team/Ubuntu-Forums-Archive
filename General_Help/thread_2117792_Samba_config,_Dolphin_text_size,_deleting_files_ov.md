---
title: "Samba config, Dolphin text size, deleting files over smb shares, and window features."
date: 2013-02-19
forum: General Help
---

### Post by Roasted on 2013-02-19
Running Kubuntu 12.04 64 bit with KDE 4.10. I have a few questions I'm trying to figure out.

Samba - I noticed that I could just right click a folder and share it via Samba under the share tab. I ran the smbpasswd -a user command to add my Samba user and just like that my Samba configs worked. Thing is, smb.conf has no additional shares that I could see. Where on earth does KDE store the smb configs at?

Dolphin - I recall in older KDE versions that the text size of the left navigation would scale according to how wide the left nav section is. This is not happening in 4.10 and I'd like to make that text size larger. Any idea how one could do this?

Dolphin/Samba II - In the event I want to delete something from a Samba share, I must highlight the item and hit delete. If I right click and hit move to trash (which the del key is assigned to from what I can see), it says something about that this task does not support the protocol trash. Eh? When I right click and see "Move to trash" it says (del) right next to it. What's the difference then?

**EDIT - Figured this one out. Setting is within System Settings - Window Behavior - (left side) Window Behavior - Titlebar Actions. KDE, I love you, but you have so many dang features it's not difficult to get lost in configuring them! :P  **     Window feature - In Ubuntu, I used to be able to right click on a window's titlebar and it would background that window. I grew to depend on this feature quite a bit. This is a feature I have not tracked down in KDE. Does it exist? If so, how would one enable it?

Thanks everyone!

---

### Post by csillva on 2013-02-20
> **Roasted said:**
> In Ubuntu, I used to be able to right click on a window's titlebar and it would background that window. I grew to depend on this feature quite a bit. This is a feature I have not tracked down in KDE. Does it exist? If so, how would one enable it?

In the future I'd recommend marking this thread as solved - since you found the solution - and then starting a new thread for the second question. If someone who knew the answer to your second question, but not the first, was browsing the forums they would not click into your thread to help you out. 

Now I'm about to prove me wrong, but it's a good principle to live by anyway. 

>system settings >window behavior > title bar actions tab >title bar & frame, under active, right button: change to minimize

---

