---
title: "Mount Point mistake.. how to correct?"
date: 2007-07-05
forum: General Help
---

### Post by stevesheldon on 2007-07-05
Last night I thought I would try to set up my Garmin sat nav under Wine to update its files using the Garmin POI loader. The software needs my Garmin to appear at a fixed location, so I went into the properties for the drive and set a fixed mount point. The fixed mount point was accepted OK, but as soon as I plugged it back in to test the mounting, an error appeared saying unable to mount successfully due to a space or / in the mount path which is not allowed. Now I cannot access the drive to remodify the parameters.
Does anyone know where I find the mount path so I can delete it?
I am running Feisty Fawn, AMD64, 1Gb ram, and 320Gb SATA HDD.
Many thanks in advance for any help in fixing my mounting problem 
Steve Sheldon
[email]steve.sheldon@photo-me.co.uk[/email]

---

### Post by jazzgossen on 2007-07-05
Look at [this thread.]("http://ubuntuforums.org/showthread.php?t=376404") You need to edit /system/storage/volumes/_org_freedesktop_Hal_devices_volume_uuid_2463_ABF7/mount_point in gconf-editor.

---

