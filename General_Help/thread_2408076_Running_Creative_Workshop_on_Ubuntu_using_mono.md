---
title: "Running Creative Workshop on Ubuntu using mono"
date: 2018-12-13
forum: General Help
---

### Post by Jonners59 on 2018-12-13
I am trying to run Wanhao's application for 3D printer slicing on my xUbuntu PC.  This is a Windows application, but SHOULD run on Ubuntu with mono installed.  So I have installed mono

I installed mono:
```
sudo apt-get install mono-complete 
```

I cd to where the CreationWorkshop.exe file is

I type the following in a terminal:
```
mono ./CreationWorkshop.exe 
```

I get the following error message....
```
......... warning: iCCP: cHRM chunk does not match sRGBlibpng warning: iCCP: known incorrect sRGB profile
libpng warning: iCCP: cHRM chunk does not match sRGB
libpng warning: iCCP: known incorrect sRGB profile
libpng warning: iCCP: cHRM chunk does not match sRGB
X11 Error encountered: 
  Error: BadMatch (invalid parameter attributes)
  Request:     154 (5)
  Resource ID: 0x5000090
  Serial:      2179
  Hwnd:        Hwnd, Mapped:False ClientWindow:0x5000090, WholeWindow:0x500008F, Zombie=False, Parent:[Hwnd, Mapped:True ClientWindow:0x5000086, WholeWindow:0x5000085, Zombie=False, Parent:[Hwnd, Mapped:True ClientWindow:0x5000084, WholeWindow:0x5000083, Zombie=False, Parent:[Hwnd, Mapped:True ClientWindow:0x5000082, WholeWindow:0x5000081, Zombie=False, Parent:[Hwnd, Mapped:True ClientWindow:0x5000080, WholeWindow:0x500007F, Zombie=False, Parent:[Hwnd, Mapped:True ClientWindow:0x500007E, WholeWindow:0x500007D, Zombie=False, Parent:[Hwnd, Mapped:True ClientWindow:0x500007C, WholeWindow:0x500007B, Zombie=False, Parent:[Hwnd, Mapped:True ClientWindow:0x500007A, WholeWindow:0x5000079, Zombie=False, Parent:[<null>]]]]]]]]
  Control:     UV_DLP_3D_Printer.GUI.Controls.ctlGL  at System.Environment.get_StackTrace () [0x00000] in <0f8aeac9d63d4b8aa575761bb4e65b79>:0 
  at System.Windows.Forms.XplatUIX11.HandleError (System.IntPtr display, System.Windows.Forms.XErrorEvent& error_event) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at OpenTK.Platform.X11.Glx.MakeCurrent (System.IntPtr , System.IntPtr , System.IntPtr ) [0x00000] in <6e87929761c543a4bfb6d5acaea62619>:0 
  at OpenTK.Platform.X11.Glx.MakeCurrent (System.IntPtr display, System.IntPtr drawable, OpenTK.ContextHandle context) [0x00000] in <6e87929761c543a4bfb6d5acaea62619>:0 
  at OpenTK.Platform.X11.X11GLContext.MakeCurrent (OpenTK.Platform.IWindowInfo window) [0x00000] in <6e87929761c543a4bfb6d5acaea62619>:0 
  at OpenTK.Graphics.GraphicsContext.MakeCurrent (OpenTK.Platform.IWindowInfo window) [0x00000] in <6e87929761c543a4bfb6d5acaea62619>:0 
  at OpenTK.GLControl.MakeCurrent () [0x00000] in <1b9440a0f8834418a8d369f909728a32>:0 
  at OpenTK.GLControl.OnHandleCreated (System.EventArgs e) [0x00000] in <1b9440a0f8834418a8d369f909728a32>:0 
  at System.Windows.Forms.Control.WmCreate (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.WndProc (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.ScrollableControl.WndProc (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.ContainerControl.WndProc (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.UserControl.WndProc (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control+ControlWindowTarget.OnMessage (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control+ControlNativeWindow.WndProc (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.NativeWindow.WndProc (System.IntPtr hWnd, System.Windows.Forms.Msg msg, System.IntPtr wParam, System.IntPtr lParam) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.XplatUIX11.SendMessage (System.IntPtr hwnd, System.Windows.Forms.Msg message, System.IntPtr wParam, System.IntPtr lParam) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.XplatUIX11.CreateWindow (System.Windows.Forms.CreateParams cp) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.XplatUI.CreateWindow (System.Windows.Forms.CreateParams cp) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.NativeWindow.CreateHandle (System.Windows.Forms.CreateParams cp) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.CreateHandle () [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.CreateControl () [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.CreateControl () [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.WmShowWindow (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.WndProc (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.ScrollableControl.WndProc (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control+ControlWindowTarget.OnMessage (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control+ControlNativeWindow.WndProc (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.NativeWindow.WndProc (System.IntPtr hWnd, System.Windows.Forms.Msg msg, System.IntPtr wParam, System.IntPtr lParam) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.XplatUIX11.SendMessage (System.IntPtr hwnd, System.Windows.Forms.Msg message, System.IntPtr wParam, System.IntPtr lParam) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.XplatUIX11.CreateWindow (System.Windows.Forms.CreateParams cp) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.XplatUI.CreateWindow (System.Windows.Forms.CreateParams cp) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.NativeWindow.CreateHandle (System.Windows.Forms.CreateParams cp) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.CreateHandle () [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.CreateControl () [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.CreateControl () [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.WmShowWindow (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.WndProc (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.ScrollableControl.WndProc (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.ContainerControl.WndProc (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.SplitContainer.WndProc (System.Windows.Forms.Message& msg) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control+ControlWindowTarget.OnMessage (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control+ControlNativeWindow.WndProc (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.NativeWindow.WndProc (System.IntPtr hWnd, System.Windows.Forms.Msg msg, System.IntPtr wParam, System.IntPtr lParam) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.XplatUIX11.SendMessage (System.IntPtr hwnd, System.Windows.Forms.Msg message, System.IntPtr wParam, System.IntPtr lParam) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.XplatUIX11.CreateWindow (System.Windows.Forms.CreateParams cp) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.XplatUI.CreateWindow (System.Windows.Forms.CreateParams cp) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.NativeWindow.CreateHandle (System.Windows.Forms.CreateParams cp) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.CreateHandle () [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.CreateControl () [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.CreateControl () [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.WmShowWindow (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.WndProc (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.ScrollableControl.WndProc (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.ContainerControl.WndProc (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.UserControl.WndProc (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control+ControlWindowTarget.OnMessage (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control+ControlNativeWindow.WndProc (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.NativeWindow.WndProc (System.IntPtr hWnd, System.Windows.Forms.Msg msg, System.IntPtr wParam, System.IntPtr lParam) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.XplatUIX11.SendMessage (System.IntPtr hwnd, System.Windows.Forms.Msg message, System.IntPtr wParam, System.IntPtr lParam) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.XplatUIX11.CreateWindow (System.Windows.Forms.CreateParams cp) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.XplatUI.CreateWindow (System.Windows.Forms.CreateParams cp) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.NativeWindow.CreateHandle (System.Windows.Forms.CreateParams cp) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.CreateHandle () [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.CreateControl () [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.CreateControl () [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.WmShowWindow (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.WndProc (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.ScrollableControl.WndProc (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control+ControlWindowTarget.OnMessage (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control+ControlNativeWindow.WndProc (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.NativeWindow.WndProc (System.IntPtr hWnd, System.Windows.Forms.Msg msg, System.IntPtr wParam, System.IntPtr lParam) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.XplatUIX11.SendMessage (System.IntPtr hwnd, System.Windows.Forms.Msg message, System.IntPtr wParam, System.IntPtr lParam) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.XplatUIX11.CreateWindow (System.Windows.Forms.CreateParams cp) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.XplatUI.CreateWindow (System.Windows.Forms.CreateParams cp) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.NativeWindow.CreateHandle (System.Windows.Forms.CreateParams cp) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.CreateHandle () [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.CreateControl () [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.CreateControl () [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.WmShowWindow (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.WndProc (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.ScrollableControl.WndProc (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control+ControlWindowTarget.OnMessage (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control+ControlNativeWindow.WndProc (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.NativeWindow.WndProc (System.IntPtr hWnd, System.Windows.Forms.Msg msg, System.IntPtr wParam, System.IntPtr lParam) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.XplatUIX11.SendMessage (System.IntPtr hwnd, System.Windows.Forms.Msg message, System.IntPtr wParam, System.IntPtr lParam) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.XplatUIX11.CreateWindow (System.Windows.Forms.CreateParams cp) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.XplatUI.CreateWindow (System.Windows.Forms.CreateParams cp) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.NativeWindow.CreateHandle (System.Windows.Forms.CreateParams cp) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.CreateHandle () [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.CreateControl () [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.CreateControl () [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.WmShowWindow (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.WndProc (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.ScrollableControl.WndProc (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.ContainerControl.WndProc (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.SplitContainer.WndProc (System.Windows.Forms.Message& msg) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control+ControlWindowTarget.OnMessage (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control+ControlNativeWindow.WndProc (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.NativeWindow.WndProc (System.IntPtr hWnd, System.Windows.Forms.Msg msg, System.IntPtr wParam, System.IntPtr lParam) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.XplatUIX11.SendMessage (System.IntPtr hwnd, System.Windows.Forms.Msg message, System.IntPtr wParam, System.IntPtr lParam) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.XplatUIX11.CreateWindow (System.Windows.Forms.CreateParams cp) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.XplatUI.CreateWindow (System.Windows.Forms.CreateParams cp) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.NativeWindow.CreateHandle (System.Windows.Forms.CreateParams cp) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.CreateHandle () [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.CreateControl () [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.CreateControl () [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.SetVisibleCore (System.Boolean value) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Form.SetVisibleCore (System.Boolean value) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.set_Visible (System.Boolean value) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Application.RunLoop (System.Boolean Modal, System.Windows.Forms.ApplicationContext context) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Application.Run (System.Windows.Forms.ApplicationContext context) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Application.Run (System.Windows.Forms.Form mainForm) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at UV_DLP_3D_Printer.Program.Main () [0x00000] in <881ed22c1c3942f4a1027d64b8778a16>:0 


OpenTK.Graphics.GraphicsContextException: Failed to make context current.
  at OpenTK.Platform.X11.X11GLContext.MakeCurrent (OpenTK.Platform.IWindowInfo window) [0x0010e] in <6e87929761c543a4bfb6d5acaea62619>:0 
  at OpenTK.Graphics.GraphicsContext.MakeCurrent (OpenTK.Platform.IWindowInfo window) [0x00000] in <6e87929761c543a4bfb6d5acaea62619>:0 
  at OpenTK.GLControl.MakeCurrent () [0x00017] in <1b9440a0f8834418a8d369f909728a32>:0 
  at OpenTK.GLControl.OnHandleCreated (System.EventArgs e) [0x0007a] in <1b9440a0f8834418a8d369f909728a32>:0 
  at System.Windows.Forms.Control.WmCreate (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control.WndProc (System.Windows.Forms.Message& m) [0x0021c] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.ScrollableControl.WndProc (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.ContainerControl.WndProc (System.Windows.Forms.Message& m) [0x00029] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.UserControl.WndProc (System.Windows.Forms.Message& m) [0x00027] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control+ControlWindowTarget.OnMessage (System.Windows.Forms.Message& m) [0x00000] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.Control+ControlNativeWindow.WndProc (System.Windows.Forms.Message& m) [0x0000b] in <69ecb40f27a1431a99620933ba9a8b39>:0 
  at System.Windows.Forms.NativeWindow.WndProc (System.IntPtr hWnd, System.Windows.Forms.Msg msg, System.IntPtr wParam, System.IntPtr lParam) [0x00085] in <69ecb40f27a1431a99620933ba9a8b39>:0 
Stacktrace:


/proc/self/maps:
40725000-407c6000 rw-p 00000000 00:00 0 
40b36000-40d62000 rwxp 00000000 00:00 0 
41bb1000-41bc1000 rwxp 00000000 00:00 0 
55927a1b0000-55927a5e7000 r-xp 00000000 08:13 1321220                    /usr/bin/mono-sgen
55927a7e6000-55927a7ed000 r--p 00436000 08:13 1321220                    /usr/bin/mono-sgen
55927a7ed000-55927a7f2000 rw-p 0043d000 08:13 1321220                    /usr/bin/mono-sgen
55927a7f2000-55927a809000 rw-p 00000000 00:00 0 
55927c7bb000-55927eb1c000 rw-p 00000000 00:00 0                          [heap]
7fbf45e6c000-7fbf45eec000 rw-p 00000000 00:00 0 
7fbf45eef000-7fbf45ff4000 rw-s 00000000 00:06 500                        /dev/nvidiactl
7fbf45ff4000-7fbf47413000 r-xp 00000000 08:13 1063705                    /usr/lib/x86_64-linux-gnu/libnvidia-glcore.so.390.77
7fbf47413000-7fbf47434000 rwxp 0141f000 08:13 1063705                    /usr/lib/x86_64-linux-gnu/libnvidia-glcore.so.390.77
7fbf47434000-7fbf47870000 r-xp 01440000 08:13 1063705                    /usr/lib/x86_64-linux-gnu/libnvidia-glcore.so.390.77
7fbf47870000-7fbf47a6f000 ---p 0187c000 08:13 1063705                    /usr/lib/x86_64-linux-gnu/libnvidia-glcore.so.390.77
7fbf47a6f000-7fbf47de2000 rw-p 0187b000 08:13 1063705                    /usr/lib/x86_64-linux-gnu/libnvidia-glcore.so.390.77
7fbf47de2000-7fbf47dfc000 rw-p 00000000 00:00 0 
7fbf47dfc000-7fbf47dff000 r-xp 00000000 08:13 1445600                    /usr/lib/x86_64-linux-gnu/tls/libnvidia-tls.so.390.77
7fbf47dff000-7fbf47fff000 ---p 00003000 08:13 1445600                    /usr/lib/x86_64-linux-gnu/tls/libnvidia-tls.so.390.77
7fbf47fff000-7fbf48000000 rw-p 00003000 08:13 1445600                    /usr/lib/x86_64-linux-gnu/tls/libnvidia-tls.so.390.77
7fbf48000000-7fbf48043000 rw-p 00000000 00:00 0 
7fbf48043000-7fbf4c000000 ---p 00000000 00:00 0 
7fbf4c000000-7fbf4c021000 rw-p 00000000 00:00 0 
7fbf4c021000-7fbf50000000 ---p 00000000 00:00 0 
7fbf50000000-7fbf50022000 rw-p 00000000 00:00 0 
7fbf50022000-7fbf54000000 ---p 00000000 00:00 0 


Unhandled Exception:
System.NullReferenceException: Object reference not set to an instance of an object
[ERROR] FATAL UNHANDLED EXCEPTION: System.NullReferenceException: Object reference not set to an instance of an object



```

---

### Post by Jonners59 on 2018-12-17
Any help, please??????

---

