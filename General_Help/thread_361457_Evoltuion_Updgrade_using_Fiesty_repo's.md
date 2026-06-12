---
title: "Evoltuion Updgrade using Fiesty repo's"
date: 2007-02-14
forum: General Help
---

### Post by IndigoMontoya on 2007-02-14
I was using Evolution with the exchange connector and it was usable for bit, but now it is losing connection to the backend server more than it is keeping it.  Because of that it is not useful to me anymore.  So I want to install a newer version of evolution (and all its assoicated programs) and I saw that the fiesty repo's have a 2.9.X version.  I dont care if it breaks evolution (right now I don't use it anyway) but I do not want the rest of my system to break.  M

My question is if I can (and how) get the updated evolution via the fiesty repo's without affecting my system as a whole.  I will also accept a direct download of the .debs needed.

Thanks!!

Scott

---

### Post by IndigoMontoya on 2007-02-14
I downloaded the debs from launchpad.net and then did a dpg -i *.deb and got this.

Clearly this is not the way to go about this.  Thoughts?

```
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on libatk1.0-0 (>= 1.13.1); however:
  Version of libatk1.0-0 on system is 1.12.3-0ubuntu1.
 evolution depends on libc6 (>= 2.5-0ubuntu1); however:
  Version of libc6 on system is 2.4-1ubuntu12.3.
 evolution depends on libcairo2 (>= 1.3.12); however:
  Version of libcairo2 on system is 1.2.4-1ubuntu2.
 evolution depends on libcamel1.2-10 (>= 1.9.91); however:
  Package libcamel1.2-10 is not installed.
 evolution depends on libdbus-1-3 (>= 0.94); however:
  Version of libdbus-1-3 on system is 0.93-0ubuntu3.1.
 evolution depends on libdbus-glib-1-2 (>= 0.72); however:
  Version of libdbus-glib-1-2 on system is 0.71-1ubuntu1.
 evolution depends on libebook1.2-9 (>= 1.9.91); however:
  Version of libebook1.2-9 on system is 1.8.1-0ubuntu3.
 evolution depends on libecal1.2-7 (>= 1.9.91); however:
  Version of libecal1.2-7 on system is 1.8.1-0ubuntu3.
 evolution depends on libedataserver1.2-9 (>= 1.9.91); however:
  Package libedataserver1.2-9 is not installed.
 evolution depends on libedataserverui1.2-8 (>= 1.9.91); however:
  Version of libedataserverui1.2-8 on system is 1.8.1-0ubuntu3.
 evolution depends on libegroupwise1.2-13 (>= 1.9.91); however:
  Package libegroupwise1.2-13 is not installed.
 evolution depends on libexchange-storage1.2-3 (>= 1.9.91); however:
  Package libexchange-storage1.2-3 is not installed.
 evolution depends on libfontconfig1 (>= 2.4.0); however:
  Version of libfontconfig1 on system is 2.3.2-7ubuntu2.
 evolution depends on libglib2.0-0 (>= 2.12.9); however:
  Version of libglib2.0-0 on system is 2.12.4-0ubuntu1.
 evolution depends on libgnome-keyring0 (>= 0.7.1); however:
  Version of libgnome-keyring0 on system is 0.6.0-0ubuntu2.
 evolution depends on libgnome-pilot2 (>= 2.0.15); however:
  Version of libgnome-pilot2 on system is 2.0.14-0ubuntu2.
 evolution depends on libgnomeprint2.2-0 (>= 2.17.0); however:
  Version of libgnomeprint2.2-0 on system is 2.12.1-5ubuntu1.
 evolution depends on libgnomeprintui2.2-0 (>= 2.17.0); however:
  Version of libgnomeprintui2.2-0 on system is 2.12.1-4ubuntu2.
 evolution depends on libgnomeui-0 (>= 2.17.1); however:
  Version of libgnomeui-0 on system is 2.16.1-0ubuntu2.
 evolution depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Version of libgnomevfs2-0 on system is 2.16.1-0ubuntu7.
 evolution depends on libgtkhtml3.8-15 (>= 3.13.91); however:
  Version of libgtkhtml3.8-15 on system is 3.12.1-0ubuntu1.
 evolution depends on libnm-glib0; however:
  Package libnm-glib0 is not installed.
 evolution depends on libpango1.0-0 (>= 1.15.5); however:
  Version of libpango1.0-0 on system is 1.14.5-0ubuntu1.
 evolution depends on libpng12-0 (>= 1.2.13-4); however:
  Version of libpng12-0 on system is 1.2.8rel-5.1ubuntu0.1.
 evolution depends on libsoup2.2-8 (>= 2.2.98); however:
  Version of libsoup2.2-8 on system is 2.2.96-0ubuntu2.1.
 evolution depends on libxml2 (>= 2.6.27); however:
  Version of libxml2 on system is 2.6.26.dfsg-2ubuntu4.
 evolution depends on evolution-data-server (>= 1.9.91); however:
  Version of evolution-data-server on system is 1.8.1-0ubuntu3.
dpkg: error processing evolution (--install):
 dependency problems - leaving unconfigured
Setting up evolution-common (2.9.91-0ubuntu1) ...

dpkg: dependency problems prevent configuration of evolution-dbg:
 evolution-dbg depends on evolution (= 2.9.91-0ubuntu1); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-dbg (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-dev:
 evolution-dev depends on evolution (= 2.9.91-0ubuntu1); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-dev (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on evolution (>= 2.9.91); however:
  Package evolution is not configured yet.
 evolution-plugins depends on libatk1.0-0 (>= 1.13.1); however:
  Version of libatk1.0-0 on system is 1.12.3-0ubuntu1.
 evolution-plugins depends on libc6 (>= 2.5-0ubuntu1); however:
  Version of libc6 on system is 2.4-1ubuntu12.3.
 evolution-plugins depends on libcairo2 (>= 1.3.12); however:
  Version of libcairo2 on system is 1.2.4-1ubuntu2.
 evolution-plugins depends on libcamel1.2-10 (>= 1.9.91); however:
  Package libcamel1.2-10 is not installed.
 evolution-plugins depends on libdbus-1-3 (>= 0.94); however:
  Version of libdbus-1-3 on system is 0.93-0ubuntu3.1.
 evolution-plugins depends on libdbus-glib-1-2 (>= 0.72); however:
  Version of libdbus-glib-1-2 on system is 0.71-1ubuntu1.
 evolution-plugins depends on libebook1.2-9 (>= 1.9.91); however:
  Version of libebook1.2-9 on system is 1.8.1-0ubuntu3.
 evolution-plugins depends on libedataserver1.2-9 (>= 1.9.91); however:
  Package libedataserver1.2-9 is not installed.
 evolution-plugins depends on libedataserverui1.2-8 (>= 1.9.91); however:
  Version of libedataserverui1.2-8 on system is 1.8.1-0ubuntu3.
 evolution-plugins depends on libfontconfig1 (>= 2.4.0); however:
  Version of libfontconfig1 on system is 2.3.2-7ubuntu2.
 evolution-plugins depends on libglib2.0-0 (>= 2.12.9); however:
  Version of libglib2.0-0 on system is 2.12.4-0ubuntu1.
 evolution-plugins depends on libgnome-keyring0 (>= 0.7.1); however:
  Version of libgnome-keyring0 on system is 0.6.0-0ubuntu2.
 evolution-plugins depends on libgnomeprint2.2-0 (>= 2.17.0); however:
  Version of libgnomeprint2.2-0 on system is 2.12.1-5ubuntu1.
 evolution-plugins depends on libgnomeprintui2.2-0 (>= 2.17.0); however:
  Version of libgnomeprintui2.2-0 on system is 2.12.1-4ubuntu2.
 evolution-plugins depends on libgnomeui-0 (>= 2.17.1); however:
  Version of libgnomeui-0 on system is 2.16.1-0ubuntu2.
 evolution-plugins depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Version of libgnomevfs2-0 on system is 2.16.1-0ubuntu7.
 evolution-plugins depends on libgtkhtml3.8-15 (>= 3.13.91); however:
  Version of libgtkhtml3.8-15 on system is 3.12.1-0ubuntu1.
 evolution-plugins depends on libpango1.0-0 (>= 1.15.5); however:
  Version of libpango1.0-0 on system is 1.14.5-0ubuntu1.
 evolution-plugins depends on libxml2 (>= 2.6.27); however:
  Version of libxml2 on system is 2.6.26.dfsg-2ubuntu4.
dpkg: error processing evolution-plugins (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins-experimental:
 evolution-plugins-experimental depends on libatk1.0-0 (>= 1.13.1); however:
  Version of libatk1.0-0 on system is 1.12.3-0ubuntu1.
 evolution-plugins-experimental depends on libc6 (>= 2.5-0ubuntu1); however:
  Version of libc6 on system is 2.4-1ubuntu12.3.
 evolution-plugins-experimental depends on libcairo2 (>= 1.3.12); however:
  Version of libcairo2 on system is 1.2.4-1ubuntu2.
 evolution-plugins-experimental depends on libdbus-1-3 (>= 0.94); however:
  Version of libdbus-1-3 on system is 0.93-0ubuntu3.1.
 evolution-plugins-experimental depends on libdbus-glib-1-2 (>= 0.72); however:
  Version of libdbus-glib-1-2 on system is 0.71-1ubuntu1.
 evolution-plugins-experimental depends on libebook1.2-9 (>= 1.9.91); however:
  Version of libebook1.2-9 on system is 1.8.1-0ubuntu3.
 evolution-plugins-experimental depends on libecal1.2-7 (>= 1.9.91); however:
  Version of libecal1.2-7 on system is 1.8.1-0ubuntu3.
 evolution-plugins-experimental depends on libedataserver1.2-9 (>= 1.9.91); however:
  Package libedataserver1.2-9 is not installed.
 evolution-plugins-experimental depends on libedataserverui1.2-8 (>= 1.9.91); however:
  Version of libedataserverui1.2-8 on system is 1.8.1-0ubuntu3.
 evolution-plugins-experimental depends on libfontconfig1 (>= 2.4.0); however:
  Version of libfontconfig1 on system is 2.3.2-7ubuntu2.
 evolution-plugins-experimental depends on libglib2.0-0 (>= 2.12.9); however:
  Version of libglib2.0-0 on system is 2.12.4-0ubuntu1.
 evolution-plugins-experimental depends on libgnome-keyring0 (>= 0.7.1); however:
  Version of libgnome-keyring0 on system is 0.6.0-0ubuntu2.
 evolution-plugins-experimental depends on libgnomeprint2.2-0 (>= 2.17.0); however:
  Version of libgnomeprint2.2-0 on system is 2.12.1-5ubuntu1.
 evolution-plugins-experimental depends on libgnomeprintui2.2-0 (>= 2.17.0); however:
  Version of libgnomeprintui2.2-0 on system is 2.12.1-4ubuntu2.
 evolution-plugins-experimental depends on libgnomeui-0 (>= 2.17.1); however:
  Version of libgnomeui-0 on system is 2.16.1-0ubuntu2.
 evolution-plugins-experimental depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Version of libgnomevfs2-0 on system is 2.16.1-0ubuntu7.
 evolution-plugins-experimental depends on libgtkhtml3.8-15 (>= 3.13.91); however:
  Version of libgtkhtml3.8-15 on system is 3.12.1-0ubuntu1.
 evolution-plugins-experimental depends on libpango1.0-0 (>= 1.15.5); however:
  Version of libpango1.0-0 on system is 1.14.5-0ubuntu1.
 evolution-plugins-experimental depends on libxml2 (>= 2.6.27); however:
  Version of libxml2 on system is 2.6.26.dfsg-2ubuntu4.
 evolution-plugins-experimental depends on evolution (= 2.9.91-0ubuntu1); however:
  Package evolution is not configured yet.

```

---

### Post by dcstar on 2007-02-14
> **IndigoMontoya said:**
> I downloaded the debs from launchpad.net and then did a dpg -i *.deb and got this.

Clearly this is not the way to go about this.  Thoughts?
........

The Edgy version of Evolution could not be Backported to Dapper, I expect that the same issues arise when attempting to Backport this version to be used with Edgy.

There is a HOWTO in the forum on setting up your own Backports, you can try it with Evolution and report back to us if it was successful (or not).

---

