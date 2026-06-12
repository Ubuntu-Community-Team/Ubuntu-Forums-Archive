---
title: "Thunar: hot-plug removable drive"
date: 2014-04-06
forum: General Help
---

### Post by vasa1 on 2014-04-06
In Thunar 1.6.3 *Edit > Preferences > Advanced > Configure the management of removable drives and media > Storage > Removable storage*, what does "**hot-plugged**" mean in the first option?

---

### Post by coldraven on 2014-04-06
AFAIK Hot-plugged or Hot-swapped refers to systems with drives that can be connected while switched on. Try Googling "NAS hot-plug" for network attached servers with this ability.
I suppose that the only difference is that flash drives, SD cards and CDs are mounted as "Media" and HDDs are mounted as "Filesystem" or "Drives". (sorry but using Nautilus at the moment).
It could just as well have said "Connected" instead of "Hot-plugged" as most people would be doing it when the PC is switched on.
If you plugged in a drive that had a huge amount of data you might not want it to mount immediately because it would take a long time to display the content .
I'm not an expert but I hope this helps.

---

### Post by Toz on 2014-04-07
I just spent some time going through the code to see if I can figure out the difference. Here is what I found:

1. "Hot-plugged" refers to the xfconf key -> /thunar-volman/automount-drives
2. "Inserted" refers to the xfconf key -> /thunar-volman/automount-media
(Note: you can use the Settings Editor to view xfconf keys)

The source code file that references/uses these keys is [tvm-block-device.c]("http://git.xfce.org/xfce/thunar-volman/tree/thunar-volman/tvm-block-device.c"). 

The snippet referring to automount-drives is:
```
else if (is_partition || is_volume)
    {
      /* check if automounting drives is enabled */
      automount = xfconf_channel_get_bool (context->channel, "/automount-drives/enabled",
                                           FALSE);
      if (automount)
        {
          /* mount the partition and continue with inspecting its contents */
          tvm_block_device_mount (context);
        }
      else
        {
          /* finish processing the device */
          tvm_device_handler_finished (context);
        }
    }
```

The snippet referring to automount-media is:
```
if (is_cdrom)
...
...
...
          else if (data_tracks > 0)
            {
automount_disc:
              /* check if automounting media is enabled */
              automount = xfconf_channel_get_bool (context->channel, 
                                                   "/automount-media/enabled", FALSE);
              if (automount)
                {
                  /* mount the CD/DVD and continue with inspecting its contents */
                  tvm_block_device_mount (context);
                }
            }
```

So, if I'm reading this correctly, "hot-plugged" refers to any device that has a partition whereas "inserted" refers to audio/video CD/DVDs.

---

