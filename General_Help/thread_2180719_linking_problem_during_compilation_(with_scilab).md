---
title: "linking problem during compilation (with scilab)"
date: 2013-10-14
forum: General Help
---

### Post by Mlaine on 2013-10-14
Hello,

since the Ubuntu's version 12.04LTS (I also tried with me most recend version without any success, I'm unable to compile my software. I'm linking scilab development library and when it's trying to make the link a lot of functions seems to miss of link.
I'm a 64bits version but don't think it's related.

for example (all needed libraries should have been added)
```

/usr/bin/c++   -Wall -Wextra -lpthread -ldl -O3 -DNDEBUG    CMakeFiles/odinSimDevice.dir/main-sim.cpp.o CMakeFiles/odinSimDevice.dir/simulator.cpp.o  -o ../../bin/odinSimDevice -rdynamic -L/usr/lib/scilab -L/usr/../lib/scilab -L/usr/modules/.libs -L/usr/modules/api_scilab/.libs  (-lscilab)
 -L/usr/bin -lomniORB4 -lomnithread -lomniDynamic4 /usr/lib/scilab/libscilab.so /usr/lib/scilab/libsciapi_scilab.so ../../lib/libodinStubs.so.4.8 ../../lib/libodinCom.so.4.8 ../../lib/libodinScilab.so.4.8 ../../lib/libodinDeviceLayersCore.so.4.8 /usr/lib/scilab/libscilab.so /usr/lib/scilab/libsciapi_scilab.so ../../lib/libodinCom.so.4.8 ../../lib/libodinStubs.so.4.8 -lQtGui -lQtXml -lQtCore -lomniORB4 -lomnithread -lomniDynamic4 ../../lib/libodinMath.so.4.8 -Wl,-rpath,/usr/lib/scilab:/usr/../lib/scilab:/usr/modules/.libs:/usr/modules/api_scilab/.libs:/usr/bin:/home/melaine/INRIA/odin/build2/lib:
/usr/lib/scilab/libsciapi_scilab.so: undefined reference to `stack_'
/usr/lib/scilab/libsciapi_scilab.so: undefined reference to `stackg_'
/usr/lib/scilab/libsciapi_scilab.so: undefined reference to `vGetPointerFromDoubleComplex'
/usr/lib/scilab/libsciapi_scilab.so: undefined reference to `freeArrayOfString'
/usr/lib/scilab/libsciapi_scilab.so: undefined reference to `getExecMode'
../../lib/libodinScilab.so.4.8: undefined reference to `Call_ScilabOpen'
```

I tried after some counsel to build a local scilab to solve this problem but now I have problem à MPI level (with I don't use, only scilab use them

```

/usr/bin/g++   -Wall -Wextra -lpthread -ldl -m64 -lmpi_cxx -fno-stack-protector -O3 -DNDEBUG    CMakeFiles/odinSimDevice.dir/main-sim.cpp.o CMakeFiles/odinSimDevice.dir/simulator.cpp.o  -o ../../bin/odinSimDevice -rdynamic -L/usr/local/lib/scilab -L/usr/local/../lib/scilab -L/usr/local/modules/.libs -L/usr/local/modules/api_scilab/.libs -L/usr/local/bin -lomniORB4 -lomnithread -lomniDynamic4 /usr/local/lib/scilab/libscilab.so /usr/local/lib/scilab/libscicall_scilab.so /usr/local/lib/scilab/libscilab-cli.so ../../lib/libodinStubs.so.5.0 ../../lib/libodinCom.so.5.0 ../../lib/libodinScilab.so.5.0 ../../lib/libodinDeviceLayersCore.so.5.0 /usr/local/lib/scilab/libscilab.so /usr/local/lib/scilab/libscicall_scilab.so /usr/local/lib/scilab/libscilab-cli.so ../../lib/libodinMath.so.5.0 ../../lib/libodinCom.so.5.0 ../../lib/libodinStubs.so.5.0 -lQtGui -lQtXml -lQtCore -lomniORB4 -lomnithread -lomniDynamic4 -lpthread -ldl -Wl,-rpath,/usr/local/lib/scilab:/usr/local/../lib/scilab:/usr/local/modules/.libs:/usr/local/modules/api_scilab/.libs:/usr/local/bin:/home/melaine/INRIA/odin/build2/lib: 
/usr/local/lib/scilab/libscihdf5.so.5: undefined reference to `ompi_mpi_cxx_op_intercept'
/usr/local/lib/scilab/libscihdf5.so.5: undefined reference to `MPI::Datatype::Free()'
/usr/local/lib/scilab/libscihdf5.so.5: undefined reference to `MPI::Comm::Comm()'
/usr/local/lib/scilab/libscihdf5.so.5: undefined reference to `MPI::Win::Free()'

mpi_cxx is installed
 --$ locate libmpi_cxx.so
/usr/lib/libmpi_cxx.so
/usr/lib/libmpi_cxx.so.0
/usr/lib/libmpi_cxx.so.0.0.1
/usr/lib/openmpi/lib/libmpi_cxx.so
/usr/lib/openmpi/lib/libmpi_cxx.so.0.0.1

```

If someone could help me, it's really frustrating that a project which was working in version 11.10 do not compile anymore. (I already posted in french forum and scilab bug for help but didn't get any solution yet... after more than 6 month)

Thanks in advance

---

