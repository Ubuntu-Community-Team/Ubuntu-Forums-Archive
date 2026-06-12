---
title: "Wings3D crashes when I try to make a shape"
date: 2007-11-08
forum: General Help
---

### Post by dyankee23 on 2007-11-08
I'm running Gutsy, and haven't had any problems with it until I tried firing up my Wings3D.

When I tried to create a shape, the program crashed.  I uninstalled and reinstalled Wings with both Add/Remove and apt-get, but the error persists.  Here's the terminal output on startup:

>  [{buffer_size,24},{depth_size,32},{stencil_size,8},{accum_size,16}]
  [{buffer_size,24},{depth_size,24},{stencil_size,8},{accum_size,16}]
Actual: RGBA: 8 8 8 0 Depth: 24 Stencil: 8 Accum: 16 16 16 16
Failed to load perlin_noise_drv in /usr/lib/erlang/lib/wings-0.98.36/plugins/accel
Driver compiled with incorrect version of erl_driver.h
wpc_pnoise:init/0 bad return value: {'EXIT',
                                     {startup_fault,
                                      [{pnoise,start,0},
                                       {wpc_pnoise,init,0},
                                       {wings_plugin,init_plugin,2},
                                       {wings_plugin,init_plugins,1},
                                       {wings,init,1}]}}
Failed to load wings_ogla_drv in /usr/lib/erlang/lib/wings-0.98.36/plugins/accel 
Driver compiled with incorrect version of erl_driver.h
wpc_ogla:init/0 bad return value: {'EXIT',
                                   {startup_fault,
                                    [{wpc_ogla,init,0},
                                     {wings_plugin,init_plugin,2},
                                     {wings_plugin,init_plugins,1},
                                     {wings,init,1}]}}


Any help would be appreciated.

---

### Post by wildman2 on 2007-11-21
Same thing happened to me.
Driver compiled with incorrect version of erl_driver.h

---

### Post by salviablue on 2008-03-01
Has anyone managed to come up with a solution yet. I read somewhere to install the lastest erl whatsit and then reinstall wings3d and that makes it work. Well not for me, or I just am not doing things right. ANYONE?? (I really want to make some ships for Oolite!)

---

### Post by salviablue on 2008-03-01
Perfect fix found (I think). Download the latest dev release.
wings3d-0.99.01
[http://www.wings3d.com](http://www.wings3d.com)

It sdevelopment release but I have had no problems with it whatsoever (so far, touch wood).

gutsy ati radeon express 200M (advent 7201 laptop)

---

