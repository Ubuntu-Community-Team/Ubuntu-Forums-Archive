---
title: "Apxs error"
date: 2005-10-11
forum: General Help
---

### Post by dbee on 2005-10-11
I am trying to install some DSO's in apache2 but the apxs function doesn't seem to want to compile anything ... :( 

apxs -cia mod_chroot.c

mod_chroot.c:98: error: initializer element is not constant
mod_chroot.c:98: error: (near initialization for `chroot_cmds[0]')
mod_chroot.c:100: error: syntax error before "chroot_module"
mod_chroot.c:100: warning: type defaults to `int' in declaration of `chroot_module'
mod_chroot.c:101: error: `STANDARD20_MODULE_STUFF' undeclared here (not in a function)
mod_chroot.c:101: error: initializer element is not constant
mod_chroot.c:101: error: (near initialization for `chroot_module')
mod_chroot.c:102: warning: excess elements in scalar initializer
mod_chroot.c:102: warning: (near initialization for `chroot_module')
mod_chroot.c:103: warning: excess elements in scalar initializer
mod_chroot.c:103: warning: (near initialization for `chroot_module')
mod_chroot.c:104: warning: excess elements in scalar initializer
mod_chroot.c:104: warning: (near initialization for `chroot_module')
mod_chroot.c:105: warning: excess elements in scalar initializer
mod_chroot.c:105: warning: (near initialization for `chroot_module')
mod_chroot.c:106: warning: excess elements in scalar initializer
mod_chroot.c:106: warning: (near initialization for `chroot_module')
mod_chroot.c:108: warning: excess elements in scalar initializer
mod_chroot.c:108: warning: (near initialization for `chroot_module')
mod_chroot.c:108: warning: data definition has no type or storage class
apxs:Break: Command failed with rc=1

anybody got any suggestions ???

---

### Post by dbee on 2005-10-12
bump :)

---

