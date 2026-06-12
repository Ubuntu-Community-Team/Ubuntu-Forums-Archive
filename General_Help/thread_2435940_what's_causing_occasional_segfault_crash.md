---
title: "what's causing occasional segfault crash?"
date: 2020-01-28
forum: General Help
---

### Post by tominto on 2020-01-28
Hello
I'm running 18.04 with the latest updates.   I've been getting occasional segfault crashes that I've only really ever noticed while running flightgear.  I'm not sure though if the problem is with flightgear, ubuntu, or a hardware issue?  Recently I've started starting flightgear with gdb and here is the output 

```
Thread 1 "fgfs" received signal SIGSEGV, Segmentation fault.
0x00007fffb6ee5eb3 in ?? () from /usr/lib/x86_64-linux-gnu/dri/radeonsi_dri.so
(gdb) bt full
#0  0x00007fffb6ee5eb3 in  () at /usr/lib/x86_64-linux-gnu/dri/radeonsi_dri.so
#1  0x00007fffb6e05bd9 in  () at /usr/lib/x86_64-linux-gnu/dri/radeonsi_dri.so
#2  0x00007fffb6ee7d5d in  () at /usr/lib/x86_64-linux-gnu/dri/radeonsi_dri.so
#3  0x00007ffff563b8c2 in osg::Geometry::drawPrimitivesImplementation(osg::RenderInfo&) const () at /usr/lib/x86_64-linux-gnu/libosg.so.131
#4  0x00007ffff563de91 in osg::Geometry::drawImplementation(osg::RenderInfo&) const () at /usr/lib/x86_64-linux-gnu/libosg.so.131
#5  0x00007ffff60d2720 in osgUtil::RenderLeaf::render(osg::RenderInfo&, osgUtil::RenderLeaf*) () at /usr/lib/x86_64-linux-gnu/libosgUtil.so.131
#6  0x00007ffff60ccf55 in osgUtil::RenderBin::drawImplementation(osg::RenderInfo&, osgUtil::RenderLeaf*&) () at /usr/lib/x86_64-linux-gnu/libosgUtil.so.131
#7  0x00007ffff60d7c72 in osgUtil::RenderStage::drawImplementation(osg::RenderInfo&, osgUtil::RenderLeaf*&) () at /usr/lib/x86_64-linux-gnu/libosgUtil.so.131
#8  0x00007ffff60cd9fb in osgUtil::RenderBin::draw(osg::RenderInfo&, osgUtil::RenderLeaf*&) () at /usr/lib/x86_64-linux-gnu/libosgUtil.so.131
#9  0x00007ffff60d7024 in osgUtil::RenderStage::drawInner(osg::RenderInfo&, osgUtil::RenderLeaf*&, bool&) () at /usr/lib/x86_64-linux-gnu/libosgUtil.so.131
#10 0x00007ffff60d84ee in osgUtil::RenderStage::draw(osg::RenderInfo&, osgUtil::RenderLeaf*&) () at /usr/lib/x86_64-linux-gnu/libosgUtil.so.131
#11 0x00007ffff60e104e in osgUtil::SceneView::draw() ()
    at /usr/lib/x86_64-linux-gnu/libosgUtil.so.131
#12 0x00007ffff5cf4e66 in osgViewer::Renderer::cull_draw() ()
    at /usr/lib/x86_64-linux-gnu/libosgViewer.so.131
---Type <return> to continue, or q <return> to quit---
#13 0x00007ffff565a399 in osg::GraphicsContext::runOperations() ()
    at /usr/lib/x86_64-linux-gnu/libosg.so.131
#14 0x00007ffff5d2a885 in osgViewer::ViewerBase::renderingTraversals() ()
    at /usr/lib/x86_64-linux-gnu/libosgViewer.so.131
#15 0x0000555556028bab in fgOSMainLoop() ()
#16 0x00005555560c53bf in fgMainInit(int, char**) ()
#17 0x0000555555881131 in main ()
(gdb) 
```



Additional system info: AMD KAVERI A10-7800 APU (DRM 2.50.0, 4.15.0-76-generic, LLVM 9.0.0)
Any help would be appreciated 
Thanks

---

### Post by mörgæs on 2020-01-30
Have you tried a clean install of 19.10?

If it's a bug in 18.04 it could be fixed in a later release.

---

### Post by Yellow Pasque on 2020-01-31
>  I'm not sure though if the problem is with flightgear, ubuntu, or a hardware issue?

My guess would be a bug with the radeonsi 3D driver, but if you don't run other 3D-intensive programs that use the same code paths Flightgear does, it's hard to rule out the problem being specific to Flightgear. If possible, I think I would try a distro with newer components as mörgæs noted. If you are comfortable using/removing PPA's, you could even try a newer mesa version on your current install.

Just a note: If you want the backtrace to be more informative, install the libgl1-mesa-dri-dbg package (or report the bug on Launchpad, which will automatically take care of it).

---

