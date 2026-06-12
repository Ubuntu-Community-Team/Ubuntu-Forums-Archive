---
title: "Recently reinstalled... Resolution messed up."
date: 2007-09-09
forum: General Help
---

### Post by Ace02 on 2007-09-09
I installed Ubuntu for the first time on this machine just a couple of days ago. About a two hours ago I messed things up pretty bad, and just wanted to do a fresh reinstall. Through the installation, I went to manual since I didn't want to resize a partition and didn't want to use the whole disk. My then current Ubuntu partition, I ticked in format and set it to the root dir (/) and continued on. I installed all of the updates from the update manager, but things are a little bit different now. My Windows partition used to show up as "volume 220GB" and I had to mount it, where it would show up as "disk" on the desktop. Now it just shows up as sda1 on the desktop, and I can't unmount it. This doesn't bother me, but I guess it's something to note. The thing that *does* bother me, is that my resolution only goes up to 1024x768. Just three hours ago I had it at 1280x1024 in Ubuntu. I can't use 1024x768 on this monitor, everything looks blurry and it gives me a headache...

If anyone has some insight or fixes they could share, I would really appreciate it!

---

### Post by Ace02 on 2007-09-09
I've fixed it, here's what I did for anyone else who may encounter this in the future:

```

sudo nvidia-settings

```

Run the above command in the terminal, and enter your password. On the left there should be a Display Configuration tab to click, then on the right you should be able to set the resolution, hit Apply. Then you'll need to click the Save to X Configuration File, if you don't do this it seems that you'll have to run the above command every time you start your computer. You can go ahead and quit out of the *n*Vidia window. Now go to System>Preferences>Screen resolution and select the resolution that was previously unavailable, and tick in Make Default for this Computer.

I'm not sure if this would work with non-*n*Vidia graphics cards.

---

