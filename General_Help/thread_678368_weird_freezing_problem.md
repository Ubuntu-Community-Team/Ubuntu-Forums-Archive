---
title: "weird freezing problem"
date: 2008-01-25
forum: General Help
---

### Post by saygin on 2008-01-25
Hi all,

I have a weird screen freeze problem. When I press the "log off/shut down" button on the top-right corner of the screen, everything freezes. I mean, the mouse and keyboard still work, however, I can't click on anything, or nothing responds. By the way my system monitor applet on the panel still shows the CPU and Network graphs continuously. But of course, I nothing happens when I click on it. What can I do? please help...

(by the way, I tried reinstalling such things like "gnome-applets" via the synaptic, but nothing changed.)

---

### Post by Metaljaz on 2008-01-25
Are you able to do anything on the computer or does this just happen when you are ready to shut down?

---

### Post by saygin on 2008-01-26
I didn't understand what you mean. But, everything is normal, I can use it as there is no problem. Whenever I click that button, screen freezes. Maybe, it is because of using fsck.ext3. When I was trying to open the computer, it started to check the root filesystem and then said, I should do it manually. Then I did it. It broke my nvidia driver and I reinstalled it. And everything was OK. I don't know why I didn't realize it before, maybe I was too sleepy... 

I think it is a lost file problem. blabla.glade file may be missing. in "/usr/share/gnome-applets/glade" folder, there are some .glade files for applets but there is no file for log out button. Is this a problem? I mean, should there be one for this applet?  Or is there another reason for this?

---

### Post by saygin on 2008-01-26
ok, I've found it, for the other users who might have the same issue, it is power management daemon. I don't know why it depends on it, but after fsck, it is unchecked in System -> Preferences -> Sessions. I checked it and everything about it is OK now.

---

