---
title: "Thunderbird cant save attachments"
date: 2021-03-26
forum: General Help
---

### Post by firesdhgsht on 2021-03-26
Hello. Does anybody know how to convince Thunderbird 78.8.1 (64-bit) on Ubuntu  Budgie 20.10 to use regular paths? At the moment it cant save  attachments because of this error:

[ATTACH=CONFIG]288190[/ATTACH]
I just realised that notepadqq has the same problem. Here is my gparted view:

 [URL="https://aws1.discourse-cdn.com/standard17/uploads/ubuntubudgie/original/2X/1/17d03fabcee071035bf69cd866564164f5b4ab15.png"][IMG]https://aws1.discourse-cdn.com/standard17/uploads/ubuntubudgie/optimized/2X/1/17d03fabcee071035bf69cd866564164f5b4ab15_2_690x318.png[/IMG] 

[/URL]

---

### Post by ajgreeny on 2021-03-26
Was your thunderbird installed as a snap or using the normal ***sudo apt install thunderbird*** method, the snap needing further configuration from the software-centre if it was installed that way in order to allow access to less usual parts of the filesystem.

I can not tell you any more detail as I do not have any snaps installed on my system, nor have I ever used the software-centre or gnome-software as I now think it's called; I always use terminal or synaptic, giving much more detail and control of what's happening.

---

### Post by firesdhgsht on 2021-03-26
Thanks. It was installed via the software center from snapcraft.io if I see it correctly. 

> to allow access to less usual parts of the filesystem.

Is "Documents" considered "less usual". If so, how do I further configure Thunderbird?

---

### Post by deadflowr on 2021-03-26
Looks like you're affected by this bug: [https://bugs.launchpad.net/ubuntu/+source/xdg-desktop-portal/+bug/1905623]("https://bugs.launchpad.net/ubuntu/+source/xdg-desktop-portal/+bug/1905623")

---

### Post by Dennis N on 2021-03-26
1) What is the 'regular path' you are trying to save to?
2) Please post the output of:
> snap connections thunderbird
which should show us what's connected and what isn't.

---

### Post by firesdhgsht on 2021-03-26
Notepadqq is also affected and cannot restore sessions. Here is the TB output:

[ATTACH=CONFIG]288191[/ATTACH]

What is the 'regular path' you are trying to save to? **Downloads**

---

### Post by firesdhgsht on 2021-03-26
> **deadflowr said:**
> Looks like you're affected by this bug: [https://bugs.launchpad.net/ubuntu/+source/xdg-desktop-portal/+bug/1905623](https://bugs.launchpad.net/ubuntu/+source/xdg-desktop-portal/+bug/1905623)

So it seems it is solved in 21.04. My Budgie is still 20.10. How do I update to 21.04? Thanks

---

### Post by Hagar Delest on 2021-03-26
Wait 22-APR-2021: [https://www.omgubuntu.co.uk/2021/01/ubuntu-21-04-release-features](https://www.omgubuntu.co.uk/2021/01/ubuntu-21-04-release-features)
In the bug report, comment #7 may help.

---

### Post by Dennis N on 2021-03-26
Well, if the 'Documents' folder is at ~/Documents, then you should be able to access that location, since the 'home' interface is connected. But locations inside your home folder are the only places you can access, given the way this snap is configured.

Could access require a key? The 'gpg-keys' is not connected. You can enable key access with:
```
snap connect thunderbird:gpg-keys
```

Otherwise, the problem may be the bug that's been mentioned.

---

### Post by ajgreeny on 2021-03-26
Another alternative option for you is to remove the thunderbird snap version with ***sudo snap remove thunderbird*** and install using the .deb version with ***sudo apt install thunderbird***.  Until very recently, Feb 25th, 20.04 repos had thunderbird version 68 only which did upset some users but it was then updated to 78 as it still is when installed using apt.

That version will save things to wherever you want with no problems.

---

### Post by firesdhgsht on 2021-03-26
Good stuff. Thank you for all the help. As soon as I replaced all the snap apps by their apt counterparts they work as intended. Stranger things.

---

### Post by ajgreeny on 2021-03-27
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

### Post by merliner on 2021-04-17
I've seen this problem using the snap tbird on v18.04 with xfce4.
I haven't solved it yet, but using the top menu Message ->Attachments ->Save All does manage to work

I'll likely hasten to upgrade to 20.04 and move to the standard distribution tbird

---

