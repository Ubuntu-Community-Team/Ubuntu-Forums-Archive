---
title: "Is it possible to have both GNOME and KDE installed?"
date: 2007-10-31
forum: General Help
---

### Post by Zdravko on 2007-10-31
Hi!
Is it possible to have both GNOME (the standard Ubuntu) and KDE DE at the same time? How do I choose the DE? Will the other DE interfere with GNOME? Are there any issues like slowing down processes etc.?
Thanks in advance!

---

### Post by jfinkels on 2007-10-31
> **Zdravko said:**
> Hi!
Is it possible to have both GNOME (the standard Ubuntu) and KDE DE at the same time? How do I choose the DE? Will the other DE interfere with GNOME? Are there any issues like slowing down processes etc.?
Thanks in advance!

Yes, just do ```
sudo aptitude install kubuntu-desktop
```

You can choose the X session to start when the login manager (GDM) starts up after Ubuntu finishes its initial boot sequence and the X window system starts.

Installing kubuntu-desktop will install a bunch of KDE-native applications that will be added to your main menu and won't follow the look and feel of GNOME applications, but there should be no breakage.

I see no reason for processes to run more slowly. However, installing KDE will take up a hefty chunk of hard drive space (about 750MB?).

---

### Post by Zdravko on 2007-10-31
750 MB Woot? Maybe I should stick to one of the DE forever? Or should I give KDE a try for a while? Everyone says it is betterthan GNOME, but I've never tried it yet.

---

### Post by nowshining on 2007-10-31
it's ur choice after u use kde for awhile then u should be able to uninstall Gnome, however it will take the gnome apps with it I think. :)

---

### Post by MrFSL on 2007-10-31
> Everyone says it is betterthan GNOME,


....well... not "EVERYONE"...

---

### Post by JBAlaska on 2007-10-31
Personaly, I prefer Gnome desktop to KDE..but there are some very cool KDE apps, like Dolphin, KVirc, ktorrent, konqueror and KompoZer.

---

### Post by tubasoldier on 2007-10-31
I personally think KDE has a lot more apps that are sweet. Amarok, digikam, kooka, K3B... 

However, I like both KDE and GNOME. I switch between the two when I get tired of one. They could learn a lot from each other if they sat down and worked together.

But of course desktop environment is totally a personal opinion. I say use them and see which one fits your needs the best.

---

### Post by jfinkels on 2007-10-31
I am currently using and LOVING the ion window manager. Forget those clunky desktop environments and say hello to pure efficiency.

---

### Post by ramjet_1953 on 2007-10-31
Yes, there are some really nice KDE apps like k3b, k9copy, Kate, etc.

However, you don't need to install KDE to use them under GNOME.

When you choose to install a KDE app under GNOME, it will install only the bare essentials to make it work.

Regards,
Roger 8)

---

### Post by Zdravko on 2007-10-31
Hmmm. Let me see. Will we have KDE4 in Hardy?

---

