---
title: "Can't run WINE"
date: 2008-01-14
forum: General Help
---

### Post by DrQuincy on 2008-01-14
I can't seem to run anything with wine. If I try to run anything or run the config I get this:

```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
wine: Unhandled page fault on read access to 0x00000014 at address 0x7e0df6be (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000014 in 32-bit code (0x7e0df6be).
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801b8,symt:0x4c1654)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801b8,symt:0x4c1654)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801b8,symt:0x4c1654)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801b8,symt:0x4c1780)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801b8,symt:0x4c1780)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801b8,symt:0x4c1780)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480190,symt:0x4c15c8)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480190,symt:0x4c15c8)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480190,symt:0x4c15c8)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c18b8)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c18b8)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c18b8)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c18b8)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c199c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c199c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c199c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c199c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c1a80)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c1a80)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c1a80)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c1a80)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c1be4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c1be4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c1be4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c21ac)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c21ac)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c21ac)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c21ac)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c25c8)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c25c8)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c25c8)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c267c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c267c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c267c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c27cc)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c27cc)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c27cc)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c2a7c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c2a7c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c2a7c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c2a7c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c2b7c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c2b7c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c2b7c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c2b7c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c2cec)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c2cec)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c2cec)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c2cec)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c2e8c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c2e8c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c2e8c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c2e8c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c2f80)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c2f80)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c2f80)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c31a4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c31a4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c31a4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c31a4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c32d8)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c32d8)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c32d8)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c32d8)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c3454)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c3454)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c3454)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c3454)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c3a68)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c3a68)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c3a68)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c3a68)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c3b58)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c3b58)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c3b58)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c3c2c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c3c2c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c3c2c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c3d18)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c3d18)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c3d18)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c3d18)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4809f8,symt:0x4c3f4c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4809f8,symt:0x4c3f4c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4809f8,symt:0x4c3f4c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4809f8,symt:0x4c4124)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4809f8,symt:0x4c4124)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4809f8,symt:0x4c4124)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c477c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c477c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c477c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c4c04)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c4c04)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c4c04)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c4c04)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c4c04)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c50dc)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c50dc)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c50dc)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480190,symt:0x4c59cc)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480190,symt:0x4c59cc)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480190,symt:0x4c59cc)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c5d30)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c5d30)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4c5d30)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4809f8,symt:0x4c7334)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4809f8,symt:0x4c7334)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4809f8,symt:0x4c7334)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4809f8,symt:0x4c7334)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4813d0,symt:0x4c75f8)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __gxx_exception_class (a)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801b8,symt:0x4c9f48)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801b8,symt:0x4c9f48)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801b8,symt:0x4c9f48)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801b8,symt:0x4ca074)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801b8,symt:0x4ca074)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801b8,symt:0x4ca074)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480190,symt:0x4c9ebc)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480190,symt:0x4c9ebc)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480190,symt:0x4c9ebc)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4ca1ac)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4ca1ac)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4ca1ac)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4ca1ac)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4ca290)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4ca290)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4ca290)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4ca290)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4ca3f4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4ca3f4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4ca3f4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4ca3f4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4ca4d8)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4ca4d8)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4ca4d8)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4caa20)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4caa20)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4caa20)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4caa20)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cae3c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cae3c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cae3c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4caef0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4caef0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4caef0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cb040)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cb040)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cb040)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cb2f0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cb2f0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cb2f0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cb2f0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cb470)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cb470)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cb470)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cb470)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cb560)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cb560)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cb560)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cb560)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cb700)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cb700)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cb700)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cb700)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cb7f4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cb7f4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cb7f4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cba18)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cba18)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cba18)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cba18)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cbb4c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cbb4c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cbb4c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cbb4c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cbd48)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cbd48)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cbd48)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cbd48)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cc2dc)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cc2dc)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cc2dc)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cc2dc)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cc3cc)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cc3cc)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cc3cc)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cc4a0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cc4a0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cc4a0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cc60c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cc60c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cc60c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cc60c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4809ec,symt:0x4cc7c0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4809ec,symt:0x4cc7c0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4809ec,symt:0x4cc7c0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4809ec,symt:0x4cc998)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4809ec,symt:0x4cc998)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4809ec,symt:0x4cc998)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cd0f0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cd0f0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cd0f0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cd578)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cd578)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cd578)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cd578)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cd578)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cda50)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cda50)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4802bc,symt:0x4cda50)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __gxx_exception_class (a)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801f4,symt:0x4cf75c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801f4,symt:0x4cf75c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801f4,symt:0x4cf75c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801f4,symt:0x4cfc6c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801f4,symt:0x4cfc6c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801f4,symt:0x4cfc6c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801f4,symt:0x4cfc6c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801f4,symt:0x4cfc6c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801f4,symt:0x4bfe98)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801f4,symt:0x4bfe98)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801f4,symt:0x4bfe98)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __gxx_exception_class (a)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x1c at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x490e3c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x490e3c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x490e3c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x490e3c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x490e3c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x490e3c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x490e3c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x490e3c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x490e3c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x490e3c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x490e3c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801cc,symt:0x490cc0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801cc,symt:0x490cc0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801cc,symt:0x490cc0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801cc,symt:0x490cc0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801cc,symt:0x490cc0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801cc,symt:0x490cc0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x1c at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480370,symt:0x491164)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480370,symt:0x491164)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480370,symt:0x491164)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480370,symt:0x491164)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480370,symt:0x491164)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480370,symt:0x491164)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480370,symt:0x491164)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480370,symt:0x491164)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801cc,symt:0x491410)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801cc,symt:0x491410)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x4801cc,symt:0x491410)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x491460)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x491460)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x491460)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x491460)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x491460)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x491460)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x491460)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x491460)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x491460)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x491460)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x491460)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x491460)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x1c at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x491604)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x491604)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x491604)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x491604)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x491604)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x1c at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x491644)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x491644)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x491644)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x491644)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34efb4,L"libgl.so.1"), for debug_info(abbrev:0x480280,symt:0x491644)
wine: Unhandled page fault on read access to 0x00000000 at address 0xb7cd9583 (thread 000b), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0xb7cd9583).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b7cd9583 ESP:0034ed7c EBP:0034ed98 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:7ee11388 ECX:00000000 EDX:00490038
 ESI:004916b0 EDI:00000000
Stack dump:
0x0034ed7c:  7ee04685 00000000 7ee0be98 7ee0be98
0x0034ed8c:  7ee11388 004916b0 0013728c 0034edd8
0x0034ed9c:  7ee05a4c 0013728c 00000000 00000725
0x0034edac:  7ee11388 7ee11388 0049168c 0034edd8
0x0034edbc:  7ee0a22f 00491694 00000004 7ee059eb
0x0034edcc:  7ee11388 00000000 00487130 0034eef8
Backtrace:
=>1 0xb7cd9583 strlen+0x33() in libc.so.6 (0x0034ed98)
  2 0x7ee05a4c symt_new_function+0x6c(module=0x1364c0, compiland=0x490ab8, name=0x0, addr=0x7e168230, size=0x7, sig_type=0x49168c) [/build/buildd/wine-0.9.46/dlls/dbghelp/symbol.c:233] in dbghelp (0x0034edd8)
  3 0x7edeb1c3 dwarf2_load_one_entry+0xf03(ctx=0x34efb4, di=<register EDI not in topmost frame>, compiland=0x490ab8) [/build/buildd/wine-0.9.46/dlls/dbghelp/dwarf.c:1562] in dbghelp (0x0034eef8)
  4 0x7edecd33 dwarf2_parse+0xc13(module=0x1364c0, load_offset=0x7d49f000, thunks=0x34f220, debug=0x7eb14725, debug_size=0x292d5, abbrev=0x7efea9fa, abbrev_size=0x2d80, str=0x7eb072bc, str_size=0xbd9f, line=0x7eb0177a, line_size=0x5138, loclist=0xffffffff, loclist_size=0x0) [/build/buildd/wine-0.9.46/dlls/dbghelp/dwarf.c:2009] in dbghelp (0x0034f0f8)
  5 0x7edee7f9 elf_load_debug_info+0x829(module=0x1364c0, fmap=0x34f318) [/build/buildd/wine-0.9.46/dlls/dbghelp/elf_module.c:1092] in dbghelp (0x0034f378)
  6 0x7edf34eb module_get_debug+0x18b(pair=<register EDI not in topmost frame>) [/build/buildd/wine-0.9.46/dlls/dbghelp/module.c:303] in dbghelp (0x0034f5d8)
  7 0x7ee079d7 SymFromAddr+0x57(hProcess=0x24, Address=<register ESI not in topmost frame>, Displacement=0x34f6c8, Symbol=0x34f700) [/build/buildd/wine-0.9.46/dlls/dbghelp/symbol.c:1043] in dbghelp (0x0034f618)
  8 0x7ee4549d stack_get_current_symbol+0x5d(symbol=0x34f700) [/build/buildd/wine-0.9.46/programs/winedbg/stack.c:143] in winedbg (0x0034f6d8)
  9 0x7ee36928 display_print+0x68() [/build/buildd/wine-0.9.46/programs/winedbg/display.c:174] in winedbg (0x0034f868)
  10 0x7ee475bc wait_exception+0x10ec() [/build/buildd/wine-0.9.46/programs/winedbg/tgt_active.c:180] in winedbg (0x0034fbf8)
  11 0x7ee482ea dbg_active_auto+0x2aa(argc=0x3, argv=<is not available>) [/build/buildd/wine-0.9.46/programs/winedbg/tgt_active.c:951] in winedbg (0x0034fe58)
  12 0x7ee4ca41 main+0x4e1(argc=0x3, argv=0x1103ac) [/build/buildd/wine-0.9.46/programs/winedbg/winedbg.c:544] in winedbg (0x0034fed8)
  13 0x7ee5161b __wine_spec_exe_entry+0x5b(peb=0x7ffdf000) [/build/buildd/wine-0.9.46/dlls/winecrt0/exe_entry.c:36] in winedbg (0x0034ff08)
  14 0x7b874c7e start_process+0xee(arg=0x0) [/build/buildd/wine-0.9.46/dlls/kernel32/process.c:839] in kernel32 (0x0034ffe8)
  15 0xb7de99d7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0xb7cd9583 strlen+0x33 in libc.so.6: movl       0x0(%eax),%ecx
Modules:
Module  Address                 Debug info      Name (23 modules)
ELF     7b800000-7b929000       Dwarf           kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7ed87000-7edd0000       Deferred        advapi32<elf>
  \-PE  7ed90000-7edd0000       \               advapi32
ELF     7edd0000-7ee1a000       Dwarf           dbghelp<elf>
  \-PE  7ede0000-7ee1a000       \               dbghelp
ELF     7ee1a000-7ee64000       Dwarf           winedbg<elf>
  \-PE  7ee30000-7ee64000       \               winedbg
ELF     7ee64000-7ee6f000       Deferred        libnss_files.so.2
ELF     7ee6f000-7ee87000       Deferred        libnsl.so.1
ELF     7ee87000-7ee90000       Deferred        libnss_compat.so.2
ELF     7ee91000-7eea6000       Deferred        psapi<elf>
  \-PE  7eea0000-7eea6000       \               psapi
ELF     7efc5000-7efea000       Deferred        libm.so.6
ELF     7efef000-7eff9000       Deferred        libnss_nis.so.2
ELF     b7c65000-b7c69000       Deferred        libdl.so.2
ELF     b7c69000-b7db3000       Export          libc.so.6
ELF     b7db4000-b7dcc000       Deferred        libpthread.so.0
ELF     b7de2000-b7ef6000       Dwarf           libwine.so.1
ELF     b7ef8000-b7f14000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a (D) c:\windows\system32\winedbg.exe
        0000000b    0 <==
00000008 
        00000009    0

```

I've tried removing and reinstalling. Any ideas? I'm on Ubuntu Gutsy.

---

### Post by Sef on 2008-01-14
1) How are you installing and removing it?

2) What are your system specs?

3) What *buntu and version are you using?

---

### Post by DrQuincy on 2008-01-14
Hi there, sorry for the lack of information.

**1) How are you installing and removing it?**
Through the shell, *sudo apt-get install wine*

**2) What are your system specs?**
AMD Athlon Dual Core 4200+ with ATI X1300 Pro

**3) What *buntu and version are you using?**
I'm on Gnome (i.e. Ubuntu) but running Compiz Fusion under XGL (if that matters.). 32-bit version.

---

### Post by Cleanser23 on 2008-01-14
there is your issue right there, you are running 64 bit and the aptitude is arch 32, so you have to get the tarball and compile yourself so it uses 64 bit libs and stuff.

---

### Post by DrQuincy on 2008-01-14
I'm running the 32-bit version of Ubuntu though. Does that matter?

---

### Post by ubu-for on 2008-01-14
Uninstall Wine and try a version from [this site](http://wine.budgetdedicated.com/archive/index.html).

---

