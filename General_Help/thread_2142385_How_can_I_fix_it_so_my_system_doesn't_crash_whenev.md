---
title: "How can I fix it so my system doesn't crash whenever i go to “System Settings &gt; Detai"
date: 2013-05-05
forum: General Help
---

### Post by fwaokda on 2013-05-05
How can I fix it so my system doesn't crash whenever i go to "System Settings > Details"? Or even where/how would I go about troubleshooting the issue? Thanks!

---

### Post by deadflowr on 2013-05-05
You could try running gnome-control-center from the terminal and see if any errors output.

Post 'em if it does.

---

### Post by fwaokda on 2013-05-05
> **deadflowr said:**
> You could try running gnome-control-center from the terminal and see if any errors output.

Post 'em if it does.

Thanks! That's a good tip for in the future so I can get an error log.  Here is what it said.

```
(gnome-control-center:9579): info-cc-panel-WARNING **: PackageKit version 7.4.0 not supported
OpenGL Warning: glFlushVertexArrayRangeNV not found in mesa table
OpenGL Warning: glVertexArrayRangeNV not found in mesa table
OpenGL Warning: glCombinerInputNV not found in mesa table
OpenGL Warning: glCombinerOutputNV not found in mesa table
OpenGL Warning: glCombinerParameterfNV not found in mesa table
OpenGL Warning: glCombinerParameterfvNV not found in mesa table
OpenGL Warning: glCombinerParameteriNV not found in mesa table
OpenGL Warning: glCombinerParameterivNV not found in mesa table
OpenGL Warning: glFinalCombinerInputNV not found in mesa table
OpenGL Warning: glGetCombinerInputParameterfvNV not found in mesa table
OpenGL Warning: glGetCombinerInputParameterivNV not found in mesa table
OpenGL Warning: glGetCombinerOutputParameterfvNV not found in mesa table
OpenGL Warning: glGetCombinerOutputParameterivNV not found in mesa table
OpenGL Warning: glGetFinalCombinerInputParameterfvNV not found in mesa table
OpenGL Warning: glGetFinalCombinerInputParameterivNV not found in mesa table
OpenGL Warning: glDeleteFencesNV not found in mesa table
OpenGL Warning: glFinishFenceNV not found in mesa table
OpenGL Warning: glGenFencesNV not found in mesa table
OpenGL Warning: glGetFenceivNV not found in mesa table
OpenGL Warning: glIsFenceNV not found in mesa table
OpenGL Warning: glSetFenceNV not found in mesa table
OpenGL Warning: glTestFenceNV not found in mesa table
OpenGL Warning: XGetVisualInfo returned 0 visuals for 0xb8625e50
OpenGL Warning: Retry with 0x8002 returned 0 visuals
Segmentation fault (core dumped)

```

---

