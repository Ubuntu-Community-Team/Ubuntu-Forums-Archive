---
title: "nautilus-flac-converter - How to Install in Ubuntu??"
date: 2008-07-05
forum: General Help
---

### Post by OzzyFrank on 2008-07-05
**nautilus-flac-converter** is a script for the Nautilus context menu to convert from .flac audio format to .ogg. Here is the link to the archive:

[https://sourceforge.net/project/showfiles.php?group_id=158972](https://sourceforge.net/project/showfiles.php?group_id=158972)

Here are the usual install instructions for compiling it from source:

[COLOR="Indigo"]tar jxvf nautilus-flac-converter-0.0.5.tar.bz2
cd nautilus-flac-converter-0.0.3/
./configure
make
sudo make install[/COLOR]

However, when configuring I get errors about dependencies at the end:

[COLOR="Navy"]checking for NAUTILUS... configure: error: Package requirements (
	libnautilus-extension >= 2.12.0
	gtk+-2.0 >= 2.12.0
	gio-2.0 >= 2.15.1
) were not met:

No package 'libnautilus-extension' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables NAUTILUS_CFLAGS
and NAUTILUS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.[/COLOR]

I have **libnautilus-extension** (though is listed in Synaptic as **libnautilus-extension1**), as far as I know **gtk+** is installed, since I use Gnome, but don't know what **gio** is, as it doesn't show up in Synaptic.

Any idea how to get this happening in Ubuntu?

---

### Post by OzzyFrank on 2008-08-11
OK... no one clever enough to know the answer?

---

### Post by ramjet_1953 on 2008-08-11
A few basic things to check.

1. Have you installed the [COLOR="Blue"]build-essential[/COLOR] package?

2. When compiling you almost always need the [COLOR="Blue"].dev package[/COLOR] associated with any dependency. ie If a package called 'fred" is required, you will also need fred.dev.

3. It is also a good idea to install the [COLOR="Blue"]checkinstall[/COLOR] package, as this allows you to create a .deb package of what you compile and you can then install and uninstall easily, using the package manager.

3. A bit off topic, but you may want to check out the [COLOR="Blue"]soundkonverter[/COLOR] package. It is a KDE package, but should also work OK under GNOME. It allows drag and drop conversion of virtually any sound file. It is available in the repositories.

Regards,
Roger :cool:

---

