---
title: "problem running winows executabe on ubuntu 12.04 with mono 2.10.8.1"
date: 2013-06-09
forum: General Help
---

### Post by msousa on 2013-06-09
Hi

I'm trying to run a windows executable on ubuntu 12.04 with mono 2.10.8.1 and am getting an exception. I'll only post the top of the stacktrace so as not to add too much clutter:

X11 Error encountered:
  Error: BadRequest (invalid request code or no such operation)
  Request:     153 (19)
  Resource ID: 0x52
  Serial:      17
  Hwnd:        Hwnd, Mapped:False ClientWindow:0x52, WholeWindow:0x52, Zombie=False, Parent:[<null>]
  Control:     <handle 52 non-existant>   at System.Environment.get_StackTrace()
   at System.Windows.Forms.XplatUIX11.HandleError(IntPtr display, XErrorEvent ByRef error_event)
   at OpenTK.Platform.X11.Glx.ChooseFBConfig(IntPtr , Int32 , System.Int32[] , Int32 ByRef )
   at OpenTK.Platform.X11.X11GraphicsMode.SelectVisualUsingFBConfig(ColorFormat color, Int32 depth, Int32 stencil, Int32 samples, ColorFormat accum, Int32 buffers, Boolean stereo)
   at OpenTK.Platform.X11.X11GraphicsMode.SelectGraphicsMode(ColorFormat color, Int32 depth, Int32 stencil, Int32 samples, ColorFormat accum, Int32 buffers, Boolean stereo)


There's a bunch more to the stack I could post if necessary. The executable I attempt to run with mono is:
$ mono ArdupilotMegaPlanner10.exe

Any idea how to go about fixing this? I've tried looking for anything missing so far everthing I've installe has not helped.
Thanks...

---

### Post by ahallubuntu on 2013-06-09
~

---

### Post by QIII on 2013-06-09
msousa is running mono, which means he is trying to run a .NET project and not Wine.

;)

mono is a version of Microsoft's .NET CLR.  With mono installed, .NET exes will run natively on Linux.

---

### Post by msousa on 2013-06-09
QIII, I have mono 2.10.8.1 installed and when I attempt the following:

$ mono ArdupilotMegaPlanner10.exe

I get the stack trace presented in my original question.

Here's some output from mono:
$ mono -V
Mono JIT compiler version 2.10.8.1 (Debian 2.10.8.1-1ubuntu2.2)
Copyright (C) 2002-2011 Novell, Inc, Xamarin, Inc and Contributors. [www.mono-project.com](www.mono-project.com)


I feel like I'm still missing something.
One more bit on info, before the errors, the splash of the executable I'm trying to run comes up for a brief moment.

---

### Post by QIII on 2013-06-09
I understood you were using mono, just didn't think the other poster did.

Where does the stack trace start?  Should be down towards the bottom.

Could you post the whole thing (between code tags)?

---

### Post by msousa on 2013-06-09
QIII, do you want the [INFO] line also? It's quite a bit if stuff.

---

### Post by QIII on 2013-06-09
What is really the most telling is probably the starting point where the exception is thrown.

So at least the first few items at the bottom.

Not sure it will provide anything obvious, but it will at least provide a place to start looking.

---

### Post by msousa on 2013-06-09
I made it smaller by just redirecting stderr to the output file, so here it is.

```

Stacktrace:

  at (wrapper managed-to-native) OpenTK.Platform.X11.Glx.ChooseFBConfig (intptr,int,int[],int&) <0xffffffff>
  at OpenTK.Platform.X11.X11GraphicsMode.SelectVisualUsingFBConfig (OpenTK.Graphics.ColorFormat,int,int,int,OpenTK.Graphics.ColorFormat,int,bool) <0x0038f>
  at OpenTK.Platform.X11.X11GraphicsMode.SelectGraphicsMode (OpenTK.Graphics.ColorFormat,int,int,int,OpenTK.Graphics.ColorFormat,int,bool) <0x0010f>
  at OpenTK.Graphics.GraphicsMode.LazySelectGraphicsMode () <0x0009b>
  at OpenTK.Graphics.GraphicsMode.get_Index () <0x00017>
  at OpenTK.X11GLControl..ctor (OpenTK.Graphics.GraphicsMode,System.Windows.Forms.Control) <0x000a7>
  at OpenTK.GLControlFactory.CreateGLControl (OpenTK.Graphics.GraphicsMode,System.Windows.Forms.Control) <0x00133>
  at OpenTK.GLControl.OnHandleCreated (System.EventArgs) <0x00107>
  at ArdupilotMega.Controls.HUD.OnHandleCreated (System.EventArgs) <0x0003f>
  at System.Windows.Forms.Control.WmCreate (System.Windows.Forms.Message&) <0x0001d>
  at System.Windows.Forms.Control.WndProc (System.Windows.Forms.Message&) <0x002d7>
  at System.Windows.Forms.ScrollableControl.WndProc (System.Windows.Forms.Message&) <0x00013>
  at System.Windows.Forms.ContainerControl.WndProc (System.Windows.Forms.Message&) <0x0005b>
  at System.Windows.Forms.UserControl.WndProc (System.Windows.Forms.Message&) <0x0006b>
  at System.Windows.Forms.Control/ControlWindowTarget.OnMessage (System.Windows.Forms.Message&) <0x00024>
  at System.Windows.Forms.Control/ControlNativeWindow.WndProc (System.Windows.Forms.Message&) <0x00036>
  at System.Windows.Forms.NativeWindow.WndProc (intptr,System.Windows.Forms.Msg,intptr,intptr) <0x002f0>
  at System.Windows.Forms.XplatUIX11.SendMessage (intptr,System.Windows.Forms.Msg,intptr,intptr) <0x00313>
  at System.Windows.Forms.XplatUIX11.CreateWindow (System.Windows.Forms.CreateParams) <0x00ce4>
  at System.Windows.Forms.XplatUI.CreateWindow (System.Windows.Forms.CreateParams) <0x00024>
  at System.Windows.Forms.NativeWindow.CreateHandle (System.Windows.Forms.CreateParams) <0x0003f>
  at System.Windows.Forms.Control.CreateHandle () <0x00069>
  at System.Windows.Forms.Control.CreateControl () <0x00087>
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.Control.CreateControl () <0xffffffff>
  at System.Windows.Forms.Control.CreateControl () <0x0010f>
  at System.Windows.Forms.Control.WmShowWindow (System.Windows.Forms.Message&) <0x00193>
  at System.Windows.Forms.Control.WndProc (System.Windows.Forms.Message&) <0x002c7>
  at System.Windows.Forms.ScrollableControl.WndProc (System.Windows.Forms.Message&) <0x00013>
  at System.Windows.Forms.Control/ControlWindowTarget.OnMessage (System.Windows.Forms.Message&) <0x00024>
  at System.Windows.Forms.Control/ControlNativeWindow.WndProc (System.Windows.Forms.Message&) <0x00036>
  at System.Windows.Forms.NativeWindow.WndProc (intptr,System.Windows.Forms.Msg,intptr,intptr) <0x002f0>
  at System.Windows.Forms.XplatUIX11.SendMessage (intptr,System.Windows.Forms.Msg,intptr,intptr) <0x00313>
  at System.Windows.Forms.XplatUIX11.CreateWindow (System.Windows.Forms.CreateParams) <0x00eec>
  at System.Windows.Forms.XplatUI.CreateWindow (System.Windows.Forms.CreateParams) <0x00024>
  at System.Windows.Forms.NativeWindow.CreateHandle (System.Windows.Forms.CreateParams) <0x0003f>
  at System.Windows.Forms.Control.CreateHandle () <0x00069>
  at System.Windows.Forms.Control.CreateControl () <0x00087>
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.Control.CreateControl () <0xffffffff>
  at System.Windows.Forms.Control.CreateControl () <0x0010f>
  at System.Windows.Forms.Control.WmShowWindow (System.Windows.Forms.Message&) <0x00193>
  at System.Windows.Forms.Control.WndProc (System.Windows.Forms.Message&) <0x002c7>
  at System.Windows.Forms.ScrollableControl.WndProc (System.Windows.Forms.Message&) <0x00013>
  at System.Windows.Forms.ContainerControl.WndProc (System.Windows.Forms.Message&) <0x0005b>
  at System.Windows.Forms.SplitContainer.WndProc (System.Windows.Forms.Message&) <0x00013>
  at System.Windows.Forms.Control/ControlWindowTarget.OnMessage (System.Windows.Forms.Message&) <0x00024>
  at System.Windows.Forms.Control/ControlNativeWindow.WndProc (System.Windows.Forms.Message&) <0x00036>
  at System.Windows.Forms.NativeWindow.WndProc (intptr,System.Windows.Forms.Msg,intptr,intptr) <0x002f0>
  at System.Windows.Forms.XplatUIX11.SendMessage (intptr,System.Windows.Forms.Msg,intptr,intptr) <0x00313>
  at System.Windows.Forms.XplatUIX11.CreateWindow (System.Windows.Forms.CreateParams) <0x00eec>
  at System.Windows.Forms.XplatUI.CreateWindow (System.Windows.Forms.CreateParams) <0x00024>
  at System.Windows.Forms.NativeWindow.CreateHandle (System.Windows.Forms.CreateParams) <0x0003f>
  at System.Windows.Forms.Control.CreateHandle () <0x00069>
  at System.Windows.Forms.Control.CreateControl () <0x00087>
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.Control.CreateControl () <0xffffffff>
  at System.Windows.Forms.Control.CreateControl () <0x0010f>
  at System.Windows.Forms.Control.WmShowWindow (System.Windows.Forms.Message&) <0x00193>
  at System.Windows.Forms.Control.WndProc (System.Windows.Forms.Message&) <0x002c7>
  at System.Windows.Forms.ScrollableControl.WndProc (System.Windows.Forms.Message&) <0x00013>
  at System.Windows.Forms.Control/ControlWindowTarget.OnMessage (System.Windows.Forms.Message&) <0x00024>
  at System.Windows.Forms.Control/ControlNativeWindow.WndProc (System.Windows.Forms.Message&) <0x00036>
  at System.Windows.Forms.NativeWindow.WndProc (intptr,System.Windows.Forms.Msg,intptr,intptr) <0x002f0>
  at System.Windows.Forms.XplatUIX11.SendMessage (intptr,System.Windows.Forms.Msg,intptr,intptr) <0x00313>
  at System.Windows.Forms.XplatUIX11.CreateWindow (System.Windows.Forms.CreateParams) <0x00eec>
  at System.Windows.Forms.XplatUI.CreateWindow (System.Windows.Forms.CreateParams) <0x00024>
  at System.Windows.Forms.NativeWindow.CreateHandle (System.Windows.Forms.CreateParams) <0x0003f>
  at System.Windows.Forms.Control.CreateHandle () <0x00069>
  at System.Windows.Forms.Control.CreateControl () <0x00087>
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.Control.CreateControl () <0xffffffff>
  at System.Windows.Forms.Control.CreateControl () <0x0010f>
  at System.Windows.Forms.Control.WmShowWindow (System.Windows.Forms.Message&) <0x00193>
  at System.Windows.Forms.Control.WndProc (System.Windows.Forms.Message&) <0x002c7>
  at System.Windows.Forms.ScrollableControl.WndProc (System.Windows.Forms.Message&) <0x00013>
  at System.Windows.Forms.ContainerControl.WndProc (System.Windows.Forms.Message&) <0x0005b>
  at System.Windows.Forms.SplitContainer.WndProc (System.Windows.Forms.Message&) <0x00013>
  at System.Windows.Forms.Control/ControlWindowTarget.OnMessage (System.Windows.Forms.Message&) <0x00024>
  at System.Windows.Forms.Control/ControlNativeWindow.WndProc (System.Windows.Forms.Message&) <0x00036>
  at System.Windows.Forms.NativeWindow.WndProc (intptr,System.Windows.Forms.Msg,intptr,intptr) <0x002f0>
  at System.Windows.Forms.XplatUIX11.SendMessage (intptr,System.Windows.Forms.Msg,intptr,intptr) <0x00313>
  at System.Windows.Forms.XplatUIX11.CreateWindow (System.Windows.Forms.CreateParams) <0x00eec>
  at System.Windows.Forms.XplatUI.CreateWindow (System.Windows.Forms.CreateParams) <0x00024>
  at System.Windows.Forms.NativeWindow.CreateHandle (System.Windows.Forms.CreateParams) <0x0003f>
  at System.Windows.Forms.Control.CreateHandle () <0x00069>
  at System.Windows.Forms.Control.CreateControl () <0x00087>
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.Control.CreateControl () <0xffffffff>
  at System.Windows.Forms.Control.CreateControl () <0x0010f>
  at System.Windows.Forms.Control.WmShowWindow (System.Windows.Forms.Message&) <0x00193>
  at System.Windows.Forms.Control.WndProc (System.Windows.Forms.Message&) <0x002c7>
  at System.Windows.Forms.ScrollableControl.WndProc (System.Windows.Forms.Message&) <0x00013>
  at System.Windows.Forms.ContainerControl.WndProc (System.Windows.Forms.Message&) <0x0005b>
  at System.Windows.Forms.UserControl.WndProc (System.Windows.Forms.Message&) <0x0006b>
  at System.Windows.Forms.MyUserControl.WndProc (System.Windows.Forms.Message&) <0x00017>
  at System.Windows.Forms.Control/ControlWindowTarget.OnMessage (System.Windows.Forms.Message&) <0x00024>
  at System.Windows.Forms.Control/ControlNativeWindow.WndProc (System.Windows.Forms.Message&) <0x00036>
  at System.Windows.Forms.NativeWindow.WndProc (intptr,System.Windows.Forms.Msg,intptr,intptr) <0x002f0>
  at System.Windows.Forms.XplatUIX11.SendMessage (intptr,System.Windows.Forms.Msg,intptr,intptr) <0x00313>
  at System.Windows.Forms.XplatUIX11.CreateWindow (System.Windows.Forms.CreateParams) <0x00eec>
  at System.Windows.Forms.XplatUI.CreateWindow (System.Windows.Forms.CreateParams) <0x00024>
  at System.Windows.Forms.NativeWindow.CreateHandle (System.Windows.Forms.CreateParams) <0x0003f>
  at System.Windows.Forms.Control.CreateHandle () <0x00069>
  at System.Windows.Forms.Control.CreateControl () <0x00087>
  at System.Windows.Forms.Control.SetVisibleCore (bool) <0x0009f>
  at System.Windows.Forms.Control.set_Visible (bool) <0x00032>
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.Control.set_Visible (bool) <0xffffffff>
  at ArdupilotMega.Controls.MainSwitcher/Screen.set_Visible (bool) <0x00023>
  at ArdupilotMega.Controls.MainSwitcher.ShowScreen (string) <0x00423>
  at ArdupilotMega.MainV2.MenuFlightData_Click (object,System.EventArgs) <0x00027>
  at ArdupilotMega.MainV2.MainV2_Load (object,System.EventArgs) <0x004cb>
  at System.Windows.Forms.Form.OnLoad (System.EventArgs) <0x00075>
  at System.Windows.Forms.Form.OnLoadInternal (System.EventArgs) <0x0007f>
  at System.Windows.Forms.Form.OnCreateControl () <0x00053>
  at System.Windows.Forms.Control.CreateControl () <0x00127>
  at System.Windows.Forms.Control.WmShowWindow (System.Windows.Forms.Message&) <0x00193>
  at System.Windows.Forms.Control.WndProc (System.Windows.Forms.Message&) <0x002c7>
  at System.Windows.Forms.ScrollableControl.WndProc (System.Windows.Forms.Message&) <0x00013>
  at System.Windows.Forms.ContainerControl.WndProc (System.Windows.Forms.Message&) <0x0005b>
  at System.Windows.Forms.Form.WndProc (System.Windows.Forms.Message&) <0x0024f>
  at ArdupilotMega.MainV2.WndProc (System.Windows.Forms.Message&) <0x0015f>
  at System.Windows.Forms.Control/ControlWindowTarget.OnMessage (System.Windows.Forms.Message&) <0x00024>
  at System.Windows.Forms.Control/ControlNativeWindow.WndProc (System.Windows.Forms.Message&) <0x00036>
  at System.Windows.Forms.NativeWindow.WndProc (intptr,System.Windows.Forms.Msg,intptr,intptr) <0x002f0>
  at System.Windows.Forms.XplatUIX11.SendMessage (intptr,System.Windows.Forms.Msg,intptr,intptr) <0x00313>
  at System.Windows.Forms.XplatUIX11.MapWindow (System.Windows.Forms.Hwnd,System.Windows.Forms.WindowType) <0x001fb>
  at System.Windows.Forms.XplatUIX11.CreateWindow (System.Windows.Forms.CreateParams) <0x00d53>
  at System.Windows.Forms.XplatUI.CreateWindow (System.Windows.Forms.CreateParams) <0x00024>
  at System.Windows.Forms.NativeWindow.CreateHandle (System.Windows.Forms.CreateParams) <0x0003f>
  at System.Windows.Forms.Control.CreateHandle () <0x00069>
  at System.Windows.Forms.Form.CreateHandle () <0x0001b>
  at System.Windows.Forms.Control.CreateControl () <0x00087>
  at System.Windows.Forms.Control.SetVisibleCore (bool) <0x0009f>
  at System.Windows.Forms.Form.SetVisibleCore (bool) <0x002ef>
  at System.Windows.Forms.Control.set_Visible (bool) <0x00032>
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.Control.set_Visible (bool) <0xffffffff>
  at System.Windows.Forms.Application.RunLoop (bool,System.Windows.Forms.ApplicationContext) <0x002cf>
  at System.Windows.Forms.Application.Run (System.Windows.Forms.ApplicationContext) <0x0005f>
  at System.Windows.Forms.Application.Run (System.Windows.Forms.Form) <0x00033>
  at ArdupilotMega.Program.Main () <0x003f3>
  at (wrapper runtime-invoke) object.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

    mono() [0x4916ba]
    mono() [0x4e0d4f]
    mono() [0x41bc77]
    /lib/x86_64-linux-gnu/libpthread.so.0(+0xfcb0) [0x7f00cccb9cb0]
    /usr/lib/fglrx/libGL.so.1(glXGetFBConfigs+0x2e) [0x7f0095d944ce]
    /usr/lib/fglrx/libGL.so.1(+0x3814a) [0x7f0095d9514a]
    /usr/lib/fglrx/libGL.so.1(glXChooseFBConfig+0x49) [0x7f0095d953a9]
    [0x409f6718]

Debug info from gdb:

[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
[New Thread 0x7f00975f9700 (LWP 2841)]
[New Thread 0x7f00ad671700 (LWP 2839)]
[New Thread 0x7f00ad6b2700 (LWP 2838)]
[New Thread 0x7f00b4226700 (LWP 2836)]
[New Thread 0x7f00b4267700 (LWP 2835)]
[New Thread 0x7f00bee3c700 (LWP 2833)]
[New Thread 0x7f00bf86e700 (LWP 2831)]
[New Thread 0x7f00caeaf700 (LWP 2830)]
[New Thread 0x7f00cc207700 (LWP 2829)]
0x00007f00cccb8d2d in read () from /lib/x86_64-linux-gnu/libpthread.so.0
  Id   Target Id         Frame 
  10   Thread 0x7f00cc207700 (LWP 2829) "mono" 0x00007f00cccb5d84 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/x86_64-linux-gnu/libpthread.so.0
  9    Thread 0x7f00caeaf700 (LWP 2830) "mono" 0x00007f00cccb7fd0 in sem_wait () from /lib/x86_64-linux-gnu/libpthread.so.0
  8    Thread 0x7f00bf86e700 (LWP 2831) "dconf worker" 0x00007f00cc9d3313 in poll () from /lib/x86_64-linux-gnu/libc.so.6
  7    Thread 0x7f00bee3c700 (LWP 2833) "gdbus" 0x00007f00cc9d3313 in poll () from /lib/x86_64-linux-gnu/libc.so.6
  6    Thread 0x7f00b4267700 (LWP 2835) "mono" 0x00007f00cccb952d in nanosleep () from /lib/x86_64-linux-gnu/libpthread.so.0
  5    Thread 0x7f00b4226700 (LWP 2836) "mono" 0x00007f00cccb80c1 in sem_timedwait () from /lib/x86_64-linux-gnu/libpthread.so.0
  4    Thread 0x7f00ad6b2700 (LWP 2838) "mono" 0x00007f00cc9df363 in epoll_wait () from /lib/x86_64-linux-gnu/libc.so.6
  3    Thread 0x7f00ad671700 (LWP 2839) "mono" 0x00007f00cccb80c1 in sem_timedwait () from /lib/x86_64-linux-gnu/libpthread.so.0
  2    Thread 0x7f00975f9700 (LWP 2841) "mono" 0x00007f00cccb80c1 in sem_timedwait () from /lib/x86_64-linux-gnu/libpthread.so.0
* 1    Thread 0x7f00cd7cc740 (LWP 2828) "mono" 0x00007f00cccb8d2d in read () from /lib/x86_64-linux-gnu/libpthread.so.0

Thread 10 (Thread 0x7f00cc207700 (LWP 2829)):
#0  0x00007f00cccb5d84 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/x86_64-linux-gnu/libpthread.so.0
#1  0x00000000005dce33 in ?? ()
#2  0x00000000005d70dc in ?? ()
#3  0x00000000005db577 in ?? ()
#4  0x00007f00cccb1e9a in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#5  0x00007f00cc9deccd in clone () from /lib/x86_64-linux-gnu/libc.so.6
#6  0x0000000000000000 in ?? ()

Thread 9 (Thread 0x7f00caeaf700 (LWP 2830)):
#0  0x00007f00cccb7fd0 in sem_wait () from /lib/x86_64-linux-gnu/libpthread.so.0
#1  0x00000000005c1e48 in mono_sem_wait ()
#2  0x000000000050ff9b in ?? ()
#3  0x0000000000592727 in ?? ()
#4  0x00000000005bc832 in ?? ()
#5  0x00000000005dcc1d in ?? ()
#6  0x00007f00cccb1e9a in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#7  0x00007f00cc9deccd in clone () from /lib/x86_64-linux-gnu/libc.so.6
#8  0x0000000000000000 in ?? ()

Thread 8 (Thread 0x7f00bf86e700 (LWP 2831)):
#0  0x00007f00cc9d3313 in poll () from /lib/x86_64-linux-gnu/libc.so.6
#1  0x00007f00c9279036 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x00007f00c927949a in g_main_loop_run () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#3  0x00007f00bf87398b in ?? () from /usr/lib/x86_64-linux-gnu/gio/modules/libdconfsettings.so
#4  0x00007f00c929a9e5 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#5  0x00007f00cccb1e9a in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#6  0x00007f00cc9deccd in clone () from /lib/x86_64-linux-gnu/libc.so.6
#7  0x0000000000000000 in ?? ()

Thread 7 (Thread 0x7f00bee3c700 (LWP 2833)):
#0  0x00007f00cc9d3313 in poll () from /lib/x86_64-linux-gnu/libc.so.6
#1  0x00007f00c9279036 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x00007f00c927949a in g_main_loop_run () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#3  0x00007f00c1ab9406 in ?? () from /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0
#4  0x00007f00c929a9e5 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#5  0x00007f00cccb1e9a in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#6  0x00007f00cc9deccd in clone () from /lib/x86_64-linux-gnu/libc.so.6
#7  0x0000000000000000 in ?? ()

Thread 6 (Thread 0x7f00b4267700 (LWP 2835)):
#0  0x00007f00cccb952d in nanosleep () from /lib/x86_64-linux-gnu/libpthread.so.0
#1  0x00000000005bbbb6 in ?? ()
#2  0x0000000000589488 in ?? ()
#3  0x0000000000592727 in ?? ()
#4  0x00000000005bc832 in ?? ()
#5  0x00000000005dcc1d in ?? ()
#6  0x00007f00cccb1e9a in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#7  0x00007f00cc9deccd in clone () from /lib/x86_64-linux-gnu/libc.so.6
#8  0x0000000000000000 in ?? ()

Thread 5 (Thread 0x7f00b4226700 (LWP 2836)):
#0  0x00007f00cccb80c1 in sem_timedwait () from /lib/x86_64-linux-gnu/libpthread.so.0
#1  0x00000000005c1f3b in mono_sem_timedwait ()
#2  0x000000000058b93f in ?? ()
#3  0x0000000000592727 in ?? ()
#4  0x00000000005bc832 in ?? ()
#5  0x00000000005dcc1d in ?? ()
#6  0x00007f00cccb1e9a in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#7  0x00007f00cc9deccd in clone () from /lib/x86_64-linux-gnu/libc.so.6
#8  0x0000000000000000 in ?? ()

Thread 4 (Thread 0x7f00ad6b2700 (LWP 2838)):
#0  0x00007f00cc9df363 in epoll_wait () from /lib/x86_64-linux-gnu/libc.so.6
#1  0x0000000000589eb8 in ?? ()
#2  0x0000000000592727 in ?? ()
#3  0x00000000005bc832 in ?? ()
#4  0x00000000005dcc1d in ?? ()
#5  0x00007f00cccb1e9a in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#6  0x00007f00cc9deccd in clone () from /lib/x86_64-linux-gnu/libc.so.6
#7  0x0000000000000000 in ?? ()

Thread 3 (Thread 0x7f00ad671700 (LWP 2839)):
#0  0x00007f00cccb80c1 in sem_timedwait () from /lib/x86_64-linux-gnu/libpthread.so.0
#1  0x00000000005c1f3b in mono_sem_timedwait ()
#2  0x000000000058b93f in ?? ()
#3  0x0000000000592727 in ?? ()
#4  0x00000000005bc832 in ?? ()
#5  0x00000000005dcc1d in ?? ()
#6  0x00007f00cccb1e9a in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#7  0x00007f00cc9deccd in clone () from /lib/x86_64-linux-gnu/libc.so.6
#8  0x0000000000000000 in ?? ()

Thread 2 (Thread 0x7f00975f9700 (LWP 2841)):
#0  0x00007f00cccb80c1 in sem_timedwait () from /lib/x86_64-linux-gnu/libpthread.so.0
#1  0x00000000005c1f3b in mono_sem_timedwait ()
#2  0x000000000058b93f in ?? ()
#3  0x0000000000592727 in ?? ()
#4  0x00000000005bc832 in ?? ()
#5  0x00000000005dcc1d in ?? ()
#6  0x00007f00cccb1e9a in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#7  0x00007f00cc9deccd in clone () from /lib/x86_64-linux-gnu/libc.so.6
#8  0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7f00cd7cc740 (LWP 2828)):
#0  0x00007f00cccb8d2d in read () from /lib/x86_64-linux-gnu/libpthread.so.0
#1  0x000000000049185e in ?? ()
#2  0x00000000004e0d4f in ?? ()
#3  0x000000000041bc77 in ?? ()
#4  <signal handler called>
#5  0x00007f0095d944ce in glXGetFBConfigs () from /usr/lib/fglrx/libGL.so.1
#6  0x00007f0095d9514a in ?? () from /usr/lib/fglrx/libGL.so.1
#7  0x00007f0095d953a9 in glXChooseFBConfigSGIX () from /usr/lib/fglrx/libGL.so.1
#8  0x00000000409f6718 in ?? ()
#9  0x0000000001afd760 in ?? ()
#10 0x00000000029a7e68 in ?? ()
#11 0x0000000001afd760 in ?? ()
#12 0x00007f00ad0c0460 in ?? ()
#13 0x0000000000000000 in ?? ()

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================


```

---

### Post by msousa on 2013-06-09
looks like I messed up this code tag pretty well :(

---

### Post by QIII on 2013-06-10
What version of Ubuntu are you using and which fglrx driver?

It looks to me like something in your application is trying to access system information using glx or hardware acceleration and you don't have it.

In the ATI Driver wiki link in my signature, go to "4. Enabling Video Hardware Acceleration"  

It may be more than you need, but install the packages I suggest right under that heading, one of which is libva-glx1.

Let me know if adding all that helps.

---

### Post by msousa on 2013-06-10
I will try this. I have ubuntu 12.04. Thanks...

---

### Post by QIII on 2013-06-10
Is that 12.04/12.04.1 or is it 12.04.2?

---

### Post by msousa on 2013-06-10
ubuntu version = 12.04
fglrx version = 2:8.960-0ubuntu1.1

Not sure if this is helpful, but I ran fglrxinfo and got the following:
$ fglrxinfo 
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

I did as you suggested from the "Enabling Video Hardware Acceleration" and ended up with the following from vainfo:

$ sudo vainfo
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit
mike@mike-Aspire-7535:~/ardupilot$ ll /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so 
lrwxrwxrwx 1 root root 17 Apr 21  2012 /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so -> xvba_drv_video.so

Because  of the above error I tried suggestions from this site,  [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide), in  the section "Using the xvda-va Driver (VA-API)" installing libva-x11-1,  unfortunately vainfo still gave the same error messages.

Any idea what my next steps would be?

Thanks...

---

### Post by msousa on 2013-06-10
> **QIII said:**
> Is that 12.04/12.04.1 or is it 12.04.2?

$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise

---

### Post by QIII on 2013-06-11
OK.

What is the model of your GPU?

---

### Post by msousa on 2013-06-12
> **QIII said:**
> OK.

What is the model of your GPU?

QIII, what is the command to use to find that out?

What if I don't have one?

---

### Post by QIII on 2013-06-12
In the terminal, type

```
lspci
```

That's a lower-case "ell", not a "one".

Scan down until you find a line that has "VGA compatible controller" in it.

Post that line back here and we'll take a look.

---

### Post by msousa on 2013-06-12
I think this is what you're looking for:

01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS780M/RS780MN [Mobility Radeon HD 3200 Graphics]

---

### Post by QIII on 2013-06-12
Thanks.

This makes things clear, but I don't think you are going to like the news.

AMD/ATI stopped continuing development of the fglrx driver for all HD 4000 models and earlier.  Those cards will still work with the legacy driver in the 12.04 and 12.04.1 repo.  However, beginning with 12.04.2, changes in the kernel and the change from X Server 1.12 to 1.13 mean that the older driver, no longer updated, will not work.  You need an HD 5000 or later series.

There are ways to get those older cards to work, but I recommend against them so strongly that I will not even bother to point them out.  They effectively break your system using a kludge that is bound to cause problems with future updates and dependencies.  As a matter of fact, I have already worked with two forum users for whom just that happened.

So...

I can't tell you what to do, but 12.04 and 12.04.1 are supported until 2017 and the fglrx driver in the 12.04/12.04.1 repo will still work.  I won't say to do it, but if you were to reinstall 12.04 or 12.04.1, you would have access to a driver that will work.

AMD/ATI caught us all off guard with this.  This was not a great service to the Linux community -- particularly when there are new systems still on the shelves with some of those GPUs.

Sorry for the bad news.

---

### Post by msousa on 2013-06-15
QIII, thanks for your help. It was at least an education in Linux. I  guess I will need to find an alternative to the windows executable...

---

