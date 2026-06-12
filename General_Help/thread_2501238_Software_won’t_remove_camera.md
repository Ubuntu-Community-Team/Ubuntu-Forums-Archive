---
title: "Software won’t remove camera"
date: 2024-09-28
forum: General Help
---

### Post by wilsojeffrey on 2024-09-28
I like to get rid of anything I don’t/won’t use on this machine. Upgraded to the latest LTS this morning and it put the camera back on (deleted it on the previous version). It won’t uninstall. Provides the warning message, then just doesn’t do anything. Other app installs/uninstalls seem to work, but the camera one won’t. Is there a terminal command that I can use?

---

### Post by QIII on 2024-09-29
What warning message are you being given?

---

### Post by wilsojeffrey on 2024-09-29
No warning messages. I click “uninstall “ and it just doesn’t do anything

---

### Post by ajgreeny on 2024-09-29
> **wilsojeffrey said:**
> No warning messages. I click “uninstall “ and it just doesn’t do anything
But what exactly are you trying to uninstall? 
We can't help you without knowing the details of what you've done so far and which application you can't remove.

---

### Post by wilsojeffrey on 2024-09-29
It&#8217;s just called &#8220;Camera&#8221;.

---

### Post by Rubi1200 on 2024-09-29
I am not sure what app you mean.

Any chance you can take a screenshot of where you are trying to uninstall from and posting it here?

Thanks.

---

### Post by tea for one on 2024-09-29
> **wilsojeffrey said:**
> It’s just called “Camera”.
Is this it?
[https://apps.gnome.org/en-GB/Snapshot/](https://apps.gnome.org/en-GB/Snapshot/)
[https://packages.ubuntu.com/noble/gnome-snapshot](https://packages.ubuntu.com/noble/gnome-snapshot)

---

### Post by yancek on 2024-09-29
> It&#8217;s just called &#8220;Camera&#8221;.                 

Are you trying to do this from the graphical Ubuntu Software manager?  Have you tried removing it by using a terminal.  If it is the software from the first link in post 7, this is not software installed on a default system so you might go to your notes from the time you installed it.   Check to see if it is flatpak or snap before trying to uninstall, explained at the link below.

[https://askubuntu.com/questions/1457293/how-to-find-whether-an-app-is-a-snap-or-a-flatpak-or-a-native-app-in-terminal](https://askubuntu.com/questions/1457293/how-to-find-whether-an-app-is-a-snap-or-a-flatpak-or-a-native-app-in-terminal)

The home page seems to indicate it is a 'flatpak' so doing an online search to remove flatpak software should give you a number of results such as the link below.

  [https://forums.linuxmint.com/viewtopic.php?t=387079](https://forums.linuxmint.com/viewtopic.php?t=387079)

---

### Post by ajgreeny on 2024-09-29
I can find no application named camera in the Ubuntu repos though I admit that my search does not include snap-store, flatpacks or appimages. All I can see is camera.app which is for downloading/importing pictures from a digital camera and not what I think you're asking about.

Please tell us more.
Where did this camera application come from and how did you install it?

---

### Post by yancek on 2024-09-29
On Ubuntu 22.04, clicking on Ubuntu Software and then the search menu when it opens, type in Camera and it shows.  It's what is showed in the first link in post 7 and looks to be poorly rated and seems to be a flatpak install which is probably why it doesn't uninstall/delete from  Ubuntu Software.

---

### Post by Norm24 on 2024-09-29
In 24.04 "Camera" is listed twice in Software as a Flatpak and an Ubuntu .deb.The Flatpak version is:Snapshot 47.0.1 release and the .deb is:Version 0.1.0git20221220.

---

### Post by wilsojeffrey on 2024-09-30
> **tea for one said:**
> Is this it?
[https://apps.gnome.org/en-GB/Snapshot/](https://apps.gnome.org/en-GB/Snapshot/)
[https://packages.ubuntu.com/noble/gnome-snapshot](https://packages.ubuntu.com/noble/gnome-snapshot)

Yes.That's it

---

### Post by wilsojeffrey on 2024-09-30
I don't know how to attach a screenshot

---

### Post by wilsojeffrey on 2024-09-30
Awesome. Just want it gone

---

### Post by tea for one on 2024-09-30
> **wilsojeffrey said:**
> Is there a terminal command that I can use?
```
sudo apt remove gnome-snapshot
```
There may be dependencies to remove if you wish
```
sudo apt autoremove
```

---

### Post by wilsojeffrey on 2024-09-30
Thank you so much. It's gone.

---

### Post by tea for one on 2024-09-30
> **wilsojeffrey said:**
> Thank you so much. It's gone.
You're welcome
It's a nice gesture to mark the thread as solved to help other forum users/searchers:-
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by wilsojeffrey on 2024-09-30
> **tea for one said:**
> You're welcome
It's a nice gesture to mark the thread as solved to help other forum users/searchers:-
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

thanks I will

---

