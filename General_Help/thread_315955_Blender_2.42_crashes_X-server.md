---
title: "Blender 2.42 crashes X-server"
date: 2006-12-10
forum: General Help
---

### Post by OneSeventeen on 2006-12-10
I am using blender which was installed using the "add/remove" dialog, and after a while (usually only a minute or two) blender crashes the desktop, I see a cursor blinking, then a few seconds later I am allowed to log back into Ubuntu.

I've used blender a lot in Breezy and Dapper, but not in Edgy.  Any ideas why this is happening, or how I can figure out what is going on?  (since it crashes ubuntu I can't really output any error messages)

---

### Post by OneSeventeen on 2006-12-10
I just discovered strace, and here are the last few lines:```
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 7568
stat64("/home/oneseventeen/.blender/scripts/xsi_export.pyc", {st_mode=S_IFREG|0644, st_size=19555, ...}) = 0
stat64("/usr/local/sbin/blender-bin", 0xbfb018ec) = -1 ENOENT (No such file or directory)
stat64("/usr/local/bin/blender-bin", 0xbfb018ec) = -1 ENOENT (No such file or directory)
stat64("/usr/sbin/blender-bin", 0xbfb018ec) = -1 ENOENT (No such file or directory)
stat64("/usr/bin/blender-bin", {st_mode=S_IFREG|0755, st_size=9108388, ...}) = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7de26f8) = 7569
wait4(-1, X connection to :0.0 broken (explicit kill or server shutdown).

[{WIFEXITED(s) && WEXITSTATUS(s) == 1}], 0, NULL) = 7569

```
But none of this means anything to me... any ideas?

---

