---
title: "Custom kernel 2.6.9 compile fault"
date: 2004-11-06
forum: General Help
---

### Post by Burnout on 2004-11-06
I wanted to test the new 2.6.9-rc4 kernel with my Ubuntu install. So I downloaded the sources and I made it ready for install. Copyed the .config and so on...
When I try to compile the kernel, I get these faults:```
sudo make
  CHK     include/linux/version.h
make[1]: `arch/i386/kernel/asm-offsets.s' is up to date.
  CHK     include/linux/compile.h
  CC [M]  drivers/char/drm/gamma_drv.o
In file included from drivers/char/drm/gamma_drv.c:42:
drivers/char/drm/gamma_context.h: In function `gamma_context_switch_complete':
drivers/char/drm/gamma_context.h:193: error: structure has no member named `next_buffer'
drivers/char/drm/gamma_context.h:193: error: structure has no member named `next_buffer'
In file included from drivers/char/drm/gamma_drv.c:44:
drivers/char/drm/gamma_old_dma.h: In function `gamma_clear_next_buffer':
drivers/char/drm/gamma_old_dma.h:40: error: structure has no member named `next_buffer'
drivers/char/drm/gamma_old_dma.h:41: error: structure has no member named `next_queue'
drivers/char/drm/gamma_old_dma.h:41: error: structure has no member named `next_queue'
drivers/char/drm/gamma_old_dma.h:41: error: structure has no member named `next_queue'
drivers/char/drm/gamma_old_dma.h:41: error: structure has no member named `next_queue'
drivers/char/drm/gamma_old_dma.h:41: error: structure has no member named `next_queue'
drivers/char/drm/gamma_old_dma.h:41: error: structure has no member named `next_queue'
drivers/char/drm/gamma_old_dma.h:42: error: structure has no member named `next_queue'
drivers/char/drm/gamma_old_dma.h:44: error: structure has no member named `next_queue'
In file included from drivers/char/drm/gamma_drv.c:46:
drivers/char/drm/drm_drv.h: In function `gamma_release':
drivers/char/drm/drm_drv.h:808: let op: implicit declaration of function `gamma_ctxbitmap_free'
make[3]: *** [drivers/char/drm/gamma_drv.o] Fout 1
make[2]: *** [drivers/char/drm] Fout 2
make[1]: *** [drivers/char] Fout 2
make: *** [drivers] Fout 2

```Somebody got an id to solve this problem?

(If these thread is in the wrong forum, plz move than, thx)

---

### Post by Burnout on 2004-11-06
Got an answer on another forum and found a solution:> Its a known issue. You probably have it selected in your old config file. Just run make config, exit, and save it and it should disable gamma drm since its marked broken.I just set DRI_GAMMA = n and my kernel works :)

---

