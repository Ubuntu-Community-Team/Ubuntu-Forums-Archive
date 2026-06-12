---
title: "[SOLVED] Ubuntu keeps on returning back to the login screen whenever I leave my it al"
date: 2008-01-27
forum: General Help
---

### Post by mahasmb on 2008-01-27
I'm not entirely sure if my laptop restarts or not. All I know is that after I leave it alone for a while, and come back in say 30 minutes or so instead of the laptop being as I left it, it's at the login screen.

This is really annoying when I'm in the middle of something or even just leaving my laptop on so I can finish a big download.

Any ideas as to what's going on here?

---

### Post by mssever on 2008-01-27
> **mahasmb said:**
> I'm not entirely sure if my laptop restarts or not. All I know is that after I leave it alone for a while, and come back in say 30 minutes or so instead of the laptop being as I left it, it's at the login screen.

This is really annoying when I'm in the middle of something or even just leaving my laptop on so I can finish a big download.

Any ideas as to what's going on here?
The uptime command will tell you if your computer has rebooted.

Just a stab in the dark: If your machine isn't rebooting, then something must be crashing--probably causing GDM or X to crash. Look in ~/.xsession-errors for clues. Since the crash is happening when the computer is idle, there's a very remote chance that your screensaver is the culprit. Try killing it before leaving your computer.

---

### Post by shifty2 on 2008-01-27
I had the issue and disabling the screen saver stopped it logging out like that.

---

### Post by mahasmb on 2008-01-27
Here's my ~/.xsession-errors file. I'm afraid I can't make any sense of it  .

```
        
(process:16439): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:16443): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
===== BEGIN MILESTONES (/usr/sbin/sabayon-apply) =====
MainThread 2008/01/27 14:03:21.3989 (sabayon-apply): Applying profile '/etc/desktop-profiles/default.zip' for user 'maha'
MainThread 2008/01/27 14:03:23.8388 (sabayon-apply): Fatal exception!  Exiting abnormally.
MainThread 2008/01/27 14:03:23.8871 (sabayon-apply): Traceback (most recent call last):
  File "/usr/sbin/sabayon-apply", line 117, in <module>
    profile.apply (is_sabayon_session)
  File "/var/lib/python-support/python2.5/sabayon/userprofile.py", line 390, in apply
    s.apply (is_sabayon_session)
  File "/var/lib/python-support/python2.5/sabayon/sources/filessource.py", line 151, in apply
    self.storage.foreach (self.__apply_foreach, source = self.name)
  File "/var/lib/python-support/python2.5/sabayon/storage.py", line 558, in foreach
    self.__foreach_node (node, callback, user_data, source)
  File "/var/lib/python-support/python2.5/sabayon/storage.py", line 541, in __foreach_node
    callback (item_source, item_path)
  File "/var/lib/python-support/python2.5/sabayon/sources/filessource.py", line 148, in __apply_foreach
    self.storage.extract (path, self.home_dir, mandatory)
  File "/var/lib/python-support/python2.5/sabayon/storage.py", line 508, in extract
    copy_preserving_permissions (os.path.join (self.temp_path, path), dst_path)
  File "/var/lib/python-support/python2.5/sabayon/storage.py", line 484, in copy_preserving_permissions
    os.unlink (dest) # FIXME: this could fail, but that would be because the parent
OSError: [Errno 13] Permission denied: '/home/maha/Examples/ubuntu Sax.ogg'

===== END MILESTONES (/usr/sbin/sabayon-apply) =====
===== BEGIN RING BUFFER (/usr/sbin/sabayon-apply) =====
MainThread 2008/01/27 14:03:21.3989 (sabayon-apply): Applying profile '/etc/desktop-profiles/default.zip' for user 'maha'
MainThread 2008/01/27 14:03:23.8388 (sabayon-apply): Fatal exception!  Exiting abnormally.
MainThread 2008/01/27 14:03:23.8871 (sabayon-apply): Traceback (most recent call last):
  File "/usr/sbin/sabayon-apply", line 117, in <module>
    profile.apply (is_sabayon_session)
  File "/var/lib/python-support/python2.5/sabayon/userprofile.py", line 390, in apply
    s.apply (is_sabayon_session)
  File "/var/lib/python-support/python2.5/sabayon/sources/filessource.py", line 151, in apply
    self.storage.foreach (self.__apply_foreach, source = self.name)
  File "/var/lib/python-support/python2.5/sabayon/storage.py", line 558, in foreach
    self.__foreach_node (node, callback, user_data, source)
  File "/var/lib/python-support/python2.5/sabayon/storage.py", line 541, in __foreach_node
    callback (item_source, item_path)
  File "/var/lib/python-support/python2.5/sabayon/sources/filessource.py", line 148, in __apply_foreach
    self.storage.extract (path, self.home_dir, mandatory)
  File "/var/lib/python-support/python2.5/sabayon/storage.py", line 508, in extract
    copy_preserving_permissions (os.path.join (self.temp_path, path), dst_path)
  File "/var/lib/python-support/python2.5/sabayon/storage.py", line 484, in copy_preserving_permissions
    os.unlink (dest) # FIXME: this could fail, but that would be because the parent
OSError: [Errno 13] Permission denied: '/home/maha/Examples/ubuntu Sax.ogg'

===== END RING BUFFER (/usr/sbin/sabayon-apply) =====


This configuration for the debug log can be re-created
by putting the following in ~/sabayon-debug-log.conf
(use ';' to separate domain names):

[debug log]
max lines = 1000
Checking for nVidia: not present. 
Starting Xgl with options:  -accel xv:pbuffer -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama 
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
FreeFontPath: FPE "/usr/share/fonts/X11/misc/" refcount is 2, should be 1; fixing.
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
SESSION_MANAGER=local/maha-laptop:/tmp/.ICE-unix/16436
** Message: Not starting remote desktop server
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
Starting gdesklets-daemon...

Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]

Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...

Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
** (trackerd:16559): WARNING **: Tracker daemon is already running - exiting

Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]Initializing gnome-mount extension

Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]opera: [java] Disabling java due to potential problems. If you know
       what you are doing, you can set the environment variable
       OPERA_FORCE_JAVA_ENABLED to '1' to override this.
       Start Opera with '-debugjava' argument for more information.


Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
(Tomboy:16532): Gtk-WARNING **: cannot open display:  

Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]  PID TTY          TIME CMD
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]kbuildsycoca running...
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

                                        
Connected to daemon in 23605 milliseconds.
opera: spellcheck.so: cannot open shared object file: No such file or directory

(gnome-panel:16516): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -15 and height 24

(process:16902): Gtk-CRITICAL **: gtk_clipboard_get_for_display: assertion `display != NULL' failed
Adobe FlashPlayer: gtk_clipboard_get(GDK_SELECTION_PRIMARY); failed. Trying to call gtk_init(0,0);
QGVector::remove: Index 94 out of range
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x1e08685
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x1e08685

(process:24275): Gtk-CRITICAL **: gtk_clipboard_get_for_display: assertion `display != NULL' failed
Adobe FlashPlayer: gtk_clipboard_get(GDK_SELECTION_PRIMARY); failed. Trying to call gtk_init(0,0);

(process:24555): Gtk-CRITICAL **: gtk_clipboard_get_for_display: assertion `display != NULL' failed
Adobe FlashPlayer: gtk_clipboard_get(GDK_SELECTION_PRIMARY); failed. Trying to call gtk_init(0,0);

(process:946): Gtk-CRITICAL **: gtk_clipboard_get_for_display: assertion `display != NULL' failed
Adobe FlashPlayer: gtk_clipboard_get(GDK_SELECTION_PRIMARY); failed. Trying to call gtk_init(0,0);

(process:1274): Gtk-CRITICAL **: gtk_clipboard_get_for_display: assertion `display != NULL' failed
Adobe FlashPlayer: gtk_clipboard_get(GDK_SELECTION_PRIMARY); failed. Trying to call gtk_init(0,0);

(process:1446): Gtk-CRITICAL **: gtk_clipboard_get_for_display: assertion `display != NULL' failed
Adobe FlashPlayer: gtk_clipboard_get(GDK_SELECTION_PRIMARY); failed. Trying to call gtk_init(0,0);

(process:1546): Gtk-CRITICAL **: gtk_clipboard_get_for_display: assertion `display != NULL' failed
Adobe FlashPlayer: gtk_clipboard_get(GDK_SELECTION_PRIMARY); failed. Trying to call gtk_init(0,0);
opera: X Shared memory extension is not available. ZPixmap not supported
opera: Plug-in 16902 is not responding. It will be closed.
opera: Define environment variable OPERA_KEEP_BLOCKED_PLUGIN to keep blocked plug-ins.
opera: Plug-in 24275 is not responding. It will be closed.
opera: Define environment variable OPERA_KEEP_BLOCKED_PLUGIN to keep blocked plug-ins.
opera: Plug-in 24555 is not responding. It will be closed.
opera: Define environment variable OPERA_KEEP_BLOCKED_PLUGIN to keep blocked plug-ins.
opera: Plug-in 946 is not responding. It will be closed.
opera: Define environment variable OPERA_KEEP_BLOCKED_PLUGIN to keep blocked plug-ins.
opera: Plug-in 1274 is not responding. It will be closed.
opera: Define environment variable OPERA_KEEP_BLOCKED_PLUGIN to keep blocked plug-ins.
opera: Plug-in 1446 is not responding. It will be closed.
opera: Define environment variable OPERA_KEEP_BLOCKED_PLUGIN to keep blocked plug-ins.
opera: Plug-in 1546 is not responding. It will be closed.
opera: Define environ
(process:1634): Gtk-CRITICAL **: gtk_clipboard_get_for_display: assertion `display != NULL' failed
Adobe FlashPlayer: gtk_clipboard_get(GDK_SELECTION_PRIMARY); failed. Trying to call gtk_init(0,0);

(process:1674): Gtk-CRITICAL **: gtk_clipboard_get_for_display: assertion `display != NULL' failed
Adobe FlashPlayer: gtk_clipboard_get(GDK_SELECTION_PRIMARY); failed. Trying to call gtk_init(0,0);

(process:1702): Gtk-CRITICAL **: gtk_clipboard_get_for_display: assertion `display != NULL' failed
Adobe FlashPlayer: gtk_clipboard_get(GDK_SELECTION_PRIMARY); failed. Trying to call gtk_init(0,0);
Initializing gnome-mount extension

** (gnome-system-monitor:13407): WARNING **: SELinux was found but is not enabled.

Initializing gnome-mount extension

(process:23181): Gtk-CRITICAL **: gtk_clipboard_get_for_display: assertion `display != NULL' failed
Adobe FlashPlayer: gtk_clipboard_get(GDK_SELECTION_PRIMARY); failed. Trying to call gtk_init(0,0);

(process:23809): Gtk-CRITICAL **: gtk_clipboard_get_for_display: assertion `display != NULL' failed
Adobe FlashPlayer: gtk_clipboard_get(GDK_SELECTION_PRIMARY); failed. Trying to call gtk_init(0,0); 
```

---

### Post by mssever on 2008-01-27
> **mahasmb said:**
> Here's my ~/.xsession-errors file. I'm afraid I can't make any sense of it  .

Well, sabayon-apply is crashing, and Opera and Adobe Flash Player are also mentioned. You could try disabling/not using those programs for a while to see what's happening. It's possible that sabayon is crashing and taking Gnome down with it, which causes X to exit, which causes GDM to display the login screen.

---

### Post by mahasmb on 2008-01-27
Thanks! I'll try that.

---

### Post by mahasmb on 2008-02-05
Well, instead of Gutsy returning to the login screen when I leave it alone for a while, it now just turns black and stays that way even if I move the mouse or press a bunch of keys. 

I have to reboot the laptop just to be able to use it. 

Here's my ~/.xsession-errors file.

```


(process:5488): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:5492): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
Checking for nVidia: not present. 
Starting Xgl with options:  -accel xv:pbuffer -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama 
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
FreeFontPath: FPE "/usr/share/fonts/X11/misc/" refcount is 2, should be 1; fixing.
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
SESSION_MANAGER=local/maha-laptop:/tmp/.ICE-unix/5483
** Message: Not starting remote desktop server
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.


Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
Throttle level is 0
Starting gdesklets-daemon...

Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]Initializing gnome-mount extension

Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

Connecting to daemon [      ###    ]** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]DCOPClient::attachInternal. Attach failed Could not open network socket

Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]  PID TTY          TIME CMD

Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]kbuildsycoca running...

                                        
Connected to daemon in 31915 milliseconds.

(gnome-panel:5576): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -8 and height 24
/usr/bin/compiz.real (animation) - Debug: polygon.c: pset null at line 1492

/usr/bin/compiz.real (animation) - Debug: polygon.c: pset null at line 1492

/usr/bin/compiz.real (animation) - Debug: polygon.c: pset null at line 1492

Starting Azureus...
Suitable java version found [java = 1.6.0_03]
Configuring environment...
Java exec found in PATH. Verifying...
Browser check failed with: No more handles [Unknown Mozilla path (MOZILLA_FIVE_HOME not set)], InvocationTargetException
Auto-scanning for GRE/XULRunner.  You can skip this by appending the GRE path to LD_LIBRARY_PATH and setting MOZILLA_FIVE_HOME.
  checking /usr/lib/xulrunner for GRE
	Can not use GRE from /usr/lib/xulrunner because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/mozilla for GRE
	Can not use GRE from /usr/lib/mozilla because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/firefox for GRE
GRE found at /usr/lib/firefox.
Browser check failed with: XPCOM error -2147467259, InvocationTargetException
Can't create browser.  Will try to set LD_LIBRARY_PATH and hope  Azureus has better luck.
setting LD_LIBRARY_PATH to: /usr/lib/firefox
setting MOZILLA_FIVE_HOME to: /usr/lib/firefox
Loading Azureus:
java -Xmx128m -cp "./Azureus2.jar:./swt.jar" -Djava.library.path="/opt/azureus" -Dazureus.install.path="/opt/azureus" -Dazureus.script="/opt/azureus/azureus" -Dazureus.script.version=2 org.gudy.azureus2.ui.swt.Main 
changeLocale: *Default Language* != English (Canada). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Canada)' (en_CA), using 'English (default)'
Locale Initializing took 2167ms
   Core: 106ms for Loading Plugin : azemp
   Core: 239ms for Loading Plugin : azplugins
   Core: 23ms for Loading Plugin : azupnpav
   Core: 92ms for Loading Plugin : azrating
   Core: 447ms for Loading Plugin : Built In
   Core: 1505ms for Loading Torrent  2 of 3 : /home/maha/MyDocuments/downloads/AzureusDownloads/[Nyoron Subs] Mobile Suit Gundam 00 - 16 (1280x720 MP3 XviD)[15BDA6B4].avi.torrent
   Core: 3546ms for Initializing Global Torrent Manager
   Core: 151ms for Initializing Plugin: Tracker Static Pages
   Core: 256ms for Initializing Plugin: UPnP Media Server
   Core: 29ms for Initializing Plugin: StartStopRulesDefaultPlugin
   Core: 33ms for Initializing Plugin: PluginUpdate
   Core: 29ms for Initializing Plugin: UPnP
   Core: 22ms for Initializing Plugin: DHT
   Core: 11ms for Initializing Plugin: DHT Tracker
   Core: 11ms for Initializing Plugin: Magnet URI Handler
   Core: 25ms for Initializing Plugin: azextseed
Core Initializing took 5186ms
GUI Initializing took 85ms
DEBUG::Tue Feb 05 21:56:04 GMT 2008  ExternalStimulus debug
   Core: 1503ms for Initializing Plugin: azlocaltracker
   Core: 55ms for Loading Plugin : azemp
skin init took 11393ms
createWindow init took 230ms
skin layout took 1439ms
skin widgets init took 585ms
shell.open took 435ms
psDMS 12ms
processStartupDMS took 0ms

(gecko:19567): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width 250 and height -1
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so [/usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so: undefined symbol: _ZTVN10__cxxabiv121__vmi_class_type_infoE]ne

```

I really can't make any sense of any of this.

---

### Post by mssever on 2008-02-06
I'm not sure whether this will work, but have you tried disabling the screensaver? Also, when it dies, how dead is it? In other words, can you SSH in? <Ctrl><Alt>F1? <Ctrl><Alt>Backspace?

---

### Post by mahasmb on 2008-02-06
I haven't tried SSH, but I definitely have tried Ctrl+Alt+Backspace, I may have tried Ctrl+Alt+F. Nothing worked. The computer's totally dead until I restart.

I have disabled the screensaver, so I'll see if that helps.

Thank you very much so far!

---

### Post by mahasmb on 2008-02-08
Excellent! It seems to work ^_^

I've no problems yet. Again, thank you very much indeed for your help.

---

