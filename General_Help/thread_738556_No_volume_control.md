---
title: "No volume control"
date: 2008-03-28
forum: General Help
---

### Post by wushuFreak on 2008-03-28
Hi,

I recently installed a sound card. I disabled the on-board audio in BIOS. 

I am getting audio, but it is output at full volume and I cannot change it.

I re-enabled the on-board audio just to test it. At the login screen I get the drum sound out of the PCI card. After login, audio comes from the on-board (only when enabled in BIOS) and I can control the volume.

This leads me to believe that the controls are still mapped to my on-board even though they are no longer the audio source. I wanted to post and get some advice before I screw things up terribly.

Thanks in advance.

---

### Post by Bubba64 on 2008-03-28
It may be the assignment of control right click on the volume control then preferences and then pcm or master just keep searching until you find the one that controls the volume,

---

### Post by wushuFreak on 2008-03-28
I tried every one of them with no effect.

Something else I thought was interesting. When I use my keyboard volume control, I get a visual of the volume slider but it does not sync with the one on the task bar (and has no effect on the actual volume.

---

### Post by Bubba64 on 2008-03-28
I have gnome alsa mixer installed from add remove this will show all the controls, but you can show a large amount of them too with the open volume control edit then preferences click everything open then search for a controller that works. My volume controller on the top panel is the one from add to panel with a right click on he panel. the stock volume control from applications has never worked on any of the distros on 3 different computers for me. I would install gnome alsa mixer from add remove that will give you the best and east access at least it does for me. On my laptop the volume control on the laptop itself work but are separate from the volume control on the panel

---

### Post by wushuFreak on 2008-03-28
I installed the gnome Alsa mixer and when I try to run it I get the following:
```
Bad key or directory name: "/apps/gnome-alsamixer/display_mixers/": Key/directory may not end with a slash '/'
Bad key or directory name: "/apps/gnome-alsamixer/display_names/": Key/directory may not end with a slash '/'

```

It will open, but has no effect.

---

### Post by Bubba64 on 2008-03-28
Are you clicking on it from sound and video or running it from the terminal. To be honest with you this seems to be more technical than I can help you with so hopefully somebody who is more knowledgeable will post.

---

### Post by wushuFreak on 2008-03-28
I am clicking on it from sound and video.

When I do I get a pop-up with the following message:

An error occurred while loading or saving configuration information for GNOME ALSA Mixer. Some of your configuration settings may not work properly.

It has a details button which is where I obtained the previous information.

---

### Post by Bubba64 on 2008-03-28
I have no other ideas sorry, but I do wonder if you have tried a restart after the changing of the bios status that sometimes can make things work but that is my unknowledgeable thing I generally try.

---

### Post by wushuFreak on 2008-03-28
I have done a few restarts since. 

Well, I certainly appreciate your efforts. I will keep at it.

---

