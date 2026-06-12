---
title: "OpenGL 2.0 Not Available"
date: 2013-11-20
forum: General Help
---

### Post by rahulmutt on 2013-11-20
I compiled [this]("https://github.com/jckarter/hello-gl") C source code that utilizes OpenGL and obtained the following output upon execution:
--
OpenGL 2.0 not available
--

The program checks GLEW_VERSION_2_0 and prints the above if it's value is false. 

Running lspci gives this:
--
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (re
v 03)                                                                                                       
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Co
ntroller (rev 03)
--

Running glxinfo | grep "OpenGL" gives this:
--
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945GME x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 8.0.4
OpenGL extensions:
--
Does this imply that my OpenGL version is 1.4? According to [this]("http://en.wikipedia.org/wiki/Comparison_of_Intel_graphics_processing_units") and finding the 945 Mobile chipset, we find that OpenGL version 2.1 is supported on linux and 1.4 is supported on windows. It just so happens that I am dual booting lubuntu with Windows XP (which hasn't been used in over year). Is there a way I can update the Mesa implementation of OpenGL to 2.0? Another thing to note is that I had to force enable WebGL in firefox in order to view WebGL rendered objects. Firefox before changing the settings said that were problems/clashes with the drivers which was why WebGL was disabled by default. WebGL ran successfully after changing the settings, but had a lot of lag - my computer normally lags for videos during initialization. Could this be a problem too? Yet another detail is that I recently ran a Haskell graphical program that uses a binding to OpenGL 3.2 and that ran without problems.

---

