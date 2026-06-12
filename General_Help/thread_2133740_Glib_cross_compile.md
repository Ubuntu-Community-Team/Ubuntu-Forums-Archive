---
title: "Glib cross compile"
date: 2013-04-09
forum: General Help
---

### Post by rspock on 2013-04-09
I'm trying to cross compile glib for an arm based board. I use the arm-linux-gnueabi toolchain.

The ./configure steps went fine but make had an error:


warning: libgmodule-[COLOR=#800000]2.0[/COLOR].so.[COLOR=#800000]0[/COLOR], needed by ./.libs/libgio-[COLOR=#800000]2.0[/COLOR].so, not found ([COLOR=#00008B]try[/COLOR] [COLOR=#00008B]using[/COLOR] -rpath or -rpath-link)./.libs/libgio-[COLOR=#800000]2.0[/COLOR].so: undefined reference to `g_module_close[COLOR=#800000]'[/COLOR]./.libs/libgio-[COLOR=#800000]2.0[/COLOR].so: undefined reference to `g_module_symbol[COLOR=#800000]'[/COLOR]./.libs/libgio-[COLOR=#800000]2.0[/COLOR].so: undefined reference to `g_module_supported[COLOR=#800000]'[/COLOR]./.libs/libgio-[COLOR=#800000]2.0[/COLOR].so: undefined reference to `g_module_open[COLOR=#800000]'[/COLOR]./.libs/libgio-[COLOR=#800000]2.0[/COLOR].so: undefined reference to `g_module_error[COLOR=#800000]'[/COLOR]collect2: error: ld returned [COLOR=#800000]1[/COLOR] exit status

---

