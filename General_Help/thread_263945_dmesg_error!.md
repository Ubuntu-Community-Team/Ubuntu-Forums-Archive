---
title: "dmesg error!"
date: 2006-09-23
forum: General Help
---

### Post by Biffy on 2006-09-23
When typing "dmesg" it is flooded with error messages that almost look the same. Here it is:

> [20936332.216000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf5b25c0 still mapped
[20936332.224000] [fglrx:firegl_rmmap] *ERROR* map 0xdf5b25d0 still in use (map_count=1)
[20936332.224000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf5b25c0 still mapped
[20936332.224000] [fglrx:firegl_rmmap] *ERROR* map 0xeab8fb50 still in use (map_count=1)
[20936332.224000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xeab8fb40 still mapped
[20936332.240000] [fglrx:firegl_rmmap] *ERROR* map 0xeab8fb50 still in use (map_count=1)
[20936332.240000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xeab8fb40 still mapped
[20936332.240000] [fglrx:firegl_rmmap] *ERROR* map 0xdf5b25d0 still in use (map_count=1)
[20936332.240000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdf5b25c0 still mapped
[20936332.244000] [fglrx:firegl_rmmap] *ERROR* map 0xeab8f250 still in use (map_count=1)
[20936332.244000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xeab8f240 still mapped

1) What does it mean?
2) Is it bad for my system? I haven't noticed any performance issues
3) How can i make it go away?

I'm using kernel 2.6.15-26-686 (synaptic says: 2.6.15-26.46)

---

