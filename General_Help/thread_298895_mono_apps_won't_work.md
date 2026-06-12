---
title: "mono apps won't work?"
date: 2006-11-13
forum: General Help
---

### Post by steven43126 on 2006-11-13
Hi,

Been trying to mono to work properly for sometime now i have un-installed and reinstalled it but still the same problem so any help would be greatly appreciated.

As an example this is the output i get when i try to run beagle-search 

>  beagle-search 

** (/usr/lib/beagle/Search.exe:19249): WARNING **: The following assembly referenced from /usr/lib/beagle/Search.exe could not be loaded:
     Assembly:   gnome-sharp    (assemblyref_index=10)
     Version:    2.16.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/beagle).


** (/usr/lib/beagle/Search.exe:19249): WARNING **: Could not load file or assembly 'gnome-sharp, Version=2.16.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Stacktrace:


Native stacktrace:

        beagle-search [0x815a2cd]
        beagle-search [0x8124868]
        [0xffffe440]
        beagle-search(mono_object_new+0x18) [0x8093e98]
        beagle-search(mono_exception_from_name_two_strings+0x44) [0x80cacc4]
        beagle-search(mono_get_exception_file_not_found2+0x4c) [0x80cae2c]
        beagle-search [0x80eaae0]
        beagle-search [0x80f5b85]
        beagle-search(mono_class_vtable+0x35f) [0x8090dff]
        beagle-search(mono_object_new+0x18) [0x8093e98]
        beagle-search(mono_exception_from_name_two_strings+0x44) [0x80cacc4]
        beagle-search(mono_get_exception_file_not_found2+0x4c) [0x80cae2c]
        beagle-search [0x80eaae0]
        beagle-search [0x80f5b85]
        beagle-search(mono_class_vtable+0x35f) [0x8090dff]
        beagle-search(mono_object_new+0x18) [0x8093e98]
        beagle-search(mono_exception_from_name_domain+0x2f) [0x80cb04f]
        beagle-search(mono_exception_from_name+0x28) [0x80cb0c8]
        beagle-search(mono_exception_from_name_msg+0x24) [0x80cb3f4]
        beagle-search [0x81463d0]
        beagle-search [0x814691b]
        beagle-search(mono_runtime_exec_main+0x62) [0x8093752]
        beagle-search(mono_runtime_run_main+0x1b9) [0x8093a39]
        beagle-search(mono_main+0xe41) [0x8058d71]
        beagle-search [0x8057a42]
        /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d818cc]
        beagle-search [0x8057991]


but locate shows 

locate gnome-sharp
/usr/lib/pkgconfig/gnome-sharp-2.0.pc
/usr/lib/pkgconfig/gnome-sharp.pc
/usr/lib/mono/gac/gnome-sharp
/usr/lib/mono/gac/gnome-sharp/1.0.0.0__35e10195dab3c99f
/usr/lib/mono/gac/gnome-sharp/1.0.0.0__35e10195dab3c99f/gnome-sharp.dll.config
/usr/lib/mono/gac/gnome-sharp/1.0.0.0__35e10195dab3c99f/gnome-sharp.dll
/usr/lib/mono/gac/gnome-sharp/2.16.0.0__35e10195dab3c99f
/usr/lib/mono/gac/gnome-sharp/2.16.0.0__35e10195dab3c99f/gnome-sharp.dll.config
/usr/lib/mono/gac/gnome-sharp/2.16.0.0__35e10195dab3c99f/gnome-sharp.dll
/usr/lib/mono/gac/policy.2.4.gnome-sharp
/usr/lib/mono/gac/policy.2.4.gnome-sharp/0.0.0.0__35e10195dab3c99f
/usr/lib/mono/gac/policy.2.4.gnome-sharp/0.0.0.0__35e10195dab3c99f/policy.2.4.gnome-sharp.dll
/usr/lib/mono/gac/policy.2.4.gnome-sharp/0.0.0.0__35e10195dab3c99f/policy.2.4.config
/usr/lib/mono/gac/policy.2.6.gnome-sharp
/usr/lib/mono/gac/policy.2.6.gnome-sharp/0.0.0.0__35e10195dab3c99f
/usr/lib/mono/gac/policy.2.6.gnome-sharp/0.0.0.0__35e10195dab3c99f/policy.2.6.gnome-sharp.dll
/usr/lib/mono/gac/policy.2.6.gnome-sharp/0.0.0.0__35e10195dab3c99f/policy.2.6.config
/usr/lib/mono/gac/policy.2.8.gnome-sharp
/usr/lib/mono/gac/policy.2.8.gnome-sharp/0.0.0.0__35e10195dab3c99f
/usr/lib/mono/gac/policy.2.8.gnome-sharp/0.0.0.0__35e10195dab3c99f/policy.2.8.gnome-sharp.dll
/usr/lib/mono/gac/policy.2.8.gnome-sharp/0.0.0.0__35e10195dab3c99f/policy.2.8.config
/usr/lib/mono/gtk-sharp-2.0/gnome-sharp.dll
/usr/lib/mono/gtk-sharp-2.0/policy.2.4.gnome-sharp.dll
/usr/lib/mono/gtk-sharp-2.0/policy.2.6.gnome-sharp.dll
/usr/lib/mono/gtk-sharp-2.0/policy.2.8.gnome-sharp.dll
/usr/lib/mono/gtk-sharp/gnome-sharp.dll

so i have it installed ?

many thanks in advance.
steve.

---

### Post by j o e l on 2006-12-28
Hello, Steven.  Any luck with this?  I get the same type of error when attempting to run my mono apps in Edgy.  Like your's, mine all worked in Dapper. :-k 

If I find a solution, I'll be sure to post it here.

My thread can be found [here.]("http://ubuntuforums.org/showthread.php?p=1941321#post1941321")

Good luck!

- j o e l

---

### Post by zanglang on 2006-12-28
You seem to be missing libgnome2.0-cil. Try installing it and see what happens? :p

---

