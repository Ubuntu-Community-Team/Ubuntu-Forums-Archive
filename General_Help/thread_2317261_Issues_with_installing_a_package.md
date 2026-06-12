---
title: "Issues with installing a package"
date: 2016-03-14
forum: General Help
---

### Post by jeremy68 on 2016-03-14
Hello, all! I'm currently experiencing an issue with installing a package, "Torch".

I'm looking to install this: [http://www.makeuseof.com/tag/create-neural-paintings-deepstyle-ubuntu/](http://www.makeuseof.com/tag/create-neural-paintings-deepstyle-ubuntu/)

Directions are being followed. I've done this before on another computer running an older version of Ubuntu (14); not quite sure why I'm experiencing issues now.

I'm having trouble with the Torch installation step -- everything before that works fine as long as long as I include "
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) vivid main universe" into the sources list, and I install cmake before installing any of the preceding dependencies.

Anyways, when I install torch using the directions from the website ([http://torch.ch/docs/getting-started.html](http://torch.ch/docs/getting-started.html)) and I run "bash install-deps" I receive the following error:

---

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:



The following packages have unmet dependencies:
 libqt4-core : Depends: libqt4-dbus (= 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6) but 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 is to be installed
               Depends: libqt4-network (= 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6) but 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 is to be installed
               Depends: libqt4-script (= 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6) but 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 is to be installed
               Depends: libqt4-test (= 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6) but 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 is to be installed
               Depends: libqt4-xml (= 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6) but 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 is to be installed
               Depends: libqtcore4 (= 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6) but 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 is to be installed
 libqt4-gui : Depends: libqt4-designer (= 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6) but 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 is to be installed
              Depends: libqt4-opengl (= 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6) but 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 is to be installed
              Depends: libqt4-svg (= 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6) but 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 is to be installed
              Depends: libqtgui4 (= 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6) but 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 is to be installed
E: Unable to correct problems, you have held broken packages.

---

I can run "dpkg --get-selections | grep hold" or "sudo apt-mark showhold" but no results are returned. Using "sudo apt-get autoremove" doesn't remedy the problem either. (These were all proposed solutions from threads on various sites offering a solution

Interestingly enough I try to install Synaptic package manager to see if I can work with the issue from there using "sudo apt-get install synaptic" and I receive a similar error:

---
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 synaptic : Depends: libxapian22 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

I'd really appreciate any help offered. This particular project on github seems very interesting and I'd love to try it out. Thank you all in advance. Once again, it's very much appreciated.

---

### Post by T.J. on 2016-03-15
I've not looked deeply into this, but it looks like you are trying to install an older package on a newer and unsupported version of Ubuntu. Since Torch is not an official package, but comes from a third party, you have no guarantees that it was packaged properly.   I do not know your level of skill and I certainly mean no disrespect, but following those instructions is very unwise if you do not have experience with packaging.  You could damage your install beyond your ability to repair.

I'm not here to just shoot down your plans, I can help you!  I am a programmer.  I can't promise anything right now, but I may be able to package the program you need.  I can't do anything for the next few days.  I have family and work obligations that I have to attend to first.  I might be able to help you next week, if you are still willing.  Please send me a personal message on the board if you are interested.

---

### Post by jeremy68 on 2016-03-15
I've sent you a PM. I very much appreciate this.

I'm going to leave this as unsolved because, really, I'm still looking for a solution.

---

### Post by QIII on 2016-03-15
Since the question was asked in the open forum, please do not conclude it via PM.  That is discourteous in the extreme to any other member who might have a similar issue in the future and be thus robbed of an answer.

A question asked in the forums should be answered there.  The community exists not to answer each individual's question entirely in isolation, but to provide free exchange of information with all users.

Thank you.

---

### Post by ian-weisser on 2016-03-15
You should really let the Torch devs know that their install script is out of date, and no longer works with the current version of Ubuntu.
It may be very easy for them to fix.

Better yet, the community of Torch users is welcome to package the software for Debian/Ubuntu so it can be installed from Software Center.

---

### Post by deadflowr on 2016-03-15
What version is actually in use?
The repo listed is for a dead release (vivid)
and only a mention of having installed on an older Ubuntu 14(?).

No mention of the current version...
Or did I miss it?

---

### Post by T.J. on 2016-03-20
> **QIII said:**
> Since the question was asked in the open forum, please do not conclude it via PM.  That is discourteous in the extreme to any other member who might have a similar issue in the future and be thus robbed of an answer.

A question asked in the forums should be answered there.  The community exists not to answer each individual's question entirely in isolation, but to provide free exchange of information with all users.

Thank you.

Apologies. I only asked for a PM to confirm actual interest in possibly packaging it.  I want to make sure the time is well spent and it will be used, since any port I do would be unofficial.  I have not made packages for Debian for a while, since I usually just install into /usr/local. I'm happy to do it to help out someone else though.   I use Debian and will have to setup a host for Ubuntu. In spite of Ubuntu being based on Debian Sid, they are actually very different when it comes to packaging dependencies - so it might take me a little longer.

---

### Post by T.J. on 2016-03-20
> **jeremy68 said:**
> I've sent you a PM. I very much appreciate this.

I'm going to leave this as unsolved because, really, I'm still looking for a solution.

Which version of Ubuntu are you using?

---

### Post by jeremy68 on 2016-03-22
Most recent. 15.10.

---

### Post by jeremy68 on 2016-03-22
That's fine. I'm still very interested/thankful. Did you get the PM?

---

### Post by jeremy68 on 2016-03-22
> **ian-weisser said:**
> You should really let the Torch devs know that their install script is out of date, and no longer works with the current version of Ubuntu.
It may be very easy for them to fix.

Better yet, the community of Torch users is welcome to package the software for Debian/Ubuntu so it can be installed from Software Center.

I've made multiple posts but no replies from the devs.

---

### Post by T.J. on 2016-03-22
> **jeremy68 said:**
> That's fine. I'm still very interested/thankful. Did you get the PM?

Yes, thank you.  =)

15.10.. Good!  That is the one thing I didn't know, and needed.  Since I use a customized version of Debian 8, I'll need to setup a machine with 15.10 tomorrow and then can get started.  It will certainly take me a few days to get  handle on everything.  As a disclaimer, I'm not promising anything. I can't promise to make it work or  any results until I get a chance to look at the code. What I will do is my best to try to deliver to you a working package.  I'll post updates here to keep you appraised of how things are going.

---

### Post by T.J. on 2016-03-24
Just a quick update.  Finally got 15.10 to install.  It didn't work properly on my hardware until I patched it.  So I will be downloading the torch source code today or tomorrow. =)  I'll keep you posted here rather than a PM so everyone else can follow if they so desire.

---

### Post by jeremy68 on 2016-03-25
Awesome, T.J.

If there's any way I can help, let me know.

---

### Post by T.J. on 2016-03-25
First test results...

I followed the original instructions with some changes to fix problems. I need to see if the software is actually viable before bothering to  package it.  I have it installed successfully and am running a test  render now.

The instructions are a bit inaccurate.  I'm not surprised that you had trouble. 


I'll keep you posted. 

P.S. Very hopeful.  Please be very patient when using this software. =)  It is slow, and I do mean it. VERY SLOW.

---

### Post by T.J. on 2016-03-25
It seems to have worked as advertised. It took just over an hour and forty minutes to render a single composite with a 960x720 photo on my somewhat antiquated 6 core AMD 1090T processor.

Now I have to get to my "day job", so looking at packaging will have to wait until tomorrow or the next day.  More soon.

---

### Post by jeremy68 on 2016-03-25
Woah. Care to share results?

---

### Post by T.J. on 2016-03-26
[FONT=Loma][FONT=Loma][FONT=Loma][FONT=Loma][FONT=Loma]It may take me longer with my current  work schedule to [FONT=Loma]decide  the  best way to package Torch for you.  I'm sorry to admit that my  Debian/Ubuntu packaging skills are less than stellar these days, from  lack of use. [/FONT][/FONT][/FONT]I'm posting these instructions for you  in case you want to get working right away and not wait - which is  completely understandable. [FONT=Loma] Please read everything first before you start if you decide to try this.  My workstation is setup for development so it is possible I missed something. [/FONT][FONT=Loma]I sometimes make errors. =)[/FONT][FONT=Loma]  I[/FONT][/FONT][/FONT] must emphasize as a disclaimer that a lot of this is not officially supported code, so there are no bug patches or security updates available from Canonical or Ubuntu.  

No matter, I will try to help you in any way as best I can.

[/FONT][FONT=Loma]In your first post, you mentioned trying to import from Vivid.  [/FONT][FONT=Loma]Please completely purge any files that you imported from Vivid. [/FONT][FONT=Loma]R[/FONT][FONT=Loma]emove the &#8220;deb [FONT=Loma][http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu)[/FONT] vivid main universe&#8221;  [/FONT][FONT=Loma]source and re-sync your packages. [/FONT][FONT=Loma]Make sure there aren't any holds.

[/FONT][FONT=Loma]
[/FONT]
 [FONT=Loma]**1. install Git**[/FONT]
 [FONT=Loma]*sudo apt-get install git*[/FONT]
 [FONT=Loma]
**2. Install Lua**[/FONT]
 [FONT=Loma]*sudo apt-get install lua5.2*[/FONT]
 
 [FONT=Loma]**3. Install Lua Compiler**[/FONT]
 [FONT=Loma]*sudo apt-get install luajit*[/FONT]
 
 
 [FONT=Loma]**4. Change ownership of /usr/local**[/FONT]
 s[FONT=Loma][I]udo chown <your personal username> /usr/local -Rv

[/I](e.g. sudo chown bob /usr/local -Rv)[/FONT]
 [FONT=Loma]
By default and tradition, personal packages not provided by your OS intended to be system-wide are installed in /usr/local. Since most Linux desktops are used only by one person, it is highly desirable for you to take over /usr/local if you are going to be compiling personal packages from source.  It avoids the necessity of using root or sudo much of the time and is therefore safer. If someone else's script is buggy, running it as root can be a huge problem.  If [/FONT][FONT=Loma]your installation[/FONT][FONT=Loma] is server, or has multiple users, this may be an issue. [/FONT][FONT=Loma]In 99.9% of cases, it shouldn't matter regardless, but programmers tend toward caution. [FONT=Loma][/FONT]

[/FONT][FONT=Loma]**5. install Torch**[/FONT]
                          *[FONT=Loma]curl -s [/FONT]*[I][FONT=Loma]https://raw.githubusercontent.com/torch/ezinstall/master/install-all | bash

[/FONT][/I]

    [FONT=Loma]**6. Test Torch**[/FONT]
 [FONT=Loma]*luajit -ltorch*[/FONT]
 
 [FONT=Loma]Use ctrl +d to exit the shell when satisfied.[/FONT]
 
 [FONT=Loma]**7. Install dev files for other modules**[/FONT][FONT=Loma]
[/FONT][FONT=Loma]*sudo apt-get install libprotobuf-dev protobuf-compiler*[/FONT]
 
 
 [FONT=Loma]**8. Install Loadcaffe**[/FONT]
 [FONT=Loma]*sudo luarocks install loadcaffe*[/FONT]
 
 
 [FONT=Loma]**9. install image**[/FONT]
 [FONT=Loma]*sudo luarocks install image*[/FONT]
 
 
 [FONT=Loma]**10. install nn**[/FONT]
 [FONT=Loma]*sudo *[/FONT][FONT=Loma]*luarocks install nn*[/FONT]
 
 
 [FONT=Loma]**11. make Deepstyle directory in your home**[/FONT]
 [FONT=Loma]*mkdir Deepstyle*[/FONT]
 [FONT=Loma]*cd Deepstyle*[/FONT]
                         *[FONT=Loma][I]git clone [https://github.com/jcjohnson/neural-style.git](https://github.com/jcjohnson/neural-style.git)*[/FONT][/I]
  [FONT=Loma]*cd neural-style*[/FONT]
 [FONT=Loma]*sh models/download_models.sh*[/FONT]
 
 
 [FONT=Loma]From this point the webpage should work, [/FONT][FONT=Loma]starting with the 
&#8220;[/FONT]th neural_style.lua -style_image YOURPAINTINGHERE.jpg - content_image YOURPHOTOHERE.jpg -gpu -1[FONT=Loma]&#8221;
[/FONT]

---

### Post by jeremy68 on 2016-03-28
T.J. - 

If you are still interested in creating the package, that's fine but the instructions you have provided are more than sufficient. I've got it up and working. There's a few issues with installing one of the optional dependencies - namely, the CUDA backend - and if you are interested in pursuing this tiresome effort further then I can post the issues in the same thread when I have access to the computer. If not, though, I'm going to mark this as solved and keep trying/ask elsewhere . . . you've done enough and (inadvertently?) taught me more than most.

---

### Post by jeremy68 on 2016-03-28
[If you wanted to take a look: here's a post I made over at the github.]

                  CUDA installed fine, followed directions on nvidia site. Only issue is with cunn.
  the output of **luarocks install cunn** : 
  Installing [https://raw.githubusercontent.com/torch/rocks/master/cunn-scm-1.rockspec](https://raw.githubusercontent.com/torch/rocks/master/cunn-scm-1.rockspec)...
Using [https://raw.githubusercontent.com/torch/rocks/master/cunn-scm-1.rockspec](https://raw.githubusercontent.com/torch/rocks/master/cunn-scm-1.rockspec)... switching to 'build' mode
  Missing dependencies for cunn:
cutorch >= 1.0
  Using [https://raw.githubusercontent.com/torch/rocks/master/cutorch-scm-1.rockspec](https://raw.githubusercontent.com/torch/rocks/master/cutorch-scm-1.rockspec)... switching to 'build' mode
Cloning into 'cutorch'...
remote: Counting objects: 107, done.
remote: Compressing objects: 100% (102/102), done.
remote: Total 107 (delta 9), reused 40 (delta 3), pack-reused 0
Receiving objects: 100% (107/107), 161.61 KiB | 0 bytes/s, done.
Resolving deltas: 100% (9/9), done.
Checking connectivity... done.
cmake -E make_directory build && cd build && cmake ..  -DCMAKE_BUILD_TYPE=Release -DCMAKE_PREFIX_PATH="/usr/local/bin/.."  -DCMAKE_INSTALL_PREFIX="/usr/local/lib/luarocks/rocks/cutorch/scm-1"  && make -j$(getconf _NPROCESSORS_ONLN) install
  -- The C compiler identification is GNU 5.2.1
-- The CXX compiler identification is GNU 5.2.1
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Found Torch7 in /usr/local
-- Found CUDA: /usr/local/cuda (found suitable version "7.5", minimum required is "6.5") 
-- MAGMA not found. Compiling without MAGMA support
-- Automatic GPU detection failed. Building for all known architectures.
-- Compiling for CUDA architecture: 2.0 2.1(2.0) 3.0 3.5 5.0 5.2
-- Configuring done
-- Generating done
-- Build files have been written to: /tmp/luarocks_cutorch-scm-1-3274/cutorch/build
[  2%] [  5%] [  7%] [ 10%] [ 13%] [ 15%] Building NVCC (Device) object  lib/THC/CMakeFiles/THC.dir/THC_generated_THCReduceApplyUtils.cu.o
Building NVCC (Device) object lib/THC/CMakeFiles/THC.dir/THC_generated_THCTensor.cu.o
Building NVCC (Device) object lib/THC/CMakeFiles/THC.dir/THC_generated_THCStorage.cu.o
Building NVCC (Device) object lib/THC/CMakeFiles/THC.dir/THC_generated_THCBlas.cu.o
Building NVCC (Device) object lib/THC/CMakeFiles/THC.dir/THC_generated_THCStorageCopy.cu.o
Building NVCC (Device) object lib/THC/CMakeFiles/THC.dir/THC_generated_THCHalf.cu.o
In file included from /usr/local/cuda/include/cuda_runtime.h:76:0,
                 from :0:
/usr/local/cuda/include/host_config.h:115:2: error: #error --  unsupported GNU version! gcc versions later than 4.9 are not supported!
 #error -- unsupported GNU version! gcc versions later than 4.9 are not supported!
  ^
In file included from /usr/local/cuda/include/cuda_runtime.h:76:0,
                 from :0:
/usr/local/cuda/include/host_config.h:115:2: error: #error --  unsupported GNU version! gcc versions later than 4.9 are not supported!
 #error -- unsupported GNU version! gcc versions later than 4.9 are not supported!
  ^
In file included from /usr/local/cuda/include/cuda_runtime.h:76:0,
                 from :0:
/usr/local/cuda/include/host_config.h:115:2: error: #error --  unsupported GNU version! gcc versions later than 4.9 are not supported!
 #error -- unsupported GNU version! gcc versions later than 4.9 are not supported!
  ^
In file included from /usr/local/cuda/include/cuda_runtime.h:76:0,
                 from :0:
/usr/local/cuda/include/host_config.h:115:2: error: #error --  unsupported GNU version! gcc versions later than 4.9 are not supported!
 #error -- unsupported GNU version! gcc versions later than 4.9 are not supported!
  ^
In file included from /usr/local/cuda/include/cuda_runtime.h:76:0,
                 from :0:
/usr/local/cuda/include/host_config.h:115:2: error: #error --  unsupported GNU version! gcc versions later than 4.9 are not supported!
 #error -- unsupported GNU version! gcc versions later than 4.9 are not supported!
  ^
In file included from /usr/local/cuda/include/cuda_runtime.h:76:0,
                 from :0:
/usr/local/cuda/include/host_config.h:115:2: error: #error --  unsupported GNU version! gcc versions later than 4.9 are not supported!
 #error -- unsupported GNU version! gcc versions later than 4.9 are not supported!
  ^
CMake Error at THC_generated_THCTensor.cu.o.cmake:206 (message):
  Error generating
  /tmp/luarocks_cutorch-scm-1-3274/cutorch/build/lib/THC/CMakeFiles/THC.dir//./THC_generated_THCTensor.cu.o
  lib/THC/CMakeFiles/THC.dir/build.make:87: recipe for target 'lib/THC/CMakeFiles/THC.dir/THC_generated_THCTensor.cu.o' failed
make[2]: *** [lib/THC/CMakeFiles/THC.dir/THC_generated_THCTensor.cu.o] Error 1
make[2]: *** Waiting for unfinished jobs....
CMake Error at THC_generated_THCBlas.cu.o.cmake:206 (message):
  Error generating
  /tmp/luarocks_cutorch-scm-1-3274/cutorch/build/lib/THC/CMakeFiles/THC.dir//./THC_generated_THCBlas.cu.o
  lib/THC/CMakeFiles/THC.dir/build.make:63: recipe for target 'lib/THC/CMakeFiles/THC.dir/THC_generated_THCBlas.cu.o' failed
make[2]: *** [lib/THC/CMakeFiles/THC.dir/THC_generated_THCBlas.cu.o] Error 1
CMake Error at THC_generated_THCStorageCopy.cu.o.cmake:206 (message):
  Error generating
  /tmp/luarocks_cutorch-scm-1-3274/cutorch/build/lib/THC/CMakeFiles/THC.dir//./THC_generated_THCStorageCopy.cu.o
  lib/THC/CMakeFiles/THC.dir/build.make:79: recipe for target  'lib/THC/CMakeFiles/THC.dir/THC_generated_THCStorageCopy.cu.o' failed
make[2]: *** [lib/THC/CMakeFiles/THC.dir/THC_generated_THCStorageCopy.cu.o] Error 1
CMake Error at THC_generated_THCReduceApplyUtils.cu.o.cmake:206 (message):
  Error generating
  /tmp/luarocks_cutorch-scm-1-3274/cutorch/build/lib/THC/CMakeFiles/THC.dir//./THC_generated_THCReduceApplyUtils.cu.o
  lib/THC/CMakeFiles/THC.dir/build.make:55: recipe for target  'lib/THC/CMakeFiles/THC.dir/THC_generated_THCReduceApplyUtils.cu.o'  failed
make[2]: *** [lib/THC/CMakeFiles/THC.dir/THC_generated_THCReduceApplyUtils.cu.o] Error 1
CMake Error at THC_generated_THCHalf.cu.o.cmake:206 (message):
  Error generating
  /tmp/luarocks_cutorch-scm-1-3274/cutorch/build/lib/THC/CMakeFiles/THC.dir//./THC_generated_THCHalf.cu.o
  lib/THC/CMakeFiles/THC.dir/build.make:247: recipe for target 'lib/THC/CMakeFiles/THC.dir/THC_generated_THCHalf.cu.o' failed
make[2]: *** [lib/THC/CMakeFiles/THC.dir/THC_generated_THCHalf.cu.o] Error 1
CMake Error at THC_generated_THCStorage.cu.o.cmake:206 (message):
  Error generating
  /tmp/luarocks_cutorch-scm-1-3274/cutorch/build/lib/THC/CMakeFiles/THC.dir//./THC_generated_THCStorage.cu.o
  lib/THC/CMakeFiles/THC.dir/build.make:71: recipe for target 'lib/THC/CMakeFiles/THC.dir/THC_generated_THCStorage.cu.o' failed
make[2]: *** [lib/THC/CMakeFiles/THC.dir/THC_generated_THCStorage.cu.o] Error 1
CMakeFiles/Makefile2:156: recipe for target 'lib/THC/CMakeFiles/THC.dir/all' failed
make[1]: *** [lib/THC/CMakeFiles/THC.dir/all] Error 2
Makefile:116: recipe for target 'all' failed
make: *** [all] Error 2
  Error: Failed installing dependency: [https://raw.githubusercontent.com/torch/rocks/master/cutorch-scm-1.rockspec](https://raw.githubusercontent.com/torch/rocks/master/cutorch-scm-1.rockspec) - Build error: Failed building.



  **luarocks install cutorch** returns this:



  Installing [https://raw.githubusercontent.com/torch/rocks/master/cutorch-scm-1.rockspec](https://raw.githubusercontent.com/torch/rocks/master/cutorch-scm-1.rockspec)...
Using [https://raw.githubusercontent.com/torch/rocks/master/cutorch-scm-1.rockspec](https://raw.githubusercontent.com/torch/rocks/master/cutorch-scm-1.rockspec)... switching to 'build' mode
Cloning into 'cutorch'...
remote: Counting objects: 107, done.
remote: Compressing objects: 100% (102/102), done.
remote: Total 107 (delta 9), reused 40 (delta 3), pack-reused 0
Receiving objects: 100% (107/107), 161.61 KiB | 0 bytes/s, done.
Resolving deltas: 100% (9/9), done.
Checking connectivity... done.
cmake -E make_directory build && cd build && cmake ..  -DCMAKE_BUILD_TYPE=Release -DCMAKE_PREFIX_PATH="/usr/local/bin/.."  -DCMAKE_INSTALL_PREFIX="/usr/local/lib/luarocks/rocks/cutorch/scm-1"  && make -j$(getconf _NPROCESSORS_ONLN) install
  -- The C compiler identification is GNU 5.2.1
-- The CXX compiler identification is GNU 5.2.1
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Found Torch7 in /usr/local
-- Found CUDA: /usr/local/cuda (found suitable version "7.5", minimum required is "6.5") 
-- MAGMA not found. Compiling without MAGMA support
-- Automatic GPU detection failed. Building for all known architectures.
-- Compiling for CUDA architecture: 2.0 2.1(2.0) 3.0 3.5 5.0 5.2
-- Configuring done
-- Generating done
-- Build files have been written to: /tmp/luarocks_cutorch-scm-1-7182/cutorch/build
[  2%] [  5%] [  7%] [ 10%] Building NVCC (Device) object lib/THC/CMakeFiles/THC.dir/THC_generated_THCReduceApplyUtils.cu.o
Building NVCC (Device) object lib/THC/CMakeFiles/THC.dir/THC_generated_THCHalf.cu.o
[ 13%] [ 15%] Building NVCC (Device) object lib/THC/CMakeFiles/THC.dir/THC_generated_THCTensor.cu.o
Building NVCC (Device) object lib/THC/CMakeFiles/THC.dir/THC_generated_THCStorage.cu.o
Building NVCC (Device) object lib/THC/CMakeFiles/THC.dir/THC_generated_THCStorageCopy.cu.o
Building NVCC (Device) object lib/THC/CMakeFiles/THC.dir/THC_generated_THCBlas.cu.o
In file included from /usr/local/cuda/include/cuda_runtime.h:76:0,
                 from :0:
/usr/local/cuda/include/host_config.h:115:2: error: #error --  unsupported GNU version! gcc versions later than 4.9 are not supported!
 #error -- unsupported GNU version! gcc versions later than 4.9 are not supported!
  ^
In file included from /usr/local/cuda/include/cuda_runtime.h:76:0,
                 from :0:
/usr/local/cuda/include/host_config.h:115:2: error: #error --  unsupported GNU version! gcc versions later than 4.9 are not supported!
 #error -- unsupported GNU version! gcc versions later than 4.9 are not supported!
  ^
In file included from /usr/local/cuda/include/cuda_runtime.h:76:0,
                 from :0:
/usr/local/cuda/include/host_config.h:115:2: error: #error --  unsupported GNU version! gcc versions later than 4.9 are not supported!
 #error -- unsupported GNU version! gcc versions later than 4.9 are not supported!
  ^
In file included from /usr/local/cuda/include/cuda_runtime.h:76:0,
                 from :0:
/usr/local/cuda/include/host_config.h:115:2: error: #error --  unsupported GNU version! gcc versions later than 4.9 are not supported!
 #error -- unsupported GNU version! gcc versions later than 4.9 are not supported!
  ^
In file included from /usr/local/cuda/include/cuda_runtime.h:76:0,
                 from :0:
/usr/local/cuda/include/host_config.h:115:2: error: #error --  unsupported GNU version! gcc versions later than 4.9 are not supported!
 #error -- unsupported GNU version! gcc versions later than 4.9 are not supported!
  ^
In file included from /usr/local/cuda/include/cuda_runtime.h:76:0,
                 from :0:
/usr/local/cuda/include/host_config.h:115:2: error: #error --  unsupported GNU version! gcc versions later than 4.9 are not supported!
 #error -- unsupported GNU version! gcc versions later than 4.9 are not supported!
  ^
CMake Error at THC_generated_THCBlas.cu.o.cmake:206 (message):
  Error generating
  /tmp/luarocks_cutorch-scm-1-7182/cutorch/build/lib/THC/CMakeFiles/THC.dir//./THC_generated_THCBlas.cu.o
  lib/THC/CMakeFiles/THC.dir/build.make:63: recipe for target 'lib/THC/CMakeFiles/THC.dir/THC_generated_THCBlas.cu.o' failed
make[2]: *** [lib/THC/CMakeFiles/THC.dir/THC_generated_THCBlas.cu.o] Error 1
make[2]: *** Waiting for unfinished jobs....
CMake Error at THC_generated_THCReduceApplyUtils.cu.o.cmake:206 (message):
  Error generating
  /tmp/luarocks_cutorch-scm-1-7182/cutorch/build/lib/THC/CMakeFiles/THC.dir//./THC_generated_THCReduceApplyUtils.cu.o
  lib/THC/CMakeFiles/THC.dir/build.make:55: recipe for target  'lib/THC/CMakeFiles/THC.dir/THC_generated_THCReduceApplyUtils.cu.o'  failed
make[2]: *** [lib/THC/CMakeFiles/THC.dir/THC_generated_THCReduceApplyUtils.cu.o] Error 1
CMake Error at THC_generated_THCTensor.cu.o.cmake:206 (message):
  Error generating
  /tmp/luarocks_cutorch-scm-1-7182/cutorch/build/lib/THC/CMakeFiles/THC.dir//./THC_generated_THCTensor.cu.o
  lib/THC/CMakeFiles/THC.dir/build.make:87: recipe for target 'lib/THC/CMakeFiles/THC.dir/THC_generated_THCTensor.cu.o' failed
make[2]: *** [lib/THC/CMakeFiles/THC.dir/THC_generated_THCTensor.cu.o] Error 1
CMake Error at THC_generated_THCStorageCopy.cu.o.cmake:206 (message):
  Error generating
  /tmp/luarocks_cutorch-scm-1-7182/cutorch/build/lib/THC/CMakeFiles/THC.dir//./THC_generated_THCStorageCopy.cu.o
  lib/THC/CMakeFiles/THC.dir/build.make:79: recipe for target  'lib/THC/CMakeFiles/THC.dir/THC_generated_THCStorageCopy.cu.o' failed
make[2]: *** [lib/THC/CMakeFiles/THC.dir/THC_generated_THCStorageCopy.cu.o] Error 1
CMake Error at THC_generated_THCStorage.cu.o.cmake:206 (message):
  Error generating
  /tmp/luarocks_cutorch-scm-1-7182/cutorch/build/lib/THC/CMakeFiles/THC.dir//./THC_generated_THCStorage.cu.o
  lib/THC/CMakeFiles/THC.dir/build.make:71: recipe for target 'lib/THC/CMakeFiles/THC.dir/THC_generated_THCStorage.cu.o' failed
make[2]: *** [lib/THC/CMakeFiles/THC.dir/THC_generated_THCStorage.cu.o] Error 1
CMake Error at THC_generated_THCHalf.cu.o.cmake:206 (message):
  Error generating
  /tmp/luarocks_cutorch-scm-1-7182/cutorch/build/lib/THC/CMakeFiles/THC.dir//./THC_generated_THCHalf.cu.o
  lib/THC/CMakeFiles/THC.dir/build.make:247: recipe for target 'lib/THC/CMakeFiles/THC.dir/THC_generated_THCHalf.cu.o' failed
make[2]: *** [lib/THC/CMakeFiles/THC.dir/THC_generated_THCHalf.cu.o] Error 1
CMakeFiles/Makefile2:156: recipe for target 'lib/THC/CMakeFiles/THC.dir/all' failed
make[1]: *** [lib/THC/CMakeFiles/THC.dir/all] Error 2
Makefile:116: recipe for target 'all' failed
make: *** [all] Error 2
  Error: Build error: Failed building.
  Is it an issue with Torch itself? I installed it using curl -s [https://raw.githubusercontent.com/torch/ezinstall/master/install-all](https://raw.githubusercontent.com/torch/ezinstall/master/install-all) | bash



  Thank you in advance.

---

### Post by T.J. on 2016-03-28
> 
 If not, though, I'm going to mark this as solved and keep trying/ask elsewhere . . . you've done enough and (inadvertently?) taught me more than most.


I may have helped a little, but your own perseverance made the difference. A lot of people simply give up.  As for me, it is not a burden but a pleasure to help when and where I can.  It's the whole point of open code - to have a community that can help each other out.

I apologise if I sounded overly preachy or "teachy" (Is that a word?).  I've spent far too much time with my face in books or tech manuals.  Posting the instructions was a deliberate thought.  You seem very competent and I wanted to enable you to help yourself, especially if the end result might have been a flawed package on my part. It is just as well. Any package would be obsoleted by rapid releases every 6 months anyway, but those instructions can be used almost indefinitely. That is why I don't package things anymore and my packaging skills are deficient. There are a dozen different versions of Linux, each with radically different packaging and release schedules. Packaging under Linux, while very useful, also sacrifices a lot of time that can otherwise be used to improve code. 

> 
...If you wanted to take a look: here's a post I made over at the github.]


Let's just keep using this thread as it is directly related.

I'd be happy to do so.  Since you suggested the package will no longer be needed, I'll spend the time I was going to devote to the package to helping you with CUDA instead. I have some Nvidia hardware so this would be an interesting experiment in CUDA.  I suspect you may have a GCC issue on your hands.  I'll have to run some tests. That will take a few days.  

I'm spending some time with my brother this week, and that takes precedence.  I'll get back to you soon, though! =)

---

### Post by T.J. on 2016-04-03
Sill going to work on this, just been really busy. =)

---

### Post by jeremy68 on 2016-04-12
I understand! Thank you for your time once again.

---

### Post by T.J. on 2016-04-13
I still intend to help you with CUDA.  I have a deadline to meet at work and reconfigured my workstation, which meant dropping Ubuntu for the moment.  I'm sorry I have not gotten back to you sooner.  I should be clear of this mess by next week.

---

### Post by T.J. on 2016-04-16
Could you report back your GCC version? Ex: [I]gcc -v 

[/I]After reviewing your message, I see the GCC in your message is version 5.2.1. Your CUDA code is not supported in GCC 5. 

1. You will have to switch GCC versions and recompile if you are going to use it as is. Switching versions is not as big a deal as you might think.  Each release of Debian (and thus Ubuntu) has two versions of GCC for this very reason. The downside is that you would have to switch compilers and then recompile every step you have already done because you would be back-stepping versions of GCC to an inferior/older version. This is the best, most stable option.

 - or -

2. Check with the maintainers of the git and see if they have a patch for GCC v5.

 - or -

3. If you are feeling brave, I might even be able to update the existing code for GCC v5, but I can't promise that will generate the correct object code. Usually, programmers install GCC version checks for a reason that isn't readily apparent, such as an unfixed bug in GCC or using a library that has no source code.


Let me know which route you want to take and we can proceed happily.  (Don't mind my numbering things.  It's not pomposity, merely trying to keep my thoughts in order. I need that some days as I can be absentminded.)

---

### Post by T.J. on 2016-05-05
I haven't heard back from you in 2 weeks or so, so if you want to proceed, let me know by private message.  Otherwise, I'll assume the matter closed.

---

### Post by QIII on 2016-05-06
Again:  Please do not conduct support via PM.  See my comments above.

---

### Post by T.J. on 2016-05-08
> **QIII said:**
> Again:  Please do not conduct support via PM.  See my comments above.

Relax, friend. I never suggested such. I only suggested a message to allow me to know that the original poster is still interested.

---

