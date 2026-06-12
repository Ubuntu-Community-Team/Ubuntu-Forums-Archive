---
title: "gkrellmlaunch"
date: 2007-10-06
forum: General Help
---

### Post by phillips321 on 2007-10-06
[http://gkrellmlaunch.sourceforge.net/]("http://gkrellmlaunch.sourceforge.net/")

I'm trying to install this small plugin for gkrellm but for some reason i keep getting errors when i try to make it.

Is it because it can't find the gkrellm directory?

```
phillips321@LinuxDesktop:~/temp/gkrellmlaunch-0.5$ sudo make
Password:
gcc  -O2 -Wall -fPIC `pkg-config gtk+-2.0 --cflags` -g    -c -o gkrellmlaunch.o gkrellmlaunch.c
/bin/sh: pkg-config: not found
In file included from gkrellmlaunch.c:36:
/usr/include/gkrellm2/gkrellm.h:30:21: error: gtk/gtk.h: No such file or directory
In file included from gkrellmlaunch.c:36:
/usr/include/gkrellm2/gkrellm.h:195: error: expected specifier-qualifier-list before âgfloatâ
/usr/include/gkrellm2/gkrellm.h:219: error: expected specifier-qualifier-list before âPangoFontDescriptionâ
/usr/include/gkrellm2/gkrellm.h:232: error: expected specifier-qualifier-list before âgcharâ
/usr/include/gkrellm2/gkrellm.h:266: error: expected specifier-qualifier-list before âGdkPixmapâ
/usr/include/gkrellm2/gkrellm.h:300: error: expected specifier-qualifier-list before âgcharâ
/usr/include/gkrellm2/gkrellm.h:317: error: expected specifier-qualifier-list before âgintâ
/usr/include/gkrellm2/gkrellm.h:329: error: expected specifier-qualifier-list before âgintâ
/usr/include/gkrellm2/gkrellm.h:338: error: expected specifier-qualifier-list before âgintâ
/usr/include/gkrellm2/gkrellm.h:348: error: expected specifier-qualifier-list before âGdkPixbufâ
/usr/include/gkrellm2/gkrellm.h:383: error: expected specifier-qualifier-list before âgintâ
/usr/include/gkrellm2/gkrellm.h:431: error: expected specifier-qualifier-list before âGdkPixmapâ
/usr/include/gkrellm2/gkrellm.h:473: error: expected specifier-qualifier-list before âGtkWidgetâ
/usr/include/gkrellm2/gkrellm.h:516: error: expected specifier-qualifier-list before âgpointerâ
/usr/include/gkrellm2/gkrellm.h:534: error: expected specifier-qualifier-list before âgintâ
/usr/include/gkrellm2/gkrellm.h:589: error: expected specifier-qualifier-list before âGdkPixmapâ
/usr/include/gkrellm2/gkrellm.h:598: error: expected specifier-qualifier-list before âGtkWidgetâ
/usr/include/gkrellm2/gkrellm.h:610: error: expected specifier-qualifier-list before âgcharâ
/usr/include/gkrellm2/gkrellm.h:621: error: expected specifier-qualifier-list before âGtkWidgetâ
/usr/include/gkrellm2/gkrellm.h:703: error: expected specifier-qualifier-list before âgintâ
/usr/include/gkrellm2/gkrellm.h:740: error: expected specifier-qualifier-list before âgpointerâ
/usr/include/gkrellm2/gkrellm.h:758: error: expected specifier-qualifier-list before âgcharâ
/usr/include/gkrellm2/gkrellm.h:779: error: expected specifier-qualifier-list before âgcharâ
/usr/include/gkrellm2/gkrellm.h:796: error: expected specifier-qualifier-list before âgpointerâ
/usr/include/gkrellm2/gkrellm.h:802: error: expected specifier-qualifier-list before âgbooleanâ
/usr/include/gkrellm2/gkrellm.h:816: error: expected specifier-qualifier-list before âgintâ
/usr/include/gkrellm2/gkrellm.h:828: error: expected specifier-qualifier-list before âgintâ
/usr/include/gkrellm2/gkrellm.h:835: error: expected specifier-qualifier-list before âgcharâ
/usr/include/gkrellm2/gkrellm.h:943: error: expected specifier-qualifier-list before âgintâ
/usr/include/gkrellm2/gkrellm.h:1006: error: expected specifier-qualifier-list before âGtkWidgetâ
/usr/include/gkrellm2/gkrellm.h:1042: error: expected specifier-qualifier-list before âgcharâ
/usr/include/gkrellm2/gkrellm.h:1064: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
In file included from /usr/include/gkrellm2/gkrellm.h:1067,
                 from gkrellmlaunch.c:36:
/usr/include/gkrellm2/gkrellm-public-proto.h:42: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:45: error: expected declaration specifiers or â...â before âgbooleanâ
/usr/include/gkrellm2/gkrellm-public-proto.h:46: error: expected declaration specifiers or â...â before âgbooleanâ
/usr/include/gkrellm2/gkrellm-public-proto.h:47: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_chart_enable_visibilityâ
/usr/include/gkrellm2/gkrellm-public-proto.h:49: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_is_chart_visibleâ
/usr/include/gkrellm2/gkrellm-public-proto.h:51: error: expected declaration specifiers or â...â before âgpointerâ
/usr/include/gkrellm2/gkrellm-public-proto.h:53: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_draw_chart_labelâ
/usr/include/gkrellm2/gkrellm-public-proto.h:55: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:55: error: expected declaration specifiers or â...â before âgcharâ
/usr/include/gkrellm2/gkrellm-public-proto.h:64: error: expected declaration specifiers or â...â before âGdkPixmapâ
/usr/include/gkrellm2/gkrellm-public-proto.h:64: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:67: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_chart_widthâ
/usr/include/gkrellm2/gkrellm-public-proto.h:68: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:69: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:70: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_get_chart_scalemaxâ
/usr/include/gkrellm2/gkrellm-public-proto.h:71: error: expected declaration specifiers or â...â before âGdkPixmapâ
/usr/include/gkrellm2/gkrellm-public-proto.h:72: error: expected declaration specifiers or â...â before âGdkColorâ
/usr/include/gkrellm2/gkrellm-public-proto.h:72: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:74: error: expected declaration specifiers or â...â before âGdkPixmapâ
/usr/include/gkrellm2/gkrellm-public-proto.h:74: error: expected declaration specifiers or â...â before âGdkColorâ
/usr/include/gkrellm2/gkrellm-public-proto.h:79: error: expected declaration specifiers or â...â before âGdkPixmapâ
/usr/include/gkrellm2/gkrellm-public-proto.h:80: error: expected declaration specifiers or â...â before âGdkPixmapâ
/usr/include/gkrellm2/gkrellm-public-proto.h:80: error: expected declaration specifiers or â...â before âgcharâ
/usr/include/gkrellm2/gkrellm-public-proto.h:81: error: expected declaration specifiers or â...â before âgcharâ
/usr/include/gkrellm2/gkrellm-public-proto.h:83: error: expected declaration specifiers or â...â before âgulongâ
/usr/include/gkrellm2/gkrellm-public-proto.h:85: error: expected declaration specifiers or â...â before âgbooleanâ
/usr/include/gkrellm2/gkrellm-public-proto.h:86: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_get_chartdata_hideâ
/usr/include/gkrellm2/gkrellm-public-proto.h:87: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_get_current_chartdataâ
/usr/include/gkrellm2/gkrellm-public-proto.h:88: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_get_chartdata_dataâ
/usr/include/gkrellm2/gkrellm-public-proto.h:89: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:90: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:91: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:92: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:92: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:93: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:101: error: expected declaration specifiers or â...â before âgbooleanâ
/usr/include/gkrellm2/gkrellm-public-proto.h:101: error: expected declaration specifiers or â...â before âgfloatâ
/usr/include/gkrellm2/gkrellm-public-proto.h:101: error: expected declaration specifiers or â...â before âgfloatâ
/usr/include/gkrellm2/gkrellm-public-proto.h:101: error: expected declaration specifiers or â...â before âgfloatâ
/usr/include/gkrellm2/gkrellm-public-proto.h:102: error: expected declaration specifiers or â...â before âgfloatâ
/usr/include/gkrellm2/gkrellm-public-proto.h:102: error: expected declaration specifiers or â...â before âgfloatâ
/usr/include/gkrellm2/gkrellm-public-proto.h:102: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:102: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:104: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:105: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_get_chartconfig_grid_resolutionâ
/usr/include/gkrellm2/gkrellm-public-proto.h:107: error: expected declaration specifiers or â...â before âgpointerâ
/usr/include/gkrellm2/gkrellm-public-proto.h:108: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:111: error: expected declaration specifiers or â...â before âgcharâ
/usr/include/gkrellm2/gkrellm-public-proto.h:113: error: expected declaration specifiers or â...â before âgbooleanâ
/usr/include/gkrellm2/gkrellm-public-proto.h:115: error: expected declaration specifiers or â...â before âgbooleanâ
/usr/include/gkrellm2/gkrellm-public-proto.h:117: error: expected declaration specifiers or â...â before âgbooleanâ
/usr/include/gkrellm2/gkrellm-public-proto.h:118: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:119: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_get_chartconfig_fixed_gridsâ
/usr/include/gkrellm2/gkrellm-public-proto.h:121: error: expected declaration specifiers or â...â before âgpointerâ
/usr/include/gkrellm2/gkrellm-public-proto.h:122: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_get_chartconfig_heightâ
/usr/include/gkrellm2/gkrellm-public-proto.h:124: error: expected declaration specifiers or â...â before âgpointerâ
/usr/include/gkrellm2/gkrellm-public-proto.h:125: error: expected declaration specifiers or â...â before âgbooleanâ
/usr/include/gkrellm2/gkrellm-public-proto.h:127: error: expected declaration specifiers or â...â before âgcharâ
/usr/include/gkrellm2/gkrellm-public-proto.h:127: error: expected declaration specifiers or â...â before âgcharâ
/usr/include/gkrellm2/gkrellm-public-proto.h:128: error: expected declaration specifiers or â...â before âgcharâ
/usr/include/gkrellm2/gkrellm-public-proto.h:128: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:134: error: expected declaration specifiers or â...â before âgcharâ
/usr/include/gkrellm2/gkrellm-public-proto.h:135: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:136: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:137: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_panel_configure_get_heightâ
/usr/include/gkrellm2/gkrellm-public-proto.h:138: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:142: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_panel_enable_visibilityâ
/usr/include/gkrellm2/gkrellm-public-proto.h:144: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_is_panel_visibleâ
/usr/include/gkrellm2/gkrellm-public-proto.h:145: error: expected declaration specifiers or â...â before âgbooleanâ
/usr/include/gkrellm2/gkrellm-public-proto.h:147: error: expected declaration specifiers or â...â before âgbooleanâ
/usr/include/gkrellm2/gkrellm-public-proto.h:153: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:153: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:160: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:160: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:161: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:161: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:161: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:162: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:162: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:162: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:162: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:163: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:164: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:164: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:164: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:164: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:165: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:165: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:166: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:167: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:167: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:169: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:169: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:170: error: expected declaration specifiers or â...â before âgcharâ
/usr/include/gkrellm2/gkrellm-public-proto.h:171: error: expected declaration specifiers or â...â before âgulongâ
/usr/include/gkrellm2/gkrellm-public-proto.h:172: error: expected declaration specifiers or â...â before âgbooleanâ
/usr/include/gkrellm2/gkrellm-public-proto.h:175: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:177: error: expected declaration specifiers or â...â before âgbooleanâ
/usr/include/gkrellm2/gkrellm-public-proto.h:178: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:183: error: expected declaration specifiers or â...â before âgcharâ
/usr/include/gkrellm2/gkrellm-public-proto.h:185: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:185: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:185: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:186: error: expected declaration specifiers or â...â before âgcharâ
/usr/include/gkrellm2/gkrellm-public-proto.h:188: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:188: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:188: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:191: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:191: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:191: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:191: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:191: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:192: error: expected declaration specifiers or â...â before âGdkPixmapâ
/usr/include/gkrellm2/gkrellm-public-proto.h:193: error: expected declaration specifiers or â...â before âGdkBitmapâ
/usr/include/gkrellm2/gkrellm-public-proto.h:193: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:193: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:193: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:195: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:196: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:196: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:196: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:196: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:197: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:197: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:198: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:199: error: expected declaration specifiers or â...â before âgcharâ
/usr/include/gkrellm2/gkrellm-public-proto.h:200: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:201: error: expected declaration specifiers or â...â before âgcharâ
/usr/include/gkrellm2/gkrellm-public-proto.h:202: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:202: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:203: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:203: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:205: error: expected declaration specifiers or â...â before âgcharâ
/usr/include/gkrellm2/gkrellm-public-proto.h:206: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:206: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:207: error: expected declaration specifiers or â...â before âgcharâ
/usr/include/gkrellm2/gkrellm-public-proto.h:208: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:208: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:210: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:210: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:210: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:212: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:212: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:212: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:214: error: expected declaration specifiers or â...â before âgbooleanâ
/usr/include/gkrellm2/gkrellm-public-proto.h:216: error: expected declaration specifiers or â...â before âgbooleanâ
/usr/include/gkrellm2/gkrellm-public-proto.h:218: error: expected declaration specifiers or â...â before âgbooleanâ
/usr/include/gkrellm2/gkrellm-public-proto.h:221: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:221: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:223: error: expected declaration specifiers or â...â before âgcharâ
/usr/include/gkrellm2/gkrellm-public-proto.h:225: error: expected declaration specifiers or â...â before âgcharâ
/usr/include/gkrellm2/gkrellm-public-proto.h:228: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:228: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:229: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:229: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:230: error: expected declaration specifiers or â...â before âgbooleanâ
/usr/include/gkrellm2/gkrellm-public-proto.h:234: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_is_decal_visibleâ
/usr/include/gkrellm2/gkrellm-public-proto.h:236: error: expected declaration specifiers or â...â before âgbooleanâ
/usr/include/gkrellm2/gkrellm-public-proto.h:237: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:239: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:241: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:241: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:243: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:243: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:243: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:243: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:252: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:254: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:257: error: expected declaration specifiers or â...â before âgbooleanâ
/usr/include/gkrellm2/gkrellm-public-proto.h:257: error: expected declaration specifiers or â...â before âgbooleanâ
/usr/include/gkrellm2/gkrellm-public-proto.h:258: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:258: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:258: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:259: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:259: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:259: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:259: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:263: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:263: error: expected declaration specifiers or â...â before âgpointerâ
/usr/include/gkrellm2/gkrellm-public-proto.h:264: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_in_buttonâ
/usr/include/gkrellm2/gkrellm-public-proto.h:265: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_in_decalâ
/usr/include/gkrellm2/gkrellm-public-proto.h:270: error: expected declaration specifiers or â...â before âgbooleanâ
/usr/include/gkrellm2/gkrellm-public-proto.h:278: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_load_piximageâ
/usr/include/gkrellm2/gkrellm-public-proto.h:280: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_load_piximage_from_inlineâ
/usr/include/gkrellm2/gkrellm-public-proto.h:282: error: expected â;â, â,â or â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:284: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:285: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:288: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_scale_pixbuf_to_pixmapâ
/usr/include/gkrellm2/gkrellm-public-proto.h:291: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:293: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_scale_piximage_to_pixmapâ
/usr/include/gkrellm2/gkrellm-public-proto.h:296: error: expected declaration specifiers or â...â before âGdkDrawableâ
/usr/include/gkrellm2/gkrellm-public-proto.h:297: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:297: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:297: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:297: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:298: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:300: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_scale_theme_backgroundâ
/usr/include/gkrellm2/gkrellm-public-proto.h:305: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_clone_pixmapâ
/usr/include/gkrellm2/gkrellm-public-proto.h:306: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_clone_bitmapâ
/usr/include/gkrellm2/gkrellm-public-proto.h:307: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:308: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:313: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:314: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_set_gkrellmrc_piximage_borderâ
/usr/include/gkrellm2/gkrellm-public-proto.h:316: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_get_gkrellmrc_integerâ
/usr/include/gkrellm2/gkrellm-public-proto.h:317: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:318: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_get_gkrellmrc_piximage_borderâ
/usr/include/gkrellm2/gkrellm-public-proto.h:323: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:325: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:327: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:329: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:330: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:339: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_using_default_themeâ
/usr/include/gkrellm2/gkrellm-public-proto.h:340: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_get_theme_scaleâ
/usr/include/gkrellm2/gkrellm-public-proto.h:342: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_config_window_shownâ
/usr/include/gkrellm2/gkrellm-public-proto.h:347: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:347: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:348: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_style_is_themedâ
/usr/include/gkrellm2/gkrellm-public-proto.h:349: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:350: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:351: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:351: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:356: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:361: error: expected declaration specifiers or â...â before âgcharâ
/usr/include/gkrellm2/gkrellm-public-proto.h:361: error: expected declaration specifiers or â...â before âgcharâ
/usr/include/gkrellm2/gkrellm-public-proto.h:362: error: expected declaration specifiers or â...â before âgbooleanâ
/usr/include/gkrellm2/gkrellm-public-proto.h:362: error: expected declaration specifiers or â...â before âgbooleanâ
/usr/include/gkrellm2/gkrellm-public-proto.h:362: error: expected declaration specifiers or â...â before âgbooleanâ
/usr/include/gkrellm2/gkrellm-public-proto.h:363: error: expected declaration specifiers or â...â before âgfloatâ
/usr/include/gkrellm2/gkrellm-public-proto.h:363: error: expected declaration specifiers or â...â before âgfloatâ
/usr/include/gkrellm2/gkrellm-public-proto.h:363: error: expected declaration specifiers or â...â before âgfloatâ
/usr/include/gkrellm2/gkrellm-public-proto.h:363: error: expected declaration specifiers or â...â before âgfloatâ
/usr/include/gkrellm2/gkrellm-public-proto.h:363: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:366: error: expected declaration specifiers or â...â before âgfloatâ
/usr/include/gkrellm2/gkrellm-public-proto.h:372: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_alert_is_activatedâ
/usr/include/gkrellm2/gkrellm-public-proto.h:374: error: expected declaration specifiers or â...â before âgbooleanâ
/usr/include/gkrellm2/gkrellm-public-proto.h:374: error: expected declaration specifiers or â...â before âgbooleanâ
/usr/include/gkrellm2/gkrellm-public-proto.h:376: error: expected declaration specifiers or â...â before âgpointerâ
/usr/include/gkrellm2/gkrellm-public-proto.h:378: error: expected declaration specifiers or â...â before âgpointerâ
/usr/include/gkrellm2/gkrellm-public-proto.h:380: error: expected declaration specifiers or â...â before âgpointerâ
/usr/include/gkrellm2/gkrellm-public-proto.h:382: error: expected declaration specifiers or â...â before âgpointerâ
/usr/include/gkrellm2/gkrellm-public-proto.h:384: error: expected declaration specifiers or â...â before âgpointerâ
/usr/include/gkrellm2/gkrellm-public-proto.h:386: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_alert_decal_visibleâ
/usr/include/gkrellm2/gkrellm-public-proto.h:389: error: expected declaration specifiers or â...â before âgcharâ
/usr/include/gkrellm2/gkrellm-public-proto.h:389: error: expected declaration specifiers or â...â before âgcharâ
/usr/include/gkrellm2/gkrellm-public-proto.h:390: error: expected declaration specifiers or â...â before âgcharâ
/usr/include/gkrellm2/gkrellm-public-proto.h:392: error: expected declaration specifiers or â...â before âgfloatâ
/usr/include/gkrellm2/gkrellm-public-proto.h:392: error: expected declaration specifiers or â...â before âgfloatâ
/usr/include/gkrellm2/gkrellm-public-proto.h:393: error: expected declaration specifiers or â...â before âgfloatâ
/usr/include/gkrellm2/gkrellm-public-proto.h:393: error: expected declaration specifiers or â...â before âgfloatâ
/usr/include/gkrellm2/gkrellm-public-proto.h:394: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:395: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:396: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:396: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:398: error: expected declaration specifiers or â...â before âgbooleanâ
/usr/include/gkrellm2/gkrellm-public-proto.h:398: error: expected declaration specifiers or â...â before âgbooleanâ
/usr/include/gkrellm2/gkrellm-public-proto.h:402: error: expected declaration specifiers or â...â before âgcharâ
/usr/include/gkrellm2/gkrellm-public-proto.h:408: error: expected declaration specifiers or â...â before âgcharâ
/usr/include/gkrellm2/gkrellm-public-proto.h:411: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:413: error: expected declaration specifiers or â...â before âgpointerâ
/usr/include/gkrellm2/gkrellm-public-proto.h:416: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_alert_plugin_get_dataâ
/usr/include/gkrellm2/gkrellm-public-proto.h:419: error: expected declaration specifiers or â...â before âgcharâ
/usr/include/gkrellm2/gkrellm-public-proto.h:419: error: expected declaration specifiers or â...â before âgcharâ
/usr/include/gkrellm2/gkrellm-public-proto.h:419: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:424: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_add_chart_styleâ
/usr/include/gkrellm2/gkrellm-public-proto.h:425: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_add_meter_styleâ
/usr/include/gkrellm2/gkrellm-public-proto.h:426: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_lookup_chart_style_idâ
/usr/include/gkrellm2/gkrellm-public-proto.h:427: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_lookup_meter_style_idâ
/usr/include/gkrellm2/gkrellm-public-proto.h:431: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:432: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:433: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:454: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:455: error: expected declaration specifiers or â...â before âgintâ
/usr/include/gkrellm2/gkrellm-public-proto.h:456: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:457: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:458: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:459: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:460: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:461: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:466: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:467: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:468: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:469: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:470: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:471: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:472: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:473: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_demo_modeâ
/usr/include/gkrellm2/gkrellm-public-proto.h:474: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_update_HZâ
/usr/include/gkrellm2/gkrellm-public-proto.h:475: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:476: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_get_timer_ticksâ
/usr/include/gkrellm2/gkrellm-public-proto.h:478: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:479: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_plugin_debugâ
/usr/include/gkrellm2/gkrellm-public-proto.h:484: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:485: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:486: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:487: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:489: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:490: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:493: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:495: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:498: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:500: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:503: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:505: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:507: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:509: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:512: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:514: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:515: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:517: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:525: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:526: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_dup_stringâ
/usr/include/gkrellm2/gkrellm-public-proto.h:527: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_locale_dup_stringâ
/usr/include/gkrellm2/gkrellm-public-proto.h:528: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:529: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:530: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:532: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_125_sequenceâ
/usr/include/gkrellm2/gkrellm-public-proto.h:542: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_smp_cpusâ
/usr/include/gkrellm2/gkrellm-public-proto.h:543: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_cpu_statsâ
/usr/include/gkrellm2/gkrellm-public-proto.h:548: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_disk_temperature_displayâ
/usr/include/gkrellm2/gkrellm-public-proto.h:550: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:555: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_net_routesâ
/usr/include/gkrellm2/gkrellm-public-proto.h:556: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_net_statsâ
/usr/include/gkrellm2/gkrellm-public-proto.h:557: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:563: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_get_mail_mute_modeâ
/usr/include/gkrellm2/gkrellm-public-proto.h:564: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_add_external_mboxâ
/usr/include/gkrellm2/gkrellm-public-proto.h:567: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:572: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_client_modeâ
/usr/include/gkrellm2/gkrellm-public-proto.h:573: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:576: error: expected declaration specifiers or â...â before âgcharâ
/usr/include/gkrellm2/gkrellm-public-proto.h:576: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:577: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:579: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_client_send_to_serverâ
/usr/include/gkrellm2/gkrellm-public-proto.h:580: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_client_check_server_versionâ
/usr/include/gkrellm2/gkrellm-public-proto.h:584: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:587: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:591: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_gdk_string_widthâ
/usr/include/gkrellm2/gkrellm-public-proto.h:592: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_gdk_string_markup_widthâ
/usr/include/gkrellm2/gkrellm-public-proto.h:593: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_gdk_text_widthâ
/usr/include/gkrellm2/gkrellm-public-proto.h:595: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgkrellm_gdk_text_markup_widthâ
/usr/include/gkrellm2/gkrellm-public-proto.h:597: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:600: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:603: error: expected â)â before â*â token
/usr/include/gkrellm2/gkrellm-public-proto.h:606: error: expected â)â before â*â token
gkrellmlaunch.c:54: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
gkrellmlaunch.c:70: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âGKrellMLaunchAboutâ
gkrellmlaunch.c:83: error: expected specifier-qualifier-list before âgintâ
gkrellmlaunch.c:95: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
gkrellmlaunch.c:107: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âlistModifiedâ
gkrellmlaunch.c:109: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âstyle_idâ
gkrellmlaunch.c:114: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
gkrellmlaunch.c:115: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
gkrellmlaunch.c:116: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
gkrellmlaunch.c:117: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
gkrellmlaunch.c:121: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
gkrellmlaunch.c:126: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âselectedRowâ
gkrellmlaunch.c: In function âbuttonPressâ:
gkrellmlaunch.c:133: error: âgcharâ undeclared (first use in this function)
gkrellmlaunch.c:133: error: (Each undeclared identifier is reported only once
gkrellmlaunch.c:133: error: for each function it appears in.)
gkrellmlaunch.c:133: error: âcmdRunâ undeclared (first use in this function)
gkrellmlaunch.c:134: error: âgintâ undeclared (first use in this function)
gkrellmlaunch.c:134: error: expected â;â before âiâ
gkrellmlaunch.c:135: error: expected â;â before âselectedâ
gkrellmlaunch.c:137: error: âGListâ undeclared (first use in this function)
gkrellmlaunch.c:137: error: âlistâ undeclared (first use in this function)
gkrellmlaunch.c:157: error: âselectedâ undeclared (first use in this function)
gkrellmlaunch.c:157: warning: implicit declaration of function âGPOINTER_TO_INTâ
gkrellmlaunch.c:157: error: âGkrellmDecalbuttonâ has no member named âdataâ
gkrellmlaunch.c:168: error: âiâ undeclared (first use in this function)
gkrellmlaunch.c:168: error: âlauncherListâ undeclared (first use in this function)
gkrellmlaunch.c:168: warning: left-hand operand of comma expression has no effect
gkrellmlaunch.c:168: warning: left-hand operand of comma expression has no effect
gkrellmlaunch.c:177: warning: implicit declaration of function âg_strdupâ
gkrellmlaunch.c:177: error: âGLauncherâ has no member named âcmdâ
gkrellmlaunch.c:178: warning: implicit declaration of function âg_spawn_command_line_asyncâ
gkrellmlaunch.c:183: warning: implicit declaration of function âg_freeâ
gkrellmlaunch.c: At top level:
gkrellmlaunch.c:187: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âpanel_expose_eventâ
gkrellmlaunch.c: In function âsetVisibilityâ:
gkrellmlaunch.c:218: error: âGListâ undeclared (first use in this function)
gkrellmlaunch.c:218: error: âlistâ undeclared (first use in this function)
gkrellmlaunch.c:220: error: âlauncherListâ undeclared (first use in this function)
gkrellmlaunch.c:223: error: âGLauncherâ has no member named âvisibleâ
gkrellmlaunch.c:225: error: âGLauncherâ has no member named âpanelâ
gkrellmlaunch.c:229: error: âGLauncherâ has no member named âpanelâ
gkrellmlaunch.c: In function âupdate_pluginâ:
gkrellmlaunch.c:237: error: âGListâ undeclared (first use in this function)
gkrellmlaunch.c:237: error: âlistâ undeclared (first use in this function)
gkrellmlaunch.c:239: error: âlauncherListâ undeclared (first use in this function)
gkrellmlaunch.c:242: error: âGLauncherâ has no member named âpanelâ
gkrellmlaunch.c: In function âsave_plugin_configâ:
gkrellmlaunch.c:252: error: âGListâ undeclared (first use in this function)
gkrellmlaunch.c:252: error: âlistâ undeclared (first use in this function)
gkrellmlaunch.c:253: error: âgcharâ undeclared (first use in this function)
gkrellmlaunch.c:253: error: âptrâ undeclared (first use in this function)
gkrellmlaunch.c:255: error: âlauncherListâ undeclared (first use in this function)
gkrellmlaunch.c:263: error: âGLauncherâ has no member named âlabelâ
gkrellmlaunch.c:271: error: âGLauncherâ has no member named âvisibleâ
gkrellmlaunch.c:272: error: âGLauncherâ has no member named âlabelâ
gkrellmlaunch.c:272: error: âGLauncherâ has no member named âcmdâ
gkrellmlaunch.c: In function âapply_plugin_configâ:
gkrellmlaunch.c:278: error: âgcharâ undeclared (first use in this function)
gkrellmlaunch.c:278: error: âstringâ undeclared (first use in this function)
gkrellmlaunch.c:279: error: âgintâ undeclared (first use in this function)
gkrellmlaunch.c:279: error: expected â;â before âiâ
gkrellmlaunch.c:280: error: expected â;â before ârowâ
gkrellmlaunch.c:282: error: âGListâ undeclared (first use in this function)
gkrellmlaunch.c:282: error: âlistâ undeclared (first use in this function)
gkrellmlaunch.c:283: error: ânewListâ undeclared (first use in this function)
gkrellmlaunch.c:288: error: âlistModifiedâ undeclared (first use in this function)
gkrellmlaunch.c:300: error: ârowâ undeclared (first use in this function)
gkrellmlaunch.c:300: warning: implicit declaration of function âGTK_CLISTâ
gkrellmlaunch.c:300: error: âlauncherCListâ undeclared (first use in this function)
gkrellmlaunch.c:300: error: invalid type argument of â->â
gkrellmlaunch.c:302: warning: implicit declaration of function âg_new0â
gkrellmlaunch.c:302: error: expected expression before âGLauncherâ
gkrellmlaunch.c:302: warning: assignment makes pointer from integer without a cast
gkrellmlaunch.c:303: warning: implicit declaration of function âg_list_appendâ
gkrellmlaunch.c:305: warning: implicit declaration of function âgtk_clist_set_row_dataâ
gkrellmlaunch.c:310: warning: implicit declaration of function âgtk_clist_get_textâ
gkrellmlaunch.c:311: error: âGLauncherâ has no member named âvisibleâ
gkrellmlaunch.c:317: warning: implicit declaration of function âgkrellm_dup_stringâ
gkrellmlaunch.c:317: error: âGLauncherâ has no member named âlabelâ
gkrellmlaunch.c:323: error: âGLauncherâ has no member named âcmdâ
gkrellmlaunch.c:330: error: âlauncherListâ undeclared (first use in this function)
gkrellmlaunch.c:333: error: âGLauncherâ has no member named âpanelâ
gkrellmlaunch.c:334: warning: implicit declaration of function âg_list_removeâ
gkrellmlaunch.c:350: error: âstyle_idâ undeclared (first use in this function)
gkrellmlaunch.c:354: error: âiâ undeclared (first use in this function)
gkrellmlaunch.c:354: warning: left-hand operand of comma expression has no effect
gkrellmlaunch.c:354: warning: left-hand operand of comma expression has no effect
gkrellmlaunch.c:357: error: âGLauncherâ has no member named âpanelâ
gkrellmlaunch.c:358: error: âGLauncherâ has no member named âdecalâ
gkrellmlaunch.c:358: error: âGLauncherâ has no member named âpanelâ
gkrellmlaunch.c:359: error: âGLauncherâ has no member named âlabelâ
gkrellmlaunch.c:359: warning: passing argument 3 of âgkrellm_create_decal_textâ from incompatible pointer type
gkrellmlaunch.c:359: error: too many arguments to function âgkrellm_create_decal_textâ
gkrellmlaunch.c:364: error: âGLauncherâ has no member named âpanelâ
gkrellmlaunch.c:364: error: too many arguments to function âgkrellm_panel_configureâ
gkrellmlaunch.c:365: warning: implicit declaration of function âgkrellm_panel_createâ
gkrellmlaunch.c:365: error: âlauncherVboxâ undeclared (first use in this function)
gkrellmlaunch.c:365: error: âGLauncherâ has no member named âpanelâ
gkrellmlaunch.c:370: error: âGLauncherâ has no member named âpanelâ
gkrellmlaunch.c:370: error: âGLauncherâ has no member named âdecalâ
gkrellmlaunch.c:371: error: âGLauncherâ has no member named âlabelâ
gkrellmlaunch.c:371: error: too many arguments to function âgkrellm_draw_decal_textâ
gkrellmlaunch.c:373: error: âGLauncherâ has no member named âpanelâ
gkrellmlaunch.c:373: error: âGLauncherâ has no member named âdecalâ
gkrellmlaunch.c:375: warning: implicit declaration of function âGINT_TO_POINTERâ
gkrellmlaunch.c:375: warning: passing argument 4 of âgkrellm_put_decal_in_meter_buttonâ makes pointer from integer without a cast
gkrellmlaunch.c:380: warning: implicit declaration of function âgtk_signal_connectâ
gkrellmlaunch.c:380: warning: implicit declaration of function âGTK_OBJECTâ
gkrellmlaunch.c:380: error: âGLauncherâ has no member named âpanelâ
gkrellmlaunch.c:381: error: âGtkSignalFuncâ undeclared (first use in this function)
gkrellmlaunch.c:381: error: expected â)â before âpanel_expose_eventâ
gkrellmlaunch.c:390: error: âFALSEâ undeclared (first use in this function)
gkrellmlaunch.c: At top level:
gkrellmlaunch.c:394: error: expected â)â before â*â token
gkrellmlaunch.c:433: error: expected â)â before â*â token
gkrellmlaunch.c:458: error: expected â)â before â*â token
gkrellmlaunch.c:480: error: expected â)â before â*â token
gkrellmlaunch.c:501: error: expected â)â before â*â token
gkrellmlaunch.c:514: error: expected â)â before â*â token
gkrellmlaunch.c:544: error: expected â)â before â*â token
gkrellmlaunch.c:590: error: expected â)â before â*â token
gkrellmlaunch.c:615: error: expected â)â before â*â token
gkrellmlaunch.c:803: error: expected â)â before â*â token
gkrellmlaunch.c:891: warning: excess elements in struct initializer
gkrellmlaunch.c:891: warning: (near initialization for âplugin_monâ)
gkrellmlaunch.c:892: warning: excess elements in struct initializer
gkrellmlaunch.c:892: warning: (near initialization for âplugin_monâ)
gkrellmlaunch.c:893: error: âcreate_pluginâ undeclared here (not in a function)
gkrellmlaunch.c:893: warning: excess elements in struct initializer
gkrellmlaunch.c:893: warning: (near initialization for âplugin_monâ)
gkrellmlaunch.c:894: warning: excess elements in struct initializer
gkrellmlaunch.c:894: warning: (near initialization for âplugin_monâ)
gkrellmlaunch.c:895: error: âcreate_plugin_tabâ undeclared here (not in a function)
gkrellmlaunch.c:895: warning: excess elements in struct initializer
gkrellmlaunch.c:895: warning: (near initialization for âplugin_monâ)
gkrellmlaunch.c:896: warning: excess elements in struct initializer
gkrellmlaunch.c:896: warning: (near initialization for âplugin_monâ)
gkrellmlaunch.c:897: warning: excess elements in struct initializer
gkrellmlaunch.c:897: warning: (near initialization for âplugin_monâ)
gkrellmlaunch.c:898: error: âload_plugin_configâ undeclared here (not in a function)
gkrellmlaunch.c:898: warning: excess elements in struct initializer
gkrellmlaunch.c:898: warning: (near initialization for âplugin_monâ)
gkrellmlaunch.c:899: warning: excess elements in struct initializer
gkrellmlaunch.c:899: warning: (near initialization for âplugin_monâ)
gkrellmlaunch.c:901: warning: excess elements in struct initializer
gkrellmlaunch.c:901: warning: (near initialization for âplugin_monâ)
gkrellmlaunch.c:902: warning: excess elements in struct initializer
gkrellmlaunch.c:902: warning: (near initialization for âplugin_monâ)
gkrellmlaunch.c:903: warning: excess elements in struct initializer
gkrellmlaunch.c:903: warning: (near initialization for âplugin_monâ)
gkrellmlaunch.c:905: warning: excess elements in struct initializer
gkrellmlaunch.c:905: warning: (near initialization for âplugin_monâ)
gkrellmlaunch.c:907: warning: excess elements in struct initializer
gkrellmlaunch.c:907: warning: (near initialization for âplugin_monâ)
gkrellmlaunch.c:909: warning: excess elements in struct initializer
gkrellmlaunch.c:909: warning: (near initialization for âplugin_monâ)
gkrellmlaunch.c: In function âgkrellm_init_pluginâ:
gkrellmlaunch.c:920: error: âselectedRowâ undeclared (first use in this function)
gkrellmlaunch.c:921: error: âlistModifiedâ undeclared (first use in this function)
gkrellmlaunch.c:921: error: âFALSEâ undeclared (first use in this function)
gkrellmlaunch.c:923: error: âstyle_idâ undeclared (first use in this function)
gkrellmlaunch.c:923: warning: implicit declaration of function âgkrellm_add_meter_styleâ
make: *** [gkrellmlaunch.o] Error 1
phillips321@LinuxDesktop:~/temp/gkrellmlaunch-0.5$

```

---

### Post by ajgreeny on 2007-10-06
Have you installed build-essentials package?   You will need that for any build or compiling work you want to do.

---

