---
title: "COMSOL Multiphysics 3.4 in wine"
date: 2008-02-08
forum: General Help
---

### Post by nr4ps on 2008-02-08
Hi,

I need to use COMSOL Multiphysics v3.4 for a class I'm taking.  At the moment I have to restart into Windows whenever I need it, so I'm trying to get it working under wine.  When I try to open a file with it, it gives me an error.  I was hoping someone might be able to make sense of the following output and maybe suggest a solution.  Thanks for taking the time to read my post.

fixme:win:EnumDisplayDevicesW ((null),0,0x339cdc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x339cdc,0x00000000), stub!
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:imm:ImmGetDefaultIMEWnd (0x1002c - (nil) 0x120090 ): semi-stub
fixme:imm:ImmGetOpenStatus (0x17d108): semi-stub
fixme:imm:ImmSetConversionStatus (0x17d108, 1, 0): stub
fixme:imm:ImmGetDefaultIMEWnd (0x1002c - 0x1002e 0x120090 ): semi-stub
fixme:shell:DllGetClassObject failed for CLSID=
        {208d2c60-3aea-1069-a2d7-08002b30309d} (My Network Places)
err:shell:SHCoCreateInstance LoadFromShell failed for CLSID=
        {208d2c60-3aea-1069-a2d7-08002b30309d} (My Network Places)
Exception:
        java.lang.InternalError: Could not bind shell folder to interface
        (rethrown as com.femlab.util.FlFatalException)
Messages:
        Fatal error.
        - Type: InternalError

Stack trace:
        at sun.awt.shell.Win32ShellFolder2.initSpecial(Native Method)
        at sun.awt.shell.Win32ShellFolder2.access$300(Unknown Source)
        at sun.awt.shell.Win32ShellFolder2$1.call(Unknown Source)
        at sun.awt.shell.Win32ShellFolder2$1.call(Unknown Source)
        at sun.awt.shell.Win32ShellFolder2$ComTask.execute(Unknown Source)
        at sun.awt.shell.Win32ShellFolder2.<init>(Unknown Source)
        at sun.awt.shell.Win32ShellFolderManager2.getNetwork(Unknown Source)
        at sun.awt.shell.Win32ShellFolder2$7.call(Unknown Source)
        at sun.awt.shell.Win32ShellFolder2$7.call(Unknown Source)
        at sun.awt.shell.Win32ShellFolder2$ComTask.execute(Unknown Source)
        at sun.awt.shell.Win32ShellFolder2.getFileSystemPath(Unknown Source)
        at sun.awt.shell.Win32ShellFolder2.access$400(Unknown Source)
        at sun.awt.shell.Win32ShellFolder2$11.call(Unknown Source)
        at sun.awt.shell.Win32ShellFolder2$11.call(Unknown Source)
        at sun.awt.shell.Win32ShellFolder2$ComTask.execute(Unknown Source)
        at sun.awt.shell.Win32ShellFolder2.getChildByPath(Unknown Source)
        at sun.awt.shell.Win32ShellFolderManager2.getPersonal(Unknown Source)
        at sun.awt.shell.Win32ShellFolder2$10.call(Unknown Source)
        at sun.awt.shell.Win32ShellFolder2$10.call(Unknown Source)
        at java.util.concurrent.FutureTask$Sync.innerRun(Unknown Source)
        at java.util.concurrent.FutureTask.run(Unknown Source)
        at java.util.concurrent.ThreadPoolExecutor$Worker.runTask(Unknown Source)
        at java.util.concurrent.ThreadPoolExecutor$Worker.run(Unknown Source)
        at sun.awt.shell.Win32ShellFolder2$ComTaskExecutor$2.run(Unknown Source)
        at java.lang.Thread.run(Unknown Source)
fixme:imm:ImmGetDefaultIMEWnd (0x1002c - 0x1002e 0x120090 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10030 - 0x1002e 0x120090 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10030 - 0x1002e 0x120090 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10030 - 0x1002e 0x120090 ): semi-stub
fixme:imm:ImmGetOpenStatus (0x180d30): semi-stub
fixme:imm:ImmSetConversionStatus (0x180d30, 1, 0): stub
fixme:imm:ImmGetDefaultIMEWnd (0x10030 - 0x1002e 0x120090 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10030 - 0x1002e 0x120090 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x1002c - 0x1002e 0x120090 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10030 - 0x1002e 0x120090 ): semi-stub
fixme:imm:ImmGetOpenStatus (0x181320): semi-stub
fixme:imm:ImmSetConversionStatus (0x181320, 1, 0): stub
fixme:imm:ImmGetDefaultIMEWnd (0x1002c - 0x1002e 0x120090 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x1002c - 0x1002e 0x120090 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x1002c - 0x1002e 0x120090 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x1002c - 0x1002e 0x120090 ): semi-stub

---

### Post by junkyjunk on 2008-03-19
I think the best way to ask COmsol to send a Trial DVD (they do it free of charge but you might have to exchange a few e-mails). DVD comes with Windows (32&64), Linux, OS X versions with all modules. You can then install it natively and then use the serial # you have.

junky

---

