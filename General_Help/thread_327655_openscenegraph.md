---
title: "openscenegraph"
date: 2006-12-29
forum: General Help
---

### Post by trop on 2006-12-29
I think I may be interpreting this wrong, but looking at the url below I believe that the binary has been updated? Looking at Synaptic pkg manager I still see 0.9.9 listed.

[https://launchpad.net/distros/ubuntu/+source/openscenegraph/+bug/56935](https://launchpad.net/distros/ubuntu/+source/openscenegraph/+bug/56935)

Thanks

---

### Post by sunfisher on 2007-01-01
I've been trying to use openscenegraph and had problems w/ the binaries as well as an error in compiling version 1.2 (listed below). The problem w/ the binaries is similar between my desktop, laptop and the machines at work. All problems with detecting vertical sync. 

My compile error is as follows:
g++  -O2 -L/usr/X11R6/lib -L../../../lib/Linux32   OrientationConverter.o osgconv.o   -lstdc++ -losgProducer -lProducer -losgText -losg -losgUtil -losgGA -losgDB -lGLU -lGL  -lOpenThreads   -o osgconv
../../../lib/Linux32/libosgProducer.so: undefined reference to `Producer::PipeTimer::_thePipeTimer'
../../../lib/Linux32/libosgProducer.so: undefined reference to `Producer::Camera::FrameTimeStampSet::~FrameTimeStampSet()'
../../../lib/Linux32/libosgProducer.so: undefined reference to `Producer::PipeTimer::setReturnType(Producer::PipeTimer::ReturnType)'
../../../lib/Linux32/libosgProducer.so: undefined reference to `OpenThreads::GetNumberOfProcessors()'
collect2: ld returned 1 exit status

Any suggestions?
Thanks,

---

