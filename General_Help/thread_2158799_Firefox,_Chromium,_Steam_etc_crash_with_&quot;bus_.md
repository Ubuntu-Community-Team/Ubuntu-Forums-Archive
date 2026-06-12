---
title: "Firefox, Chromium, Steam etc crash with &quot;bus error&quot;"
date: 2013-06-30
forum: General Help
---

### Post by Soulcrusher on 2013-06-30
I am having trouble with applications that crash at startup or randomly while using. The error that causes the applications to fail is usually "bus error".
When I run steam through the terminal, it won't show up and I get this:
> Running Steam on ubuntu 13.04 64-bit
STEAM_RUNTIME has been set by the user to: /home/nils/.local/share/Steam/ubuntu12_32/steam-runtime
Installing breakpad exception handler for appid(steam)/version(1370553818_client)
Installing breakpad exception handler for appid(steam)/version(1370553818_client)
unlinked 0 orphaned pipes
Gtk-Message: Failed to load module "overlay-scrollbar"
Installing breakpad exception handler for appid(steam)/version(1370553818_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20130630204936_1.dmp
/home/nils/.local/share/Steam/steam.sh: line 704:  5038 Bus error               (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
If I run Firefox through terminal and try to add a dictionary, add plugins or visit certain sites, it crashes and the terminal says:
> (process:5465): GLib-CRITICAL **: g_slice_set_config: assertion `sys_page_size == 0' failed
Bus error (core dumped)

Chromium crashes randomly as well. I cannot access its log but I assume it's the same error.

Anyone got an idea what's wrong? I have used another installation of Ubuntu on this system without having this issue. I am running Ubuntu 13.04.

---

### Post by sanderj on 2013-06-30
I would start by running memtest86 from the GRUB boot menu, and let it run for a few hours.

---

### Post by pqwoerituytrueiwoq on 2013-06-30
Check the disk utlity and or gsmartcontrol and make sure the HDD is not failing
IF YOU HEAR TICKING FROM THE HDD BACK EVERYTHING UP IT IS DYING

---

### Post by Soulcrusher on 2013-07-02
Thanks for the replies both. I haven't tried running the memtest but I will soon. Even though I suspect it's not the issue as I run windows allongside it with no problems, it could not hurt to check it.

As for the HDD, I tend to be very cautious about HDD failure as it sadly happened quite a few times already to me. I did run a smart test and other than having a 2 sec spinup time (7200rpm), it is a perfectly healthy half year old drive.

---

