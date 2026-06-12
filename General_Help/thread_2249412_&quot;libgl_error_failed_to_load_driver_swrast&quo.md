---
title: "&quot;libgl error failed to load driver: swrast&quot;"
date: 2014-10-22
forum: General Help
---

### Post by crimson30 on 2014-10-22
(Lack of) technical level: I've been running Ubuntu on a server for years just fine using only samba and ssh.  I'm taking an online class that requires use of octave and so I installed xrdp and octave (today).  I'm currently using xfce for the rdp session and it works great.

If I go into octave and do something simple like:
a=1
plot(a)

I get:
"libgl error failed to load driver: swrast"

If I do the same thing in gnuplot, it works fine.

Running lshw -c video, I get:
  *-display UNCLAIMED
       description: VGA compatible controller
       product: MGA G200eW WPCM450
       vendor: Matrox Electronics Systems Ltd.
       physical id: 3
       bus info: pci@0000:07:03.0
       version: 0a
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: latency=64 maxlatency=32 mingnt=16
       resources: memory:dd000000-ddffffff memory:df000000-df003fff memory:de800000-deffffff

Update: Unfortunately, my server is in a difficult location (rack-mounted in a ventilation shaft), but I logged in locally and using the default desktop (unity, I think), it works.

Any ideas on how to get it to work under xfce??

---

### Post by whitethunder922 on 2014-11-04
I'm having a similar problem:

$ glxinfo
name of display: :0
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: NVIDIA Corporation
...

$ locate swrast
/usr/lib/i386-linux-gnu/dri/kms_swrast_dri.so
/usr/lib/i386-linux-gnu/dri/swrast_dri.so
/usr/lib/x86_64-linux-gnu/dri/kms_swrast_dri.so
/usr/lib/x86_64-linux-gnu/dri/swrast_dri.so

I'm guessing it's a path issue but I don't know what the right path should be.

---

