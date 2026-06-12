---
title: "OpenGL drivers"
date: 2012-11-20
forum: General Help
---

### Post by deathyr on 2012-11-20
Hi, i tried to play a program with PlayOnLinux and i get this error:
```
err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is  disabled,  most likely your OpenGL drivers haven't been installed  correctly (using gl rendere "ATI radeon hd 5700 Series", version" 1.4  (2.1 (4.2.11627 Compatibility Profile context))").                      
```How can i fix it?
Thanks.

---

### Post by Mark Phelps on 2012-11-20
Message indicates that the "program" you're trying to run needs video drivers you do not have installed.

Before you try to force the installation of drivers, we need to know which version of Ubuntu you are running -- as 12.10 has problems with AMD restricted drivers.

---

### Post by deathyr on 2012-11-20
Oh sorry, I run 12.04 (precise) 64-bit.

---

### Post by efflandt on 2012-11-20
Most likely for 12.04 you just need to load **Additional Drivers** from **Dash** and "Activate" the **fglrx** that it suggests.

If you installed drivers downloaded elsewhere (like AMD/ATI) and/or Additional Drivers says "Activated, but not in use" I am not sure how you would fix that.  Although, it appears that you are just using the default Radeon driver that came with the system.

---

### Post by deathyr on 2012-11-21
In Additional Drivers i have:
ATI/AMD proprietary FGLRX graphics driver (this is activated and in use)
and
ATI/AMD proprietary FGLRX graphics driver (post-release update)

everytime i try to activate the second one the installation fails (I attach the log)
> Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

---

### Post by Mark Phelps on 2012-11-21
> **deathyr said:**
> In Additional Drivers i have:
ATI/AMD proprietary FGLRX graphics driver (this is activated and in use)
and
ATI/AMD proprietary FGLRX graphics driver (post-release update)

everytime i try to activate the second one the installation fails (I attach the log)

The second one does not work -- and unfortunately, there are no messages indicating that trying to activate this is a waste of time.

---

### Post by deathyr on 2012-11-23
I found this comand on the internet, shoul i try or should i just quit everything?
sudo apt-get install fglrx fglrx-amdcccle

---

### Post by COMECON on 2012-11-23
> **deathyr said:**
> I found this comand on the internet, shoul i try or should i just quit everything?
sudo apt-get install fglrx fglrx-amdcccle

I think it basically does the same that jockey...
Try running this on a terminal: *glxinfo | grep direct* and paste the output. (you'll need to install **mesa-utils**).

---

### Post by deathyr on 2012-11-23
I think i already installed **mesa-utils **because i didn't get an error
> direct rendering: Yes
    GL_AMD_multi_draw_indirect, GL_AMD_name_gen_delete, 
    GL_ARB_draw_indirect, GL_ARB_draw_instanced, 
    GL_EXT_copy_buffer, GL_EXT_copy_texture, GL_EXT_direct_state_access, 


---

