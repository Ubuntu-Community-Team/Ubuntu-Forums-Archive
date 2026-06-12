---
title: "Which version to Roll my Own and Stallman's Spyware comments"
date: 2013-11-13
forum: General Help
---

### Post by electricrider on 2013-11-13
I'd like to roll my own distro. I'm going to use a combo of either Remastersys or Relinux and Ubuntu Builder. I'm thinking about using 13.04. I need a bare bones distro to build on top of and I've seen the Mini CD but I think it's way too small - incomplete for my needs. I'd like a version of Ubuntu that has no Unity but Only Gnome and No extra GNU software installed except only the GNU apps that are critical to the operation of the OS, no user apps - I want to add all my own user apps.

Is there a distro version like this? I have seen Ubuntu GNOME and it uses Gnome 3.6 or 3.8 I believe but I do not want that Gnome 3.8 style interface as seen here: [http://www.youtube.com/watch?v=w7eRLhduMvI](http://www.youtube.com/watch?v=w7eRLhduMvI) I don't want that interface to even be installed on the system at all - at least if it has to be installed, i want to lock it down so it is NOT accessible to the user.. I think what I want is Gnome 3.6 or 8's fallback session that resembles Gnome 2, so I can build on top of that using AWN and Gnomenu which will then take the place of any visible Gnome.

Is there is a distro like this or if not.. whats the best way (quickest way - not a linux power user) for me to get this set up to build on?

I'm very concerned about Stallman's comments here about Ubuntu phoning home with your search results and telling Amazon.com to spam my PC with ads - Have a look: [http://www.youtube.com/watch?v=CP8CNp-vksc](http://www.youtube.com/watch?v=CP8CNp-vksc)

I need to be absolutely sure this feature does not wind up in my distro. 

Thanks.

---

### Post by whatthefunk on 2013-11-13
Ive never used Remastersys or Relinux before, but my impression is that you make a distro image based on the layout of your current install.  If this is true, you would just need to do a minimal Ubuntu install, purge the Unity stuff, and add the Gnome stuff you want.

---

### Post by electricrider on 2013-11-13
Whats the best way to do a minimal install? Whats the best way to remove Unity .. see.... I haven't used Ubuntu Gnome yet so I don't know what that interface is.. i haven't used Unity so I don't know the difference between Unity and that Gnome interface i'm seeing in the video - Is that actually Unity that i'm seeing in that video or is it a feature of Gnome 3.8?

Will all versions of gnome work in 13.04 or do I have to use 3.8?

Thanks again, and thank you for the reply.

---

### Post by mörgæs on 2013-11-13
Search results being transferred to Amazon is only a 'feature' in Ubuntu, not in X/Lubuntu.

---

### Post by QIII on 2013-11-13
Nor Kubuntu. And the "spyware" thing is really tiresome.

If you want something just like Ubuntu without the shopping lens, just disable it (it can be completely uninstalled if you want) and remaster it.

---

### Post by electricrider on 2013-11-13
Sorry if your tired of hearing about Stallman's comments but I had to ask. I didn't know it could be uninstalled as easily.. I didn't know if it was heavily integrated into the core of the OS or not.. that perhaps it was something Canonical would lock down.

I wouldn't worry about Stallman. He's got a great vision but until GNU and Open Source take my store bought AAA game titles like Crysis 1,2,3, Fallout 3, New Vegas, Battlefield 4 etc and allow me insert disk, install and play, without Wine, without a no cd crack then they Cannot tell folks they cannot use the closed source software they need to get the job done.  It's only "Unethical" in Richards mind. Keeping people from the tools they need IMO is way more unethical. Richard would probably say, " shut up and go write some software" but I don't see him or his team addressing these issues.

Thanks folks.

---

### Post by QIII on 2013-11-13
Until those who write and distribute those titles release versions that will run on Linux, we won't be able to use them.  Nobody in the Open Source community is keeping game distributors from writing proprietary Linux versions.

Stallman can bark all he wants, but if someone writes salable proprietary Linux titles, they'll sell.

If Stallman doesn't like it, too bad for him.

---

### Post by electricrider on 2013-11-13
I agree with that I do.. I just keep hoping for a back engineering of all the proprietary dependencies needed for those games.  I guess that's part of my dream. React OS couldn't get past that so they winded up using Wine.

---

### Post by QIII on 2013-11-13
Those who would do the work still have to feed their kids.

It's an ROI game, and with a 2% market share, Linux loses.  It's just not a wise business decision.  I don't blame anyone for not doing it.

---

### Post by ibjsb4 on 2013-11-13
> I think what I want is Gnome 3.6 or 8's fallback session that resembles Gnome 2

Use the mini iso and do just a command-line-install, then ..

```
sudo apt-get install lightdm synaptic gnome-terminal firefox && sudo apt-get install --no-install-recommends gnome-session-fallback nautilus
```

That will give you next to nothing (no unity either), but yet it has all thats needed to build a Classic desktop.

The panels and Terminal will be black on black at first boot.  The panel background needs to be set on both, press Alt + right click where the panels should be for your context menu.

---

### Post by electricrider on 2013-11-17
Thanks for the answers folks. I may try the Mini after all. though I'm still trying to figure out what version i will use. Seems some apps i wanna use won't work with 13.04 or 13.10

---

### Post by mörgæs on 2013-11-17
Good,  then please mark the thread 'solved'.

---

