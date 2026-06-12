---
title: "Only Unity 2D after update ... bug maybe?"
date: 2013-02-26
forum: General Help
---

### Post by Future Warthog on 2013-02-26
I have Ubuntu 12.04 LTS (am going to upgrade when 13.04 comes out, maybe  earlier to 12.10...dunno) on a Toshiba Satellite A105 S4284 (I believe)  w. Intel Centrino Duo chip. 
Here's my graphics card info, from terminal:
```

nate@texno-Satellite-A105:~$ lspci | grep 
VGA 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) 

```Anyways, I did a whole bunch of Ubuntu updates yesterday (running Unity  3D plenty fine for all of my previous using as well as regular GNOME)  and now I can only start in Unity 2D. I ran the
```

  /usr/lib/nux/unity_support_test -p 

``` command from the terminal and this is what I got:
```

OpenGL vendor string:   VMware, Inc. 
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300) 
OpenGL version string:  2.1 Mesa 8.0.4  
Not software rendered:    no 
Not blacklisted:          yes 
GLX fbconfig:             yes 
GLX texture from pixmap:  yes 
GL npot or rect textures: yes 
GL vertex program:        yes 
GL fragment program:      yes 
GL vertex buffer object:  yes 
GL framebuffer object:    yes 
GL version is 1.4+:       yes  
Unity 3D supported:       no

```Unity 3D worked great for my using (11.04 to 12.04 LTS) and it was fine on 12.04 LTS *until* I updated. GNOME 3 also worked fine, but it also will only start in GNOME Classic mode.

I ran the 
```

     unity --replace

```command in terminal (got it from another post similar to my problem, didn't help though), but it just said "Hello there! Have a whole  caboodle of error messages that make almost no sense!" and froze, taking  my system with it. I had to Ctrl+C the command and log out, because  Unity 2D froze.
I had run *apt-get update*  prior to this, so I thought I would restart my computer, but nothing changed, I had the same problem when I logged back in. 
I would post the output, but restarting the computer erased the info I copied (duh, should have known, since *copy*/*paste* is stored in RAM), so I don't have that. I can run it again, it that will help.

I tried logging in as guest, same problem. I created a new account and tried logging that way, ditto.

Any help is accepted,
   ~packpatfan

---

