---
title: "can finish compileing a new kernel?"
date: 2007-09-05
forum: General Help
---

### Post by atlfalcons866 on 2007-09-05
after i compile i get this
WARNING: vmlinux(.text+0xc010116f): Section mismatch: reference to .init.text:start_kernel (between 'is386' and 'check_x87')
WARNING: vmlinux(.text+0xc033d5f8): Section mismatch: reference to .init.text: (between 'rest_init' and 'alloc_node_mem_map')
WARNING: vmlinux(.text+0xc0342ef0): Section mismatch: reference to .init.text: (between 'iret_exc' and '_etext')
WARNING: vmlinux(.text+0xc0342efc): Section mismatch: reference to .init.text: (between 'iret_exc' and '_etext')
WARNING: vmlinux(.text+0xc0342f08): Section mismatch: reference to .init.text: (between 'iret_exc' and '_etext')
WARNING: vmlinux(.text+0xc0342f14): Section mismatch: reference to .init.text: (between 'iret_exc' and '_etext')
WARNING: vmlinux(.text+0xc033d6c0): Section mismatch: reference to .init.text:__alloc_bootmem_node (between 'alloc_node_mem_map' and 'zone_wait_table_init')
WARNING: vmlinux(.text+0xc033d74e): Section mismatch: reference to .init.text:__alloc_bootmem_node (between 'zone_wait_table_init' and '__sched_text_start')
WARNING: vmlinux(.text+0xc03436da): Section mismatch: reference to .init.text: (between 'iret_exc' and '_etext')
ERROR: "libertas_remove_mesh" [drivers/net/wireless/libertas/usb8xxx.ko] undefined!
ERROR: "libertas_add_card" [drivers/net/wireless/libertas/usb8xxx.ko] undefined!
ERROR: "libertas_send_tx_feedback" [drivers/net/wireless/libertas/usb8xxx.ko] undefined!
ERROR: "libertas_prepare_and_send_command" [drivers/net/wireless/libertas/usb8xxx.ko] undefined!
ERROR: "libertas_remove_card" [drivers/net/wireless/libertas/usb8xxx.ko] undefined!
ERROR: "libertas_add_mesh" [drivers/net/wireless/libertas/usb8xxx.ko] undefined!
ERROR: "libertas_process_rxed_packet" [drivers/net/wireless/libertas/usb8xxx.ko] undefined!
ERROR: "libertas_interrupt" [drivers/net/wireless/libertas/usb8xxx.ko] undefined!
ERROR: "libertas_activate_card" [drivers/net/wireless/libertas/usb8xxx.ko] undefined!
make[2]: *** [__modpost] Error 1
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.22'
make: *** [debian/stamp-build-kernel] Error 2

---

### Post by Shootfast on 2007-09-22
I get the same error, following the Master Kernel Thread

---

### Post by atlfalcons866 on 2007-09-22
thats what i did too

---

