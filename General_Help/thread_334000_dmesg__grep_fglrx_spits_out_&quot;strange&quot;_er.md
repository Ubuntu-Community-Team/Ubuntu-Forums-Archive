---
title: "dmesg | grep fglrx spits out &quot;strange&quot; errors with ATI Radeon 9600"
date: 2007-01-08
forum: General Help
---

### Post by EdThaSlayer on 2007-01-08
My ATI Radeon 9600  with the fgrlx and direct rendering enabled seems to get a max fps of 1200. So I tried to investigate this and somehow when typing "dmesg | grep fglrx" I get these error messages. :confused: 
I only decided to post a portion of the result. But, everytime I try this I see this big ERROR but don't know why that error appears. Or is this normal? Iam running Dapper Drake ](*,) 
```

[17195246.476000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.476000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.492000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.492000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.492000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.492000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.496000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.496000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.508000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.508000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.516000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.516000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.524000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.524000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.524000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.524000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.548000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.548000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.548000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.548000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.676000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.676000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.676000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.676000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.732000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.732000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.732000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.732000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.740000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.740000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.740000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.740000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.760000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.760000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.760000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.760000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.780000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.780000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.780000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.780000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.784000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.784000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.788000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.788000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.804000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.804000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.808000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.808000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.812000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.812000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.812000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.812000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.828000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.828000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.828000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.828000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.864000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.864000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.864000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.864000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.888000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.888000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.888000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.888000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.924000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.924000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.924000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.924000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.932000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.932000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.932000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.932000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.964000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.964000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195246.964000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195246.964000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195247.000000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195247.000000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195247.000000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)
[17195247.000000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xea605cc0 still mapped
[17195247.024000] [fglrx:firegl_rmmap] *ERROR* map 0xea605cd0 still in use (map_count=1)

```

---

