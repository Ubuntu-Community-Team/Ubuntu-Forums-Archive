---
title: "Mohaa linux, OpenGL errors"
date: 2004-10-30
forum: General Help
---

### Post by sertmann on 2004-10-30
Ok this should be a bit more of a mainstream problem than the japanese input one...

getting the error below trying to start the native mohaa client, getting some OpenGL errors - however, UT2004 runs just fine, which seems odd to me...

any suggestions?

I'm using the nvidia glx drivers from restricted.... i've had this working in Debian so it should be able to work in ubuntu after some fixing, just don't know what to fix...

> 
sertmann@edesk:~/Games/mohaa/mohaa $ ./mohaa_lnx
--- Common Initialization ---
Medal of Honor Allied Assault 1.11 linux-i386 Sep  3 2004
----- FS_Startup -----
Current search path:
/home/sertmann/.mohaa/main
/home/sertmann/Games/mohaa/mohaa/main
/home/sertmann/Games/mohaa/mohaa/main/Pak5.pk3 (259 files)
/home/sertmann/Games/mohaa/mohaa/main/Pak4.pk3 (593 files)
/home/sertmann/Games/mohaa/mohaa/main/Pak3.pk3 (669 files)
/home/sertmann/Games/mohaa/mohaa/main/Pak2.pk3 (4722 files)
/home/sertmann/Games/mohaa/mohaa/main/Pak1.pk3 (772 files)
/home/sertmann/Games/mohaa/mohaa/main/Pak0.pk3 (11175 files)

----------------------
18190 files in pk3 files
execing default.cfg
execing menu.cfg
couldn't exec newconfig.cfg
Config: unnamedsoldier.cfg
STUB: wtf in unix/linux_general_extras.c line 95.
STUB: wtf in unix/linux_general_extras.c line 101.
couldn't exec configs/unnamedsoldier.cfg
couldn't exec localized.cfg
execing autoexec.cfg
Unknown command "fov"
couldn't exec custom.cfg
You are now setup for easy mode.
----- Client Initialization -----
Called FadeSound with: 0.000000
----- Initializing Renderer ----
----- R_Init -----
...loading libGL.so: SDL: SDL_GL_LoadLibrary() failed! rc == (-1).
SDL_GetError() reports "Could not load OpenGL library".
failed
...loading libMesaVoodooGL.so.3.1: SDL: SDL_GL_LoadLibrary() failed! rc == (-1).SDL_GetError() reports "Could not load OpenGL library".
failed
ASSERT: [qcommon/common.c:406] GLimp_Init() - could not load OpenGL subsystem
 (fyi)
----- CL_Shutdown -----
-----------------------
Error: GLimp_Init() - could not load OpenGL subsystem



---

