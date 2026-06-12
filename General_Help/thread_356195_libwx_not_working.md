---
title: "libwx not working"
date: 2007-02-08
forum: General Help
---

### Post by gwi on 2007-02-08
I tried to run k-map ([http://k-map.sourceforge.net/)](http://k-map.sourceforge.net/)), which needs libwx. I installed libwxgtk2.6-0 and libwxbase2.6-0 (using Synaptic).
When I start k-map, is says:
```
libwx_gtk2_xrc-2.6.so.0: cannot open shared object file: No such file or directory

```
Looking in /usr/lib I see libwx_gtk2u_xrc-2.6.so.0. All libwx files have an 'u' in their name, but k-map does not expect that. I created symbolic links to the files reported as being missing, like this:
```
lrwxrwxrwx 1 root root 24 2007-02-08 11:40 libwx_gtk2_adv-2.6.so.0 -> libwx_gtk2u_adv-2.6.so.0
lrwxrwxrwx 1 root root 25 2007-02-08 11:40 libwx_gtk2_core-2.6.so.0 -> libwx_gtk2u_core-2.6.so.0
lrwxrwxrwx 1 root root 25 2007-02-08 11:40 libwx_gtk2_html-2.6.so.0 -> libwx_gtk2u_html-2.6.so.0
lrwxrwxrwx 1 root root 24 2007-02-08 11:37 libwx_gtk2_xrc-2.6.so.0 -> libwx_gtk2u_xrc-2.6.so.0

```
Now I get the error message
```
/usr/lib/libwx_gtk2_core-2.6.so.0: version `WX_2.6' not found
```

Can someone tell me why the wxlib packages have other names than expected?
How can I get wxlib working?

I am using Ubuntu 6.10 (kernel 2.6.17-10-generic).

---

