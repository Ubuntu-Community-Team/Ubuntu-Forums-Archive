---
title: "some applications do not show windows in ubuntu 15.04"
date: 2015-04-30
forum: General Help
---

### Post by epicshadowkrazee on 2015-04-30
after installing ubuntu 15.04, applications such as synaptic package manager, google chrome, and occasionally a terminal (all i've encountered so far), will show on the launcher as if they are running, but no window is displayed and the titlebar remains blank, providing no access to the application. what might the problem be? i'm a chrome guy, and i'm using firefox until we get this straightened out.

---

### Post by dino99 on 2015-04-30
the solutions are:
- opening a terminal to run the app and see what you get as warnings/errors
- open nautilus to check /var/log/
- run journalctl

you might find some usefull errors to help you fix that issue

---

### Post by epicshadowkrazee on 2015-04-30
terminal shows:

johnathan@johnathan-Satellite-A205:~$ google-chrome-stable 
[12865:12865:0430/220721:ERROR:url_pattern_set.cc(240)] Invalid url pattern: chrome://print/*

shows up on launcher, no window.

add deluge bittorrent client to the list, as well. no window here either. terminal below.

johnathan@johnathan-Satellite-A205:~$ deluge-gtk
johnathan@johnathan-Satellite-A205:~$ deluge
johnathan@johnathan-Satellite-A205:~$

shows up on launcher, no window, no error messages.

also,
/var/log has several folders and files, what am i looking for exactly?

references to chrome found in syslog include:

Apr 29 23:53:01 johnathan-Satellite-A205 gnome-session[1294]: [email]get_contentWindow@chrome://global/content/bindings/browser.xml[/email]:404:54
Apr 29 23:53:01 johnathan-Satellite-A205 gnome-session[1294]: [email]get_securityUI@chrome://global/content/bindings/browser.xml[/email]:654:17
Apr 29 23:53:01 johnathan-Satellite-A205 gnome-session[1294]: [email]browser_XBL_Constructor@chrome://global/content/bindings/browser.xml[/email]:778:17
Apr 29 23:53:01 johnathan-Satellite-A205 gnome-session[1294]: WARNING: content window passed to PrivateBrowsingUtils.isWindowPrivate. Use isContentWindowPrivate instead (but only for frame scripts).

and this one, over and over, but with different times(?) at the end.

Apr 29 23:54:44 johnathan-Satellite-A205 gnome-session[1294]: [email]Ki@http://www.google.com/chrome/assets/consumer/js/tiffany/tiffany.min.js[/email]:359:400

---

### Post by epicshadowkrazee on 2015-04-30
searching journalctl output has a clue, perhaps?

found my launch attempt in log:

[2311:2311:0430/215350:ERROR:url_pattern_set.cc(240)] Invalid url pattern: chrome://print/*
Apr 30 21:53:54 johnathan-Satellite-A205 gnome-session[945]: ERROR 2015-04-30 21:53:54 unity <unknown>:0 AtkObject* unity_a11y_get_accessible(nux::Object*): assertion 'object != NULL' failed
Apr 30 21:53:55 johnathan-Satellite-A205 gnome-session[945]: message repeated 13 times: [ ERROR 2015-04-30 21:53:54 unity <unknown>:0 AtkObject* unity_a11y_get_accessible(nux::Object*): assertion 'object != NULL' failed]
Apr 30 21:53:55 johnathan-Satellite-A205 gnome-session[945]: ERROR 2015-04-30 21:53:54 unity <unknown>:0 atk_object_ref_state_set: assertion 'ATK_IS_OBJECT (accessible)' failed
Apr 30 21:53:55 johnathan-Satellite-A205 gnome-session[945]: ERROR 2015-04-30 21:53:54 unity <unknown>:0 atk_state_set_contains_state: assertion 'ATK_IS_STATE_SET (set)' failed
Apr 30 21:53:55 johnathan-Satellite-A205 gnome-session[945]: ERROR 2015-04-30 21:53:54 unityy <unknown>:0 g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Apr 30 21:53:55 johnathan-Satellite-A205 gnome-session[945]: ERROR 2015-04-30 21:53:55 unity <unknown>:0 AtkObject* unity_a11y_get_accessible(nux::Object*): assertion 'object != NULL' failed
Apr 30 21:53:55 johnathan-Satellite-A205 gnome-session[945]: message repeated 27 times: [ ERROR 2015-04-30 21:53:55 unity <unknown>:0 AtkObject* unity_a11y_get_accessible(nux::Object*): assertion 'object != NULL' failed]

---

