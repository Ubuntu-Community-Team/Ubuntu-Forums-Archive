---
title: "How to increase font size of KDE  application"
date: 2023-11-30
forum: General Help
---

### Post by satimis on 2023-11-30
Hi all,

I have kdenlive running here. I want to increase the font size of its display/desktop.  But I couldn't find kdeglobals.  Please advise where is it located?  OR is there any other way increasing the font size?

Please advise.

Thanks

Regards

---

### Post by dragonfly41 on 2023-11-30
I happen to have kdenlive installed for past experiment. Can't see any obvious tweaks at first glance but perhaps here ..

[https://docs.kdenlive.org/en/user_interface/customizing_interface.html](https://docs.kdenlive.org/en/user_interface/customizing_interface.html)

---

### Post by satimis on 2023-11-30
> **dragonfly41 said:**
> I happen to have kdenlive installed for past experiment. Can't see any obvious tweaks at first glance but perhaps here ..

[https://docs.kdenlive.org/en/user_interface/customizing_interface.html](https://docs.kdenlive.org/en/user_interface/customizing_interface.html)
Gnome-tweaks can't help.
Font size: 28
Scaling Factor: 1.80

Even increasing to 58

fonts on Kdenlive don't change at all.  I have read several Kdenlive tutorials online but I couldn't discover anything related.

I suppose they are controlled by KDE configuration.  But also I couldn't find anything related on Ubuntu.

Regards

---

### Post by SeijiSensei on 2023-11-30
If you used Kubuntu, you wouldn't have this problem.

---

### Post by satimis on 2023-11-30
> **dragonfly41 said:**
> I happen to have kdenlive installed for past experiment. Can't see any obvious tweaks at first glance but perhaps here ..

[https://docs.kdenlive.org/en/user_interface/customizing_interface.html](https://docs.kdenlive.org/en/user_interface/customizing_interface.html)
Hi dragonfly,

Further to my previous posting

I'll install a KDE desktop Ubuntu 22.04 VM and test Kdenlive to see whether there is mini-font size problem.

I'll come back later.

Regards

---

### Post by satimis on 2023-11-30
> **SeijiSensei said:**
> If you used Kubuntu, you wouldn't have this problem.
Hi,

Thanks for your advice.

What is the differece between Kubuntu and Ubuntu with KDE desktop?

Regards

---

### Post by dragonfly41 on 2023-11-30
Two thoughts ..

Perhaps Kubuntu might run separately in VM?

Perhaps kdenlive could be built from source (e.g. using Qt Creator since it is Qt5)? But that is a big undertaking.

---

### Post by satimis on 2023-11-30
> **dragonfly41 said:**
> Two thoughts ..

Perhaps Kubuntu might run separately in VM?

Perhaps kdenlive could be built from source (e.g. using Qt Creator since it is Qt5)? But that is a big undertaking.
Now I have Kubuntu 22.04 running as VM. Pls refers to screenshot attached.

Its operation is not the same as Ubuntu.  I'm now configuring it.  I'll run Flatpak to install Kdenlive later.

Regards

---

### Post by satimis on 2023-11-30
Hi all,

On Kubuntu Terminal run following commands;
```

$ flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
$ flatpak install flathub org.kde.kdenlive
$ flatpak run org.kde.kdenlive

```

Kdenlive starts.  Its desktop is much better.  Please refers to screenshot.

But "Pin to Task Manager" is greyout".  I'll ask Kubuntu Forum its fix.

Regards

---

