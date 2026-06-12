---
title: "Error configuring Evolution to use Exchange server type"
date: 2005-05-02
forum: General Help
---

### Post by Ceeeez on 2005-05-02
1) Evolution is configured, but when I try to complie ximian-connector-2.2.1I get the following message below:

2) I have used the following command, export PKG_CONFIG_PATH="$PKG_CONFIG_PATH:/usr/lib/pkgconfig , /usr/lib/share, and /usr/lib" to modify the PKG_CONFIG_PATH environment.

3) I have also used the locate command to verify all files are present.

4) I hvae used the cp command to force all the files to look into a single directory just to get past the error.

5) Modified the /etc/lo.so.conf file to include the search paths.


 \\:D/  ](*,) 

Reference #1:
----------------------
checking for evolution-shell-2.2 libedataserverui-1.2 libedata-book-1.2 libedata-cal-1.2 libsoup-2.2 libglade-2.0 libgnomeui-2.0 camel-provider-1.2... Package libedataserverui-1.2 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libedataserverui-1.2.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libedataserverui-1.2' found

configure: error: Library requirements (evolution-shell-2.2 libedataserverui-1.2 libedata-book-1.2 libedata-cal-1.2 libsoup-2.2 libglade-2.0 libgnomeui-2.0 camel-provider-1.2) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.


Thank you in advance,

---

