---
title: "X11 error when running a game in wine"
date: 2007-05-13
forum: General Help
---

### Post by echomikeromeo on 2007-05-13
I installed and configured wine, got it working fine, and installed the game that the whole rigamarole was about (*Starship Titanic*, designed by Douglas Adams, if that's relevant) but when I try to start the game I get as far as the game's startup splash screen-type thing before I encounter this error:

```
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fd51c88) -> (0x10028,00000011)
fixme:avifile:AVIFileExit (): stub!
err:x11drv:GrabPointer Window procedure has been changed!
```

I'm not *exactly* a noob, but I'm not precisely technologically literate, so if anyone can figure out what this means and/or how to fix it I'd be grateful.

I'm using Ubuntu 7.04, Wine 0.9.5 on a Dell Inspiron 2500 laptop.

EDIT: Updating to the latest version of Wine produced a slightly different message:
```
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x173f40) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x173710) -> (0x1002a,00000011)
fixme:avifile:AVIFileExit (): stub!
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x173710) -> ((nil),00000000)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:d3d:IWineD3DDeviceImpl_Release (0x173f40) Device released with resources still bound, acceptable but unexpected
fixme:d3d:dumpResources Leftover resource 0x1c0f80 with type 1,WINED3DRTYPE_SURFACE
```

Yeah, I still have no idea what that means.

---

### Post by echomikeromeo on 2007-05-21
Sorry to bump this if that's rude, but I'm still wondering if anyone could help me with this issue.

---

### Post by adam_kimber on 2007-12-08
I get the following error when using wine version: wine-0.9.50

```
adam:~/Wine Drive C/Program Files/Starship Titanic$ wine ST.exe 
fixme:win:EnumDisplayDevicesW ((null),0,0x34f954,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:avifile:AVIFileExit (): stub!
fixme:d3d:IWineD3DDeviceImpl_Release (0xf90020) Device released with resources still bound, acceptable but unexpected
fixme:d3d:dumpResources Leftover resource 0xf32620 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0xf332d8 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0xf324c0 with type 1,WINED3DRTYPE_SURFACE
err:d3d:IWineD3DDeviceImpl_Release Context array not freed!
wine: Unhandled page fault on read access to 0xffff000e at address 0xa93230f (thread 0009), starting debugger...
err:dbghelp:pe_load_msc_debug_info -Debug info stripped, but no .DBG file in module L"sh33w32"

```

The [Wine Application DB]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=4445") has this crash as a known bug but nothing seems to have been fixed. :(

---

