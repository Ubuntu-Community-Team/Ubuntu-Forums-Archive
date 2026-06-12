---
title: "Include objTools in kernel debians (linux-headers and linux-image)"
date: 2019-08-12
forum: General Help
---

### Post by coolpul on 2019-08-12
Hi,
We are compiling kernel and creating debians of linux kernel.
Recently, we found that it does not contain **objTools **source files in the debians.
Is there a way, we can include it in debians and will be available after installing debians?

We tried the following:
Approach1:
1. In config file, we enabled [COLOR=#000000]**CONFIG_STACK_VALIDATION**
2. Ran [B]make-kpkg -j4 --rootcmd fakeroot --initrd --append-to-version=-12 kernel_image kernel_headers
[/B]
Approach2:
[/COLOR]1. In config file, we enabled [COLOR=#000000][B]CONFIG_STACK_VALIDATION
[/B]2. Added [/COLOR][COLOR=#008B8B][FONT=Menlo](cd $srctree; find tools/objtool -type f -executable) >> "$objtree/debian/hdrsrcfiles"[/FONT][/COLOR][COLOR=#000000] in [/COLOR]**scripts/package/builddeb**[COLOR=#000000] file[/COLOR]
[COLOR=#000000]3. Ran [B]make-kpkg -j4 --rootcmd fakeroot --initrd --append-to-version=-12 kernel_image kernel_headers
[/B][/COLOR][COLOR=#000000]
Both above created debian files but objTools folder had only Makefile inside linux-headers debian.

When I added **kernel_source** in make-kpkg command, it created debian but on installing it is showing linux-source-12.tar.bz2.

I want to get objTools folders along with all files on installing kernel debians.

Please help.

[/COLOR]

---

