---
title: "Install on HDD almost not working... invalid ELF header"
date: 2015-04-27
forum: General Help
---

### Post by mart-e on 2015-04-27
Hello,

I apology for the vague title but I don't really know how to describe my problem.
I have installed ubuntu 15.04 x84_64 on my freshly built PC on the SSD drive (everything seems to works fine). As I changed my mind, I wanted to install it on the HDD instead (taken from a previous computer). I used the same live USB but with target on sdb (so the hard drive) but this time it's no longer working.

I have very few apps I am able to launch. Firefox works (I am writing this post with it) but not nautilus, gnome-terminal or gedit (no error, just not launching). When I open the dash, it founds 0 application.
Hopefully, I have access to a terminal through another tty and /var/log/syslog gives a lot of errors.
[https://gist.github.com/anonymous/461d3e81e79c4edddf96](https://gist.github.com/anonymous/461d3e81e79c4edddf96)

For instance, when I try to launch nautilus, I get
```
Apr 26 20:34:08 ubu2 org.freedesktop.FileManager1[1484]: /usr/bin/nautilus: error while loading shared libraries: /usr/lib/x86_64-linux-gnu/tracker-1.0/libtracker-data.so.0: invalid ELF header
```

or for gedit
```
Apr 27 18:35:03 ubu2 com.canonical.Unity.Scope.Applications[1206]: gedit: error while loading shared libraries: /usr/lib/x86_64-linux-gnu/gedit/libgedit-private.so: invalid ELF header
```

when I search for an application in the menu
```
Apr 27 18:43:01 ubu2 gnome-session[1322]: WARN  2015-04-27 18:43:01 unity.dash.view DashView.cpp:1252 Search failed  ''=> Timed out waiting for scope proxy connection
Apr 27 18:43:01 ubu2 gnome-session[1322]: WARN  2015-04-27 18:43:01 unity.dash.scopeproxy ScopeProxy.cpp:516 Could not search '' on home.scope => Timed out waiting for scope proxy connection
Apr 27 18:43:15 ubu2 gnome-session[1322]: WARN  2015-04-27 18:43:15 unity{?*} <unknown>:0 unity-scope-proxy-remote.vala:399: Unable to set_active (/com/canonical/unity/home): Unable to connect to service
Apr 27 18:43:17 ubu2 gnome-session[1322]: WARN  2015-04-27 18:43:17 unity.dash.view DashView.cpp:1252 Search failed  ''=> Timed out waiting for scope proxy connection
Apr 27 18:43:17 ubu2 gnome-session[1322]: WARN  2015-04-27 18:43:17 unity.dash.scopeproxy ScopeProxy.cpp:516 Could not search '' on home.scope => Timed out waiting for scope proxy connection
Apr 27 18:43:22 ubu2 gnome-session[1322]: WARN  2015-04-27 18:43:22 unity.dash.view DashView.cpp:1252 Search failed  'firefox'=> Timed out waiting for scope proxy connection
Apr 27 18:43:22 ubu2 gnome-session[1322]: WARN  2015-04-27 18:43:22 unity.dash.scopeproxy ScopeProxy.cpp:516 Could not search 'firefox' on home.scope => Timed out waiting for scope proxy connection
Apr 27 18:43:28 ubu2 gnome-session[1322]: WARN  2015-04-27 18:43:28 unity{?*} <unknown>:0 unity-scope-proxy-remote.vala:399: Unable to set_active (/com/canonical/unity/home): Unable to connect to service
Apr 27 18:43:31 ubu2 gnome-session[1322]: WARNING: content window passed to PrivateBrowsingUtils.isWindowPrivate. Use isContentWindowPrivate instead (but only for frame scripts).

```

Sso it looks like everything is broken and yet, I am able to use firefox, connect to internet and watch a youtube video (I am not wondering if I did not install FirefoxOS ;-) )

any idea what it could be ? Broken hardware ? Service not launching ?

Thanks

**edit**: I have checked the problematic file on the install on my SSD and on my HDD and they are different
```
$ sha256sum /usr/lib/x86_64-linux-gnu/tracker-1.0/libtracker-data.so.0 /mnt/usr/lib/x86_64-linux-gnu/tracker-1.0/libtracker-data.so.0
be140b912c0e5d56610f6f26f4fb3130f405e42f3658ebaeaf53535f364fe518  /usr/lib/x86_64-linux-gnu/tracker-1.0/libtracker-data.so.0
b198ccaac58ec3967c790ccd50a0c12f20c43727455a5354849ec91d6afa1a10  /mnt/usr/lib/x86_64-linux-gnu/tracker-1.0/libtracker-data.so.0

```

It's already the second time I make this install :-/

---

