---
title: "Switched to Generic Kernel, All startup customizations gone"
date: 2006-11-25
forum: General Help
---

### Post by hatsix on 2006-11-25
So I upgraded to Edgy, finally figured out that I had to use the -generic kernel to get both Cores of my Core Duo working. When I boot to my -generic kernel, however, my fstab doesn't auto-mount my SMB shares (it did before, the lines are still in there, and I can mount the shares after I'm in Gnome), and I can't get anything to save to my session-startup.

My FSTAB: 
```

//wanderbyte/library		/library			smbfs	dmask=777,fmask=777	0	0
//wanderbyte/TorrentsToDownload	/incoming/WanderbyteTorrents	smbfs	dmask=777,fmask=777	0	0

```

I've tried to add beryl-manager to my session startup, logging out right away to see if it accepted the changes, but nothing works.

Am I supposed to run any commands when I switch kernels? I don't know why Edgy automagically installed the i386 Kernel, rather than the Generic Kernel... I can't find anything on the forums ](*,)

---

