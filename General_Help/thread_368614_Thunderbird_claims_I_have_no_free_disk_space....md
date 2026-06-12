---
title: "Thunderbird claims I have no free disk space..."
date: 2007-02-23
forum: General Help
---

### Post by Starlight on 2007-02-23
Hello, I have a problem. A few days ago I decided to update everything on my system with Adept, and since then Thunderbird refuses to download new emails, and says I have no free disk space for them. I have about 320 MB free, and I made sure that all the directories which Thunderbird uses for emails are on the disk with free space... I even tried deleting a lot of emails, and also a few larger files from my disk, but Thunderbird still says I have no free disk space. Can someone help me fix it?

---

### Post by gwpritch on 2007-02-23
try this:

```
sudo apt-get clean
```

then try again.

If that doesn't work post results of:

```
df -a
```

---

### Post by Starlight on 2007-02-23
> **gwpritch said:**
> try this:

```
sudo apt-get clean
```

then try again.

If that doesn't work post results of:

```
df -a
```
It seems that it works now after doing sudo apt-get clean, thanks! :)

---

### Post by gwpritch on 2007-02-23
When you did your upgrade, Adept downloaded all the packages to your /var directory. I don't use thunderbird but I imagine it also stores email data there. apt-get clean removes all those .deb files from the apt cache, freeing up the necessary space.

---

### Post by Starlight on 2007-02-24
Cool, thanks for telling me :)

---

