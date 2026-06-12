---
title: "A couple of problems"
date: 2004-10-26
forum: General Help
---

### Post by OrangeSlice on 2004-10-26
Yes, I am a noob.  Only been using Ubuntu for about a month.  And Linux in general for about 3.  Now that that's out of the way, let's move on to business.

One thing is, I seem to have two separate versions of GLIB installed.  2.0.7 and 2.4.0.  I have no idea how it happened, but they are conflicting with each other and giving me problems when installing software.  Of course, if I remove one, I remove both of them it seems.  And last time that happened I had to boot into a failsafe terminal and manually reinstall it.  Which isn't much of a problem, but if there's a way around it, I'd like to know.

My other issue is while trying to install an application from cvs.  autoconf (./configure) gets through just fine, but running Make hits a screenfull of errors.

/usr/bin/ld: warning: libstdc++.so.3, needed by /usr/bin/../lib/libsigc-1.2.so.5 , may conflict with libstdc++.so.5
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../libgdk-x11-2.0.so: undefined reference to `g_unsetenv'
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../libgtk-x11-2.0.so: undefined reference to `g_str_has_prefix'
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../libgtk-x11-2.0.so: undefined reference to `g_object_interface_find_property'
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../libgtk-x11-2.0.so: undefined reference to `g_type_instance_get_private'
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../libgtk-x11-2.0.so: undefined reference to `g_completion_complete_utf8'
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../libgdk-x11-2.0.so: undefined reference to `g_fprintf'
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../libgtk-x11-2.0.so: undefined reference to `g_param_spec_get_redirect_target'
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../libgtk-x11-2.0.so: undefined reference to `g_object_class_override_property'
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../libgtk-x11-2.0.so: undefined reference to `g_type_class_add_private'
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../libgtk-x11-2.0.so: undefined reference to `g_object_interface_install_property'
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../libglibmm-2.0.so: undefined reference  to `g_set_application_name'
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../libgtk-x11-2.0.so: undefined reference to `g_markup_printf_escaped'
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../libglibmm-2.0.so: undefined reference  to `g_markup_parse_context_get_element'
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../libglibmm-2.0.so: undefined reference  to `g_get_application_name'
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../libgtk-x11-2.0.so: undefined reference to `g_value_take_string'
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../libgtk-x11-2.0.so: undefined reference to `g_sprintf'
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../libgtk-x11-2.0.so: undefined reference to `g_str_has_suffix'
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../libgtk-x11-2.0.so: undefined reference to `g_markup_vprintf_escaped'
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../libpango-1.0.so: undefined reference to `g_unichar_get_mirror_char'

Clearly, as shown by the top line, libsigc is conflicting.  But I can't remove it, via apt-get remove or dpkg -r, both report that the package isn't installed.  The other lines... hell, I don't know.  Help me  :?

---

