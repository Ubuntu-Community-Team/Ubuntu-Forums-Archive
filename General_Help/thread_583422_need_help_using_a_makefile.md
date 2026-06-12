---
title: "need help using a makefile"
date: 2007-10-20
forum: General Help
---

### Post by foldor on 2007-10-20
I have been trying to install avview from the source and I have used ./configure and after great pain have managed to get it to create the makefile. Now however I cannot get it to compile. 

Here is a log of the error I get.

> make  all-am
make[1]: Entering directory `/home/ryan/Desktop/avview-0.80.7'
if gcc -DHAVE_CONFIG_H -I. -I. -I. -I -I/usr/include/tcl8.4/tk-private/generic   -Wall -O2 -DAVVIEW_VERSION=\"0.80.7\"  -g -O2 -MT avview_shell-xv.o -MD -MP -MF ".deps/avview_shell-xv.Tpo" \
	  -c -o avview_shell-xv.o `test -f 'xv.c' || echo './'`xv.c; \
	then mv -f ".deps/avview_shell-xv.Tpo" ".deps/avview_shell-xv.Po"; \
	else rm -f ".deps/avview_shell-xv.Tpo"; exit 1; \
	fi
make[1]: Leaving directory `/home/ryan/Desktop/avview-0.80.7'

xv.c:23:33: error: X11/extensions/XShm.h: No such file or directory
xv.c:24:34: error: X11/extensions/Xvlib.h: No such file or directory
xv.c:25:17: error: tcl.h: No such file or directory
xv.c:26:16: error: tk.h: No such file or directory
xv.c: In function ‘xv_notify_handler’:
xv.c:30: warning: implicit declaration of function ‘fprintf’
xv.c:30: warning: incompatible implicit declaration of built-in function ‘fprintf’
xv.c:30: error: ‘stderr’ undeclared (first use in this function)
xv.c:30: error: (Each undeclared identifier is reported only once
xv.c:30: error: for each function it appears in.)
xv.c: At top level:
xv.c:33: error: expected ‘)’ before ‘client_data’
xv.c:73: error: expected ‘)’ before ‘client_data’
xv.c:120: error: expected ‘)’ before ‘client_data’
xv.c:177: error: expected ‘)’ before ‘client_data’
xv.c:230: error: expected ‘)’ before ‘client_data’
xv.c:277: error: expected ‘)’ before ‘client_data’
xv.c:331: error: expected ‘)’ before ‘client_data’
xv.c:386: error: expected ‘)’ before ‘client_data’
xv.c:442: error: expected ‘)’ before ‘client_data’
xv.c:504: error: expected ‘)’ before ‘client_data’
xv.c:551: error: expected ‘)’ before ‘client_data’
xv.c:606: error: expected ‘)’ before ‘client_data’
xv.c:670: error: expected ‘)’ before ‘client_data’
xv.c:736: error: expected ‘)’ before ‘client_data’
xv.c:787: error: expected ‘)’ before ‘client_data’
xv.c:823: error: expected ‘)’ before ‘client_data’
xv.c:863: error: expected ‘)’ before ‘client_data’
xv.c:903: error: expected ‘)’ before ‘client_data’
xv.c:943: error: expected ‘)’ before ‘client_data’
xv.c:982: error: expected ‘)’ before ‘client_data’
xv.c:1015: error: expected specifier-qualifier-list before ‘Tcl_CmdProc’
xv.c:1017: error: ‘xv_numadaptors’ undeclared here (not in a function)
xv.c:1017: warning: excess elements in struct initializer
xv.c:1017: warning: (near initialization for ‘xv_commands[0]’)
xv.c:1018: error: ‘xv_adaptor_name’ undeclared here (not in a function)
xv.c:1018: warning: excess elements in struct initializer
xv.c:1018: warning: (near initialization for ‘xv_commands[1]’)
xv.c:1019: error: ‘xv_adaptor_type’ undeclared here (not in a function)
xv.c:1019: warning: excess elements in struct initializer
xv.c:1019: warning: (near initialization for ‘xv_commands[2]’)
xv.c:1020: error: ‘xv_adaptor_ports’ undeclared here (not in a function)
xv.c:1020: warning: excess elements in struct initializer
xv.c:1020: warning: (near initialization for ‘xv_commands[3]’)
xv.c:1021: error: ‘xv_num_port_encodings’ undeclared here (not in a function)
xv.c:1021: warning: excess elements in struct initializer
xv.c:1021: warning: (near initialization for ‘xv_commands[4]’)
xv.c:1022: error: ‘xv_port_encodings’ undeclared here (not in a function)
xv.c:1022: warning: excess elements in struct initializer
xv.c:1022: warning: (near initialization for ‘xv_commands[5]’)
xv.c:1023: error: ‘xv_port_encoding_name’ undeclared here (not in a function)
xv.c:1023: warning: excess elements in struct initializer
xv.c:1023: warning: (near initialization for ‘xv_commands[6]’)
xv.c:1024: error: ‘xv_port_encoding_id’ undeclared here (not in a function)
xv.c:1024: warning: excess elements in struct initializer
xv.c:1024: warning: (near initialization for ‘xv_commands[7]’)
xv.c:1025: error: ‘xv_port_encoding_size’ undeclared here (not in a function)
xv.c:1025: warning: excess elements in struct initializer
xv.c:1025: warning: (near initialization for ‘xv_commands[8]’)
xv.c:1026: error: ‘xv_num_port_attributes’ undeclared here (not in a function)
xv.c:1026: warning: excess elements in struct initializer
xv.c:1026: warning: (near initialization for ‘xv_commands[9]’)
xv.c:1027: error: ‘xv_port_attribute_name’ undeclared here (not in a function)
xv.c:1027: warning: excess elements in struct initializer
xv.c:1027: warning: (near initialization for ‘xv_commands[10]’)
xv.c:1028: error: ‘xv_port_attribute_type’ undeclared here (not in a function)
xv.c:1028: warning: excess elements in struct initializer
xv.c:1028: warning: (near initialization for ‘xv_commands[11]’)
xv.c:1029: error: ‘xv_port_attribute_range’ undeclared here (not in a function)
xv.c:1029: warning: excess elements in struct initializer
xv.c:1029: warning: (near initialization for ‘xv_commands[12]’)
xv.c:1030: error: ‘xv_putvideo’ undeclared here (not in a function)
xv.c:1030: warning: excess elements in struct initializer
xv.c:1030: warning: (near initialization for ‘xv_commands[13]’)
xv.c:1031: error: ‘xv_stopvideo’ undeclared here (not in a function)
xv.c:1031: warning: excess elements in struct initializer
xv.c:1031: warning: (near initialization for ‘xv_commands[14]’)
xv.c:1032: error: ‘xv_grabport’ undeclared here (not in a function)
xv.c:1032: warning: excess elements in struct initializer
xv.c:1032: warning: (near initialization for ‘xv_commands[15]’)
xv.c:1033: error: ‘xv_ungrabport’ undeclared here (not in a function)
xv.c:1033: warning: excess elements in struct initializer
xv.c:1033: warning: (near initialization for ‘xv_commands[16]’)
xv.c:1034: error: ‘xv_getportattribute’ undeclared here (not in a function)
xv.c:1034: warning: excess elements in struct initializer
xv.c:1034: warning: (near initialization for ‘xv_commands[17]’)
xv.c:1035: error: ‘xv_setportattribute’ undeclared here (not in a function)
xv.c:1035: warning: excess elements in struct initializer
xv.c:1035: warning: (near initialization for ‘xv_commands[18]’)
xv.c:1036: error: ‘xv_getwindowbackgroundpixel’ undeclared here (not in a function)
xv.c:1036: warning: excess elements in struct initializer
xv.c:1036: warning: (near initialization for ‘xv_commands[19]’)
xv.c:1037: warning: excess elements in struct initializer
xv.c:1037: warning: (near initialization for ‘xv_commands[20]’)
xv.c:1040: error: expected ‘)’ before ‘*’ token
xv.c:1045: fatal error: opening dependency file .deps/avview_shell-xv.Tpo: Permission denied
compilation terminated.
make[1]: *** [avview_shell-xv.o] Error 1
make: *** [all] Error 2


---

