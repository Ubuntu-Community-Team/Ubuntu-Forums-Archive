---
title: "after suspend seems white splash around the windows 16.04 lts"
date: 2017-04-02
forum: General Help
---

### Post by fuy2 on 2017-04-02
hi, when i login after suspend, there are white splashs around all windows. and "close"  "maximize" "minimize" buttons disappeared. how can i fix it?

[IMG]http://i.hizliresim.com/nRON8B.png[/IMG]

******lsb_release -a

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

******lspci -nnk | egrep "VGA|3D|Display" -A2

01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM206 [GeForce GTX 950] [10de:1402] (rev a1)
    Subsystem: ASUSTeK Computer Inc. GM206 [GeForce GTX 950] [1043:8554]
    Kernel driver in use: nvidia


******glxinfo | grep render

direct rendering: Yes
OpenGL renderer string: GeForce GTX 950/PCIe/SSE2
    GL_ARB_conditional_render_inverted, GL_ARB_conservative_depth, 
    GL_KHR_robustness, GL_KTX_buffer_region, GL_NVX_conditional_render, 
    GL_NV_conditional_render, GL_NV_conservative_raster, 
    GL_NV_parameter_buffer_object2, GL_NV_path_rendering, 
    GL_NV_path_rendering_shared_edge, GL_NV_pixel_data_range, 
    GL_ARB_compute_variable_group_size, GL_ARB_conditional_render_inverted, 
    GL_KHR_robustness, GL_KTX_buffer_region, GL_NVX_conditional_render, 
    GL_NV_conditional_render, GL_NV_conservative_raster, 
    GL_NV_parameter_buffer_object2, GL_NV_path_rendering, 
    GL_NV_path_rendering_shared_edge, GL_NV_pixel_data_range, 
    GL_EXT_protected_textures, GL_EXT_raster_multisample, GL_EXT_render_snorm, 
    GL_NV_conditional_render, GL_NV_conservative_raster, GL_NV_copy_buffer, 
    GL_NV_packed_float_linear, GL_NV_path_rendering, 
    GL_NV_path_rendering_shared_edge, GL_NV_pixel_buffer_object, 
    GL_OES_element_index_uint, GL_OES_fbo_render_mipmap, 

******xrandr

Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 510mm x 287mm
   1920x1080     60.00*+  59.94    50.00  
   1680x1050     59.95  
   1600x900      60.00  
   1440x900      59.89  
   1280x1024     75.02    60.02  
   1280x800      59.81  
   1280x720      60.00    59.94    50.00  
   1152x864      75.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32    56.25  
   720x576       50.00  
   720x480       59.94  
   640x480       75.00    72.81    59.94  
DVI-D-0 disconnected (normal left inverted right x axis y axis)



******dpkg -l | egrep "nvidia|bumblebee|nvidia-prime|fglrx"

ii  nvidia-375                                  375.39-0ubuntu0.16.04.1                       amd64        NVIDIA binary driver - version 375.39
ii  nvidia-opencl-icd-375                       375.39-0ubuntu0.16.04.1                       amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                0.8.2                                         amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                             361.42-0ubuntu1                               amd64        Tool for configuring the NVIDIA graphics driver

---

### Post by fuy2 on 2017-04-03
error still continue..

---

### Post by Futant on 2017-04-04
During five years of using various versions of Ubuntu on the same laptop with integrated nvidia graphics (mostly a trouble-free ride), I've noticed different behaviours like this on waking from suspend - usually the behaviour lasts for a few days or weeks then is fixed with an update (which sometimes introduces a new problem with suspend). The problems are usually solved by logging out and in again, they are frustrating though. 

Currently I'm getting a very similar problem to yours, and it's been a couple of weeks I think. Previous to this suspend had been working perfectly for quite a while for the first time ever, which was nice while it lasted :p To be honest I used to spend a lot more time on these issues as they arose but now I don't really bother as they usually sort themselves out... lazy!

Look into [bug reports]("https://help.ubuntu.com/community/ReportingBugs") as they help Ubuntu developers improve the experience for everyone!

Also, please use code tags when posting terminal activity, and use the 'attachments' button (little paperclip) to upload images - these things make the post easier to read ;)

---

### Post by scriber on 2017-04-04
As I've posted in another thread [https://ubuntuforums.org/showthread.php?t=2356541](https://ubuntuforums.org/showthread.php?t=2356541)  I am having the exact same problem, and when this started happening it also broke my WiFI connection too, I have no idea if it's related but it sure seems so.

Looks like I'll just have to be patient and wait till it is fixed after seeing this thread. :(

---

