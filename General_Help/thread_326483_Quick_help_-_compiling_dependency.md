---
title: "Quick help - compiling dependency"
date: 2006-12-27
forum: General Help
---

### Post by s_h_a_d_o_w_s on 2006-12-27
I was compiling gtkpod, 

```
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for strerror in -lcposix... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc option to accept ANSI C... none needed
checking for pkg-config... ok
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PACKAGE... no
configure: error: *** No package 'libglade-2.0' found
See `config.log' for more details.
dugster@dugster-desktop:/usr/src/gtkpod-0.99.8$
```But installing it:

```
dugster@dugster-desktop:/usr/src/gtkpod-0.99.8$ sudo apt-get install libglade-2.0
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libglade-2.0
dugster@dugster-desktop:/usr/src/gtkpod-0.99.8$ sudo apt-get install 

```AND

```
libglade-2.0-dev
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libglade-2.0-dev
dugster@dugster-desktop:/usr/src/gtkpod-0.99.8$

```I'm noobish at compiling, I googled to install libglade but i'm just not getting it. Any help would be appreciated.

---

### Post by meng on 2006-12-27
There is a libglade2-0 package, not sure if that's what you need.
By the way, did you know that you can install gtkpod from the repositories, you need to have universe enabled though. If you do it that way, the installer (apt-get or aptitude) will take care of the dependencies for you.

---

