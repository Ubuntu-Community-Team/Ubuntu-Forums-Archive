---
title: "Default/Pre-loaded Splash Screen"
date: 2007-08-27
forum: General Help
---

### Post by ArtF10 on 2007-08-27
Hi, I have a question regarding Splash Screen Manager.

Can someone please tell me what is installed by default in Ubuntu, by entering the word splash in Synaptic?  I'd like to know what package is installed...there is only one.  I installed Splash Screen MAnager and want to Completely Remove it but forgot which package was installed by default so I don't know exactly which packages to remove.

Here's what I did:

I searched for Splash in Synaptic and and installed it but I find that it 

a.  only accepts .Jpg files as splash screens NOT .svg.gz.  If I say Install and Open an .svg.gz file, it just closes the Splash screen manager.

b.  it only changes the image in the small rectangular box that appears when Ubuntu is loading.  I thought that this software would change the ENTIRE splash screen...i.e. it would fill the enter screen, NO?  Am I missing something?  Would an .svg.gz (or OTHER) file fill the enter screen or is this all I can expect?

---

### Post by Steve1961 on 2007-08-27
> **ArtF10 said:**
> Hi, I have a question regarding Splash Screen Manager.

Can someone please tell me what is installed by default in Ubuntu, by entering the word splash in Synaptic?  I'd like to know what package is installed...there is only one.  I installed Splash Screen MAnager and want to Completely Remove it but forgot which package was installed by default so I don't know exactly which packages to remove.

Here's what I did:

I searched for Splash in Synaptic and and installed it but I find that it 

a.  only accepts .Jpg files as splash screens NOT .svg.gz.  If I say Install and Open an .svg.gz file, it just closes the Splash screen manager.

b.  it only changes the image in the small rectangular box that appears when Ubuntu is loading.  I thought that this software would change the ENTIRE splash screen...i.e. it would fill the enter screen, NO?  Am I missing something?  Would an .svg.gz (or OTHER) file fill the enter screen or is this all I can expect?

The splash screen manager just manages the gdm splash - the small splash that loads after you log in.  I think you're talking about the boot splash - called usplash:

[http://ubuntuforums.org/showthread.php?t=524085&highlight=usplash](http://ubuntuforums.org/showthread.php?t=524085&highlight=usplash)

---

### Post by ArtF10 on 2007-08-27
Actually, I'm talking about the small splash that loads after logging in.  The default screen is light brown with a light brown box(presumably this is the small splash...I see Nautilus inside the box) in the centre of it.  I was hoping to change the entire screen from light brown to silver, rather than change just the small splash (box) to silver while leaving the rest of the screen light brown.

---

### Post by Dark Star on 2007-08-27
You mean Gnome Splach Screen Manager :? Ok do this
```
sudo aptitude remove gnome-splashscreen-manager
```

---

### Post by ArtF10 on 2007-08-27
Thanks.

Will it remove all dependencies as well because a few packages were installed through Synaptic, not just one.

---

