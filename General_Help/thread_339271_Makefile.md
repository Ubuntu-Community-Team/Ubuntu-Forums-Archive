---
title: "Makefile"
date: 2007-01-15
forum: General Help
---

### Post by Ryan H on 2007-01-15
I'm trying to install linux-dri-modules 2.5.15-27, the same number as my kernel, because I can't find it in AMD 64.

I'm running Drapper Drake.

I opened it up and all there was is a file named Makefile, plus the other file to be compiled, how do I change this to a configure file? It's contents are: > SUBDIRS=linux-core

ifndef RUNNING_REL
RUNNING_REL := $(shell uname -r)
endif

ifndef LINUXDIR
LINUXDIR := $(shell if [ -e /lib/modules/$(RUNNING_REL)/source ]; then \
                 echo /lib/modules/$(RUNNING_REL)/source; \
                 else echo /lib/modules/$(RUNNING_REL)/build; fi)
endif

all: 
	@list='$(SUBDIRS)'; \
	for subdir in $$list; do \
		(cd $$subdir && $(MAKE) LINUXDIR=$(LINUXDIR)); \
	done;

install: all
	@list='$(SUBDIRS)'; \
	for subdir in $$list; do \
		(cd $$subdir && \
		if [ ! -e $(DESTDIR)/lib/linux-dri-modules/$(RUNNING_REL) ]; \
		then \
			mkdir -p $(DESTDIR)/lib/linux-dri-modules/$(RUNNING_REL); \
		fi; \
		cp -f *.ko $(DESTDIR)/lib/linux-dri-modules/$(RUNNING_REL)); \
	done;

clean: 
	@list='$(SUBDIRS)'; \
	for subdir in $$list; do \
		(cd $$subdir && $(MAKE)  LINUXDIR=$(LINUXDIR) clean); \
	done;


Any help would be greatly appreciated.

-Ryan H

---

### Post by smartbei on 2007-01-15
I'm somewhat new, but as far as I know the purpose of the configure file is to create the makefile. If you already have one, you can skip that step and just do:
```
make
sudo make install
```

---

### Post by Ryan H on 2007-01-15
Duh, thanks. I get this error when I do it though:
```
make[1]: Entering directory `/usr/local/src/linux-dri-modules/linux-core'
+ ln -s ../shared-core/drm.h drm.h
+ ln -s ../shared-core/drm_sarea.h drm_sarea.h
+ ln -s ../shared-core/mga_dma.c mga_dma.c
+ ln -s ../shared-core/mga_drm.h mga_drm.h
+ ln -s ../shared-core/mga_drv.h mga_drv.h
+ ln -s ../shared-core/mga_irq.c mga_irq.c
+ ln -s ../shared-core/mga_state.c mga_state.c
+ ln -s ../shared-core/mga_ucode.h mga_ucode.h
+ ln -s ../shared-core/mga_warp.c mga_warp.c
+ ln -s ../shared-core/r128_drv.h r128_drv.h
+ ln -s ../shared-core/r128_drm.h r128_drm.h
+ ln -s ../shared-core/r128_cce.c r128_cce.c
+ ln -s ../shared-core/r128_state.c r128_state.c
+ ln -s ../shared-core/r128_irq.c r128_irq.c
+ ln -s ../shared-core/radeon_drv.h radeon_drv.h
+ ln -s ../shared-core/radeon_drm.h radeon_drm.h
+ ln -s ../shared-core/radeon_cp.c radeon_cp.c
+ ln -s ../shared-core/radeon_irq.c radeon_irq.c
+ ln -s ../shared-core/radeon_mem.c radeon_mem.c
+ ln -s ../shared-core/radeon_state.c radeon_state.c
+ ln -s ../shared-core/r300_cmdbuf.c r300_cmdbuf.c
+ ln -s ../shared-core/r300_reg.h r300_reg.h
+ ln -s ../shared-core/sis_drv.h sis_drv.h
+ ln -s ../shared-core/sis_drm.h sis_drm.h
+ ln -s ../shared-core/tdfx_drv.h tdfx_drv.h
+ ln -s ../shared-core/via_drm.h via_drm.h
+ ln -s ../shared-core/via_drv.h via_drv.h
+ ln -s ../shared-core/via_3d_reg.h via_3d_reg.h
+ ln -s ../shared-core/via_drv.c via_drv.c
+ ln -s ../shared-core/via_irq.c via_irq.c
+ ln -s ../shared-core/via_map.c via_map.c
+ ln -s ../shared-core/via_dma.c via_dma.c
+ ln -s ../shared-core/via_verifier.c via_verifier.c
+ ln -s ../shared-core/via_verifier.h via_verifier.h
+ ln -s ../shared-core/via_video.c via_video.c
+ ln -s ../shared-core/mach64_drv.h mach64_drv.h
+ ln -s ../shared-core/mach64_drm.h mach64_drm.h
+ ln -s ../shared-core/mach64_dma.c mach64_dma.c
+ ln -s ../shared-core/mach64_irq.c mach64_irq.c
+ ln -s ../shared-core/mach64_state.c mach64_state.c
+ ln -s ../shared-core/i915_drv.h i915_drv.h
+ ln -s ../shared-core/i915_drm.h i915_drm.h
+ ln -s ../shared-core/i915_irq.c i915_irq.c
+ ln -s ../shared-core/i915_mem.c i915_mem.c
+ ln -s ../shared-core/i915_dma.c i915_dma.c
+ ln -s ../shared-core/savage_drv.h savage_drv.h
+ ln -s ../shared-core/savage_drm.h savage_drm.h
+ ln -s ../shared-core/savage_bci.c savage_bci.c
+ ln -s ../shared-core/savage_state.c savage_state.c
+ ln -s ../shared-core/nv_drv.h nv_drv.h
sh ../scripts/create_linux_pci_lists.sh < ../shared-core/drm_pciids.txt
rm -f linux
ln -s . linux
make -C /lib/modules/2.6.15-27-amd64-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make: Entering an unknown directory
make: *** /lib/modules/2.6.15-27-amd64-generic/build: No such file or directory.  Stop.
make: Leaving an unknown directory
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/local/src/linux-dri-modules/linux-core'
make: *** [all] Error 2

```

-Ryan H

---

### Post by Ryan H on 2007-01-15
Does God not allow Beryl on AMD 64? :(

-Ryan H

---

