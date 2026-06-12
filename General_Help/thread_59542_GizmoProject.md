---
title: "GizmoProject"
date: 2005-08-24
forum: General Help
---

### Post by Jad on 2005-08-24
Hi, 
I'm trying to install Gizmo application which is a replacement of SKype
but i'm having some installing errors
```

jad@madi:~/Desktop $ sudo dpkg -i libsipphoneapi_0.78.20050817.1-1_i386.deb gizmo_0.8.0.6-1_i386.deb
Selecting previously deselected package libsipphoneapi.
(Reading database ... 146244 files and directories currently installed.)
Unpacking libsipphoneapi (from libsipphoneapi_0.78.20050817.1-1_i386.deb) ...
Selecting previously deselected package gizmo.
Unpacking gizmo (from gizmo_0.8.0.6-1_i386.deb) ...
dpkg: dependency problems prevent configuration of libsipphoneapi:
 libsipphoneapi depends on bonjour; however:
  Package bonjour is not installed.
dpkg: error processing libsipphoneapi (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gizmo:
 gizmo depends on libsipphoneapi (>= 0.78.20050817.1); however:
  Package libsipphoneapi is not configured yet.
dpkg: error processing gizmo (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libsipphoneapi
 gizmo
```

any idea?

---

### Post by humanity_to_others on 2005-08-24
[QUOTE=Jad]
```
 Package bonjour is not installed.
```
any idea?[/QUOTE] Install package bonjour.

---

### Post by Lord Illidan on 2005-08-24
If I were you, I would do it in Synaptic... It is easier sometimes to get what you want...maybe one of the dependencies is for example, version 0.9, and the others want version 0.85, in which case you can force the conflicting package to a lower version..

---

### Post by Jad on 2005-08-24
i couldn't find bonjour in any repos, even in Debian repos
and I couldnt find bonjour package website

---

### Post by !nkubus on 2005-08-25
I have the same error, and no sign of bonjour

---

### Post by Jad on 2005-08-25
Here is what to do 

```
sudo apt-get install mdnsresponder
```
browser to the directory where you downloaded Gizmo and libsipphone library .deb files then
```

sudo dpkg -i --force-depends libsipphoneapi_0.78.20050817.1-1_i386.deb gizmo_0.8.0.6-1_i386.deb


ln -s /usr/lib/gnome-vfs-2.0/modules/libdns-sd.so /usr/lib/libdns_sd.so
```

then in terminal type gizmo 
and it will run just fine, but there is only one problem, I'm not able to register till now, and I'm not sure if it's application problem or Gizmo server problem

---

### Post by rwabel on 2005-08-25
they have added the bonjour package. installation works fine. the client is still very early alpha!

---

### Post by Pointwood on 2005-08-25
[QUOTE=rwabel]they have added the bonjour package. installation works fine. the client is still very early alpha![/QUOTE] So, not really worth installing yet?

---

### Post by rwabel on 2005-08-25
[QUOTE=Pointwood]So, not really worth installing yet?[/QUOTE]
 I've just started it up and played for some minutes. As I don't have any friends using gizmo yet I can't test it. For example there preferences aren't there yet. But you can make calls and add friends

---

### Post by Jad on 2005-08-26
I'm not able to register yet
here is the debug message
```

jad@madi:~ $ gizmo
Debug: gizmo_prefs_init
Debug: gizmo_core_init
Debug: gizmo_gtk_stock_init: Loading 64 images
sipphoneapi_new: sipapi ptr: 137028488
Debug: Gizmo is using GTK v2.6.4

(gizmo:8435): Gtk-CRITICAL **: gtk_widget_grab_focus: assertion `GTK_IS_WIDGET (widget)' failed
Error: gizmo_prefs_get_string: Bad key or directory name: "/apps/gizmo/users/": Key/directory may not end with a slash (/)
Debug: anim start
Debug: Gizmo App Started
sapi_register_callbacks: sipapi ptr: 138080672
Debug: gizmo_event_trigger: GIZMO_EVENT_CORE_INIT
Debug: anim stop
Debug: on_login_radio_toggled: 0
Debug: on_register_radio_toggled: 1
Debug: http_get: URL: http://aps.plugndial.com/dll/app?class=DLL;proc=accCreateGetSecImage;SessionID=116390953336025221821350779911023208;ZoneID=1;PartnerID=0
Debug: security_image_cb: sessid: 116390953336025221821350779911023208
Debug: on_login_button_clicked
Debug: anim start
Debug: registration_cb: Success: 1  Msg:
Debug: gizmo_account_new: new account w/ id: 0
Debug: gizmo_account_new: Set user_agent_id: 0
Debug: login_thread_do
Debug: login_cb: Success: 0  Msg: Login failed! We could not validate your username and password!
Debug: anim stop
Debug: gizmo_account_destroy
Debug: gizmo_core_cleanup


```

---

### Post by Pointwood on 2005-08-26
I can start it but when I try to login it stalls at "starting user agent".

Here's what I see:
```
(gizmo:8542): Gtk-CRITICAL **: gtk_widget_grab_focus: assertion `GTK_IS_WIDGET (widget)' failed
Error: gizmo_prefs_get_string: Bad key or directory name: "/apps/gizmo/users/": Key/directory may not end with a slash (/)
Debug: anim start
Debug: Gizmo App Started
sapi_register_callbacks: sipapi ptr: 137830296
Debug: gizmo_event_trigger: GIZMO_EVENT_CORE_INIT
Debug: anim stop
Debug: on_login_button_clicked
Debug: Username: pointwood  Password: bateman
Debug: gizmo_account_new: new account w/ id: 0
Debug: gizmo_account_new: Set user_agent_id: 0
Debug: anim start
Debug: login_thread_do
Debug: gizmo_utils_get_localip: 10.0.0.3
Debug: CLIENT EVENT: SIPPCET_NETWORK_QUALITY_CHANGE - user_agent_id: 0
Debug: gizmo_account_get_by_id: Acct: 139084576 id: 0
Debug: gizmo_event_trigger: GIZMO_EVENT_CORE_NET_QUALITY
Debug: net_quality_cb: level: 50
```

UPDATE: I got it working! It hit me that maybe it didn't like that amaroK and mplayer was running. I closed those 2 and it started up :)

---

### Post by Jad on 2005-08-26
I'm having same problem, it stuck at starting user agent

---

### Post by GazaM on 2005-08-26
[QUOTE=Jad]I'm having same problem, it stuck at starting user agent[/QUOTE]
 i keep getting a segmentation fault when it tries getting past the login screen... here's the command line output, maybe someone can help:

```
gareth@ubuntu:~$ gizmo
Debug: gizmo_prefs_init
Debug: gizmo_core_init
Debug: gizmo_gtk_stock_init: Loading 64 images
sipphoneapi_new: sipapi ptr: 137065888
Debug: Gizmo is using GTK v2.6.4

(gizmo:13359): Gtk-CRITICAL **: gtk_widget_grab_focus: assertion `GTK_IS_WIDGET (widget)' failed
Debug: User: {edited out} Pwd: {edited out}
Debug: anim start
Debug: Gizmo App Started
sapi_register_callbacks: sipapi ptr: 137667496
Debug: gizmo_event_trigger: GIZMO_EVENT_CORE_INIT
Debug: anim stop
Debug: on_login_button_clicked
Debug: Username: {edited out}  Password: {edited out}
Debug: gizmo_account_new: new account w/ id: 0
Debug: gizmo_account_new: Set user_agent_id: 0
Debug: anim start
Debug: login_thread_do
Debug: gizmo_utils_get_localip: 192.168.1.3
Debug: CLIENT EVENT: SIPPCET_NETWORK_QUALITY_CHANGE - user_agent_id: 0
Debug: gizmo_account_get_by_id: Acct: 138689184 id: 0
Debug: gizmo_event_trigger: GIZMO_EVENT_CORE_NET_QUALITY
Debug: net_quality_cb: level: 50
Debug: HELPFUL STR: Registering ...
Debug: login_cb: Success: 1  Msg:
Debug: anim stop
Debug: login_save_user_info
Debug: save
Debug: gizmo_gtk_mainwindow_show
Debug: Finished loading xml widgets
Debug: gizmo_gtk_phonebook_ui_init
Debug: Sel ID: 1
Segmentation fault
```

---

### Post by se user on 2008-04-19
how would i uninstall gizmo i can't find the option to uninstall in the normal uninstaller in ubutu sorry for the noob question i am new

---

