---
title: "[SOLVED] ffmpeg:
  Depends: libc6 (&amp;gt;=2.7-1) but 2.6.1-1ubuntu10 is to be installed"
date: 2008-06-16
forum: General Help
---

### Post by Lord Xeb on 2008-06-16
This comes up whenever I try to install ffmpeg... also I cannot upload any of  my pics and vids from my camera to Photobucket... I use to but now it won't show the files that I got from my camera. Any suggestions

---

### Post by rraj.be on 2008-06-16
Just update your system and install all restricted repo's.
```

sudo apt-get update
```

Try this one too

```
sudo apt-get upgrade
```

---

### Post by Lord Xeb on 2008-06-17
> **rraj.be said:**
> Just update your system and install all restricted repo's.
```

sudo apt-get update
```

Try this one too

```
sudo apt-get upgrade
```

Will the upgrade one upgrade my system to 8.04? I do not want it until I am positive it will work right this time (had a few troubles last time). If it does, I am sticking to 7.10 for now.

---

### Post by ibuclaw on 2008-06-17
No, that shouldn't. If you don't have hardy in your sources file, you are OK!

Besides, only the Update-Manager can upgrade your system to hardy without editing your sources file.

But, if you are extremely paranoid, just copy this into the terminal
```

sudo touch /var/lib/synaptic/preferences
sudo ln -s /var/lib/synaptic/preferences /etc/apt/preferences
echo "Package: *
Pin: release a=gutsy-security
Pin-Priority: 1001

Package: *
Pin: release a=gutsy-updates
Pin-Priority: 900

Package: *
Pin: release a=gutsy
Pin-Priority: 800" | sudo tee -a /etc/apt/preferences

```
And by the (very very slim) chance that your system wants to upgrade to hardy, then the above should stop it and prefer the gutsy repos above all else.

Regards
Iain

[EDIT]
When you finally **DO** decide to switch to Hardy, run this command to change your preferences file
```
sudo sed -i 's/gutsy/hardy/g' /etc/apt/preferences
```

---

### Post by Lord Xeb on 2008-06-17
Thanks man! That did it.

---

### Post by Anduu on 2008-06-17
You are trying to install a version of ffmpeg that is not compatible with Gutsy.Hardy uses libc6 version 2.7-1.

Exactly where is this version of ffmpeg you are trying to install from?

Oop I see you fixed it.I assume you had some hardy repos active by mistake?

---

