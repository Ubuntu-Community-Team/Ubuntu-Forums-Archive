---
title: "CAD Tool fails to work on Ubuntu7.04 and 7.10"
date: 2008-02-01
forum: General Help
---

### Post by adav on 2008-02-01
I'm having trouble getting a CAD tool called Forte to work on Ubuntu 7.10 Gutsy installed on an Intel Core2 Duo laptop. I upgraded recently from Ubuntu 7.04 Feisty, but even before, the tool never worked. It works on other distros mostly Red Hat family 7,8,9, Enterprise 5. Forte can be found on Intel's website should anyone want to give a try installing it on their box to see the problem.

[http://www.intel.com/cd/software/products/asmo-na/eng/219776.htm](http://www.intel.com/cd/software/products/asmo-na/eng/219776.htm)

Forte relies on finding Tcl8.4, Tk8.4 and Tix8.1 all of which are installed properly, and Forte does not complain about not finding any of the relevant .so library files. However as soon as I start forte from command line, it crashes saying Segmentation fault (core dumped).

I'm enclosing the dump of 'ldd forte' on a Red Hat Enterprise Server 5  which runs it successfully. The reason I want this to work on Ubnutu is that in my experience its the best distro I've ever used, if only I can sort this problem out.

ldd forte

	linux-gate.so.1 =>  (0x0046f000)
	libtix8.1.8.4.so => /usr/lib/libtix8.1.8.4.so (0x006e4000)
	libtk8.4.so => /usr/lib/libtk8.4.so (0x4dff4000)
	libtcl8.4.so => /usr/lib/libtcl8.4.so (0x4df46000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0x4de41000)
	libXt.so.6 => /usr/lib/libXt.so.6 (0x4eea5000)
	libdl.so.2 => /lib/libdl.so.2 (0x4de00000)
	libstdc++.so.5 => /usr/lib/libstdc++.so.5 (0x00112000)
	libm.so.6 => /lib/i686/nosegneg/libm.so.6 (0x4ddd7000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x001cb000)
	libc.so.6 => /lib/i686/nosegneg/libc.so.6 (0x4dc95000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0x4de34000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x4de39000)
	libSM.so.6 => /usr/lib/libSM.so.6 (0x4e1ae000)
	libICE.so.6 => /usr/lib/libICE.so.6 (0x001d8000)
	/lib/ld-linux.so.2 (0x4dc78000)

Any help is greatly appreciated.

---

### Post by p_quarles on 2008-02-01
Moved to General Help.

---

