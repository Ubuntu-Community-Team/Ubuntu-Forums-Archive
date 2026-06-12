---
title: "WineX cvs"
date: 2004-10-29
forum: General Help
---

### Post by jayclark on 2004-10-29
Has anyone  been able to install Winex CVs on Ubuntu? I can't seem to get it installed without it running into errors.

---

### Post by cacofonix on 2004-10-29
What are the errors your getting Jay?

---

### Post by jdong on 2004-10-30
I'll answer that one:

```

jdong@jd64:~/dnld/winex/winex $ make
make[1]: Entering directory `/home/jdong/Downloads/winex/winex/unicode'
make[1]: `libwine_unicode.so' is up to date.
make[1]: Leaving directory `/home/jdong/Downloads/winex/winex/unicode'
make[1]: Entering directory `/home/jdong/Downloads/winex/winex/tools'
make[2]: Entering directory `/home/jdong/Downloads/winex/winex/tools/winebuild'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/jdong/Downloads/winex/winex/tools/winebuild'
make[2]: Entering directory `/home/jdong/Downloads/winex/winex/tools/winedump'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/jdong/Downloads/winex/winex/tools/winedump'
make[2]: Entering directory `/home/jdong/Downloads/winex/winex/tools/wmc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/jdong/Downloads/winex/winex/tools/wmc'
make[2]: Entering directory `/home/jdong/Downloads/winex/winex/tools/wrc'
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REENTRANT -I/usr/X11R6/include -o lex.ppl.o lex.ppl.c
./ppl.l:82:1: warning: "/*" within comment
./ppl.l:91:2: #endif without #if
./ppl.l: In function `pplex':
./ppl.l:305: error: `seen_junk' undeclared (first use in this function)
./ppl.l:305: error: (Each undeclared identifier is reported only once
./ppl.l:305: error: for each function it appears in.)
./ppl.l:305: error: `pp_pp' undeclared (first use in this function)
./ppl.l:310: error: `pp_ignore' undeclared (first use in this function)
./ppl.l:310: warning: implicit declaration of function `yy_pp_state'
./ppl.l:310: error: `pp_inc' undeclared (first use in this function)
./ppl.l:310: error: `tINCLUDE' undeclared (first use in this function)
./ppl.l:310: error: `pp_eol' undeclared (first use in this function)
./ppl.l:311: error: called object is not a function
./ppl.l:311: error: `pp_def' undeclared (first use in this function)
./ppl.l:312: error: `tERROR' undeclared (first use in this function)
./ppl.l:313: error: `tWARNING' undeclared (first use in this function)
./ppl.l:314: error: `tPRAGMA' undeclared (first use in this function)
./ppl.l:315: error: `tPPIDENT' undeclared (first use in this function)
./ppl.l:316: error: `pp_ifd' undeclared (first use in this function)
./ppl.l:316: error: `tUNDEF' undeclared (first use in this function)
./ppl.l:317: error: `tIFDEF' undeclared (first use in this function)
./ppl.l:318: error: `tIFNDEF' undeclared (first use in this function)
./ppl.l:319: error: `pp_if' undeclared (first use in this function)
./ppl.l:319: error: `tIF' undeclared (first use in this function)
./ppl.l:320: error: `tELIF' undeclared (first use in this function)
./ppl.l:321: error: `tELSE' undeclared (first use in this function)
./ppl.l:322: error: `tENDIF' undeclared (first use in this function)
./ppl.l:323: error: `pp_line' undeclared (first use in this function)
./ppl.l:323: error: `tLINE' undeclared (first use in this function)
./ppl.l:324: error: `tGCCLINE' undeclared (first use in this function)
./ppl.l:325: warning: implicit declaration of function `pperror'
./ppl.l:326: warning: implicit declaration of function `newline'
./ppl.l:326: error: `tNL' undeclared (first use in this function)
./ppl.l:334: warning: implicit declaration of function `make_number'
./ppl.l:334: error: `pplval' undeclared (first use in this function)
./ppl.l:335: warning: implicit declaration of function `new_string'
./ppl.l:335: warning: implicit declaration of function `add_string'
./ppl.l:335: error: `pp_iqs' undeclared (first use in this function)
./ppl.l:336: error: `pp_dqs' undeclared (first use in this function)
./ppl.l:340: error: called object is not a function
./ppl.l:362: error: `pp_defined' undeclared (first use in this function)
./ppl.l:362: error: `tDEFINED' undeclared (first use in this function)
./ppl.l:363: error: `tLSHIFT' undeclared (first use in this function)
./ppl.l:364: error: `tRSHIFT' undeclared (first use in this function)
./ppl.l:365: error: `tLOGAND' undeclared (first use in this function)
./ppl.l:366: error: `tLOGOR' undeclared (first use in this function)
./ppl.l:367: error: `tEQ' undeclared (first use in this function)
./ppl.l:368: error: `tNE' undeclared (first use in this function)
./ppl.l:369: error: `tLTE' undeclared (first use in this function)
./ppl.l:370: error: `tGTE' undeclared (first use in this function)
./ppl.l:375: error: `pp_sqs' undeclared (first use in this function)
./ppl.l:383: warning: implicit declaration of function `xstrdup'
./ppl.l:383: error: `tIDENT' undeclared (first use in this function)
./ppl.l:406: error: `tLITERAL' undeclared (first use in this function)
./ppl.l:409: error: called object is not a function
./ppl.l:415: error: `pp_macro' undeclared (first use in this function)
./ppl.l:415: error: `tMACRO' undeclared (first use in this function)
./ppl.l:416: error: `pp_define' undeclared (first use in this function)
./ppl.l:416: error: `tDEFINE' undeclared (first use in this function)
./ppl.l:435: error: `pp_mbody' undeclared (first use in this function)
./ppl.l:435: error: `tMACROEND' undeclared (first use in this function)
./ppl.l:439: error: `tELIPSIS' undeclared (first use in this function)
./ppl.l:448: error: `tCONCAT' undeclared (first use in this function)
./ppl.l:449: error: `tSTRINGIZE' undeclared (first use in this function)
./ppl.l:467: error: `pp_macscan' undeclared (first use in this function)
./ppl.l:474: error: `macexpstackentry_t' undeclared (first use in this function)./ppl.l:474: error: `mac' undeclared (first use in this function)
./ppl.l:474: warning: implicit declaration of function `pop_macro'
./ppl.l:476: warning: implicit declaration of function `put_buffer'
./ppl.l:478: warning: implicit declaration of function `free_macro'
./ppl.l:486: warning: implicit declaration of function `MACROPARENTHESES'
./ppl.l:486: error: invalid lvalue in increment
./ppl.l:487: warning: implicit declaration of function `add_text_to_macro'
./ppl.l:490: error: invalid lvalue in decrement
./ppl.l:493: warning: implicit declaration of function `macro_add_arg'
./ppl.l:506: error: `pp_comment' undeclared (first use in this function)
./ppl.l:507: error: `line_number' undeclared (first use in this function)
./ppl.l:507: error: `char_number' undeclared (first use in this function)
./ppl.l:524: warning: implicit declaration of function `ppwarning'
./ppl.l:536: error: called object is not a function
./ppl.l:543: error: `RCINCL' undeclared (first use in this function)
./ppl.l:544: error: called object is not a function
./ppl.l:545: warning: implicit declaration of function `get_string'
./ppl.l:546: error: `tDQSTRING' undeclared (first use in this function)
./ppl.l:548: warning: implicit declaration of function `put_string'
./ppl.l:555: error: called object is not a function
./ppl.l:561: error: `tSQSTRING' undeclared (first use in this function)
./ppl.l:571: error: `tIQSTRING' undeclared (first use in this function)
./ppl.l:601: warning: implicit declaration of function `string_start'
./ppl.l:608: error: `pp_entry_t' undeclared (first use in this function)
./ppl.l:608: error: `ppp' undeclared (first use in this function)
./ppl.l:610: warning: implicit declaration of function `pplookup'
./ppl.l:612: error: called object is not a function
./ppl.l:615: error: called object is not a function
./ppl.l:621: error: called object is not a function
./ppl.l:621: error: `INITIAL' undeclared (first use in this function)
./ppl.l:623: error: `tRCINCLUDE' undeclared (first use in this function)
./ppl.l:632: error: `def_special' undeclared (first use in this function)
./ppl.l:633: warning: implicit declaration of function `expand_special'
./ppl.l:635: error: `def_define' undeclared (first use in this function)
./ppl.l:636: warning: implicit declaration of function `expand_define'
./ppl.l:638: error: `def_macro' undeclared (first use in this function)
./ppl.l:639: error: `pp_macign' undeclared (first use in this function)
./ppl.l:640: warning: implicit declaration of function `push_macro'
./ppl.l:643: warning: implicit declaration of function `internal_error'
./ppl.l:667: error: `tRCINCLUDEPATH' undeclared (first use in this function)
./ppl.l:680: warning: implicit declaration of function `isprint'
./ppl.l:696: error: `pp_macexp' undeclared (first use in this function)
./ppl.l:684: error: `bufferstackentry_t' undeclared (first use in this function)./ppl.l:684: error: `bep' undeclared (first use in this function)
./ppl.l:684: warning: implicit declaration of function `pop_buffer'
./ppl.l:686: warning: implicit declaration of function `get_if_depth'
./ppl.l:699: warning: implicit declaration of function `expand_macro'
./ppl.l: At top level:
./ppl.l:730: warning: `newline' was declared implicitly `extern' and later `static'
./ppl.l:326: warning: previous declaration of `newline'
./ppl.l:730: warning: type mismatch with previous implicit declaration
./ppl.l:326: warning: previous implicit declaration of `newline'
./ppl.l:730: warning: `newline' was previously implicitly declared to return `int'
./ppl.l: In function `newline':
./ppl.l:731: error: `line_number' undeclared (first use in this function)
./ppl.l:732: error: `char_number' undeclared (first use in this function)
./ppl.l:737: error: `ncontinuations' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:770: error: parse error before "YYSTYPE"
./ppl.l:771: warning: `make_number' was declared implicitly `extern' and later `static'
./ppl.l:334: warning: previous declaration of `make_number'
./ppl.l: In function `make_number':
./ppl.l:778: warning: implicit declaration of function `toupper'
./ppl.l:778: error: `str' undeclared (first use in this function)
./ppl.l:778: error: `len' undeclared (first use in this function)
./ppl.l:812: error: `val' undeclared (first use in this function)
./ppl.l:812: error: `radix' undeclared (first use in this function)
./ppl.l:813: error: `tULONG' undeclared (first use in this function)
./ppl.l:818: error: `tSLONG' undeclared (first use in this function)
./ppl.l:823: error: `win32' undeclared (first use in this function)
./ppl.l:827: error: `tUINT' undeclared (first use in this function)
./ppl.l:841: error: `tSINT' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:852: error: parse error before '*' token
./ppl.l:853: warning: `expand_special' was declared implicitly `extern' and later `static'
./ppl.l:633: warning: previous declaration of `expand_special'
./ppl.l:853: warning: type mismatch with previous implicit declaration
./ppl.l:633: warning: previous implicit declaration of `expand_special'
./ppl.l:853: warning: `expand_special' was previously implicitly declared to return `int'
./ppl.l: In function `expand_special':
./ppl.l:857: warning: implicit declaration of function `assert'
./ppl.l:857: error: `ppp' undeclared (first use in this function)
./ppl.l:857: error: `def_special' undeclared (first use in this function)
./ppl.l:862: warning: implicit declaration of function `xrealloc'
./ppl.l:862: warning: assignment makes pointer from integer without a cast
./ppl.l:863: error: `line_number' undeclared (first use in this function)
./ppl.l:868: error: `input_name' undeclared (first use in this function)
./ppl.l:868: warning: assignment makes pointer from integer without a cast
./ppl.l:874: warning: assignment makes pointer from integer without a cast
./ppl.l:875: warning: implicit declaration of function `strftime'
./ppl.l:875: warning: implicit declaration of function `localtime'
./ppl.l:875: error: `now' undeclared (first use in this function)
./ppl.l:880: warning: assignment makes pointer from integer without a cast
./ppl.l:886: error: `debuglevel' undeclared (first use in this function)
./ppl.l:886: error: `DEBUGLEVEL_PPLEX' undeclared (first use in this function)
./ppl.l:888: error: `macexpstackidx' undeclared (first use in this function)
./ppl.l:896: warning: implicit declaration of function `push_buffer'
./ppl.l: At top level:
./ppl.l:901: error: parse error before '*' token
./ppl.l:902: warning: `expand_define' was declared implicitly `extern' and later `static'
./ppl.l:636: warning: previous declaration of `expand_define'
./ppl.l:902: warning: type mismatch with previous implicit declaration
./ppl.l:636: warning: previous implicit declaration of `expand_define'
./ppl.l:902: warning: `expand_define' was previously implicitly declared to return `int'
./ppl.l: In function `expand_define':
./ppl.l:903: error: `ppp' undeclared (first use in this function)
./ppl.l:903: error: `def_define' undeclared (first use in this function)
./ppl.l:905: error: `debuglevel' undeclared (first use in this function)
./ppl.l:905: error: `DEBUGLEVEL_PPLEX' undeclared (first use in this function)
./ppl.l:907: error: `macexpstackidx' undeclared (first use in this function)
./ppl.l:908: error: `input_name' undeclared (first use in this function)
./ppl.l:909: error: `line_number' undeclared (first use in this function)
./ppl.l: In function `add_text':
./ppl.l:929: error: `ALLOCBLOCKSIZE' undeclared (first use in this function)
./ppl.l:930: warning: assignment makes pointer from integer without a cast
./ppl.l: At top level:
./ppl.l:938: error: parse error before '*' token
./ppl.l:938: error: parse error before '*' token
./ppl.l:939: warning: return type defaults to `int'
./ppl.l: In function `add_expand_text':
./ppl.l:945: error: `mtp' undeclared (first use in this function)
./ppl.l:950: error: `exp_text' undeclared (first use in this function)
./ppl.l:951: error: `debuglevel' undeclared (first use in this function)
./ppl.l:951: error: `DEBUGLEVEL_PPLEX' undeclared (first use in this function)
./ppl.l:956: error: `exp_stringize' undeclared (first use in this function)
./ppl.l:960: error: `mep' undeclared (first use in this function)
./ppl.l:973: error: `exp_concat' undeclared (first use in this function)
./ppl.l:979: warning: implicit declaration of function `isspace'
./ppl.l:986: error: `nnl' undeclared (first use in this function)
./ppl.l:1008: error: `exp_subst' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1035: error: parse error before '*' token
./ppl.l:1036: warning: `expand_macro' was declared implicitly `extern' and later `static'
./ppl.l:699: warning: previous declaration of `expand_macro'
./ppl.l:1036: warning: type mismatch with previous implicit declaration
./ppl.l:699: warning: previous implicit declaration of `expand_macro'
./ppl.l:1036: warning: `expand_macro' was previously implicitly declared to return `int'
./ppl.l: In function `expand_macro':
./ppl.l:1037: error: `mtext_t' undeclared (first use in this function)
./ppl.l:1037: error: `mtp' undeclared (first use in this function)
./ppl.l:1041: error: `pp_entry_t' undeclared (first use in this function)
./ppl.l:1041: error: `ppp' undeclared (first use in this function)
./ppl.l:1041: error: `mep' undeclared (first use in this function)
./ppl.l:1044: error: `def_macro' undeclared (first use in this function)
./ppl.l:1053: error: `debuglevel' undeclared (first use in this function)
./ppl.l:1053: error: `DEBUGLEVEL_PPLEX' undeclared (first use in this function)
./ppl.l:1055: error: `macexpstackidx' undeclared (first use in this function)
./ppl.l:1056: error: `input_name' undeclared (first use in this function)
./ppl.l:1057: error: `line_number' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1114: warning: `new_string' was declared implicitly `extern' and later `static'
./ppl.l:335: warning: previous declaration of `new_string'
./ppl.l:1114: warning: type mismatch with previous implicit declaration
./ppl.l:335: warning: previous implicit declaration of `new_string'
./ppl.l:1114: warning: `new_string' was previously implicitly declared to return `int'
./ppl.l: In function `new_string':
./ppl.l:1119: error: `strbuf_idx' undeclared (first use in this function)
./ppl.l:1120: error: `str_startline' undeclared (first use in this function)
./ppl.l:1120: error: `line_number' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1124: warning: `add_string' was declared implicitly `extern' and later `static'
./ppl.l:335: warning: previous declaration of `add_string'
./ppl.l:1124: warning: type mismatch with previous implicit declaration
./ppl.l:335: warning: previous implicit declaration of `add_string'
./ppl.l:1124: warning: `add_string' was previously implicitly declared to return `int'
./ppl.l: In function `add_string':
./ppl.l:1127: error: `strbuf_idx' undeclared (first use in this function)
./ppl.l:1127: error: `strbuf_alloc' undeclared (first use in this function)
./ppl.l:1129: error: `ALLOCBLOCKSIZE' undeclared (first use in this function)
./ppl.l:1130: error: `strbuffer' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1139: warning: `get_string' was declared implicitly `extern' and later `static'
./ppl.l:570: warning: previous declaration of `get_string'
./ppl.l:1139: warning: type mismatch with previous implicit declaration
./ppl.l:570: warning: previous implicit declaration of `get_string'
./ppl.l:1139: warning: `get_string' was previously implicitly declared to return `int'
./ppl.l: In function `get_string':
./ppl.l:1140: warning: implicit declaration of function `xmalloc'
./ppl.l:1140: error: `strbuf_idx' undeclared (first use in this function)
./ppl.l:1141: error: `strbuffer' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1150: warning: `put_string' was declared implicitly `extern' and later `static'
./ppl.l:563: warning: previous declaration of `put_string'
./ppl.l:1150: warning: type mismatch with previous implicit declaration
./ppl.l:563: warning: previous implicit declaration of `put_string'
./ppl.l:1150: warning: `put_string' was previously implicitly declared to return `int'
./ppl.l: In function `put_string':
./ppl.l:1151: error: `strbuffer' undeclared (first use in this function)
./ppl.l:1151: error: `strbuf_idx' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1158: warning: `string_start' was declared implicitly `extern' and later `static'
./ppl.l:601: warning: previous declaration of `string_start'
./ppl.l: In function `string_start':
./ppl.l:1159: error: `str_startline' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1168: error: parse error before '*' token
./ppl.l:1169: warning: `push_buffer' was declared implicitly `extern' and later `static'
./ppl.l:1102: warning: previous declaration of `push_buffer'
./ppl.l:1169: warning: type mismatch with previous implicit declaration
./ppl.l:1102: warning: previous implicit declaration of `push_buffer'
./ppl.l:1169: warning: `push_buffer' was previously implicitly declared to return `int'
./ppl.l: In function `push_buffer':
./ppl.l:1170: error: `ppdebug' undeclared (first use in this function)
./ppl.l:1171: error: `bufferstackidx' undeclared (first use in this function)
./ppl.l:1171: error: `ppp' undeclared (first use in this function)
./ppl.l:1171: error: `filename' undeclared (first use in this function)
./ppl.l:1171: error: `incname' undeclared (first use in this function)
./ppl.l:1171: error: `pop' undeclared (first use in this function)
./ppl.l:1172: error: `MAXBUFFERSTACK' undeclared (first use in this function)
./ppl.l:1175: error: `bufferstack' undeclared (first use in this function)
./ppl.l:1178: error: `line_number' undeclared (first use in this function)
./ppl.l:1179: error: `char_number' undeclared (first use in this function)
./ppl.l:1182: error: `input_name' undeclared (first use in this function)
./ppl.l:1183: error: `ncontinuations' undeclared (first use in this function)
./ppl.l:1184: error: `include_state' undeclared (first use in this function)
./ppl.l:1185: error: `include_ppp' undeclared (first use in this function)
./ppl.l:1187: error: `include_ifdepth' undeclared (first use in this function)
./ppl.l:1188: error: `seen_junk' undeclared (first use in this function)
./ppl.l:1189: error: `pass_data' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1206: error: parse error before '*' token
./ppl.l:1207: warning: return type defaults to `int'
./ppl.l:1207: warning: type mismatch with previous implicit declaration
./ppl.l:684: warning: previous implicit declaration of `pop_buffer'
./ppl.l:1207: warning: `pop_buffer' was previously implicitly declared to return `int'
./ppl.l: In function `pop_buffer':
./ppl.l:1208: error: `bufferstackidx' undeclared (first use in this function)
./ppl.l:1216: error: `bufferstack' undeclared (first use in this function)
./ppl.l:1220: error: `line_number' undeclared (first use in this function)
./ppl.l:1221: error: `char_number' undeclared (first use in this function)
./ppl.l:1222: error: `input_name' undeclared (first use in this function)
./ppl.l:1223: error: `ncontinuations' undeclared (first use in this function)
./ppl.l:1230: error: `include_state' undeclared (first use in this function)
./ppl.l:1230: error: `seen_junk' undeclared (first use in this function)
./ppl.l:1230: error: `include_ppp' undeclared (first use in this function)
./ppl.l:1232: error: `pp_entry_t' undeclared (first use in this function)
./ppl.l:1232: error: `ppp' undeclared (first use in this function)
./ppl.l:1235: error: `includelogicentry_t' undeclared (first use in this function)
./ppl.l:1235: error: `iep' undeclared (first use in this function)
./ppl.l:1239: error: `includelogiclist' undeclared (first use in this function)
./ppl.l:1243: error: `debuglevel' undeclared (first use in this function)
./ppl.l:1243: error: `DEBUGLEVEL_PPMSG' undeclared (first use in this function)
./ppl.l:1253: error: `include_ifdepth' undeclared (first use in this function)
./ppl.l:1255: error: `pass_data' undeclared (first use in this function)
./ppl.l:1260: error: `ppdebug' undeclared (first use in this function)
./ppl.l:1275: warning: implicit declaration of function `yy_current_state'
./ppl.l:1275: error: `pp_macexp' undeclared (first use in this function)
./ppl.l:1276: warning: implicit declaration of function `macro_add_expansion'
./ppl.l: At top level:
./ppl.l:1291: error: parse error before '*' token
./ppl.l:1292: warning: `push_macro' was declared implicitly `extern' and later `static'
./ppl.l:640: warning: previous declaration of `push_macro'
./ppl.l:1292: warning: type mismatch with previous implicit declaration
./ppl.l:640: warning: previous implicit declaration of `push_macro'
./ppl.l:1292: warning: `push_macro' was previously implicitly declared to return `int'
./ppl.l: In function `push_macro':
./ppl.l:1293: error: `macexpstackidx' undeclared (first use in this function)
./ppl.l:1293: error: `MAXMACEXPSTACK' undeclared (first use in this function)
./ppl.l:1296: error: `macexpstack' undeclared (first use in this function)
./ppl.l:1298: error: `ppp' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1302: error: parse error before '*' token
./ppl.l:1303: warning: return type defaults to `int'
./ppl.l: In function `top_macro':
./ppl.l:1304: error: `macexpstackidx' undeclared (first use in this function)
./ppl.l:1304: error: `macexpstack' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1307: error: parse error before '*' token
./ppl.l:1308: warning: return type defaults to `int'
./ppl.l:1308: warning: type mismatch with previous implicit declaration
./ppl.l:698: warning: previous implicit declaration of `pop_macro'
./ppl.l:1308: warning: `pop_macro' was previously implicitly declared to return `int'
./ppl.l: In function `pop_macro':
./ppl.l:1309: error: `macexpstackidx' undeclared (first use in this function)
./ppl.l:1311: error: `macexpstack' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1314: error: parse error before '*' token
./ppl.l:1315: warning: `free_macro' was declared implicitly `extern' and later `static'
./ppl.l:478: warning: previous declaration of `free_macro'
./ppl.l:1315: warning: type mismatch with previous implicit declaration
./ppl.l:478: warning: previous implicit declaration of `free_macro'
./ppl.l:1315: warning: `free_macro' was previously implicitly declared to return `int'
./ppl.l: In function `free_macro':
./ppl.l:1318: error: `mep' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1330: warning: `add_text_to_macro' was declared implicitly `extern' and later `static'
./ppl.l:506: warning: previous declaration of `add_text_to_macro'
./ppl.l:1330: warning: type mismatch with previous implicit declaration
./ppl.l:506: warning: previous implicit declaration of `add_text_to_macro'
./ppl.l:1330: warning: `add_text_to_macro' was previously implicitly declared to return `int'
./ppl.l: In function `add_text_to_macro':
./ppl.l:1331: error: `macexpstackentry_t' undeclared (first use in this function)
./ppl.l:1331: error: `mep' undeclared (first use in this function)
./ppl.l:1337: warning: implicit declaration of function `max'
./ppl.l:1337: error: `ALLOCBLOCKSIZE' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1346: warning: `macro_add_arg' was declared implicitly `extern' and later `static'
./ppl.l:502: warning: previous declaration of `macro_add_arg'
./ppl.l:1346: warning: type mismatch with previous implicit declaration
./ppl.l:502: warning: previous implicit declaration of `macro_add_arg'
./ppl.l:1346: warning: `macro_add_arg' was previously implicitly declared to return `int'
./ppl.l: In function `macro_add_arg':
./ppl.l:1349: error: `macexpstackentry_t' undeclared (first use in this function)
./ppl.l:1349: error: `mep' undeclared (first use in this function)
./ppl.l:1368: error: `debuglevel' undeclared (first use in this function)
./ppl.l:1368: error: `DEBUGLEVEL_PPLEX' undeclared (first use in this function)
./ppl.l:1370: error: `input_name' undeclared (first use in this function)
./ppl.l:1371: error: `line_number' undeclared (first use in this function)
./ppl.l:1378: error: `pp_macexp' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1386: warning: `macro_add_expansion' was declared implicitly `extern' and later `static'
./ppl.l:1276: warning: previous declaration of `macro_add_expansion'
./ppl.l:1386: warning: type mismatch with previous implicit declaration
./ppl.l:1276: warning: previous implicit declaration of `macro_add_expansion'
./ppl.l:1386: warning: `macro_add_expansion' was previously implicitly declared to return `int'
./ppl.l: In function `macro_add_expansion':
./ppl.l:1387: error: `macexpstackentry_t' undeclared (first use in this function)
./ppl.l:1387: error: `mep' undeclared (first use in this function)
./ppl.l:1396: error: `debuglevel' undeclared (first use in this function)
./ppl.l:1396: error: `DEBUGLEVEL_PPLEX' undeclared (first use in this function)
./ppl.l:1398: error: `input_name' undeclared (first use in this function)
./ppl.l:1399: error: `line_number' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1411: warning: `put_buffer' was declared implicitly `extern' and later `static'
./ppl.l:1151: warning: previous declaration of `put_buffer'
./ppl.l:1411: warning: type mismatch with previous implicit declaration
./ppl.l:1151: warning: previous implicit declaration of `put_buffer'
./ppl.l:1411: warning: `put_buffer' was previously implicitly declared to return `int'
./ppl.l: In function `put_buffer':
./ppl.l:1415: error: `pass_data' undeclared (first use in this function)
./ppl.l: In function `do_include':
./ppl.l:1439: error: `includelogicentry_t' undeclared (first use in this function)
./ppl.l:1439: error: `iep' undeclared (first use in this function)
./ppl.l:1441: error: `includelogiclist' undeclared (first use in this function)
./ppl.l:1462: warning: implicit declaration of function `open_include'
./ppl.l:1462: warning: assignment makes pointer from integer without a cast
./ppl.l:1467: error: `seen_junk' undeclared (first use in this function)
./ppl.l:1468: error: `include_state' undeclared (first use in this function)
./ppl.l:1469: error: `include_ppp' undeclared (first use in this function)
./ppl.l:1470: error: `pass_data' undeclared (first use in this function)
./ppl.l:1473: error: `debuglevel' undeclared (first use in this function)
./ppl.l:1473: error: `DEBUGLEVEL_PPMSG' undeclared (first use in this function)
./ppl.l:1474: error: `input_name' undeclared (first use in this function)
./ppl.l:1474: error: `line_number' undeclared (first use in this function)
./ppl.l:1474: error: `include_ifdepth' undeclared (first use in this function)
./ppl.l: In function `push_ignore_state':
./ppl.l:1488: error: `pp_ignore' undeclared (first use in this function)
./ppl.l: At top level:
lex.ppl.c:15101: warning: `yyunput' defined but not used
make[2]: *** [lex.ppl.o] Error 1
make[2]: Leaving directory `/home/jdong/Downloads/winex/winex/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/home/jdong/Downloads/winex/winex/tools'
make: *** [tools] Error 2

```

---

### Post by jayclark on 2004-10-30
Yep, thats the exact error I get. I was just about to re run the cvs to get the error, but now I don't have to.

---

### Post by HungSquirrel on 2004-10-30
I got it built.  Running applications is a different matter altogether.  When I run apps, my monitor shuts itself off as if it is receiving a signal that is beyond its displayable range.

---

### Post by Perfect Storm on 2004-10-30
Why not downloading the .deb files from Cedega homepage, they work perfect on Ubuntu.

Or is there an another reason?

---

### Post by Rancoras on 2004-10-30
Well, CVS is free and the .deb files you have to pay for.

---

### Post by fng on 2004-10-30
the cvs-version is free? Why hasnt anyone told me this before!!! :)

---

### Post by IoN_PuLse on 2004-11-02
I had the same problems and fixed them with these steps:

```
sudo apt-get install flex-old
sudo apt-get install xlibs-dev
```

I actually had to restart the whole deal after installing those packages (ie: re-checkout the source and so on) but then it worked. 

I used an automated script from [here](http://cvscedega.linux-gamers.net/WineCVS.sh) that was a part of this [howto](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45).

Note: to use the script to grab from the CVS you'll need to use:
```
cvs -d:pserver:cvs@cvs.transgaming.org:/cvsroot login
``` and use cvs as the password. Do this before starting a checkout in the script. 

I'd also recommend checking out  [this site](http://frankscorner.org/) which has tips plus a useful winetools set of scripts. (to be used with regular wine, mind you)

I hope this helps some people, Ubuntu is quite good, had very few problems getting things working with it. I can't wait till they move to X.org =) I've used Knoppix, Kanotix, Yoper, Vidalinux (gentoo-based), Mandrake...but Ubuntu seems to be doing a great job keeping me using it. I think it's gnome + using firefox as the main browser (why use any other? I love FF) :)

---

