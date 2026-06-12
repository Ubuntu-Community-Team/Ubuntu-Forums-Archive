---
title: "LC-3 simulator installation on Xubuntu/eeePC version"
date: 2008-03-19
forum: General Help
---

### Post by Xtrmi on 2008-03-19
Hi I'm a computer engineering student and would like to be able to use the simulator on my eeePC. Everything seems fine until I get to the make command. Here is the output after I type make.

```
xtrmi@xtrmi-laptop:~$ sudo su
root@xtrmi-laptop:/home/xtrmi# cd /usr/lc3tools
root@xtrmi-laptop:/usr/lc3tools# make
/usr/bin/gcc -c -g -Wall -o lex.lc3.o lex.lc3.c
lex.lc3.c:19:19: error: stdio.h: No such file or directory
lex.lc3.c:20:20: error: string.h: No such file or directory
lex.lc3.c:21:19: error: errno.h: No such file or directory
lex.lc3.c:22:20: error: stdlib.h: No such file or directory
lex.lc3.c:156: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
lex.lc3.c:194: error: expected specifier-qualifier-list before ‘FILE’
lex.lc3.c:256: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘yy_buffer_stack_top’
lex.lc3.c:257: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘yy_buffer_stack_max’
lex.lc3.c:290: error: expected ‘)’ before ‘*’ token
lex.lc3.c:292: error: expected ‘)’ before ‘*’ token
lex.lc3.c:300: error: expected declaration specifiers or ‘...’ before ‘FILE’
lex.lc3.c:343: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
lc3.f:46:19: error: ctype.h: No such file or directory
lc3.f:50:20: error: unistd.h: No such file or directory
lc3.f:182: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
lc3.f:183: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
lc3.f:198:1: warning: "/*" within comment
lex.lc3.c: In function ‘lc3lex’:
lex.lc3.c:1413: error: ‘lc3in’ undeclared (first use in this function)
lex.lc3.c:1413: error: (Each undeclared identifier is reported only once
lex.lc3.c:1413: error: for each function it appears in.)
lex.lc3.c:1414: error: ‘stdin’ undeclared (first use in this function)
lex.lc3.c:1416: error: ‘lc3out’ undeclared (first use in this function)
lex.lc3.c:1417: error: ‘stdout’ undeclared (first use in this function)
lex.lc3.c:1419: error: ‘yy_buffer_stack_top’ undeclared (first use in this function)
lex.lc3.c:1419: error: ‘NULL’ undeclared (first use in this function)
lex.lc3.c:1422: warning: implicit declaration of function ‘lc3_create_buffer’
lex.lc3.c:1470: error: ‘size_t’ undeclared (first use in this function)
lc3.f:309: warning: implicit declaration of function ‘fwrite’
lc3.f:309: warning: incompatible implicit declaration of built-in function ‘fwrite’
lex.lc3.c:1843: warning: implicit declaration of function ‘lc3restart’
lex.lc3.c: In function ‘yy_get_next_buffer’:
lex.lc3.c:1887: error: ‘yy_buffer_stack_top’ undeclared (first use in this function)
lex.lc3.c:1938: error: ‘NULL’ undeclared (first use in this function)
lex.lc3.c:1941: error: ‘struct yy_buffer_state’ has no member named ‘yy_ch_buf’
lex.lc3.c:1943: error: ‘struct yy_buffer_state’ has no member named ‘yy_is_our_buffer’
lex.lc3.c:1945: error: ‘struct yy_buffer_state’ has no member named ‘yy_buf_size’
lex.lc3.c:1948: error: ‘struct yy_buffer_state’ has no member named ‘yy_buf_size’
lex.lc3.c:1948: error: ‘struct yy_buffer_state’ has no member named ‘yy_buf_size’
lex.lc3.c:1950: error: ‘struct yy_buffer_state’ has no member named ‘yy_buf_size’
lex.lc3.c:1952: error: ‘struct yy_buffer_state’ has no member named ‘yy_ch_buf’
lex.lc3.c:1954: error: ‘struct yy_buffer_state’ has no member named ‘yy_ch_buf’
lex.lc3.c:1954: error: ‘struct yy_buffer_state’ has no member named ‘yy_buf_size’
lex.lc3.c:1958: error: ‘struct yy_buffer_state’ has no member named ‘yy_ch_buf’
lex.lc3.c:1960: error: ‘struct yy_buffer_state’ has no member named ‘yy_ch_buf’
lex.lc3.c:1964: error: ‘struct yy_buffer_state’ has no member named ‘yy_ch_buf’
lex.lc3.c:1975: error: ‘size_t’ undeclared (first use in this function)
lex.lc3.c:1975: error: expected ‘;’ before ‘n’
lex.lc3.c:1975: error: ‘n’ undeclared (first use in this function)
lex.lc3.c:1975: error: expected ‘;’ before ‘num_to_read’
lex.lc3.c:1975: error: ‘EOF’ undeclared (first use in this function)
lex.lc3.c:1975: warning: implicit declaration of function ‘ferror’
lex.lc3.c:1975: error: ‘lc3in’ undeclared (first use in this function)
lex.lc3.c:1975: error: ‘errno’ undeclared (first use in this function)
lex.lc3.c:1975: warning: implicit declaration of function ‘fread’
lex.lc3.c:1975: error: expected ‘)’ before ‘num_to_read’
lex.lc3.c:1975: error: ‘EINTR’ undeclared (first use in this function)
lex.lc3.c:1975: warning: implicit declaration of function ‘clearerr’
lex.lc3.c: In function ‘input’:
lex.lc3.c:2084: error: ‘yy_buffer_stack_top’ undeclared (first use in this function)
lex.lc3.c:2107: error: ‘lc3in’ undeclared (first use in this function)
lex.lc3.c:2114: error: ‘EOF’ undeclared (first use in this function)
lex.lc3.c: At top level:
lex.lc3.c:2145: error: expected ‘)’ before ‘*’ token
lex.lc3.c: In function ‘lc3_switch_to_buffer’:
lex.lc3.c:2171: error: ‘yy_buffer_stack_top’ undeclared (first use in this function)
lex.lc3.c:2171: error: ‘NULL’ undeclared (first use in this function)
lex.lc3.c: In function ‘lc3_load_buffer_state’:
lex.lc3.c:2195: error: ‘yy_buffer_stack_top’ undeclared (first use in this function)
lex.lc3.c:2197: error: ‘lc3in’ undeclared (first use in this function)
lex.lc3.c: At top level:
lex.lc3.c:2207: error: expected ‘)’ before ‘*’ token
lex.lc3.c: In function ‘lc3_delete_buffer’:
lex.lc3.c:2241: error: ‘yy_buffer_stack_top’ undeclared (first use in this function)
lex.lc3.c:2241: error: ‘NULL’ undeclared (first use in this function)
lex.lc3.c:2244: error: ‘struct yy_buffer_state’ has no member named ‘yy_is_our_buffer’
lex.lc3.c:2245: error: ‘struct yy_buffer_state’ has no member named ‘yy_ch_buf’
lex.lc3.c: At top level:
lex.lc3.c:2258: error: expected declaration specifiers or ‘...’ before ‘FILE’
lex.lc3.c: In function ‘lc3_init_buffer’:
lex.lc3.c:2261: error: ‘errno’ undeclared (first use in this function)
lex.lc3.c:2265: error: ‘struct yy_buffer_state’ has no member named ‘yy_input_file’
lex.lc3.c:2265: error: ‘file’ undeclared (first use in this function)
lex.lc3.c:2266: error: ‘struct yy_buffer_state’ has no member named ‘yy_fill_buffer’
lex.lc3.c:2272: error: ‘yy_buffer_stack_top’ undeclared (first use in this function)
lex.lc3.c:2272: error: ‘NULL’ undeclared (first use in this function)
lex.lc3.c:2273: error: ‘struct yy_buffer_state’ has no member named ‘yy_bs_lineno’
lex.lc3.c:2274: error: ‘struct yy_buffer_state’ has no member named ‘yy_bs_column’
lex.lc3.c:2277: error: ‘struct yy_buffer_state’ has no member named ‘yy_is_interactive’
lex.lc3.c:2277: warning: implicit declaration of function ‘fileno’
lex.lc3.c: In function ‘lc3_flush_buffer’:
lex.lc3.c:2291: error: ‘struct yy_buffer_state’ has no member named ‘yy_n_chars’
lex.lc3.c:2297: error: ‘struct yy_buffer_state’ has no member named ‘yy_ch_buf’
lex.lc3.c:2298: error: ‘struct yy_buffer_state’ has no member named ‘yy_ch_buf’
lex.lc3.c:2300: error: ‘struct yy_buffer_state’ has no member named ‘yy_buf_pos’
lex.lc3.c:2300: error: ‘struct yy_buffer_state’ has no member named ‘yy_ch_buf’
lex.lc3.c:2302: error: ‘struct yy_buffer_state’ has no member named ‘yy_at_bol’
lex.lc3.c:2303: error: ‘struct yy_buffer_state’ has no member named ‘yy_buffer_status’
lex.lc3.c:2305: error: ‘yy_buffer_stack_top’ undeclared (first use in this function)
lex.lc3.c:2305: error: ‘NULL’ undeclared (first use in this function)
lex.lc3.c: In function ‘lc3push_buffer_state’:
lex.lc3.c:2317: error: ‘NULL’ undeclared (first use in this function)
lex.lc3.c:2323: error: ‘yy_buffer_stack_top’ undeclared (first use in this function)
lex.lc3.c: In function ‘lc3pop_buffer_state’:
lex.lc3.c:2347: error: ‘yy_buffer_stack_top’ undeclared (first use in this function)
lex.lc3.c:2347: error: ‘NULL’ undeclared (first use in this function)
lex.lc3.c: In function ‘lc3ensure_buffer_stack’:
lex.lc3.c:2379: warning: implicit declaration of function ‘memset’
lex.lc3.c:2379: warning: incompatible implicit declaration of built-in function ‘memset’
lex.lc3.c:2381: error: ‘yy_buffer_stack_max’ undeclared (first use in this function)
lex.lc3.c:2382: error: ‘yy_buffer_stack_top’ undeclared (first use in this function)
lex.lc3.c:2398: warning: incompatible implicit declaration of built-in function ‘memset’
lex.lc3.c: In function ‘lc3_scan_buffer’:
lex.lc3.c:2423: error: ‘struct yy_buffer_state’ has no member named ‘yy_buf_size’
lex.lc3.c:2424: error: ‘struct yy_buffer_state’ has no member named ‘yy_buf_pos’
lex.lc3.c:2424: error: ‘struct yy_buffer_state’ has no member named ‘yy_ch_buf’
lex.lc3.c:2425: error: ‘struct yy_buffer_state’ has no member named ‘yy_is_our_buffer’
lex.lc3.c:2426: error: ‘struct yy_buffer_state’ has no member named ‘yy_input_file’
lex.lc3.c:2427: error: ‘struct yy_buffer_state’ has no member named ‘yy_n_chars’
lex.lc3.c:2427: error: ‘struct yy_buffer_state’ has no member named ‘yy_buf_size’
lex.lc3.c:2428: error: ‘struct yy_buffer_state’ has no member named ‘yy_is_interactive’
lex.lc3.c:2429: error: ‘struct yy_buffer_state’ has no member named ‘yy_at_bol’
lex.lc3.c:2430: error: ‘struct yy_buffer_state’ has no member named ‘yy_fill_buffer’
lex.lc3.c:2431: error: ‘struct yy_buffer_state’ has no member named ‘yy_buffer_status’
lex.lc3.c: In function ‘lc3_scan_string’:
lex.lc3.c:2449: warning: implicit declaration of function ‘strlen’
lex.lc3.c:2449: warning: incompatible implicit declaration of built-in function ‘strlen’
lex.lc3.c: In function ‘lc3_scan_bytes’:
lex.lc3.c:2484: error: ‘struct yy_buffer_state’ has no member named ‘yy_is_our_buffer’
lex.lc3.c: In function ‘yy_fatal_error’:
lex.lc3.c:2495: warning: implicit declaration of function ‘fprintf’
lex.lc3.c:2495: warning: incompatible implicit declaration of built-in function ‘fprintf’
lex.lc3.c:2495: error: ‘stderr’ undeclared (first use in this function)
lex.lc3.c:2496: warning: implicit declaration of function ‘exit’
lex.lc3.c:2496: warning: incompatible implicit declaration of built-in function ‘exit’
lex.lc3.c: At top level:
lex.lc3.c:2530: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
lex.lc3.c:2538: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
lex.lc3.c:2576: error: expected ‘)’ before ‘*’ token
lex.lc3.c:2581: error: expected ‘)’ before ‘*’ token
lex.lc3.c: In function ‘yy_init_globals’:
lex.lc3.c:2603: error: ‘yy_buffer_stack_top’ undeclared (first use in this function)
lex.lc3.c:2604: error: ‘yy_buffer_stack_max’ undeclared (first use in this function)
lex.lc3.c:2614: error: ‘lc3in’ undeclared (first use in this function)
lex.lc3.c:2614: error: ‘FILE’ undeclared (first use in this function)
lex.lc3.c:2614: error: expected expression before ‘)’ token
lex.lc3.c:2615: error: ‘lc3out’ undeclared (first use in this function)
lex.lc3.c:2615: error: expected expression before ‘)’ token
lex.lc3.c: In function ‘lc3lex_destroy’:
lex.lc3.c:2629: error: ‘yy_buffer_stack_top’ undeclared (first use in this function)
lex.lc3.c:2629: error: ‘NULL’ undeclared (first use in this function)
lex.lc3.c: In function ‘lc3alloc’:
lex.lc3.c:2672: warning: implicit declaration of function ‘malloc’
lex.lc3.c:2672: warning: incompatible implicit declaration of built-in function ‘malloc’
lex.lc3.c: In function ‘lc3realloc’:
lex.lc3.c:2684: warning: implicit declaration of function ‘realloc’
lex.lc3.c: In function ‘lc3free’:
lex.lc3.c:2689: warning: implicit declaration of function ‘free’
lc3.f: In function ‘main’:
lc3.f:320: warning: incompatible implicit declaration of built-in function ‘fprintf’
lc3.f:320: error: ‘stderr’ undeclared (first use in this function)
lc3.f:325: warning: incompatible implicit declaration of built-in function ‘strlen’
lc3.f:326: warning: incompatible implicit declaration of built-in function ‘malloc’
lc3.f:326: error: ‘NULL’ undeclared (first use in this function)
lc3.f:327: warning: implicit declaration of function ‘perror’
lc3.f:330: warning: implicit declaration of function ‘strcpy’
lc3.f:330: warning: incompatible implicit declaration of built-in function ‘strcpy’
lc3.f:333: warning: implicit declaration of function ‘strrchr’
lc3.f:333: warning: incompatible implicit declaration of built-in function ‘strrchr’
lc3.f:333: warning: implicit declaration of function ‘strcmp’
lc3.f:339: error: ‘lc3in’ undeclared (first use in this function)
lc3.f:339: warning: implicit declaration of function ‘fopen’
lc3.f:340: warning: incompatible implicit declaration of built-in function ‘fprintf’
lc3.f:346: error: ‘objout’ undeclared (first use in this function)
lc3.f:347: warning: incompatible implicit declaration of built-in function ‘fprintf’
lc3.f:351: error: ‘symout’ undeclared (first use in this function)
lc3.f:352: warning: incompatible implicit declaration of built-in function ‘fprintf’
lc3.f:357: warning: incompatible implicit declaration of built-in function ‘fprintf’
lc3.f:362: warning: implicit declaration of function ‘puts’
lc3.f:370: warning: implicit declaration of function ‘printf’
lc3.f:370: warning: incompatible implicit declaration of built-in function ‘printf’
lc3.f:373: warning: implicit declaration of function ‘fseek’
lc3.f:373: error: ‘SEEK_SET’ undeclared (first use in this function)
lc3.f:392: warning: implicit declaration of function ‘fclose’
lc3.f: In function ‘bad_operands’:
lc3.f:409: warning: incompatible implicit declaration of built-in function ‘fprintf’
lc3.f:409: error: ‘stderr’ undeclared (first use in this function)
lc3.f: In function ‘bad_line’:
lc3.f:418: warning: incompatible implicit declaration of built-in function ‘fprintf’
lc3.f:418: error: ‘stderr’ undeclared (first use in this function)
lc3.f: In function ‘read_val’:
lc3.f:431: warning: implicit declaration of function ‘strtol’
lc3.f:440: warning: incompatible implicit declaration of built-in function ‘fprintf’
lc3.f:440: error: ‘stderr’ undeclared (first use in this function)
lc3.f: In function ‘write_value’:
lc3.f:461: warning: incompatible implicit declaration of built-in function ‘fwrite’
lc3.f:461: error: ‘objout’ undeclared (first use in this function)
lc3.f: In function ‘sym_name’:
lc3.f:467: warning: implicit declaration of function ‘strdup’
lc3.f:467: warning: incompatible implicit declaration of built-in function ‘strdup’
lc3.f:467: warning: pointer targets in initialization differ in signedness
lc3.f:471: warning: implicit declaration of function ‘isspace’
lc3.f:474: warning: pointer targets in return differ in signedness
lc3.f: In function ‘find_label’:
lc3.f:487: warning: pointer targets in assignment differ in signedness
lc3.f:488: error: ‘NULL’ undeclared (first use in this function)
lc3.f:488: warning: pointer targets in passing argument 1 of ‘find_symbol’ differ in signedness
lc3.f:495: warning: incompatible implicit declaration of built-in function ‘fprintf’
lc3.f:495: error: ‘stderr’ undeclared (first use in this function)
lc3.f:505: warning: incompatible implicit declaration of built-in function ‘fprintf’
lc3.f: In function ‘generate_instruction’:
lc3.f:526: warning: pointer targets in assignment differ in signedness
lc3.f:528: warning: implicit declaration of function ‘strchr’
lc3.f:528: warning: incompatible implicit declaration of built-in function ‘strchr’
lc3.f:528: warning: pointer targets in passing argument 1 of ‘strchr’ differ in signedness
lc3.f:528: warning: pointer targets in assignment differ in signedness
lc3.f:528: error: ‘NULL’ undeclared (first use in this function)
lc3.f:531: warning: pointer targets in passing argument 1 of ‘strchr’ differ in signedness
lc3.f:531: warning: pointer targets in assignment differ in signedness
lc3.f:539: warning: pointer targets in passing argument 1 of ‘read_val’ differ in signedness
lc3.f:548: warning: incompatible implicit declaration of built-in function ‘fprintf’
lc3.f:548: error: ‘stderr’ undeclared (first use in this function)
lc3.f:556: warning: incompatible implicit declaration of built-in function ‘fprintf’
lc3.f:570: warning: pointer targets in passing argument 1 of ‘read_val’ differ in signedness
lc3.f:572: warning: pointer targets in passing argument 1 of ‘find_label’ differ in signedness
lc3.f:580: warning: pointer targets in passing argument 1 of ‘read_val’ differ in signedness
lc3.f:589: warning: pointer targets in passing argument 1 of ‘read_val’ differ in signedness
lc3.f:596: warning: pointer targets in passing argument 1 of ‘read_val’ differ in signedness
lc3.f:598: warning: pointer targets in passing argument 1 of ‘find_label’ differ in signedness
lc3.f:606: warning: pointer targets in passing argument 1 of ‘read_val’ differ in signedness
lc3.f:608: warning: pointer targets in passing argument 1 of ‘find_label’ differ in signedness
lc3.f:621: warning: pointer targets in passing argument 1 of ‘read_val’ differ in signedness
lc3.f:640: warning: pointer targets in passing argument 1 of ‘read_val’ differ in signedness
lc3.f:644: warning: pointer targets in passing argument 1 of ‘read_val’ differ in signedness
lc3.f:659: warning: pointer targets in passing argument 1 of ‘read_val’ differ in signedness
lc3.f:662: warning: pointer targets in passing argument 1 of ‘find_label’ differ in signedness
lc3.f:693: warning: pointer targets in passing argument 1 of ‘read_val’ differ in signedness
lc3.f: In function ‘found_label’:
lc3.f:731: warning: pointer targets in initialization differ in signedness
lc3.f:734: warning: pointer targets in passing argument 1 of ‘add_symbol’ differ in signedness
lc3.f:735: warning: incompatible implicit declaration of built-in function ‘fprintf’
lc3.f:735: error: ‘stderr’ undeclared (first use in this function)
lc3.f:739: warning: incompatible implicit declaration of built-in function ‘fprintf’
lc3.f:739: error: ‘symout’ undeclared (first use in this function)
make: *** [lex.lc3.o] Error 1
root@xtrmi-laptop:/usr/lc3tools# 

```

Any suggestions would be greatly appreciated. Also I'd like to add that I'm a Linux newb so please keep it simple.:lolflag:

---

### Post by Xtrmi on 2008-03-20
Anybody? I have to write a program on LC-3 pretty soon. Please save me from using my vista 64 system.

Ok I got some advice from a classmate and have decided to just use wine.

---

