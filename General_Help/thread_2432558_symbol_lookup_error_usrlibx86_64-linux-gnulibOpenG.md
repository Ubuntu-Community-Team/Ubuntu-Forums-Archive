---
title: "symbol lookup error: /usr/lib/x86_64-linux-gnu/libOpenGL.so.0: undefined symbol: _gl"
date: 2019-12-04
forum: General Help
---

### Post by ggarra13 on 2019-12-04
I had some problems installing the nvidia graphic drivers (I was unable to login, X11 would not start, etc).  I finally installed them manually with the .run file from the NVIDIA web site and I finally got it to work.

However, when I try to run some programs that use the latest glvnd opengl, I get:

 symbol lookup error: /usr/lib/x86_64-linux-gnu/libOpenGL.so.0: undefined symbol: _glapi_tls_Current

Sure enough, if I do:

$ nm -D /usr/lib/x86_64-linux-gnu/libOpenGL.so.0 | grep glapi
                 U _glapi_tls_Current

No other GL file seems to have the _glapi_tls_Current function.  I need to fix this, so any help is appreciated.

---

### Post by ggarra13 on 2019-12-04
Never mind.  I solved it by an upgrade to the system.

---

