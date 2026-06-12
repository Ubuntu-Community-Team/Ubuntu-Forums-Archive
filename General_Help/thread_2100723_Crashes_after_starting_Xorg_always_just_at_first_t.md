---
title: "Crashes after starting Xorg always just at first time"
date: 2013-01-02
forum: General Help
---

### Post by fmmarzoa on 2013-01-02
Hi there,

I have been experimenting crashes on my Ubuntu 12.04 always at first start of Xorg right after boot. Then automatically starts again and no problems at all after hours of being used.

A collateral symptom is that I cannot change to a text terminal using CTRL+ALT+Fx at the first start neither. It simply ignores these keystrokes. But after it crashes and I login again, they work as expected.

I have an nVidia GeForce card, using last version of propietary driver, and this is my .xsession-errors: 

~$ cat .xsession-errors
openConnection: connect: No such file or directory
cannot connect to brltty at :0
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Initializing composite options...done
/usr/lib/python2.7/dist-packages/gobject/constants.py:24: Warning: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
  import gobject._gobject
** Message: applet now removed from the notification area
Initializing opengl options...done
Initializing decor options...done
Initializing resize options...done
Initializing snap options...done
Initializing unitymtgrabhandles options...done
Initializing move options...done
/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:127: RuntimeWarning: PyOS_InputHook is not available for interactive use of PyGTK
  set_interactive(1)
Initializing grid options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing gnomecompat options...done
Initializing animation options...done
** Message: using fallback from indicator to GtkStatusIcon
Initializing place options...done
Initializing water options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
I/O warning : failed to load external entity "/home/fran/.compiz/session/10bfd8b457e3a77781135715346898349100000288520041"
Initializing session options...done
Initializing blur options...done
"sni-qt/28934" WARN  20:04:29.711 void StatusNotifierItemFactory::connectToSnw() Invalid interface to SNW_SERVICE 
No systemtrayicon available
Initializing ezoom options...done
Initializing wall options...done
Initializing workarounds options...done
Initializing switcher options...done
Initializing fade options...done
Initializing scale options...done

(compiz:28926): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
Initializing unityshell options...done
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"
Setting Update "launcher_hide_mode"
** Message: moving back from GtkStatusIcon to indicator
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1000004

No bp log location saved, using default.
[000:000] Browser XEmbed support present: 1
[000:000] Browser toolkit is Gtk2.
[000:000] Using Gtk2 toolkit
[000:005] Starting client channel.
[000:006] Warning(clientchannel.cc:435): Unreadable or no port file.  Could not initiate GoogleTalkPlugin connection
[000:006] Warning(clientchannel.cc:410): Could not initiate GoogleTalkPlugin connection
[000:006] GoogleTalkPlugin not running. Starting new process...
[000:006] Warning(optionsfile.cc:47): Load: Could not open file, err=2
[000:006] Warning(pluginutils.cc:268): Failed to get GoogleTalkPlugin path. Trying default.
[000:007] Started GoogleTalkPlugin, path=/opt/google/talkplugin/GoogleTalkPlugin
[000:008] Waiting for GoogleTalkPlugin to start...
[001:103] Attempting to connect to GoogleTalkPlugin...
[001:103] Read port file, port=48541
[001:114] Initiated connection to GoogleTalkPlugin
[001:204] Socket connection established
[001:204] ScheduleOnlineCheck: Online check in 5000ms
[001:305] Got cookie response, socket is authorized
[001:305] AUTHORIZED; socket handshake complete

** (zeitgeist-datahub:31083): WARNING **: zeitgeist-datahub.vala:227: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
[006:214] HandleOnlineCheck: Starting check
[006:214] HandleOnlineCheck: OK; current state: 3

** (nautilus:28932): WARNING **: Error calling current_status: Method "current_status" with signature "" on interface "com.ubuntuone.SyncDaemon.Status" doesn't exist


** (nautilus:28932): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed


Any ideas? Thanks a lot in advance.

---

### Post by Calinou on 2013-01-02
Try using the nvidia-current-updates driver instead of nvidia-current. Fixed my computer hanging when playing Cube (2)-based games for me on a 570 GTX.

---

### Post by fmmarzoa on 2013-01-02
> **Calinou said:**
> Try using the nvidia-current-updates driver instead of nvidia-current. Fixed my computer hanging when playing Cube (2)-based games for me on a 570 GTX.

I will give it a try ASAP, thanks. 

Anyway this is not clearly a nVidia driver issue, reading the .xsession-errors it seems more likely is other thing.

Although giving that a try wouldn't harm. :-) 

Thanks a lot,

---

### Post by fmmarzoa on 2013-01-04
Hi,

I am actually using another driver because my card was not supported by nvidia-current. It is nvidia-experimental-310.

But I think it is not a problem of the driver itself, because the error messages seems to point out on another direction.

Bests,

---

### Post by fmmarzoa on 2013-01-04
Ok, it seems to be a bug on ligthdm

I have simply substituted it by gdm in:

/etc/X11/default-display-manager

And the problem's gone.

Bests,

---

