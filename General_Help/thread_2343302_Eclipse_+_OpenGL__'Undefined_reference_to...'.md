---
title: "Eclipse + OpenGL : 'Undefined reference to...'"
date: 2016-11-15
forum: General Help
---

### Post by carcox on 2016-11-15
I am trying to use OpenGL libraries with Eclipse CDT (Eclipse for C++) on Ubuntu 16.04 LTS 64 bit.

As a first test, I would like to just call glfwInit() to check if I am linking all the required libraries, but when I compile, I get many undefined references (log below). It seems some libraries are missing, but I am linking to the following libraries on Eclipse:

[IMG]https://s15.postimg.org/d9oh7wjaj/Screenshot_from_2016_11_15_10_31_08.png[/IMG]


The c++ compiler (g++) is surely finding them (no errors of 'cannot find foo library are raised), so I cannot find out which one I am missing. Any hint? Below I show all the undefined references I get when compiling.

```

10:29:43 **** Incremental Build of configuration Debug for project OpenGL_Test ****
make all 
Building target: OpenGL_Test
Invoking: GCC C++ Linker
g++ -L/opt/glfw-3.2.1/src -L/opt/glew-2.0.0/lib -L/usr/lib/x86_64-linux-gnu -o "OpenGL_Test"  ./src/main.o   -lpthread -ldl -lX11 -lXrandr -lXext -lXi -lGL -lGLU -lGLEW -lglfw3
/opt/glfw-3.2.1/src/libglfw3.a(vulkan.c.o): In function `_glfwInitVulkan':
vulkan.c:(.text+0x4a): undefined reference to `dlopen'
vulkan.c:(.text+0x95): undefined reference to `dlsym'
/opt/glfw-3.2.1/src/libglfw3.a(vulkan.c.o): In function `_glfwTerminateVulkan':
vulkan.c:(.text+0x496): undefined reference to `dlclose'
/opt/glfw-3.2.1/src/libglfw3.a(vulkan.c.o): In function `glfwGetInstanceProcAddress':
vulkan.c:(.text+0x803): undefined reference to `dlsym'
/opt/glfw-3.2.1/src/libglfw3.a(x11_init.c.o): In function `translateKeyCode':
x11_init.c:(.text+0x6a): undefined reference to `XkbKeycodeToKeysym'
x11_init.c:(.text+0x14a): undefined reference to `XkbKeycodeToKeysym'
x11_init.c:(.text+0x177): undefined reference to `XGetKeyboardMapping'
x11_init.c:(.text+0x191): undefined reference to `XFree'
/opt/glfw-3.2.1/src/libglfw3.a(x11_init.c.o): In function `createKeyTables':
x11_init.c:(.text+0xc3e): undefined reference to `XkbGetMap'
x11_init.c:(.text+0xc61): undefined reference to `XkbGetNames'
x11_init.c:(.text+0x137e): undefined reference to `XkbFreeNames'
x11_init.c:(.text+0x1394): undefined reference to `XkbFreeKeyboard'
/opt/glfw-3.2.1/src/libglfw3.a(x11_init.c.o): In function `hasUsableInputMethodStyle':
x11_init.c:(.text+0x14ac): undefined reference to `XGetIMValues'
x11_init.c:(.text+0x1506): undefined reference to `XFree'
/opt/glfw-3.2.1/src/libglfw3.a(x11_init.c.o): In function `getSupportedAtom':
x11_init.c:(.text+0x1555): undefined reference to `XInternAtom'
/opt/glfw-3.2.1/src/libglfw3.a(x11_init.c.o): In function `detectEWMH':
x11_init.c:(.text+0x15e4): undefined reference to `XInternAtom'
x11_init.c:(.text+0x160a): undefined reference to `XInternAtom'
x11_init.c:(.text+0x1653): undefined reference to `XFree'
makefile:45: recipe for target 'OpenGL_Test' failed
x11_init.c:(.text+0x168e): undefined reference to `XFree'
x11_init.c:(.text+0x16a7): undefined reference to `XFree'
x11_init.c:(.text+0x16d0): undefined reference to `XFree'
x11_init.c:(.text+0x16dc): undefined reference to `XFree'
/opt/glfw-3.2.1/src/libglfw3.a(x11_init.c.o):x11_init.c:(.text+0x16ed): more undefined references to `XFree' follow
/opt/glfw-3.2.1/src/libglfw3.a(x11_init.c.o): In function `initExtensions':
x11_init.c:(.text+0x196d): undefined reference to `XF86VidModeQueryExtension'
x11_init.c:(.text+0x19ae): undefined reference to `XRRQueryExtension'
x11_init.c:(.text+0x19e8): undefined reference to `XRRQueryVersion'
x11_init.c:(.text+0x1a75): undefined reference to `XRRGetScreenResources'
x11_init.c:(.text+0x1aa8): undefined reference to `XRRGetCrtcGammaSize'
x11_init.c:(.text+0x1adf): undefined reference to `XRRFreeScreenResources'
x11_init.c:(.text+0x1b0b): undefined reference to `XRRSelectInput'
x11_init.c:(.text+0x1b3d): undefined reference to `XineramaQueryExtension'
x11_init.c:(.text+0x1b57): undefined reference to `XineramaIsActive'
x11_init.c:(.text+0x1bea): undefined reference to `XkbQueryExtension'
x11_init.c:(.text+0x1c29): undefined reference to `XkbSetDetectableAutoRepeat'
x11_init.c:(.text+0x1c56): undefined reference to `dlopen'
x11_init.c:(.text+0x1c97): undefined reference to `dlsym'
x11_init.c:(.text+0x1cd4): undefined reference to `XInternAtom'
x11_init.c:(.text+0x1d07): undefined reference to `XInternAtom'
x11_init.c:(.text+0x1d3a): undefined reference to `XInternAtom'
x11_init.c:(.text+0x1d6d): undefined reference to `XInternAtom'
x11_init.c:(.text+0x1da0): undefined reference to `XInternAtom'
/opt/glfw-3.2.1/src/libglfw3.a(x11_init.c.o):x11_init.c:(.text+0x1dd3): more undefined references to `XInternAtom' follow
/opt/glfw-3.2.1/src/libglfw3.a(x11_init.c.o): In function `_glfwGrabErrorHandlerX11':
x11_init.c:(.text+0x2364): undefined reference to `XSetErrorHandler'
/opt/glfw-3.2.1/src/libglfw3.a(x11_init.c.o): In function `_glfwReleaseErrorHandlerX11':
x11_init.c:(.text+0x2386): undefined reference to `XSync'
x11_init.c:(.text+0x2390): undefined reference to `XSetErrorHandler'
/opt/glfw-3.2.1/src/libglfw3.a(x11_init.c.o): In function `_glfwInputErrorX11':
x11_init.c:(.text+0x23e9): undefined reference to `XGetErrorText'
/opt/glfw-3.2.1/src/libglfw3.a(x11_init.c.o): In function `_glfwCreateCursorX11':
x11_init.c:(.text+0x244f): undefined reference to `XcursorImageCreate'
x11_init.c:(.text+0x257c): undefined reference to `XcursorImageLoadCursor'
x11_init.c:(.text+0x258c): undefined reference to `XcursorImageDestroy'
/opt/glfw-3.2.1/src/libglfw3.a(x11_init.c.o): In function `_glfwPlatformInit':
x11_init.c:(.text+0x259f): undefined reference to `XInitThreads'
x11_init.c:(.text+0x25a9): undefined reference to `XOpenDisplay'
x11_init.c:(.text+0x2686): undefined reference to `XrmUniqueQuark'
x11_init.c:(.text+0x26c3): undefined reference to `XSupportsLocale'
x11_init.c:(.text+0x26d7): undefined reference to `XSetLocaleModifiers'
x11_init.c:(.text+0x26fc): undefined reference to `XOpenIM'
x11_init.c:(.text+0x273f): undefined reference to `XCloseIM'
/opt/glfw-3.2.1/src/libglfw3.a(x11_init.c.o): In function `_glfwPlatformTerminate':
x11_init.c:(.text+0x27aa): undefined reference to `dlclose'
x11_init.c:(.text+0x27f6): undefined reference to `XFreeCursor'
x11_init.c:(.text+0x2847): undefined reference to `XCloseIM'
x11_init.c:(.text+0x2887): undefined reference to `XCloseDisplay'
/opt/glfw-3.2.1/src/libglfw3.a(x11_monitor.c.o): In function `_glfwSetVideoModeX11':
x11_monitor.c:(.text+0x332): undefined reference to `XRRGetScreenResources'
x11_monitor.c:(.text+0x361): undefined reference to `XRRGetCrtcInfo'
x11_monitor.c:(.text+0x390): undefined reference to `XRRGetOutputInfo'
x11_monitor.c:(.text+0x4be): undefined reference to `XRRSetCrtcConfig'
x11_monitor.c:(.text+0x4ce): undefined reference to `XRRFreeOutputInfo'
x11_monitor.c:(.text+0x4da): undefined reference to `XRRFreeCrtcInfo'
x11_monitor.c:(.text+0x4e6): undefined reference to `XRRFreeScreenResources'
/opt/glfw-3.2.1/src/libglfw3.a(x11_monitor.c.o): In function `_glfwRestoreVideoModeX11':
x11_monitor.c:(.text+0x596): undefined reference to `XRRGetScreenResources'
x11_monitor.c:(.text+0x5c2): undefined reference to `XRRGetCrtcInfo'
x11_monitor.c:(.text+0x632): undefined reference to `XRRSetCrtcConfig'
x11_monitor.c:(.text+0x642): undefined reference to `XRRFreeCrtcInfo'
x11_monitor.c:(.text+0x64e): undefined reference to `XRRFreeScreenResources'
/opt/glfw-3.2.1/src/libglfw3.a(x11_monitor.c.o): In function `_glfwPlatformGetMonitors':
x11_monitor.c:(.text+0x6e1): undefined reference to `XRRGetScreenResources'
x11_monitor.c:(.text+0x70c): undefined reference to `XRRGetOutputPrimary'
x11_monitor.c:(.text+0x758): undefined reference to `XineramaQueryScreens'
x11_monitor.c:(.text+0x79d): undefined reference to `XRRGetCrtcInfo'
x11_monitor.c:(.text+0x7e2): undefined reference to `XRRGetOutputInfo'
x11_monitor.c:(.text+0x7ff): undefined reference to `XRRFreeOutputInfo'
x11_monitor.c:(.text+0x997): undefined reference to `XRRFreeOutputInfo'
x11_monitor.c:(.text+0xa38): undefined reference to `XRRFreeCrtcInfo'
x11_monitor.c:(.text+0xa58): undefined reference to `XRRFreeScreenResources'
x11_monitor.c:(.text+0xa6b): undefined reference to `XFree'
/opt/glfw-3.2.1/src/libglfw3.a(x11_monitor.c.o): In function `_glfwPlatformGetMonitorPos':
x11_monitor.c:(.text+0xbfa): undefined reference to `XRRGetScreenResourcesCurrent'
x11_monitor.c:(.text+0xc26): undefined reference to `XRRGetCrtcInfo'
x11_monitor.c:(.text+0xc5e): undefined reference to `XRRFreeCrtcInfo'
x11_monitor.c:(.text+0xc6a): undefined reference to `XRRFreeScreenResources'
/opt/glfw-3.2.1/src/libglfw3.a(x11_monitor.c.o): In function `_glfwPlatformGetVideoModes':
x11_monitor.c:(.text+0xce7): undefined reference to `XRRGetScreenResourcesCurrent'
x11_monitor.c:(.text+0xd13): undefined reference to `XRRGetCrtcInfo'
x11_monitor.c:(.text+0xd3f): undefined reference to `XRRGetOutputInfo'
x11_monitor.c:(.text+0xe82): undefined reference to `XRRFreeOutputInfo'
x11_monitor.c:(.text+0xe8e): undefined reference to `XRRFreeCrtcInfo'
x11_monitor.c:(.text+0xe9a): undefined reference to `XRRFreeScreenResources'
/opt/glfw-3.2.1/src/libglfw3.a(x11_monitor.c.o): In function `_glfwPlatformGetVideoMode':
x11_monitor.c:(.text+0xf57): undefined reference to `XRRGetScreenResourcesCurrent'
x11_monitor.c:(.text+0xf83): undefined reference to `XRRGetCrtcInfo'
x11_monitor.c:(.text+0xfdb): undefined reference to `XRRFreeCrtcInfo'
x11_monitor.c:(.text+0xfe7): undefined reference to `XRRFreeScreenResources'
/opt/glfw-3.2.1/src/libglfw3.a(x11_monitor.c.o): In function `_glfwPlatformGetGammaRamp':
x11_monitor.c:(.text+0x1136): undefined reference to `XRRGetCrtcGammaSize'
x11_monitor.c:(.text+0x1160): undefined reference to `XRRGetCrtcGamma'
x11_monitor.c:(.text+0x11ec): undefined reference to `XRRFreeGamma'
x11_monitor.c:(.text+0x1230): undefined reference to `XF86VidModeGetGammaRampSize'
x11_monitor.c:(.text+0x1293): undefined reference to `XF86VidModeGetGammaRamp'
/opt/glfw-3.2.1/src/libglfw3.a(x11_monitor.c.o): In function `_glfwPlatformSetGammaRamp':
x11_monitor.c:(.text+0x12f2): undefined reference to `XRRAllocGamma'
x11_monitor.c:(.text+0x1395): undefined reference to `XRRSetCrtcGamma'
x11_monitor.c:(.text+0x13a1): undefined reference to `XRRFreeGamma'
x11_monitor.c:(.text+0x1405): undefined reference to `XF86VidModeSetGammaRamp'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `waitForVisibilityNotify':
x11_window.c:(.text+0x3cc): undefined reference to `XCheckTypedWindowEvent'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `getWindowState':
x11_window.c:(.text+0x463): undefined reference to `XFree'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `findWindowByHandle':
x11_window.c:(.text+0x65b): undefined reference to `XFindContext'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `sendEventToWM':
x11_window.c:(.text+0x789): undefined reference to `XSendEvent'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `updateNormalHints':
x11_window.c:(.text+0x7b7): undefined reference to `XAllocSizeHints'
x11_window.c:(.text+0x966): undefined reference to `XSetWMNormalHints'
x11_window.c:(.text+0x972): undefined reference to `XFree'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `updateWindowMode':
x11_window.c:(.text+0xafa): undefined reference to `XChangeWindowAttributes'
x11_window.c:(.text+0xb5d): undefined reference to `XChangeProperty'
x11_window.c:(.text+0xbbf): undefined reference to `XDeleteProperty'
x11_window.c:(.text+0xc6a): undefined reference to `XChangeWindowAttributes'
x11_window.c:(.text+0xcb0): undefined reference to `XDeleteProperty'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `updateCursorImage':
x11_window.c:(.text+0xf75): undefined reference to `XDefineCursor'
x11_window.c:(.text+0xf9b): undefined reference to `XUndefineCursor'
x11_window.c:(.text+0xfcf): undefined reference to `XDefineCursor'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `createNativeWindow':
x11_window.c:(.text+0x1037): undefined reference to `XCreateColormap'
x11_window.c:(.text+0x10e4): undefined reference to `XCreateWindow'
x11_window.c:(.text+0x1164): undefined reference to `XSaveContext'
x11_window.c:(.text+0x11db): undefined reference to `XChangeProperty'
x11_window.c:(.text+0x132d): undefined reference to `XChangeProperty'
x11_window.c:(.text+0x1382): undefined reference to `XSetWMProtocols'
x11_window.c:(.text+0x13da): undefined reference to `XChangeProperty'
x11_window.c:(.text+0x1466): undefined reference to `XChangeProperty'
x11_window.c:(.text+0x146f): undefined reference to `XAllocWMHints'
x11_window.c:(.text+0x14ea): undefined reference to `XSetWMHints'
x11_window.c:(.text+0x14f9): undefined reference to `XFree'
x11_window.c:(.text+0x1534): undefined reference to `XAllocClassHint'
x11_window.c:(.text+0x1594): undefined reference to `XSetClassHint'
x11_window.c:(.text+0x15a3): undefined reference to `XFree'
x11_window.c:(.text+0x160e): undefined reference to `XChangeProperty'
x11_window.c:(.text+0x1699): undefined reference to `XCreateIC'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `writeTargetToProperty':
x11_window.c:(.text+0x1849): undefined reference to `XChangeProperty'
x11_window.c:(.text+0x1984): undefined reference to `XChangeProperty'
x11_window.c:(.text+0x1a0b): undefined reference to `XChangeProperty'
x11_window.c:(.text+0x1a1b): undefined reference to `XFree'
x11_window.c:(.text+0x1a93): undefined reference to `XChangeProperty'
x11_window.c:(.text+0x1b3a): undefined reference to `XChangeProperty'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `handleSelectionRequest':
x11_window.c:(.text+0x1ca4): undefined reference to `XSendEvent'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `pushSelectionToManager':
x11_window.c:(.text+0x1d2a): undefined reference to `XConvertSelection'
x11_window.c:(.text+0x1da9): undefined reference to `XCheckIfEvent'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `acquireMonitor':
x11_window.c:(.text+0x1e51): undefined reference to `XGetScreenSaver'
x11_window.c:(.text+0x1e7c): undefined reference to `XSetScreenSaver'
x11_window.c:(.text+0x1f40): undefined reference to `XMoveResizeWindow'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `releaseMonitor':
x11_window.c:(.text+0x2032): undefined reference to `XSetScreenSaver'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `processEvent':
x11_window.c:(.text+0x2175): undefined reference to `XFilterEvent'
x11_window.c:(.text+0x21b8): undefined reference to `XRRUpdateConfiguration'
x11_window.c:(.text+0x2366): undefined reference to `Xutf8LookupString'
x11_window.c:(.text+0x23d0): undefined reference to `Xutf8LookupString'
x11_window.c:(.text+0x24ad): undefined reference to `XLookupString'
x11_window.c:(.text+0x257c): undefined reference to `XEventsQueued'
x11_window.c:(.text+0x25a0): undefined reference to `XPeekEvent'
x11_window.c:(.text+0x2ced): undefined reference to `XSendEvent'
x11_window.c:(.text+0x2da5): undefined reference to `XConvertSelection'
x11_window.c:(.text+0x2f32): undefined reference to `XSendEvent'
x11_window.c:(.text+0x2f48): undefined reference to `XFlush'
x11_window.c:(.text+0x3046): undefined reference to `XFree'
x11_window.c:(.text+0x310e): undefined reference to `XSendEvent'
x11_window.c:(.text+0x3124): undefined reference to `XFlush'
x11_window.c:(.text+0x319d): undefined reference to `XSetICFocus'
x11_window.c:(.text+0x322a): undefined reference to `XUnsetICFocus'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwGetWindowPropertyX11':
x11_window.c:(.text+0x3420): undefined reference to `XGetWindowProperty'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformCreateWindow':
x11_window.c:(.text+0x3652): undefined reference to `XFlush'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformDestroyWindow':
x11_window.c:(.text+0x36db): undefined reference to `XDestroyIC'
x11_window.c:(.text+0x3749): undefined reference to `XGetSelectionOwner'
x11_window.c:(.text+0x3799): undefined reference to `XDeleteContext'
x11_window.c:(.text+0x37bd): undefined reference to `XUnmapWindow'
x11_window.c:(.text+0x37e1): undefined reference to `XDestroyWindow'
x11_window.c:(.text+0x3824): undefined reference to `XFreeColormap'
x11_window.c:(.text+0x3849): undefined reference to `XFlush'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformSetWindowTitle':
x11_window.c:(.text+0x389b): undefined reference to `Xutf8SetWMProperties'
x11_window.c:(.text+0x38fa): undefined reference to `XChangeProperty'
x11_window.c:(.text+0x3959): undefined reference to `XChangeProperty'
x11_window.c:(.text+0x3973): undefined reference to `XFlush'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformSetWindowIcon':
x11_window.c:(.text+0x3bd3): undefined reference to `XChangeProperty'
x11_window.c:(.text+0x3c17): undefined reference to `XDeleteProperty'
x11_window.c:(.text+0x3c2d): undefined reference to `XFlush'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformGetWindowPos':
x11_window.c:(.text+0x3c9e): undefined reference to `XTranslateCoordinates'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformSetWindowPos':
x11_window.c:(.text+0x3d13): undefined reference to `XAllocSizeHints'
x11_window.c:(.text+0x3d40): undefined reference to `XGetWMNormalHints'
x11_window.c:(.text+0x3d9a): undefined reference to `XSetWMNormalHints'
x11_window.c:(.text+0x3da6): undefined reference to `XFree'
x11_window.c:(.text+0x3dcd): undefined reference to `XMoveWindow'
x11_window.c:(.text+0x3de3): undefined reference to `XFlush'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformGetWindowSize':
x11_window.c:(.text+0x3e57): undefined reference to `XGetWindowAttributes'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformSetWindowSize':
x11_window.c:(.text+0x3f25): undefined reference to `XResizeWindow'
x11_window.c:(.text+0x3f3b): undefined reference to `XFlush'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformSetWindowSizeLimits':
x11_window.c:(.text+0x3fa7): undefined reference to `XFlush'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformSetWindowAspectRatio':
x11_window.c:(.text+0x4020): undefined reference to `XFlush'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformGetWindowFrameSize':
x11_window.c:(.text+0x41c3): undefined reference to `XCheckIfEvent'
x11_window.c:(.text+0x42a7): undefined reference to `XFree'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformIconifyWindow':
x11_window.c:(.text+0x4326): undefined reference to `XIconifyWindow'
x11_window.c:(.text+0x433c): undefined reference to `XFlush'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformRestoreWindow':
x11_window.c:(.text+0x43a7): undefined reference to `XMapWindow'
x11_window.c:(.text+0x4472): undefined reference to `XFlush'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformMaximizeWindow':
x11_window.c:(.text+0x452e): undefined reference to `XFlush'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformShowWindow':
x11_window.c:(.text+0x4571): undefined reference to `XMapWindow'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformHideWindow':
x11_window.c:(.text+0x45b2): undefined reference to `XUnmapWindow'
x11_window.c:(.text+0x45c8): undefined reference to `XFlush'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformFocusWindow':
x11_window.c:(.text+0x464a): undefined reference to `XRaiseWindow'
x11_window.c:(.text+0x4675): undefined reference to `XSetInputFocus'
x11_window.c:(.text+0x468b): undefined reference to `XFlush'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformSetWindowMonitor':
x11_window.c:(.text+0x4718): undefined reference to `XMoveResizeWindow'
x11_window.c:(.text+0x479a): undefined reference to `XMapRaised'
x11_window.c:(.text+0x47ec): undefined reference to `XMoveResizeWindow'
x11_window.c:(.text+0x4802): undefined reference to `XFlush'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformWindowFocused':
x11_window.c:(.text+0x4843): undefined reference to `XGetInputFocus'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformWindowVisible':
x11_window.c:(.text+0x48e3): undefined reference to `XGetWindowAttributes'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformWindowMaximized':
x11_window.c:(.text+0x49d0): undefined reference to `XFree'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformPollEvents':
x11_window.c:(.text+0x4a1e): undefined reference to `XPending'
x11_window.c:(.text+0x4a46): undefined reference to `XNextEvent'
x11_window.c:(.text+0x4aa7): undefined reference to `XFlush'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformWaitEvents':
x11_window.c:(.text+0x4ae4): undefined reference to `XPending'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformWaitEventsTimeout':
x11_window.c:(.text+0x4b25): undefined reference to `XPending'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformPostEmptyEvent':
x11_window.c:(.text+0x4bf2): undefined reference to `XSendEvent'
x11_window.c:(.text+0x4c08): undefined reference to `XFlush'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformGetCursorPos':
x11_window.c:(.text+0x4c86): undefined reference to `XQueryPointer'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformSetCursorPos':
x11_window.c:(.text+0x4d62): undefined reference to `XWarpPointer'
x11_window.c:(.text+0x4d7c): undefined reference to `XFlush'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformSetCursorMode':
x11_window.c:(.text+0x4e39): undefined reference to `XGrabPointer'
x11_window.c:(.text+0x4e80): undefined reference to `XUngrabPointer'
x11_window.c:(.text+0x4ed8): undefined reference to `XFlush'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformGetKeyName':
x11_window.c:(.text+0x4f89): undefined reference to `XkbKeycodeToKeysym'
x11_window.c:(.text+0x4fd7): undefined reference to `XkbTranslateKeySym'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformCreateStandardCursor':
x11_window.c:(.text+0x509a): undefined reference to `XCreateFontCursor'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformDestroyCursor':
x11_window.c:(.text+0x5110): undefined reference to `XFreeCursor'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformSetCursor':
x11_window.c:(.text+0x5153): undefined reference to `XFlush'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformSetClipboardString':
x11_window.c:(.text+0x51cd): undefined reference to `XSetSelectionOwner'
x11_window.c:(.text+0x51f4): undefined reference to `XGetSelectionOwner'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformGetClipboardString':
x11_window.c:(.text+0x52a8): undefined reference to `XGetSelectionOwner'
x11_window.c:(.text+0x5358): undefined reference to `XConvertSelection'
x11_window.c:(.text+0x5386): undefined reference to `XCheckTypedEvent'
x11_window.c:(.text+0x53f2): undefined reference to `XFree'
x11_window.c:(.text+0x5419): undefined reference to `XDeleteProperty'
/opt/glfw-3.2.1/src/libglfw3.a(x11_window.c.o): In function `_glfwPlatformGetPhysicalDevicePresentationSupport':
x11_window.c:(.text+0x55cd): undefined reference to `XVisualIDFromVisual'
/opt/glfw-3.2.1/src/libglfw3.a(posix_tls.c.o): In function `_glfwInitThreadLocalStoragePOSIX':
posix_tls.c:(.text+0x18): undefined reference to `pthread_key_create'
/opt/glfw-3.2.1/src/libglfw3.a(posix_tls.c.o): In function `_glfwTerminateThreadLocalStoragePOSIX':
posix_tls.c:(.text+0x7a): undefined reference to `pthread_key_delete'
/opt/glfw-3.2.1/src/libglfw3.a(posix_tls.c.o): In function `_glfwPlatformSetCurrentContext':
posix_tls.c:(.text+0xa4): undefined reference to `pthread_setspecific'
/opt/glfw-3.2.1/src/libglfw3.a(posix_tls.c.o): In function `_glfwPlatformGetCurrentContext':
posix_tls.c:(.text+0xbf): undefined reference to `pthread_getspecific'
/opt/glfw-3.2.1/src/libglfw3.a(glx_context.c.o): In function `chooseGLXFBConfig':
glx_context.c:(.text+0x3f4): undefined reference to `XFree'
/opt/glfw-3.2.1/src/libglfw3.a(glx_context.c.o): In function `getProcAddressGLX':
glx_context.c:(.text+0x6fe): undefined reference to `dlsym'
/opt/glfw-3.2.1/src/libglfw3.a(glx_context.c.o): In function `_glfwInitGLX':
glx_context.c:(.text+0x81d): undefined reference to `dlopen'
glx_context.c:(.text+0x8a7): undefined reference to `dlsym'
glx_context.c:(.text+0x8d5): undefined reference to `dlsym'
glx_context.c:(.text+0x903): undefined reference to `dlsym'
glx_context.c:(.text+0x931): undefined reference to `dlsym'
glx_context.c:(.text+0x95f): undefined reference to `dlsym'
/opt/glfw-3.2.1/src/libglfw3.a(glx_context.c.o):glx_context.c:(.text+0x98d): more undefined references to `dlsym' follow
/opt/glfw-3.2.1/src/libglfw3.a(glx_context.c.o): In function `_glfwTerminateGLX':
glx_context.c:(.text+0x1012): undefined reference to `dlclose'
/opt/glfw-3.2.1/src/libglfw3.a(glx_context.c.o): In function `_glfwChooseVisualGLX':
glx_context.c:(.text+0x1a12): undefined reference to `XFree'
/opt/glfw-3.2.1/src/libglfw3.a(egl_context.c.o): In function `getProcAddressEGL':
egl_context.c:(.text+0x6a1): undefined reference to `dlsym'
/opt/glfw-3.2.1/src/libglfw3.a(egl_context.c.o): In function `destroyContextEGL':
egl_context.c:(.text+0x70b): undefined reference to `dlclose'
/opt/glfw-3.2.1/src/libglfw3.a(egl_context.c.o): In function `_glfwInitEGL':
egl_context.c:(.text+0x820): undefined reference to `dlopen'
egl_context.c:(.text+0x8dd): undefined reference to `dlsym'
egl_context.c:(.text+0x90b): undefined reference to `dlsym'
egl_context.c:(.text+0x939): undefined reference to `dlsym'
egl_context.c:(.text+0x967): undefined reference to `dlsym'
egl_context.c:(.text+0x995): undefined reference to `dlsym'
/opt/glfw-3.2.1/src/libglfw3.a(egl_context.c.o):egl_context.c:(.text+0x9c3): more undefined references to `dlsym' follow
/opt/glfw-3.2.1/src/libglfw3.a(egl_context.c.o): In function `_glfwTerminateEGL':
egl_context.c:(.text+0xef9): undefined reference to `dlclose'
/opt/glfw-3.2.1/src/libglfw3.a(egl_context.c.o): In function `_glfwCreateContextEGL':
egl_context.c:(.text+0x18d7): undefined reference to `dlopen'
/opt/glfw-3.2.1/src/libglfw3.a(egl_context.c.o): In function `_glfwChooseVisualEGL':
egl_context.c:(.text+0x1aec): undefined reference to `XGetVisualInfo'
egl_context.c:(.text+0x1b41): undefined reference to `XFree'
collect2: error: ld returned 1 exit status
make: *** [OpenGL_Test] Error 1



```


My simple code is:

```

#define GLEW_STATIC


#include <iostream>
#include <GL/glew.h>
#include <GLFW/glfw3.h>




int main(int argc, char **argv){


	glfwInit();


	return 0;


}

```

---

### Post by steeldriver on 2016-11-15
I suspect it's a matter of link order

---

