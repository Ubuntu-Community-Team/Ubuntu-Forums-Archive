---
title: "Cuda shared libraries strange behaviour"
date: 2015-06-10
forum: General Help
---

### Post by abraxas334 on 2015-06-10
I am running ubuntu 14.04 with a Tesla C2075 and an old GTX  graphics card. I have installed the CUDA develoment toolkit version 6.5 and driver version 346.46. The installation was done via the .run script provided by NVIDA and not apt-get (I needed everything in a local directory).

The installation completed without problems and I tested the installation with NVIDA samples. Then a few days later and a couple of reboots later, I wanted to run a CUDA program. This then informs me that there is an unknown cuda error. I then try and run .deviceQuery in my NVIDIA samples directory and get the following output. 

```

./deviceQuery
./deviceQuery Starting...

 CUDA Device Query (Runtime API) version (CUDART static linking)

cudaGetDeviceCount returned 30
-> unknown error
Result = FAIL

``` 

If i try running the same using sudo I get a healthy looking output. 
```

sudo ./deviceQuery
./deviceQuery Starting...

 CUDA Device Query (Runtime API) version (CUDART static linking)

Detected 2 CUDA Capable device(s)

Device 0: "Tesla C2075"
  CUDA Driver Version / Runtime Version          7.0 / 6.5
  CUDA Capability Major/Minor version number:    2.0
  Total amount of global memory:                 5375 MBytes (5636292608 bytes)
  (14) Multiprocessors, ( 32) CUDA Cores/MP:     448 CUDA Cores
  GPU Clock rate:                                1147 MHz (1.15 GHz)
  Memory Clock rate:                             1566 Mhz
  Memory Bus Width:                              384-bit
  L2 Cache Size:                                 786432 bytes
  Maximum Texture Dimension Size (x,y,z)         1D=(65536), 2D=(65536, 65535), 3D=(2048, 2048, 2048)
  Maximum Layered 1D Texture Size, (num) layers  1D=(16384), 2048 layers
  Maximum Layered 2D Texture Size, (num) layers  2D=(16384, 16384), 2048 layers
  Total amount of constant memory:               65536 bytes
  Total amount of shared memory per block:       49152 bytes
  Total number of registers available per block: 32768
  Warp size:                                     32
  Maximum number of threads per multiprocessor:  1536
  Maximum number of threads per block:           1024
  Max dimension size of a thread block (x,y,z): (1024, 1024, 64)
  Max dimension size of a grid size    (x,y,z): (65535, 65535, 65535)
  Maximum memory pitch:                          2147483647 bytes
  Texture alignment:                             512 bytes
  Concurrent copy and kernel execution:          Yes with 2 copy engine(s)
  Run time limit on kernels:                     Yes
  Integrated GPU sharing Host Memory:            No
  Support host page-locked memory mapping:       Yes
  Alignment requirement for Surfaces:            Yes
  Device has ECC support:                        Enabled
  Device supports Unified Addressing (UVA):      Yes
  Device PCI Bus ID / PCI location ID:           3 / 0
  Compute Mode:
     < Default (multiple host threads can use ::cudaSetDevice() with device simultaneously) >

Device 1: "GeForce GTX 460"
  CUDA Driver Version / Runtime Version          7.0 / 6.5
  CUDA Capability Major/Minor version number:    2.1
  Total amount of global memory:                 1024 MBytes (1073414144 bytes)
  ( 7) Multiprocessors, ( 48) CUDA Cores/MP:     336 CUDA Cores
  GPU Clock rate:                                1350 MHz (1.35 GHz)
  Memory Clock rate:                             1800 Mhz
  Memory Bus Width:                              256-bit
  L2 Cache Size:                                 524288 bytes
  Maximum Texture Dimension Size (x,y,z)         1D=(65536), 2D=(65536, 65535), 3D=(2048, 2048, 2048)
  Maximum Layered 1D Texture Size, (num) layers  1D=(16384), 2048 layers
  Maximum Layered 2D Texture Size, (num) layers  2D=(16384, 16384), 2048 layers
  Total amount of constant memory:               65536 bytes
  Total amount of shared memory per block:       49152 bytes
  Total number of registers available per block: 32768
  Warp size:                                     32
  Maximum number of threads per multiprocessor:  1536
  Maximum number of threads per block:           1024
  Max dimension size of a thread block (x,y,z): (1024, 1024, 64)
  Max dimension size of a grid size    (x,y,z): (65535, 65535, 65535)
  Maximum memory pitch:                          2147483647 bytes
  Texture alignment:                             512 bytes
  Concurrent copy and kernel execution:          Yes with 1 copy engine(s)
  Run time limit on kernels:                     No
  Integrated GPU sharing Host Memory:            No
  Support host page-locked memory mapping:       Yes
  Alignment requirement for Surfaces:            Yes
  Device has ECC support:                        Disabled
  Device supports Unified Addressing (UVA):      Yes
  Device PCI Bus ID / PCI location ID:           4 / 0
  Compute Mode:
     < Default (multiple host threads can use ::cudaSetDevice() with device simultaneously) >
> Peer access from Tesla C2075 (GPU0) -> GeForce GTX 460 (GPU1) : No
> Peer access from GeForce GTX 460 (GPU1) -> Tesla C2075 (GPU0) : No

deviceQuery, CUDA Driver = CUDART, CUDA Driver Version = 7.0, CUDA Runtime Version = 6.5, NumDevs = 2, Device0 = Tesla C2075, Device1 = GeForce GTX 460
Result = PASS

```
After running it with sudo I can run ./deviceQuery without sudo and get the same output, furthermore my CUDA program runs without a problem now. 
Any ideas what is going on there? I didn't make any changes to the shared libraries etc.

---

