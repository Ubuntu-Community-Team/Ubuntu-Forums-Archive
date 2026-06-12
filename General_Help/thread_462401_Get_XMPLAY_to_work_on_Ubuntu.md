---
title: "Get XMPLAY to work on Ubuntu"
date: 2007-06-02
forum: General Help
---

### Post by coral on 2007-06-02
Hello, i have Ubuntu 7.04 and i need XMPLAY to work for a certain project.
When i start it i get something like this:
```
coral@coral:~/Desktop/XMPLAY$ sudo wine xmplay.exe 
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
err:systray:delete_icon invalid tray icon ID specified: 1
wine: Unhandled page fault on read access to 0x00230d9c at address 0x445057 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00230d9c in 32-bit code (0x00445057).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00445057 ESP:00237d94 EBP:00237d9c EFLAGS:00010202(   - 00      - -RI1)
 EAX:00002c80 EBX:7ee1595c ECX:00230d9c EDX:0044348a
 ESI:00238310 EDI:00010030
Stack dump:
0x00237d94:  00000000 00443497 00237dcc 7edf0dfa
0x00237da4:  00010030 00000047 00000000 002385a4
0x00237db4:  00000000 7ee1595c 00237dcc 7ee1595c
0x00237dc4:  00238310 00010030 00237e0c 7edf158e
0x00237dd4:  0044348a 00010030 00000047 00000000
0x00237de4:  002385a4 00000000 00000000 00000000
Backtrace:
=>1 0x00445057 in xmplay (+0x45057) (0x00237d9c)
  2 0x7edf0dfa WINPROC_wrapper+0x1a() in user32 (0x00237dcc)
  3 0x7edf158e in user32 (+0xa158e) (0x00237e0c)
  4 0x7edf5c5b in user32 (+0xa5c5b) (0x002382dc)
  5 0x7edf67fa CallWindowProcW+0xaa() in user32 (0x0023831c)
  6 0x7edbdac8 in user32 (+0x6dac8) (0x0023838c)
  7 0x7edc1820 SendMessageTimeoutW+0x1a0() in user32 (0x002383fc)
  8 0x7edc1890 SendMessageW+0x50() in user32 (0x0023843c)
  9 0x7edef25e USER_SetWindowPos+0x87e() in user32 (0x0023855c)
  10 0x7edefbc2 SetWindowPos+0xa2() in user32 (0x002385cc)
  11 0x7edf014f in user32 (+0xa014f) (0x002385fc)
  12 0x7ede813e EnumWindows+0x6e() in user32 (0x0023862c)
  13 0x7edef85e USER_SetWindowPos+0xe7e() in user32 (0x0023874c)
  14 0x7edefbc2 SetWindowPos+0xa2() in user32 (0x002387bc)
  15 0x00443622 in xmplay (+0x43622) (0x0024246c)
  16 0x7edf0dfa WINPROC_wrapper+0x1a() in user32 (0x0024249c)
  17 0x7edf158e in user32 (+0xa158e) (0x002424dc)
  18 0x7edf5c5b in user32 (+0xa5c5b) (0x002429ac)
  19 0x7edf67fa CallWindowProcW+0xaa() in user32 (0x002429ec)
  20 0x7edbdac8 in user32 (+0x6dac8) (0x00242a5c)
  21 0x7edc1820 SendMessageTimeoutW+0x1a0() in user32 (0x00242acc)
  22 0x7edc1890 SendMessageW+0x50() in user32 (0x00242b0c)
  23 0x7edef25e USER_SetWindowPos+0x87e() in user32 (0x00242c2c)
  24 0x7edefbc2 SetWindowPos+0xa2() in user32 (0x00242c9c)
  25 0x7edf014f in user32 (+0xa014f) (0x00242ccc)
  26 0x7ede813e EnumWindows+0x6e() in user32 (0x00242cfc)
  27 0x7edef85e USER_SetWindowPos+0xe7e() in user32 (0x00242e1c)
  28 0x7edefbc2 SetWindowPos+0xa2() in user32 (0x00242e8c)
  29 0x00443622 in xmplay (+0x43622) (0x0024cb3c)
  30 0x7edf0dfa WINPROC_wrapper+0x1a() in user32 (0x0024cb6c)
  31 0x7edf158e in user32 (+0xa158e) (0x0024cbac)
  32 0x7edf5c5b in user32 (+0xa5c5b) (0x0024d07c)
  33 0x7edf67fa CallWindowProcW+0xaa() in user32 (0x0024d0bc)
  34 0x7edbdac8 in user32 (+0x6dac8) (0x0024d12c)
  35 0x7edc1820 SendMessageTimeoutW+0x1a0() in user32 (0x0024d19c)
  36 0x7edc1890 SendMessageW+0x50() in user32 (0x0024d1dc)
  37 0x7edef25e USER_SetWindowPos+0x87e() in user32 (0x0024d2fc)
  38 0x7edefbc2 SetWindowPos+0xa2() in user32 (0x0024d36c)
  39 0x7edf014f in user32 (+0xa014f) (0x0024d39c)
  40 0x7ede813e EnumWindows+0x6e() in user32 (0x0024d3cc)
  41 0x7edef85e USER_SetWindowPos+0xe7e() in user32 (0x0024d4ec)
  42 0x7edefbc2 SetWindowPos+0xa2() in user32 (0x0024d55c)
  43 0x00443622 in xmplay (+0x43622) (0x0025720c)
  44 0x7edf0dfa WINPROC_wrapper+0x1a() in user32 (0x0025723c)
  45 0x7edf158e in user32 (+0xa158e) (0x0025727c)
  46 0x7edf5c5b in user32 (+0xa5c5b) (0x0025774c)
  47 0x7edf67fa CallWindowProcW+0xaa() in user32 (0x0025778c)
  48 0x7edbdac8 in user32 (+0x6dac8) (0x002577fc)
  49 0x7edc1820 SendMessageTimeoutW+0x1a0() in user32 (0x0025786c)
  50 0x7edc1890 SendMessageW+0x50() in user32 (0x002578ac)
  51 0x7edef25e USER_SetWindowPos+0x87e() in user32 (0x002579cc)
  52 0x7edefbc2 SetWindowPos+0xa2() in user32 (0x00257a3c)
  53 0x7edf014f in user32 (+0xa014f) (0x00257a6c)
  54 0x7ede813e EnumWindows+0x6e() in user32 (0x00257a9c)
  55 0x7edef85e USER_SetWindowPos+0xe7e() in user32 (0x00257bbc)
  56 0x7edefbc2 SetWindowPos+0xa2() in user32 (0x00257c2c)
  57 0x00443622 in xmplay (+0x43622) (0x002618dc)
  58 0x7edf0dfa WINPROC_wrapper+0x1a() in user32 (0x0026190c)
  59 0x7edf158e in user32 (+0xa158e) (0x0026194c)
  60 0x7edf5c5b in user32 (+0xa5c5b) (0x00261e1c)
  61 0x7edf67fa CallWindowProcW+0xaa() in user32 (0x00261e5c)
  62 0x7edbdac8 in user32 (+0x6dac8) (0x00261ecc)
  63 0x7edc1820 SendMessageTimeoutW+0x1a0() in user32 (0x00261f3c)
  64 0x7edc1890 SendMessageW+0x50() in user32 (0x00261f7c)
  65 0x7edef25e USER_SetWindowPos+0x87e() in user32 (0x0026209c)
  66 0x7edefbc2 SetWindowPos+0xa2() in user32 (0x0026210c)
  67 0x7edf014f in user32 (+0xa014f) (0x0026213c)
  68 0x7ede813e EnumWindows+0x6e() in user32 (0x0026216c)
  69 0x7edef85e USER_SetWindowPos+0xe7e() in user32 (0x0026228c)
  70 0x7edefbc2 SetWindowPos+0xa2() in user32 (0x002622fc)
  71 0x00443622 in xmplay (+0x43622) (0x0026bfac)
  72 0x7edf0dfa WINPROC_wrapper+0x1a() in user32 (0x0026bfdc)
  73 0x7edf158e in user32 (+0xa158e) (0x0026c01c)
  74 0x7edf5c5b in user32 (+0xa5c5b) (0x0026c4ec)
  75 0x7edf67fa CallWindowProcW+0xaa() in user32 (0x0026c52c)
  76 0x7edbdac8 in user32 (+0x6dac8) (0x0026c59c)
  77 0x7edc1820 SendMessageTimeoutW+0x1a0() in user32 (0x0026c60c)
  78 0x7edc1890 SendMessageW+0x50() in user32 (0x0026c64c)
  79 0x7edef25e USER_SetWindowPos+0x87e() in user32 (0x0026c76c)
  80 0x7edefbc2 SetWindowPos+0xa2() in user32 (0x0026c7dc)
  81 0x7edf014f in user32 (+0xa014f) (0x0026c80c)
  82 0x7ede813e EnumWindows+0x6e() in user32 (0x0026c83c)
  83 0x7edef85e USER_SetWindowPos+0xe7e() in user32 (0x0026c95c)
  84 0x7edefbc2 SetWindowPos+0xa2() in user32 (0x0026c9cc)
  85 0x00443622 in xmplay (+0x43622) (0x0027667c)
  86 0x7edf0dfa WINPROC_wrapper+0x1a() in user32 (0x002766ac)
  87 0x7edf158e in user32 (+0xa158e) (0x002766ec)
  88 0x7edf5c5b in user32 (+0xa5c5b) (0x00276bbc)
  89 0x7edf67fa CallWindowProcW+0xaa() in user32 (0x00276bfc)
  90 0x7edbdac8 in user32 (+0x6dac8) (0x00276c6c)
  91 0x7edc1820 SendMessageTimeoutW+0x1a0() in user32 (0x00276cdc)
  92 0x7edc1890 SendMessageW+0x50() in user32 (0x00276d1c)
  93 0x7edef25e USER_SetWindowPos+0x87e() in user32 (0x00276e3c)
  94 0x7edefbc2 SetWindowPos+0xa2() in user32 (0x00276eac)
  95 0x7edf014f in user32 (+0xa014f) (0x00276edc)
  96 0x7ede813e EnumWindows+0x6e() in user32 (0x00276f0c)
  97 0x7edef85e USER_SetWindowPos+0xe7e() in user32 (0x0027702c)
  98 0x7edefbc2 SetWindowPos+0xa2() in user32 (0x0027709c)
  99 0x00443622 in xmplay (+0x43622) (0x00280d4c)
  100 0x7edf0dfa WINPROC_wrapper+0x1a() in user32 (0x00280d7c)
  101 0x7edf158e in user32 (+0xa158e) (0x00280dbc)
  102 0x7edf5c5b in user32 (+0xa5c5b) (0x0028128c)
  103 0x7edf67fa CallWindowProcW+0xaa() in user32 (0x002812cc)
  104 0x7edbdac8 in user32 (+0x6dac8) (0x0028133c)
  105 0x7edc1820 SendMessageTimeoutW+0x1a0() in user32 (0x002813ac)
  106 0x7edc1890 SendMessageW+0x50() in user32 (0x002813ec)
  107 0x7edef25e USER_SetWindowPos+0x87e() in user32 (0x0028150c)
  108 0x7edefbc2 SetWindowPos+0xa2() in user32 (0x0028157c)
  109 0x7edf014f in user32 (+0xa014f) (0x002815ac)
  110 0x7ede813e EnumWindows+0x6e() in user32 (0x002815dc)
  111 0x7edef85e USER_SetWindowPos+0xe7e() in user32 (0x002816fc)
  112 0x7edefbc2 SetWindowPos+0xa2() in user32 (0x0028176c)
  113 0x00443622 in xmplay (+0x43622) (0x0028b41c)
  114 0x7edf0dfa WINPROC_wrapper+0x1a() in user32 (0x0028b44c)
  115 0x7edf158e in user32 (+0xa158e) (0x0028b48c)
  116 0x7edf5c5b in user32 (+0xa5c5b) (0x0028b95c)
  117 0x7edf67fa CallWindowProcW+0xaa() in user32 (0x0028b99c)
  118 0x7edbdac8 in user32 (+0x6dac8) (0x0028ba0c)
  119 0x7edc1820 SendMessageTimeoutW+0x1a0() in user32 (0x0028ba7c)
  120 0x7edc1890 SendMessageW+0x50() in user32 (0x0028babc)
  121 0x7edef25e USER_SetWindowPos+0x87e() in user32 (0x0028bbdc)
  122 0x7edefbc2 SetWindowPos+0xa2() in user32 (0x0028bc4c)
  123 0x7edf014f in user32 (+0xa014f) (0x0028bc7c)
  124 0x7ede813e EnumWindows+0x6e() in user32 (0x0028bcac)
  125 0x7edef85e USER_SetWindowPos+0xe7e() in user32 (0x0028bdcc)
  126 0x7edefbc2 SetWindowPos+0xa2() in user32 (0x0028be3c)
  127 0x00443622 in xmplay (+0x43622) (0x00295aec)
  128 0x7edf0dfa WINPROC_wrapper+0x1a() in user32 (0x00295b1c)
  129 0x7edf158e in user32 (+0xa158e) (0x00295b5c)
  130 0x7edf5c5b in user32 (+0xa5c5b) (0x0029602c)
  131 0x7edf67fa CallWindowProcW+0xaa() in user32 (0x0029606c)
  132 0x7edbdac8 in user32 (+0x6dac8) (0x002960dc)
  133 0x7edc1820 SendMessageTimeoutW+0x1a0() in user32 (0x0029614c)
  134 0x7edc1890 SendMessageW+0x50() in user32 (0x0029618c)
  135 0x7edef25e USER_SetWindowPos+0x87e() in user32 (0x002962ac)
  136 0x7edefbc2 SetWindowPos+0xa2() in user32 (0x0029631c)
  137 0x7edf014f in user32 (+0xa014f) (0x0029634c)
  138 0x7ede813e EnumWindows+0x6e() in user32 (0x0029637c)
  139 0x7edef85e USER_SetWindowPos+0xe7e() in user32 (0x0029649c)
  140 0x7edefbc2 SetWindowPos+0xa2() in user32 (0x0029650c)
  141 0x00443622 in xmplay (+0x43622) (0x002a01bc)
  142 0x7edf0dfa WINPROC_wrapper+0x1a() in user32 (0x002a01ec)
  143 0x7edf158e in user32 (+0xa158e) (0x002a022c)
  144 0x7edf5c5b in user32 (+0xa5c5b) (0x002a06fc)
  145 0x7edf67fa CallWindowProcW+0xaa() in user32 (0x002a073c)
  146 0x7edbdac8 in user32 (+0x6dac8) (0x002a07ac)
  147 0x7edc1820 SendMessageTimeoutW+0x1a0() in user32 (0x002a081c)
  148 0x7edc1890 SendMessageW+0x50() in user32 (0x002a085c)
  149 0x7edef25e USER_SetWindowPos+0x87e() in user32 (0x002a097c)
  150 0x7edefbc2 SetWindowPos+0xa2() in user32 (0x002a09ec)
  151 0x7edf014f in user32 (+0xa014f) (0x002a0a1c)
  152 0x7ede813e EnumWindows+0x6e() in user32 (0x002a0a4c)
  153 0x7edef85e USER_SetWindowPos+0xe7e() in user32 (0x002a0b6c)
  154 0x7edefbc2 SetWindowPos+0xa2() in user32 (0x002a0bdc)
  155 0x00443622 in xmplay (+0x43622) (0x002aa88c)
  156 0x7edf0dfa WINPROC_wrapper+0x1a() in user32 (0x002aa8bc)
  157 0x7edf158e in user32 (+0xa158e) (0x002aa8fc)
  158 0x7edf5c5b in user32 (+0xa5c5b) (0x002aadcc)
  159 0x7edf67fa CallWindowProcW+0xaa() in user32 (0x002aae0c)
  160 0x7edbdac8 in user32 (+0x6dac8) (0x002aae7c)
  161 0x7edc1820 SendMessageTimeoutW+0x1a0() in user32 (0x002aaeec)
  162 0x7edc1890 SendMessageW+0x50() in user32 (0x002aaf2c)
  163 0x7edef25e USER_SetWindowPos+0x87e() in user32 (0x002ab04c)
  164 0x7edefbc2 SetWindowPos+0xa2() in user32 (0x002ab0bc)
  165 0x7edf014f in user32 (+0xa014f) (0x002ab0ec)
  166 0x7ede813e EnumWindows+0x6e() in user32 (0x002ab11c)
  167 0x7edef85e USER_SetWindowPos+0xe7e() in user32 (0x002ab23c)
  168 0x7edefbc2 SetWindowPos+0xa2() in user32 (0x002ab2ac)
  169 0x00443622 in xmplay (+0x43622) (0x002b4f5c)
  170 0x7edf0dfa WINPROC_wrapper+0x1a() in user32 (0x002b4f8c)
  171 0x7edf158e in user32 (+0xa158e) (0x002b4fcc)
  172 0x7edf5c5b in user32 (+0xa5c5b) (0x002b549c)
  173 0x7edf67fa CallWindowProcW+0xaa() in user32 (0x002b54dc)
  174 0x7edbdac8 in user32 (+0x6dac8) (0x002b554c)
  175 0x7edc1820 SendMessageTimeoutW+0x1a0() in user32 (0x002b55bc)
  176 0x7edc1890 SendMessageW+0x50() in user32 (0x002b55fc)
  177 0x7edef25e USER_SetWindowPos+0x87e() in user32 (0x002b571c)
  178 0x7edefbc2 SetWindowPos+0xa2() in user32 (0x002b578c)
  179 0x7edf014f in user32 (+0xa014f) (0x002b57bc)
  180 0x7ede813e EnumWindows+0x6e() in user32 (0x002b57ec)
  181 0x7edef85e USER_SetWindowPos+0xe7e() in user32 (0x002b590c)
  182 0x7edefbc2 SetWindowPos+0xa2() in user32 (0x002b597c)
  183 0x00443622 in xmplay (+0x43622) (0x002bf62c)
  184 0x7edf0dfa WINPROC_wrapper+0x1a() in user32 (0x002bf65c)
  185 0x7edf158e in user32 (+0xa158e) (0x002bf69c)
  186 0x7edf5c5b in user32 (+0xa5c5b) (0x002bfb6c)
  187 0x7edf67fa CallWindowProcW+0xaa() in user32 (0x002bfbac)
  188 0x7edbdac8 in user32 (+0x6dac8) (0x002bfc1c)
  189 0x7edc1820 SendMessageTimeoutW+0x1a0() in user32 (0x002bfc8c)
  190 0x7edc1890 SendMessageW+0x50() in user32 (0x002bfccc)
  191 0x7edef25e USER_SetWindowPos+0x87e() in user32 (0x002bfdec)
  192 0x7edefbc2 SetWindowPos+0xa2() in user32 (0x002bfe5c)
  193 0x7edf014f in user32 (+0xa014f) (0x002bfe8c)
  194 0x7ede813e EnumWindows+0x6e() in user32 (0x002bfebc)
  195 0x7edef85e USER_SetWindowPos+0xe7e() in user32 (0x002bffdc)
  196 0x7edefbc2 SetWindowPos+0xa2() in user32 (0x002c004c)
  197 0x00443622 in xmplay (+0x43622) (0x002c9cfc)
  198 0x7edf0dfa WINPROC_wrapper+0x1a() in user32 (0x002c9d2c)
  199 0x7edf158e in user32 (+0xa158e) (0x002c9d6c)
  200 0x7edf5c5b in user32 (+0xa5c5b) (0x002ca23c)
  201 0x7edf67fa CallWindowProcW+0xaa() in user32 (0x002ca27c)
0x00445057: testl       %eax,0x0(%ecx)
Modules:
Module  Address                 Debug info      Name (91 modules)
PE        340000-  349000       Deferred        xmp-cd
PE        350000-  357000       Deferred        xmp-wadsp
PE        400000-  553000       Export          xmplay
PE      10000000-10007000       Deferred        xmp-wma
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bc98000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc98000       \               ntdll
ELF     7bd06000-7bd57000       Deferred        libgcrypt.so.11
ELF     7bd57000-7bd6c000       Deferred        libtasn1.so.3
ELF     7bd6c000-7bd9a000       Deferred        libcrypt.so.1
ELF     7bd9a000-7be0a000       Deferred        libgnutls.so.13
ELF     7be0a000-7be3b000       Deferred        libcups.so.2
ELF     7be3b000-7bf00000       Deferred        libasound.so.2
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf52000-7bf84000       Deferred        uxtheme<elf>
  \-PE  7bf60000-7bf84000       \               uxtheme
ELF     7bf84000-7bf99000       Deferred        midimap<elf>
  \-PE  7bf90000-7bf99000       \               midimap
ELF     7bf99000-7bfb1000       Deferred        msacm32<elf>
  \-PE  7bfa0000-7bfb1000       \               msacm32
ELF     7bfb1000-7bfe3000       Deferred        winealsa<elf>
  \-PE  7bfc0000-7bfe3000       \               winealsa
ELF     7bfe3000-7c000000       Deferred        imm32<elf>
  \-PE  7bff0000-7c000000       \               imm32
ELF     7c2e0000-7c2e4000       Deferred        libgpg-error.so.0
ELF     7c2e9000-7c2f2000       Deferred        libxcursor.so.1
ELF     7ccf4000-7ccf9000       Deferred        libxfixes.so.3
ELF     7ccf9000-7ccff000       Deferred        libxrandr.so.2
ELF     7cdff000-7ce02000       Deferred        libxinerama.so
ELF     7d7d2000-7d7db000       Deferred        librt.so.1
ELF     7d7db000-7d7e3000       Deferred        libxrender.so.1
ELF     7d8a6000-7e205000       Deferred        fglrx_dri.so
ELF     7e205000-7e2a5000       Deferred        libgl.so.1
ELF     7e2a5000-7e2aa000       Deferred        libxdmcp.so.6
ELF     7e2aa000-7e2ad000       Deferred        libxau.so.6
ELF     7e2ad000-7e39e000       Deferred        libx11.so.6
ELF     7e39e000-7e3ac000       Deferred        libxext.so.6
ELF     7e3ac000-7e3b1000       Deferred        libxxf86vm.so.1
ELF     7e3b1000-7e3c9000       Deferred        libice.so.6
ELF     7e3c9000-7e3d2000       Deferred        libsm.so.6
ELF     7e3d2000-7e461000       Deferred        winex11<elf>
  \-PE  7e3e0000-7e461000       \               winex11
ELF     7e4c4000-7e4e4000       Deferred        libexpat.so.1
ELF     7e4e4000-7e50f000       Deferred        libfontconfig.so.1
ELF     7e50f000-7e523000       Deferred        libz.so.1
ELF     7e523000-7e58e000       Deferred        libfreetype.so.6
ELF     7e58e000-7e5f5000       Deferred        msvcrt<elf>
  \-PE  7e5a0000-7e5f5000       \               msvcrt
ELF     7e5f5000-7e61b000       Deferred        msacm32<elf>
  \-PE  7e600000-7e61b000       \               msacm32
ELF     7e61b000-7e63b000       Deferred        mpr<elf>
  \-PE  7e620000-7e63b000       \               mpr
ELF     7e63b000-7e684000       Deferred        wininet<elf>
  \-PE  7e650000-7e684000       \               wininet
ELF     7e684000-7e697000       Deferred        libresolv.so.2
ELF     7e697000-7e6b5000       Deferred        iphlpapi<elf>
  \-PE  7e6a0000-7e6b5000       \               iphlpapi
ELF     7e6b5000-7e70a000       Deferred        rpcrt4<elf>
  \-PE  7e6c0000-7e70a000       \               rpcrt4
ELF     7e70a000-7e7a9000       Deferred        ole32<elf>
  \-PE  7e720000-7e7a9000       \               ole32
ELF     7e7a9000-7e7dc000       Deferred        winspool<elf>
  \-PE  7e7b0000-7e7dc000       \               winspool
ELF     7e7dc000-7e899000       Deferred        comctl32<elf>
  \-PE  7e7f0000-7e899000       \               comctl32
ELF     7e899000-7e8f2000       Deferred        shlwapi<elf>
  \-PE  7e8b0000-7e8f2000       \               shlwapi
ELF     7e8f2000-7e9ef000       Deferred        shell32<elf>
  \-PE  7e900000-7e9ef000       \               shell32
ELF     7e9ef000-7ea90000       Deferred        comdlg32<elf>
  \-PE  7ea00000-7ea90000       \               comdlg32
ELF     7ea90000-7eb1f000       Deferred        winmm<elf>
  \-PE  7eaa0000-7eb1f000       \               winmm
ELF     7eb1f000-7eb67000       Deferred        advapi32<elf>
  \-PE  7eb30000-7eb67000       \               advapi32
ELF     7eb67000-7eb73000       Deferred        libgcc_s.so.1
ELF     7ec6e000-7ed2e000       Deferred        gdi32<elf>
  \-PE  7ec90000-7ed2e000       \               gdi32
ELF     7ed2e000-7ee6b000       Export          user32<elf>
  \-PE  7ed50000-7ee6b000       \               user32
ELF     7ef9c000-7efa7000       Deferred        libnss_files.so.2
ELF     7efa7000-7efb1000       Deferred        libnss_nis.so.2
ELF     7efb1000-7efc8000       Deferred        libnsl.so.1
ELF     7efc8000-7efef000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7c89000-b7c8d000       Deferred        libdl.so.2
ELF     b7c8d000-b7dce000       Deferred        libc.so.6
ELF     b7dcf000-b7de6000       Deferred        libpthread.so.0
ELF     b7df7000-b7f0b000       Deferred        libwine.so.1
ELF     b7f0d000-b7f28000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) Z:\home\coral\Desktop\XMPLAY\xmplay.exe
        00000009    0 <==

```

A lot of my friends has got it working, what's wrong?

---

