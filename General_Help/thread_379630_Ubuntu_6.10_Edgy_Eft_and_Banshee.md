---
title: "Ubuntu 6.10 Edgy Eft and Banshee"
date: 2007-03-08
forum: General Help
---

### Post by louisd11 on 2007-03-08
I am very new to Ubuntu, but I am trying to install banshee and am having a hard time. I think I installed it but when i type in "banshee" in terminal I get the following output.

> :~$ banshee

** ERROR **: file domain.c: line 701 (mono_init_internal): assertion failed: (mono_defaults.monotype_class != 0)
aborting...

=================================================================
Got a SIGABRT while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Stacktrace:


Native stacktrace:

        banshee(mono_handle_native_sigsegv+0xde) [0x815644e]
        [0xffffe440]
        /lib/tls/i686/cmov/libc.so.6(abort+0x103) [0xb7cf5ef3]
        /usr/lib/libglib-2.0.so.0(g_logv+0x4c2) [0xb7e8c122]
        /usr/lib/libglib-2.0.so.0(g_log+0x29) [0xb7e8c159]
        /usr/lib/libglib-2.0.so.0(g_assert_warning+0x76) [0xb7e8c1d6]
        banshee [0x80df833]
        banshee [0x8122374]
        banshee(mono_main+0x389) [0x805c9b9]
        banshee [0x805c122]
        /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7ce08cc]
        banshee [0x805c071]
Aborted (core dumped)


Help would greatly be appreciated, thank you in advanced.

---

### Post by Kateikyoushi on 2007-03-08
How did you install banshee ?

---

### Post by louisd11 on 2007-03-08
I honestly don't remember. I used so many endful tut's that I dont rem, which one got me there. I might have downloaded it and did the ./configure. But IDK any way to remove it?

EDIT: I remember now. I used a DEB package. Titled "banshee_0.11.3+dfsg-0ubuntu1_i386.deb".

---

### Post by louisd11 on 2007-03-08
BUMP ANy one?

---

### Post by old_geekster on 2007-03-09
I installed Banshee using "Synaptic Package Manager".  It was very easy.

You can search for it in the catalog within Synaptic.  Then, mark it for Installation.

I have used all of the music players and it is definitely my favorite.

---

### Post by golem3 on 2007-03-09
There's a new version of Banshee - 0.11.5. You can find the .deb package somewhere here if you don't want to get it via apt-get. Actually, never mind, apt-get has an old version of Banshee. You have to download the source (and compile the tarball) or get the .deb file like I said.

---

### Post by louisd11 on 2007-03-09
thanx for your help but I looked through synapsis and couldn't find it. Does anyone know where I can find a DEB package I'll look around the forums.

EDIT: Hey, I found it in synapsis. Thankyou for all your help!

---

