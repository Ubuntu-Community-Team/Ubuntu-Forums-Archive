---
title: "cmake linking issue on Ubuntu"
date: 2016-01-04
forum: General Help
---

### Post by newcfd on 2016-01-04
I am using cmake to compile an application with vtk libraries.
All other libraries can be linked to my application, but one: vtkFiltersFlowPaths.
It is needed in my application. After I added it to the CMakeFile.txt, I got the following
message:
    /usr/bin/ld: cannot find -lvtkFiltersFlowPaths
Its .so file is there. No issue with other .so files. I am using dozen of vtk libraries.
Only this one has problem. All libraries are in the same lib dir. What could be the cause?
Thanks for helps in advance.

---

### Post by newcfd on 2016-01-04
Problem solved. It is a cmake issue. All other libraries are set-up with absolute lib path and only this one is done differently
I changed the related file for makefile and solved the problem.

---

