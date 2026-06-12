---
title: "Nvidia, matlab, openGL...can it be done?"
date: 2005-05-22
forum: General Help
---

### Post by hondje on 2005-05-22
I slowly grow weary :)  I have spent a lot of time linking libs from here, libs from there, unlinking, etc, trying to get Matlab to have openGL support w/ my nvidia card.  After a serious amount of effort, I grow weary, and just want to know if anyone, at all, has ever managed to do it?

Dogg

---

### Post by gsanse on 2005-09-07
I got it working but sincerely it did not bring noticeable performance improvement. Doing bench before and after gives me pratically the same results. Here is what I did. Start by taking a look at:

[http://www.mathworks.com/support/solutions/data/1-18N21.html?solution=1-18N21](http://www.mathworks.com/support/solutions/data/1-18N21.html?solution=1-18N21)

As you said everything is related to library link. The site says it should work in R14SP2, but this what I am running and after installing, opengl info gives me Mesa X11 renderer and not Nvidia. First thing I did was to execute on a terminal

ldd /usr/local/matlab704/bin/glnx86/glren.so

This indicated me that libGL.so and libGLU.so were not linked. Doing a search on my disk I found the library libGL.so.1.2.xlibmesa in /usr/X11R6/lib/nvidia. So I linked it to libGL.so both in /usr/lib and /usr/local/matlab/sys/opengl/lib/glnx86:

sudo ln -s /usr/X11R6/lib/nvidia/libGL.so.1.2.xlibmesa libGL.so
sudo ln -s /usr/X11R6/lib/nvidia/libGL.so.1.2.xlibmesa /usr/lib/libGL.so

I then restarted Matlab and opengl info gave me:

Version         = 1.2 (1.5.3 NVIDIA 71.74)
Vendor          = NVIDIA Corporation
Renderer        = GeForce2 MX/AGP/SSE/3DNOW!
MaxTextureSize  = 2048
Visual          = 0x21 (TrueColor, depth 24, RGB mask 0xff0000 0xff00 0x00ff)
Software        = true
# of Extensions = 52

Driver Bug Workarounds:
OpenGLBitmapZbufferBug    = 0
OpenGLWobbleTesselatorBug = 0
OpenGLLineSmoothingBug    = 0
OpenGLClippedImageBug     = 1
OpenGLEraseModeBug        = 0


So I guess it is working. The command ldd /usr/local/matlab704/bin/glnx86/glren.so still indicates libGLU.so is not linked but every tentative I made to link just caused me errors when trying to use OpenGL in Matlab. I am not sure what is the function of this library but I decided to stop messing with it. Hope it helps.  :) 

Regards,

gsanse

---

### Post by Novox on 2005-09-12
[QUOTE=gsanse]I got it working but sincerely it did not bring noticeable performance improvement.[/quote]

Of course, it did not:

[font=monospace]Version         = 1.2 (1.5.3 NVIDIA 71.74)
Vendor          = NVIDIA Corporation
Renderer        = GeForce2 MX/AGP/SSE/3DNOW!
MaxTextureSize  = 2048
Visual          = 0x21 (TrueColor, depth 24, RGB mask 0xff0000 0xff00 0x00ff)
**Software        = true**
# of Extensions = 52

Driver Bug Workarounds:
OpenGLBitmapZbufferBug    = 0
OpenGLWobbleTesselatorBug = 0
OpenGLLineSmoothingBug    = 0
OpenGLClippedImageBug     = 1
OpenGLEraseModeBug        = 0[/font]

As your "opengl info" output shows software rendering is still enabled. To switch to hw rendering try "opengl hardware" though it didn't work here.
And no, I don't know how to get MATLAB to properly work with OpenGL hw acceleration

---

### Post by gsanse on 2005-09-15
Novox, 

Thanks for the info, I just looked at the renderer line, did not pay attention to the software option line. Tried the opengl hardware command but it did not work. Regards,

gsanse

---

### Post by kleeman on 2005-09-15
[QUOTE=hondje]I slowly grow weary :)  I have spent a lot of time linking libs from here, libs from there, unlinking, etc, trying to get Matlab to have openGL support w/ my nvidia card.  After a serious amount of effort, I grow weary, and just want to know if anyone, at all, has ever managed to do it?

Dogg[/QUOTE]

Yes I have. What exactly goes wrong? Is the animation lousy?

My details:
Version 6.5.0.180913a Release 13 Jun 18 2002

lspci gives

0000:01:00.0 VGA compatible controller: nVidia Corporation NV35 [GeForce PCX 5900] (rev a2)

glxinfo first few lines:

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer
client glx vendor string: NVIDIA Corporation
client glx version string: 1.3
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce PCX 5900/PCI/SSE2
OpenGL version string: 1.5.3 NVIDIA 71.74

I am using the nvidia restricted modules package....

---

### Post by ernstkl on 2006-12-13
Hello,

I encountered the same problem today and post the solution here so that it may be found in the future. 

The cause of the problem is that matlab looks for /usr/lib/libGL.so but the nvidia-glx packages only contains /usr/lib/libGL.so.1.

The solution is to additionally install the nvidia-glx-dev package which has the /usr/lib/libGL.so.1 symlink.

No copying of libraries or creating links by hand required!

I did this with ubuntu edgy and previously with debian sarge.

Ernst

---

### Post by Adramelech on 2006-12-14
From: [http://www.math.dartmouth.edu/~ahb/laptop_setup/i8100_FC4_setup.html]("http://www.math.dartmouth.edu/~ahb/laptop_setup/i8100_FC4_setup.html")


> If want hardware-accelerated OpenGL rendering (I do), replace Matlab's gcc-library with FC4's:

cd /usr/local/matlab/sys/os/glnx86
mv libgcc_s.so.1 libgcc_s.so.1_orig
ln -sf /lib/libgcc_s.so.1 ./

Check with opengl info at Matlab prompt. Thanks to Mathworks support for this fix.

I installed nvidia-glx-dev and did what this guy said and it worked fine:
Version         = 1.5.8 NVIDIA 96.26
Vendor          = NVIDIA Corporation
Renderer        = unknown board/AGP/SSE2
MaxTextureSize  = 4096
Visual          = 0x27 (TrueColor, depth 24, RGB mask 0xff0000 0xff00 0x00ff)
Software        = false
# of Extensions = 94

---

### Post by eros69 on 2007-02-13
Can u pliz exppla in details 'how to add the $MATLAB/bin directory to your UNIX search path'? im using Ubuntu 6.10 Edgy. Its hard for us NBs-to-linux, we spent hours even on finding where the $PATH is! 

One day i will be there!

Please Help!

---

### Post by Belisarius on 2008-04-10
> **ernstkl said:**
> Hello,

I encountered the same problem today and post the solution here so that it may be found in the future. 

The cause of the problem is that matlab looks for /usr/lib/libGL.so but the nvidia-glx packages only contains /usr/lib/libGL.so.1.

The solution is to additionally install the nvidia-glx-dev package which has the /usr/lib/libGL.so.1 symlink.

No copying of libraries or creating links by hand required!

I did this with ubuntu edgy and previously with debian sarge.

Ernst

I've just reinstalled matlab and remember having nighmare sorting OpenGL out on my ATI laptop. Found this post and now have OpenGL working fine with Matlab and NVIDIA  on my main Desktop PC.

Thanks for posting this. Saved what little hair I have left :)

Now to load up the files from my Masters thesis and see if my brain still works after a year of .NET support!

Cheers

Andy

---

