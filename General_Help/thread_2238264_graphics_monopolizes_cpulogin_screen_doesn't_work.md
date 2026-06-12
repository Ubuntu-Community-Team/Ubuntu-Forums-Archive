---
title: "graphics monopolizes cpu/login screen doesn't work"
date: 2014-08-06
forum: General Help
---

### Post by sandwic on 2014-08-06
I just upgraded from 13.10 to 14.04.
I had the issue with login and CPU hogging in 13.10 and was hoping the upgrade might help it. This is not the case as the graphics have become more choppy and heavy load on the cpu begins to interfere with audio streaming. The computer idles at about 80% cpu usage  

these might be helpful  the output of glxinfo | grep 

render  direct rendering: Yes  
   GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer,  OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)   
  GL_MESA_ycbcr_texture, GL_NV_blend_square, GL_NV_conditional_render,


  and lspci | grep VGA & sudo lshw -C video 

 [1] 3042 01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)  
 *-display UNCLAIMED       
      description: VGA compatible controller  
      product: 771/671 PCIE VGA Display Adapter   
     vendor: Silicon Integrated Systems [SiS]    
    physical id: 0   
     bus info: pci@0000:01:00.0    
    version: 10    
    width: 32 bits   
     clock: 66MHz    
    capabilities: pm agp agp-3.0 vga_controller cap_list    
    configuration: latency=0  
      resources: memory:d0000000-dfffffff memory:fdee0000-fdefffff ioport:ef00(size=128) [1]+  Done             
       lspci | grep --color=auto VGA   


  I've tried reinstalling drivers and the x server... this problem existed on 2 computers after a fresh install of 13.10 and still I have no solution

---

