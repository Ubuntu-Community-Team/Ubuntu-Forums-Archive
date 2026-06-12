---
title: "Trouble installing Ogre 1.4.6"
date: 2008-03-07
forum: General Help
---

### Post by Titan8990 on 2008-03-07
When I run ./bootstrap I get the following outcome:

```
Samples/Common/Makefile.am:1: required directory Samples/Common/bin does not exist
Samples/Makefile.am:4: required directory Samples/SkeletalAnimation does not exist
Samples/Makefile.am:4: required directory Samples/BezierPatch does not exist
Samples/Makefile.am:4: required directory Samples/EnvMapping does not exist
Samples/Makefile.am:4: required directory Samples/Transpacency does not exist
Samples/Makefile.am:4: required directory Samples/Lighting does not exist
Samples/Makefile.am:4: required directory Samples/ParticleFX does not exist
Samples/Makefile.am:4: required directory Samples/TextureFX does not exist
Samples/Makefile.am:4: required directory Samples/SkyDome does not exist
Samples/Makefile.am:4: required directory Samples/BSP does not exist
Samples/Makefile.am:4: required directory Samples/SkyPlane does not exist
Samples/Makefile.am:4: required directory Samples/SkyBox does not exist
Samples/Makefile.am:4: required directory Samples/CameraTrack does not exist
Samples/Makefile.am:4: required directory Samples/Terrain does not exist
Samples/Makefile.am:4: required directory Samples/RenderToTexture does not exist
Samples/Makefile.am:4: required directory Samples/Water does not exist
Samples/Makefile.am:4: required directory Samples/CubeMapping does not exist
Samples/Makefile.am:4: required directory Samples/Dot3Bump does not exist
Samples/Makefile.am:4: required directory Samples/Smoke does not exist
Samples/Makefile.am:4: required directory Samples/CelShading does not exist
Samples/Makefile.am:4: required directory Samples/Fresnel does not exist
Samples/Makefile.am:4: required directory Samples/DynTex does not exist
Samples/Makefile.am:4: required directory Samples/VolumeTex does not exist
Samples/Makefile.am:4: required directory Samples/Grass does not exist
Samples/Makefile.am:4: required directory Samples/DeferredShading does not exist
Samples/Makefile.am:10: required directory Samples/Gui does not exist
Samples/Makefile.am:10: required directory Samples/FacialAnimation does not exist
Samples/Makefile.am:10: required directory Samples/OceanDemo does not exist
Samples/Makefile.am:10: required directory Samples/Compositor does not exist
Samples/Makefile.am:10: required directory Samples/Shadows does not exist
Samples/Makefile.am:10: required directory Samples/Instancing does not exist
configure.in:110: required file `Samples/Gui/Makefile.in' not found
configure.in:110: required file `Samples/Gui/src/Makefile.in' not found
configure.in:122: required file `Samples/Common/include/Makefile.in' not found
configure.in:122: required file `Samples/Common/bin/Makefile.in' not found
configure.in:122: required file `Samples/BezierPatch/Makefile.in' not found
configure.in:122: required file `Samples/BezierPatch/src/Makefile.in' not found
configure.in:122: required file `Samples/BezierPatch/include/Makefile.in' not found
configure.in:122: required file `Samples/CameraTrack/Makefile.in' not found
configure.in:122: required file `Samples/CameraTrack/src/Makefile.in' not found
configure.in:122: required file `Samples/CelShading/Makefile.in' not found
configure.in:122: required file `Samples/CelShading/src/Makefile.in' not found
configure.in:122: required file `Samples/Compositor/Makefile.in' not found
configure.in:122: required file `Samples/Compositor/src/Makefile.in' not found
configure.in:122: required file `Samples/Compositor/include/Makefile.in' not found
configure.in:122: required file `Samples/CubeMapping/Makefile.in' not found
configure.in:122: required file `Samples/CubeMapping/src/Makefile.in' not found
configure.in:122: required file `Samples/CubeMapping/include/Makefile.in' not found
configure.in:122: required file `Samples/DeferredShading/Makefile.in' not found
configure.in:122: required file `Samples/DeferredShading/src/Makefile.in' not found
configure.in:122: required file `Samples/DeferredShading/include/Makefile.in' not found
configure.in:122: required file `Samples/Dot3Bump/Makefile.in' not found
configure.in:122: required file `Samples/Dot3Bump/src/Makefile.in' not found
configure.in:122: required file `Samples/EnvMapping/Makefile.in' not found
configure.in:122: required file `Samples/EnvMapping/src/Makefile.in' not found
configure.in:122: required file `Samples/EnvMapping/include/Makefile.in' not found
configure.in:122: required file `Samples/FacialAnimation/Makefile.in' not found
configure.in:122: required file `Samples/FacialAnimation/src/Makefile.in' not found
configure.in:122: required file `Samples/Fresnel/Makefile.in' not found
configure.in:122: required file `Samples/Fresnel/src/Makefile.in' not found
configure.in:122: required file `Samples/Grass/Makefile.in' not found
configure.in:122: required file `Samples/Grass/src/Makefile.in' not found
configure.in:122: required file `Samples/Transpacency/Makefile.in' not found
configure.in:122: required file `Samples/Transpacency/src/Makefile.in' not found
configure.in:122: required file `Samples/Transpacency/include/Makefile.in' not found
configure.in:122: required file `Samples/Lighting/Makefile.in' not found
configure.in:122: required file `Samples/Lighting/src/Makefile.in' not found
configure.in:122: required file `Samples/Lighting/include/Makefile.in' not found
configure.in:122: required file `Samples/OceanDemo/Makefile.in' not found
configure.in:122: required file `Samples/OceanDemo/src/Makefile.in' not found
configure.in:122: required file `Samples/OceanDemo/include/Makefile.in' not found
configure.in:122: required file `Samples/ParticleFX/Makefile.in' not found
configure.in:122: required file `Samples/ParticleFX/src/Makefile.in' not found
configure.in:122: required file `Samples/ParticleFX/include/Makefile.in' not found
configure.in:122: required file `Samples/RenderToTexture/Makefile.in' not found
configure.in:122: required file `Samples/RenderToTexture/src/Makefile.in' not found
configure.in:122: required file `Samples/TextureFX/Makefile.in' not found
configure.in:122: required file `Samples/TextureFX/src/Makefile.in' not found
configure.in:122: required file `Samples/TextureFX/include/Makefile.in' not found
configure.in:122: required file `Samples/Shadows/Makefile.in' not found
configure.in:122: required file `Samples/Shadows/src/Makefile.in' not found
configure.in:122: required file `Samples/SkyBox/Makefile.in' not found
configure.in:122: required file `Samples/SkyBox/src/Makefile.in' not found
configure.in:122: required file `Samples/SkyBox/include/Makefile.in' not found
configure.in:122: required file `Samples/SkyDome/Makefile.in' not found
configure.in:122: required file `Samples/SkyDome/src/Makefile.in' not found
configure.in:122: required file `Samples/SkyDome/include/Makefile.in' not found
configure.in:122: required file `Samples/SkyPlane/Makefile.in' not found
configure.in:122: required file `Samples/SkyPlane/src/Makefile.in' not found
configure.in:122: required file `Samples/SkyPlane/include/Makefile.in' not found
configure.in:122: required file `Samples/Smoke/Makefile.in' not found
configure.in:122: required file `Samples/Smoke/src/Makefile.in' not found
configure.in:122: required file `Samples/Smoke/include/Makefile.in' not found
configure.in:122: required file `Samples/BSP/Makefile.in' not found
configure.in:122: required file `Samples/BSP/src/Makefile.in' not found
configure.in:122: required file `Samples/SkeletalAnimation/Makefile.in' not found
configure.in:122: required file `Samples/SkeletalAnimation/src/Makefile.in' not found
configure.in:122: required file `Samples/SkeletalAnimation/include/Makefile.in' not found
configure.in:122: required file `Samples/Terrain/Makefile.in' not found
configure.in:122: required file `Samples/Terrain/src/Makefile.in' not found
configure.in:122: required file `Samples/Terrain/include/Makefile.in' not found
configure.in:122: required file `Samples/Water/Makefile.in' not found
configure.in:122: required file `Samples/Water/src/Makefile.in' not found
configure.in:122: required file `Samples/Water/include/Makefile.in' not found
configure.in:122: required file `Samples/DynTex/Makefile.in' not found
configure.in:122: required file `Samples/DynTex/src/Makefile.in' not found
configure.in:122: required file `Samples/DynTex/include/Makefile.in' not found
configure.in:122: required file `Samples/VolumeTex/Makefile.in' not found
configure.in:122: required file `Samples/VolumeTex/src/Makefile.in' not found
configure.in:122: required file `Samples/VolumeTex/include/Makefile.in' not found
configure.in:122: required file `Samples/Instancing/Makefile.in' not found
configure.in:122: required file `Samples/Instancing/src/Makefile.in' not found
configure.in:122: required file `Samples/Instancing/include/Makefile.in' not found
```

When I try to run aclocal it gives me this:

```
aclocal:acinclude.m4:352: warning: macro `AM_PATH_CPPUNIT' not found in aclocal:acinclude.m4:352
```

./configure fails at this:

```
./configure: line 23976: syntax error near unexpected token `1.10.0,'
./configure: line 23976: `AM_PATH_CPPUNIT(1.10.0, build_unit_tests=true)'
```

I am a newb to Linux and appreciate any help you all can provide.

---

### Post by Titan8990 on 2008-03-09
bump

---

