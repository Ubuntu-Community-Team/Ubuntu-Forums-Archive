---
title: "vtk problems"
date: 2004-10-26
forum: General Help
---

### Post by ubuntu_demon on 2004-10-26
Hi,

I've installed vtk. I've done apt-cache search vtk and installed all the necessary packages (the same way I did on debian testing and that worked fine). I can't run the Medical examples (the package vtkdata provides the data).

Please help,
/usr/share/vtk/Medical/Python$ ./Medical1.py
ERROR: In /build/buildd/vtk-4.2.6/IO/vtkVolume16Reader.cxx, line 334
vtkVolume16Reader (0x825c270): Can't find file: ../../../../VTKData/Data/headsq/quarter.1

---

### Post by ubuntu_demon on 2004-10-26
The following works :
/usr/share/vtk/Medical/Python$ ./Medical1.py -D /usr/share/vtkdata

I want to know :

-how come I have to provide the dir ? (in debian testing this is not required)
-what can I do to not have to provide the dir ?

thnx

---

### Post by ubuntu_demon on 2004-10-26
the following works :
export VTK_DATA_ROOT=/usr/share/vtkdata 

but why do I have to do this ?

---

