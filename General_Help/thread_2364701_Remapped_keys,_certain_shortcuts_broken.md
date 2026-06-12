---
title: "Remapped keys, certain shortcuts broken"
date: 2017-06-26
forum: General Help
---

### Post by plkoij on 2017-06-26
I just installed Ubuntu 16.04 on a new Lenovo Ideapad. I remapped a bunch of keys including right shift and right ctrl by editing files under /usr/share/X11/xkb/symbols/. Almost everything works perfectly but certain keyboard shortcuts are broken:

When I press right shift + right ctrl + g (or h, b, or n), the keyboard shortcuts settings page interprets it as "Ctrl+Mod2+Shift R" instead of "Shift+Ctrl+G". Right shift + right ctrl + any other letter works fine. If I change right shift to left shift and/or right ctrl to left ctrl it works fine with g, h, b, and n. It's just that one combination that doesn't work. I'm at a total loss in terms of troubleshooting further.

I dind't mess with any of the letter keys in my remapping, so I don't know why those four would be behaving differently.

---

### Post by QIII on 2017-06-26
Hello!

Can you get things back to where they are default and clean?  It might be easier to get help in stages as you progress.

Cheers!

---

### Post by plkoij on 2017-06-26
I think I've gotten it back to a clean state.

---

### Post by plkoij on 2017-06-26
Here's a diff of the changes I had before:

/usr/share/X11/xkb/symbols/pc:
[FONT=courier new]29,30c29,30[/FONT]
[FONT=courier new]<     key <RTSH> {	[ Shift_R		]	};[/FONT]
[FONT=courier new]<     key <RCTL> {	[ Control_R		]	};[/FONT]
[FONT=courier new]---[/FONT]
[FONT=courier new]>     key <RTSH> {	[ Up		]	};[/FONT]
[FONT=courier new]>     key <RCTL> {	[ Home		]	};[/FONT]
[FONT=courier new]83,86c83,86[/FONT]
[FONT=courier new]<     key   <UP> {	[  Up			]	};[/FONT]
[FONT=courier new]<     key <LEFT> {	[  Left			]	};[/FONT]
[FONT=courier new]<     key <DOWN> {	[  Down			]	};[/FONT]
[FONT=courier new]<     key <RGHT> {	[  Right		]	};[/FONT]
[FONT=courier new]---[/FONT]
[FONT=courier new]>     key   <UP> {	[  Shift_R, Shift_R			]	};[/FONT]
[FONT=courier new]>     key <LEFT> {	[  Control_R, Control_R		]	};[/FONT]
[FONT=courier new]>     key <DOWN> {	[  Left			]	};[/FONT]
[FONT=courier new]>     key <RGHT> {	[  Down		]	};[/FONT]

/usr/share/X11/xkb/symbols/keypad:
[FONT=courier new]20,21c20,21[/FONT]
[FONT=courier new]<     key  <KP0> {	[  KP_Insert,	KP_0	]	};[/FONT]
[FONT=courier new]<     key <KPDL> {	[  KP_Delete,	KP_Decimal ]	};[/FONT]
[FONT=courier new]---[/FONT]
[FONT=courier new]>     key  <KP0> {	[  Right,	Right	]	};[/FONT]
[FONT=courier new]>     key <KPDL> {	[  KP_Delete,	KP_0 ]	};[/FONT]



/usr/share/X11/xkb/symbols/digital_vndr/pc:
[FONT=courier new]90c90[/FONT]
[FONT=courier new]<     key <RTSH> {       [	 Shift_R ] };[/FONT]
[FONT=courier new]---[/FONT]
[FONT=courier new]>     key <RTSH> {       [	 Up ] };[/FONT]
[FONT=courier new]95c95[/FONT]
[FONT=courier new]<     key <RCTL> {       [       Control_R ] };[/FONT]
[FONT=courier new]---[/FONT]
[FONT=courier new]>     key <RCTL> {       [       Home ] };[/FONT]
[FONT=courier new]125,126c125,126[/FONT]
[FONT=courier new]<     key <HOME> {       [	    Home ] };[/FONT]
[FONT=courier new]<     key <PGUP> {       [	   Prior ] };[/FONT]
[FONT=courier new]---[/FONT]
[FONT=courier new]>     key <HOME> {       [	    Control_R ] };[/FONT]
[FONT=courier new]>     key <PGUP> {       [	   Shift_R ] };[/FONT]
[FONT=courier new]131,134c131,134[/FONT]
[FONT=courier new]<     key	  <UP> {       [	      Up ] };[/FONT]
[FONT=courier new]<     key <LEFT> {       [	    Left ] };[/FONT]
[FONT=courier new]<     key <DOWN> {       [	    Down ] };[/FONT]
[FONT=courier new]<     key <RGHT> {       [	   Right ] };[/FONT]
[FONT=courier new]---[/FONT]
[FONT=courier new]>     key	  <UP> {       [	      Shift_R ] };[/FONT]
[FONT=courier new]>     key <LEFT> {       [	    Control_R ] };[/FONT]
[FONT=courier new]>     key <DOWN> {       [	    Left ] };[/FONT]
[FONT=courier new]>     key <RGHT> {       [	   Down ] };[/FONT]
[FONT=courier new]160,161c160,161[/FONT]
[FONT=courier new]<     key	 <KP0> {       [       KP_Insert,	     KP_0 ] };[/FONT]
[FONT=courier new]<     key <KPDL> {       [       KP_Delete,      KP_Decimal ] };[/FONT]
[FONT=courier new]---[/FONT]
[FONT=courier new]>     key	 <KP0> {       [       Right,	     Right ] };[/FONT]
[FONT=courier new]>     key <KPDL> {       [       KP_Delete,      KP_0 ] };[/FONT]

---

