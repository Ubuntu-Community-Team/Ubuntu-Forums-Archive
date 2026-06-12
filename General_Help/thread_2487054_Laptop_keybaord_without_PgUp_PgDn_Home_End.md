---
title: "Laptop keybaord without PgUp PgDn Home End"
date: 2023-05-21
forum: General Help
---

### Post by ccw127 on 2023-05-21
I am using an Asus Zephyrus ga401 laptop, and the keyboard lacks those vital navigation keys (PgUp, PgDn, Home, End). Unlike many other laptops I've used, you cant use Fn + Arrows to get those keys. In fact, Fn + Up/Dn is already mapped to changing keyboard back light brightness. Under Windows I've handled this problem using AutoHotKey and a script that allows me to use the Right Alt key + Arrows to get the 4 keys I need (and it works great in everything other than Microsoft Office). After all my searching, I'm not finding an equivalent method to do this under Ubuntu/Linux. Is there someone out there that has already run into the problem and found a work around?

Thanks,

---

### Post by MAFoElffen on 2023-05-22
RE: [https://github.com/sezanzeb/input-remapper/releases](https://github.com/sezanzeb/input-remapper/releases)

Current version to the Repo version of 
```

mafoelffen@Mikes-ThinkPad-T520:~$ apt-cache show input-remapper
Package: input-remapper
Architecture: all
Version: 1.4.0-1
Priority: optional
Section: universe/misc
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Stephen Kitt <skitt@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 9
Depends: input-remapper-gtk
Filename: pool/universe/i/input-remapper/input-remapper_1.4.0-1_all.deb
Size: 1596
MD5sum: 2b874f2787161307c91c5642842916ba
SHA1: 6ea7457e6ff5609939379d577d57f32b13c124f8
SHA256: 2b16429c780bd1d6e83d4988f357219743a6ce6b9de69e1f0472f3ad4df9e8ee
SHA512: 69d104b940e8b828a905fed285aa9e6611639c7b10abd205e5ad6eeccb846d9d082da6cc00bdffa2042762590497ea4d493562b3354fde254508417e553cb938
Homepage: https://github.com/sezanzeb/input-remapper
Description-en: Input device button mapping tool (metapackage)
 input-remapper allows users to map buttons on all input devices
 (keyboards, mice, gamepads...) in X11 and Wayland. It also supports
 combined buttons and programmable macros.
 .
 input-remapper includes a UI to configure button mappings, per
 device, and configuration to automatically apply button mappings at
 boot and on device connection.
Description-md5: 218fd59ed6f94bce22e72fdc931b3ab6

```

---

### Post by ccw127 on 2023-06-04
So I finally had a chance to play with this. I used the version in the 23.04 LTS Repo, and can get PgUp and PgDn working (Great!). But for some reason, it wont let me do Home and End. I also tried using Ctrl instead of Alt, just in case it was somehow related to my choice of the Alt key, but it made no difference. Any ideas?

---

