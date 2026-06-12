---
title: "wine and debugger"
date: 2008-03-08
forum: General Help
---

### Post by oris-rake on 2008-03-08
Ok i installed WIne and want to play at some of my windows games :)  but i get ```
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,9,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,18,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,27,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,36,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,45,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,54,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,63,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,72,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,81,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,90,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,99,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,108,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,117,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,126,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,135,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,144,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,153,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,162,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,171,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,180,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,189,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,198,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,207,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,216,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,225,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,234,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,243,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,252,2): stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x1c9f9e4,0x00000000), stub!
fixme:d3d9:IDirect3DDevice9Impl_CreateSurface (0x13cb60) call to IWineD3DDevice_CreateSurface failed
fixme:d3d9:D3D9CB_CreateSurface (0x13cb60) IDirect3DDevice9_CreateSurface failed
fixme:d3d:IWineD3DDeviceImpl_CreateTexture Failed to create surface  0x7230660
fixme:d3d9:IDirect3DDevice9Impl_CreateTexture (0x13cb60) call to IWineD3DDevice_CreateTexture failed
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
fixme:d3d9:IDirect3DDevice9Impl_CreateSurface (0x13e3c0) call to IWineD3DDevice_CreateSurface failed
fixme:d3d9:D3D9CB_CreateSurface (0x13e3c0) IDirect3DDevice9_CreateSurface failed
fixme:d3d:IWineD3DDeviceImpl_CreateTexture Failed to create surface  0x7230660
fixme:d3d9:IDirect3DDevice9Impl_CreateTexture (0x13e3c0) call to IWineD3DDevice_CreateTexture failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x14aa98) Unhandled query type 4
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x13e3c0) call to IWineD3DDevice_CreateQuery failed
wine: Unhandled page fault on execute access to 0x00000000 at address (nil) (thread 0009), starting debugger...
Unhandled exception: page fault on execute access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:00000000 ESP:01c9f254 EBP:01c9fb60 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000508 EBX:7e7dcd3c ECX:02cd2160 EDX:7e7dd940
 ESI:00000000 EDI:01c9f740
Stack dump:
0x01c9f254:  7e711d4e 00000508 00000001 00000400
0x01c9f264:  00000234 00000000 01c9f2d4 00000000
0x01c9f274:  00000000 00000000 00000000 01c9f2c8
0x01c9f284:  7e777e87 0014aa98 00000000 00110460
0x01c9f294:  7e788b91 03420020 00000508 00000000
0x01c9f2a4:  7bc40233 0000ffb8 00000000 00000000
Backtrace:
=>1 0x00000000 (0x01c9fb60)
  2 0x7e7141f6 ActivateContext+0x7b6() in wined3d (0x01c9fbf0)
  3 0x7e72e353 in wined3d (+0x2e353) (0x01c9fc50)
  4 0x7e7f687c in d3d9 (+0x687c) (0x01c9fc80)
  5 0x0058d4f5 in h5_game (+0x18d4f5) (0x00000000)
0x00000000: addb        %al,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (126 modules)
PE        350000-  38b000       Deferred        libcurl
PE        390000-  3a6000       Deferred        zlibwapi
PE        3b0000-  3dc000       Deferred        ubistats
PE        400000- 1a90000       Export          h5_game
PE       1ca0000- 1d36000       Deferred        fmod
PE      10000000-10013000       Deferred        zlib1
PE      50000000-50086000       Deferred        granny2
ELF     6b45e000-6b4af000       Deferred        libgcrypt.so.11
ELF     6b4af000-6b4dd000       Deferred        libcrypt.so.1
ELF     6b6eb000-6b708000       Deferred        imm32<elf>
  \-PE  6b6f0000-6b708000       \               imm32
ELF     6b708000-6b778000       Deferred        libgnutls.so.13
ELF     6b778000-6b800000       Deferred        libkrb5.so.3
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7b92a000-7b93a000       Deferred        libtasn1.so.3
ELF     7b93a000-7ba00000       Deferred        libasound.so.2
ELF     7bc00000-7bca3000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca3000       \               ntdll
ELF     7bcb0000-7bcd5000       Deferred        libk5crypto.so.3
ELF     7bcd5000-7bcfe000       Deferred        libgssapi_krb5.so.2
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf0d000-7bf42000       Deferred        libcups.so.2
ELF     7bf5c000-7bf74000       Deferred        msacm32<elf>
  \-PE  7bf60000-7bf74000       \               msacm32
ELF     7bf74000-7bfaa000       Deferred        winealsa<elf>
  \-PE  7bf80000-7bfaa000       \               winealsa
ELF     7bfce000-7c000000       Deferred        uxtheme<elf>
  \-PE  7bfd0000-7c000000       \               uxtheme
ELF     7c2aa000-7c2bf000       Deferred        midimap<elf>
  \-PE  7c2b0000-7c2bf000       \               midimap
PE      7c340000-7c396000       Deferred        msvcr71
PE      7c3a0000-7c41b000       Deferred        msvcp71
ELF     7c41b000-7c423000       Deferred        libkrb5support.so.0
ELF     7c43c000-7c445000       Deferred        libxcursor.so.1
ELF     7c445000-7c44a000       Deferred        libxfixes.so.3
ELF     7c44a000-7c450000       Deferred        libxrandr.so.2
ELF     7c451000-7c455000       Deferred        libgpg-error.so.0
ELF     7c455000-7c458000       Deferred        libcom_err.so.2
ELF     7c4eb000-7c4ed000       Deferred        libkeyutils.so.1
ELF     7c4ed000-7c4f0000       Deferred        libxcomposite.so.1
ELF     7c4f0000-7c4f8000       Deferred        libxrender.so.1
ELF     7c4f8000-7c4fb000       Deferred        libxinerama.so.1
ELF     7cfe9000-7cff2000       Deferred        librt.so.1
ELF     7cff2000-7dffd000       Deferred        fglrx_dri.so
ELF     7dffd000-7e008000       Deferred        libgcc_s.so.1
ELF     7e008000-7e082000       Deferred        libgl.so.1
ELF     7e082000-7e087000       Deferred        libxdmcp.so.6
ELF     7e087000-7e178000       Deferred        libx11.so.6
ELF     7e178000-7e186000       Deferred        libxext.so.6
ELF     7e1a0000-7e230000       Deferred        winex11<elf>
  \-PE  7e1b0000-7e230000       \               winex11
ELF     7e2af000-7e2cf000       Deferred        libexpat.so.1
ELF     7e2cf000-7e2fa000       Deferred        libfontconfig.so.1
ELF     7e2fa000-7e30f000       Deferred        libz.so.1
ELF     7e30f000-7e37f000       Deferred        libfreetype.so.6
ELF     7e37f000-7e382000       Deferred        libxau.so.6
ELF     7e399000-7e43a000       Deferred        comdlg32<elf>
  \-PE  7e3a0000-7e43a000       \               comdlg32
ELF     7e43a000-7e46f000       Deferred        winspool<elf>
  \-PE  7e440000-7e46f000       \               winspool
ELF     7e46f000-7e483000       Deferred        oleacc<elf>
  \-PE  7e470000-7e483000       \               oleacc
ELF     7e483000-7e4a4000       Deferred        mpr<elf>
  \-PE  7e490000-7e4a4000       \               mpr
ELF     7e4a4000-7e4f0000       Deferred        wininet<elf>
  \-PE  7e4b0000-7e4f0000       \               wininet
ELF     7e4f0000-7e516000       Deferred        msacm32<elf>
  \-PE  7e500000-7e516000       \               msacm32
ELF     7e516000-7e54d000       Deferred        dinput<elf>
  \-PE  7e520000-7e54d000       \               dinput
ELF     7e54d000-7e565000       Deferred        dinput8<elf>
  \-PE  7e550000-7e565000       \               dinput8
ELF     7e565000-7e57e000       Deferred        wsock32<elf>
  \-PE  7e570000-7e57e000       \               wsock32
ELF     7e57e000-7e597000       Deferred        crtdll<elf>
  \-PE  7e580000-7e597000       \               crtdll
ELF     7e597000-7e624000       Deferred        winmm<elf>
  \-PE  7e5a0000-7e624000       \               winmm
ELF     7e624000-7e64f000       Deferred        ws2_32<elf>
  \-PE  7e630000-7e64f000       \               ws2_32
ELF     7e64f000-7e6b5000       Deferred        msvcrt<elf>
  \-PE  7e660000-7e6b5000       \               msvcrt
ELF     7e6b5000-7e6d0000       Deferred        d3dx9_36<elf>
  \-PE  7e6c0000-7e6d0000       \               d3dx9_36
ELF     7e6d0000-7e6e9000       Deferred        d3dx9_25<elf>
  \-PE  7e6e0000-7e6e9000       \               d3dx9_25
ELF     7e6e9000-7e7df000       Export          wined3d<elf>
  \-PE  7e700000-7e7df000       \               wined3d
ELF     7e7df000-7e80f000       Export          d3d9<elf>
  \-PE  7e7f0000-7e80f000       \               d3d9
ELF     7e80f000-7e858000       Deferred        dbghelp<elf>
  \-PE  7e820000-7e858000       \               dbghelp
ELF     7e858000-7e8fb000       Deferred        oleaut32<elf>
  \-PE  7e870000-7e8fb000       \               oleaut32
ELF     7e8fb000-7e90e000       Deferred        libresolv.so.2
ELF     7e90e000-7e92c000       Deferred        iphlpapi<elf>
  \-PE  7e910000-7e92c000       \               iphlpapi
ELF     7e92c000-7e98b000       Deferred        rpcrt4<elf>
  \-PE  7e940000-7e98b000       \               rpcrt4
ELF     7e98b000-7ea2e000       Deferred        ole32<elf>
  \-PE  7e9a0000-7ea2e000       \               ole32
ELF     7ea2e000-7eaef000       Deferred        comctl32<elf>
  \-PE  7ea40000-7eaef000       \               comctl32
ELF     7eaef000-7eb47000       Deferred        shlwapi<elf>
  \-PE  7eb00000-7eb47000       \               shlwapi
ELF     7eb47000-7ec4e000       Deferred        shell32<elf>
  \-PE  7eb60000-7ec4e000       \               shell32
ELF     7ec4e000-7ec99000       Deferred        advapi32<elf>
  \-PE  7ec60000-7ec99000       \               advapi32
ELF     7ec99000-7ed31000       Deferred        gdi32<elf>
  \-PE  7ecb0000-7ed31000       \               gdi32
ELF     7ed31000-7ee6c000       Deferred        user32<elf>
  \-PE  7ed50000-7ee6c000       \               user32
ELF     7ef8b000-7ef96000       Deferred        libnss_files.so.2
ELF     7ef96000-7efa0000       Deferred        libnss_nis.so.2
ELF     7efa0000-7efb8000       Deferred        libnsl.so.1
ELF     7efb8000-7efc1000       Deferred        libnss_compat.so.2
ELF     7efc1000-7efe6000       Deferred        libm.so.6
ELF     7efeb000-7f000000       Deferred        psapi<elf>
  \-PE  7eff0000-7f000000       \               psapi
ELF     f7ce1000-f7ce5000       Deferred        libdl.so.2
ELF     f7ce5000-f7e2f000       Deferred        libc.so.6
ELF     f7e30000-f7e48000       Deferred        libpthread.so.0
ELF     f7e62000-f7f76000       Deferred        libwine.so.1
ELF     f7f78000-f7f96000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) E:\gry\Heroes of Might and Magic V\bin\H5_Game.exe
        00000014    0
        00000013    0
        00000012    0
        00000009    0 <==
0000000a 
        0000000b    0
0000000c 
        0000000f    0
        0000000e    0
        0000000d    0
00000010 
        00000011    0
Backtrace:
=>1 0x00000000 (0x01c9fb60)
  2 0x7e7141f6 ActivateContext+0x7b6() in wined3d (0x01c9fbf0)
  3 0x7e72e353 in wined3d (+0x2e353) (0x01c9fc50)
  4 0x7e7f687c in d3d9 (+0x687c) (0x01c9fc80)
  5 0x0058d4f5 in h5_game (+0x18d4f5) (0x00000000)
```


It happens with all 3d games programs and 2d games like Teewars works fine
I have fglrx drivers (Ati Radeon mobility  x1600) Compiz works glxinfo shows direct rendering: yes 

So what is wrong? 

Anyone? Please help.

---

### Post by oris-rake on 2008-03-08
Anybody?

---

### Post by oris-rake on 2008-03-09
Bump

---

