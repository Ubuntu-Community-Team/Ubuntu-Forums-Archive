---
title: "Dash has stopped displaying applications, only files &amp; media"
date: 2013-12-30
forum: General Help
---

### Post by hsweet2 on 2013-12-30
The app lens seems to have died suddenly.  I have no idea why. But it looks like my app lens is on vacation.

Below is the output of the unity command..  I added this bit which showed up on terminal as I tried to find apps on Dash. 

```

WARN  2013-12-30 08:32:56 unity.glib.dbusproxy GLibDBusProxy.cpp:182 Unable to connect to proxy: Error calling StartServiceByName for com.canonical.Unity.Lens.Applications: Timeout was reached
WARN  2013-12-30 08:32:56 unity.glib.dbusproxy GLibDBusProxy.cpp:182 Unable to connect to proxy: Error calling StartServiceByName for com.canonical.Unity.Lens.Applications: Timeout was reached

harry@living-room:~$ WARN  2013-12-30 08:35:23 unity.glib.dbusproxy GLibDBusProxy.cpp:265 Cannot call method Search proxy /com/canonical/unity/lens/applications does not exist
WARN  2013-12-30 08:35:23 unity.glib.dbusproxy GLibDBusProxy.cpp:265 Cannot call method Search proxy /com/canonical/unity/lens/applications does not exist


```

```


Welcome to Ubuntu 12.04.3 LTS (GNU/Linux 3.2.0-57-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

19 packages can be updated.
0 updates are security updates.

 
harry@living-room:~$ setsid unity
harry@living-room:~$ Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
Initializing resize options...done
Initializing place options...done
Initializing move options...done
Initializing wall options...done
Initializing wall options...done
Initializing grid options...done
Initializing session options...done
Initializing gnomecompat options...done
Initializing animation options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing workarounds options...done
Initializing scale options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing ezoom options...done

(compiz:12138): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
Initializing unityshell options...done
harry@living-room:~$ WARN  2013-12-30 08:22:51 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-calc.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2013-12-30 08:22:52 unity <unknown>:0 Failed to fetch type: No such interface `org.ayatana.bamf.window' on object at path /org/ayatana/bamf/window56627036
harry@living-room:~$ ERROR 2013-12-30 08:22:54 unity.glib-gobject <unknown>:0 g_object_unref: assertion `G_IS_OBJECT (object)' failed
Setting Update "main_menu_key"
Setting Update "run_key"
WARN  2013-12-30 08:24:16 unity.glib.dbusproxy GLibDBusProxy.cpp:182 Unable to connect to proxy: Error calling StartServiceByName for com.canonical.Unity.Lens.Applications: Timeout was reached
WARN  2013-12-30 08:24:16 unity.glib.dbusproxy GLibDBusProxy.cpp:182 Unable to connect to proxy: Error calling StartServiceByName for com.canonical.Unity.Lens.Applications: Timeout was reached
^C
harry@living-room:~$ 
 u&#57599;  12.04.3  0:*              19! 16m 0.54 4x1.6GHz 1.9G46% 2013-12-30 08:24:58



```

---

### Post by Rockiger on 2013-12-30
I have the same problem with Dash of an updated Ubuntu from 13.04 to 13.10. My other laptop with a clean installation works still fine.

---

### Post by hsweet2 on 2014-01-04
More on the story... I did a reinstall.  All was well until....  
Took me awhile to figure out that when I changed the blank, temp user folder from the install with my old one, the problem returned.
More than that, the issue seems to be somewhere in the .files and or folders (hidden).  This time I was careful and only copied the old . stuff I knew I needed and all seems good.

It would be interesting to know the exact cause, but this might be helpful to others.  And always keep your /home folder in a separate partition!

---

### Post by jim97321 on 2014-01-06
My problem of missing applications in Dash, I believe, started when I ran "Janitor" (of Ubuntu Tweak), the clean-up application, to free room on my 16GB thumbdrive install.

I did a reinstall of Unity "named" applications and Dash "named" applications and Dash was re-populated with all applications, but it was aparently only transient. Now that I have restarted my thumbdrive on a different computer, Dash is empty again (just shows a file that I previously downloaded). :(

---

### Post by jim97321 on 2014-01-06
Update: I found after rebooting my thumbdrive (on the same computer as my last post), Dash was populated this time, so I updated this thread.

---

### Post by dom134 on 2014-01-28
Hello all, I am running 13.10 and every few days I lose my applications in the Unity Dash.  Files and Folders are showing fine, but no applications.  This 'feature' is normally cured by logging out and back in again, but it is starting to become tedious.  Any thoughts?

---

