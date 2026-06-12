---
title: "Moving Wine"
date: 2007-04-21
forum: General Help
---

### Post by Harkainos on 2007-04-21
I am a pretty organized person (and totally used to windows... please bear with me). I am curious:

Could I move Wine into a 'shared' directory (that isn't in MY home folder) and put the games in there so wine can run them? Would that effect HOW Wine work?

---

### Post by fain on 2007-06-19
I am trying to do this too as i have big games in my .wine folder and want them on a separate hard drive which is a lot bigger. Really all i need is to make a drive_d and point it to a folder on a separate drive but when i do this the game does not launch. It only launches when in my home directory :( 

i also tried moveing the whole .wine dir and makeing a  sym link to my home dir but still a no go.
heres some output when i point my drive_d to a dir on my raid. the launcher is in drive_c in my home directory but when it gets the point to launch the game(on the drive_d) wine just dies completely

```
0x00437448).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:00437448 ESP:0034ff0c EBP:0034ffe8 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:7b8ae888 ECX:00000000 EDX:00000000
 ESI:00437448 EDI:7ffdf000
Stack dump:
0x0034ff0c:  7b87453e 7ffdf000 00000000 00000000
0x0034ff1c:  00000000 00000000 00000000 00000000
0x0034ff2c:  ffffffff 7b82ef70 7b843fb0 7b8ae888
0x0034ff3c:  7ffdc000 00001000 0034ffe8 4c030c34
0x0034ff4c:  37b0b794 00000001 10012a03 00000000
0x0034ff5c:  00000000 00000000 00000000 00000000
Backtrace:
=>1 0x00437448 EntryPoint() in swgclientsetup_r (0x0034ffe8)
  2 0xf7e558b7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x00437448 EntryPoint in swgclientsetup_r: call 0x0044002b
Modules:
Module  Address                 Debug info      Name (65 modules)
PE        400000-  48b000       Export          swgclientsetup_r
ELF     7b800000-7b927000       Deferred        kernel32<elf>
  \-PE  7b820000-7b927000       \               kernel32
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d5a7000-7d5c4000       Deferred        imm32<elf>
  \-PE  7d5b0000-7d5c4000       \               imm32
ELF     7d5c4000-7d5ca000       Deferred        libxrandr.so.2
ELF     7d5ca000-7d5cd000       Deferred        libxinerama.so.1
ELF     7db61000-7dbef000       Deferred        winex11<elf>
  \-PE  7db70000-7dbef000       \               winex11
ELF     7dbef000-7dc03000       Deferred        libz.so.1
ELF     7dc03000-7dc6d000       Deferred        libfreetype.so.6
ELF     7dc6d000-7dca0000       Deferred        winspool<elf>
  \-PE  7dc80000-7dca0000       \               winspool
ELF     7dca0000-7dccd000       Deferred        ws2_32<elf>
  \-PE  7dcb0000-7dccd000       \               ws2_32
ELF     7dccd000-7dd68000       Deferred        oleaut32<elf>
  \-PE  7dce0000-7dd68000       \               oleaut32
ELF     7dd68000-7ddc0000       Deferred        shlwapi<elf>
  \-PE  7dd80000-7ddc0000       \               shlwapi
ELF     7ddc0000-7ddf6000       Deferred        dinput<elf>
  \-PE  7ddd0000-7ddf6000       \               dinput
ELF     7ddf6000-7de0f000       Deferred        dinput8<elf>
  \-PE  7de00000-7de0f000       \               dinput8
ELF     7de0f000-7de22000       Deferred        libresolv.so.2
ELF     7de23000-7de2b000       Deferred        libxrender.so.1
ELF     7de30000-7de4e000       Deferred        iphlpapi<elf>
  \-PE  7de40000-7de4e000       \               iphlpapi
ELF     7de4e000-7dea3000       Deferred        rpcrt4<elf>
  \-PE  7de60000-7dea3000       \               rpcrt4
ELF     7dea3000-7df40000       Deferred        ole32<elf>
  \-PE  7deb0000-7df40000       \               ole32
ELF     7df40000-7df92000       Deferred        ddraw<elf>
  \-PE  7df50000-7df92000       \               ddraw
ELF     7df92000-7dfd9000       Deferred        advapi32<elf>
  \-PE  7dfa0000-7dfd9000       \               advapi32
ELF     7dfd9000-7e070000       Deferred        gdi32<elf>
  \-PE  7dff0000-7e070000       \               gdi32
ELF     7e070000-7e1ac000       Deferred        user32<elf>
  \-PE  7e090000-7e1ac000       \               user32
ELF     7e207000-7e213000       Deferred        libgcc_s.so.1
ELF     7e2fd000-7ec95000       Deferred        libglcore.so.1
ELF     7ec95000-7ec9a000       Deferred        libxdmcp.so.6
ELF     7ec9a000-7ed1a000       Deferred        libglu.so.1
ELF     7ed1a000-7edaf000       Deferred        libgl.so.1
ELF     7edaf000-7eea0000       Deferred        libx11.so.6
ELF     7eea0000-7eeae000       Deferred        libxext.so.6
ELF     7eeae000-7ef73000       Deferred        wined3d<elf>
  \-PE  7eec0000-7ef73000       \               wined3d
ELF     7ef73000-7ef9f000       Deferred        d3d9<elf>
  \-PE  7ef80000-7ef9f000       \               d3d9
ELF     7ef9f000-7efaa000       Deferred        libnss_files.so.2
ELF     7efaa000-7efb4000       Deferred        libnss_nis.so.2
ELF     7efb4000-7efcb000       Deferred        libnsl.so.1
ELF     7efcb000-7eff2000       Deferred        libm.so.6
ELF     7eff4000-7eff7000       Deferred        libxau.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     f7ce0000-f7ce2000       Deferred        libnvidia-tls.so.1
ELF     f7ce3000-f7ce7000       Deferred        libdl.so.2
ELF     f7ce7000-f7e28000       Deferred        libc.so.6
ELF     f7e29000-f7e40000       Deferred        libpthread.so.0
ELF     f7e4e000-f7f5f000       Export          libwine.so.1
ELF     f7f61000-f7f7f000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000035 (D) D:\program files\starwarsgalaxies\SwgClientSetup_r.exe
        00000036    0 <==
0000000a 
        0000000b    0
00000008 
        0000002b   15
        00000023    0
        00000021    0
        00000020    0
        0000001f    0
        0000001e    0
        0000001d    0
        0000001c    0
        00000009    0
fixme:shdocvw:WebBrowser_Quit (0x1bacf0)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x1bacf0)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1bacf0)
fixme:shdocvw:OleObject_Close (0x1bacf0)->(1)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x1bacf0)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1bacf0)
fixme:shdocvw:OleObject_Close (0x1bacf0)->(1)
fixme:shdocvw:ViewObject_SetAdvise (0x1bacf0)->(1 00000000 (nil))
fixme:imm:ImmReleaseContext (0x10032, 0x155ed0): stub
fixme:shdocvw:WebBrowser_Quit (0x1ac930)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x1ac930)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1ac930)
fixme:shdocvw:OleObject_Close (0x1ac930)->(1)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x1ac930)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1ac930)
fixme:shdocvw:OleObject_Close (0x1ac930)->(1)
fixme:shdocvw:ViewObject_SetAdvise (0x1ac930)->(1 00000000 (nil))
fixme:shdocvw:WebBrowser_Quit (0x785d5a8)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x785d5a8)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x785d5a8)
fixme:shdocvw:OleObject_Close (0x785d5a8)->(1)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x785d5a8)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x785d5a8)
fixme:shdocvw:OleObject_Close (0x785d5a8)->(1)
fixme:shdocvw:ViewObject_SetAdvise (0x785d5a8)->(1 00000000 (nil))
fixme:imm:ImmGetDefaultIMEWnd (0x10044 - 0x40060 0x155ed0 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x1004c - 0x40060 0x155ed0 ): semi-stub
jay@home:~/.wine/drive_c/Program Files/Sony/Station/LaunchPad$ winecfg
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
err:winecfg:load_drives GetVolumeInformation() for 'A:\' failed, setting serial to 0
```

---

