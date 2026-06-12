---
title: "Google Map causes amdgpu errors"
date: 2023-10-22
forum: General Help
---

### Post by westswamp on 2023-10-22
Recently the Google Map website started crashing my laptop: Ubuntu 23.10, Lenovo T14 Gen2, ThinkVision T32h-20
Logs:
```

19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      RW: 0x019:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      RW: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      MAPPING_ERROR: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      PERMISSION_FAULTS: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      WALKER_ERROR: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      MORE_FAULTS: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      Faulty UTCL2 client ID: CB (0x0)
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu: VM_L2_PROTECTION_FAULT_STATUS:0x00000000
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:   in page starting at address 0x00005f7e3c535000 from IH client 0x1b (UTCL2)
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu: [gfxhub0] no-retry page fault (src_id:0 ring:24 vmid:5 pasid:32774, for process chrome pid 11954 thread chrome:cs0 pid 11968)
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      RW: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      MAPPING_ERROR: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      PERMISSION_FAULTS: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      WALKER_ERROR: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      MORE_FAULTS: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      Faulty UTCL2 client ID: CB (0x0)
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu: VM_L2_PROTECTION_FAULT_STATUS:0x00000000
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:   in page starting at address 0x000060734b77e000 from IH client 0x1b (UTCL2)
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu: [gfxhub0] no-retry page fault (src_id:0 ring:24 vmid:5 pasid:32774, for process chrome pid 11954 thread chrome:cs0 pid 11968)
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      RW: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      MAPPING_ERROR: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      PERMISSION_FAULTS: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      WALKER_ERROR: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      MORE_FAULTS: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      Faulty UTCL2 client ID: CB (0x0)
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu: VM_L2_PROTECTION_FAULT_STATUS:0x00000000
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:   in page starting at address 0x000061685a9c8000 from IH client 0x1b (UTCL2)
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu: [gfxhub0] no-retry page fault (src_id:0 ring:24 vmid:5 pasid:32774, for process chrome pid 11954 thread chrome:cs0 pid 11968)
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      RW: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      MAPPING_ERROR: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      PERMISSION_FAULTS: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      WALKER_ERROR: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      MORE_FAULTS: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      Faulty UTCL2 client ID: CB (0x0)
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu: VM_L2_PROTECTION_FAULT_STATUS:0x00000000
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:   in page starting at address 0x0000625d69c11000 from IH client 0x1b (UTCL2)
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu: [gfxhub0] no-retry page fault (src_id:0 ring:24 vmid:5 pasid:32774, for process chrome pid 11954 thread chrome:cs0 pid 11968)
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      RW: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      MAPPING_ERROR: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      PERMISSION_FAULTS: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      WALKER_ERROR: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      MORE_FAULTS: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      Faulty UTCL2 client ID: CB (0x0)
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu: VM_L2_PROTECTION_FAULT_STATUS:0x00000000
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:   in page starting at address 0x0000635278e5b000 from IH client 0x1b (UTCL2)
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu: [gfxhub0] no-retry page fault (src_id:0 ring:24 vmid:5 pasid:32774, for process chrome pid 11954 thread chrome:cs0 pid 11968)
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      RW: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      MAPPING_ERROR: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      PERMISSION_FAULTS: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      WALKER_ERROR: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      MORE_FAULTS: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      Faulty UTCL2 client ID: CB (0x0)
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu: VM_L2_PROTECTION_FAULT_STATUS:0x00000000
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:   in page starting at address 0x00006447880a4000 from IH client 0x1b (UTCL2)
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu: [gfxhub0] no-retry page fault (src_id:0 ring:24 vmid:5 pasid:32774, for process chrome pid 11954 thread chrome:cs0 pid 11968)
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      RW: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      MAPPING_ERROR: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      PERMISSION_FAULTS: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      WALKER_ERROR: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      MORE_FAULTS: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      Faulty UTCL2 client ID: CB (0x0)
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu: VM_L2_PROTECTION_FAULT_STATUS:0x00000000
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:   in page starting at address 0x0000653c972ed000 from IH client 0x1b (UTCL2)
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu: [gfxhub0] no-retry page fault (src_id:0 ring:24 vmid:5 pasid:32774, for process chrome pid 11954 thread chrome:cs0 pid 11968)
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      RW: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      MAPPING_ERROR: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      PERMISSION_FAULTS: 0x3
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      WALKER_ERROR: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      MORE_FAULTS: 0x1
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      Faulty UTCL2 client ID: IA (0x2)
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu: VM_L2_PROTECTION_FAULT_STATUS:0x00500431
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:   in page starting at address 0x00006631a6537000 from IH client 0x1b (UTCL2)
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu: [gfxhub0] no-retry page fault (src_id:0 ring:24 vmid:5 pasid:32774, for process chrome pid 11954 thread chrome:cs0 pid 11968)
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      RW: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      MAPPING_ERROR: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      PERMISSION_FAULTS: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      WALKER_ERROR: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      MORE_FAULTS: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      Faulty UTCL2 client ID: CB (0x0)
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu: VM_L2_PROTECTION_FAULT_STATUS:0x00000000
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:   in page starting at address 0x00006726b5780000 from IH client 0x1b (UTCL2)
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu: [gfxhub0] no-retry page fault (src_id:0 ring:24 vmid:5 pasid:32774, for process chrome pid 11954 thread chrome:cs0 pid 11968)
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      RW: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      MAPPING_ERROR: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      PERMISSION_FAULTS: 0x3
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      WALKER_ERROR: 0x0
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      MORE_FAULTS: 0x1
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:      Faulty UTCL2 client ID: IA (0x2)
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu: VM_L2_PROTECTION_FAULT_STATUS:0x00500431
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu:   in page starting at address 0x0000681bc49ca000 from IH client 0x1b (UTCL2)
19:24:45 kernel: amdgpu 0000:07:00.0: amdgpu: [gfxhub0] no-retry page fault (src_id:0 ring:24 vmid:5 pasid:32774, for process chrome pid 11954 thread chrome:cs0 pid 11968)

```
Any suggestions?

---

### Post by MAFoElffen on 2023-10-22
Connected to this kernel bug: [https://bugzilla.kernel.org/show_bug.cgi?id=211157](https://bugzilla.kernel.org/show_bug.cgi?id=211157)

Please add this boot parameter to /etc/default/grub in line GRUB_CMDLINE_LINUX_DEFAULT=
```

amdgpu.noretry=0

```
Then save, exit, and do this to pick up the changes
```

sudo update-grub
sudo reboot

```
Test and see if you have same errors.

---

### Post by westswamp on 2024-01-06
No help
> 23:42:26 kernel: amdgpu 0000:07:00.0: amdgpu:   in page starting at address 0x00006f76313b4000 from IH client 0x1b (UTCL2)
23:42:04 systemd: Failed to start app-gnome-ubuntu\x2dreport\x2don\x2dupgrade-2812.scope - Application launched by gnome-session-binary.


---

