---
title: "gedit admin:/// no longer work"
date: 2021-04-06
forum: General Help
---

### Post by corradoventu on 2021-04-06
Try: gedit admin:///home I see an error:
```
corrado@corrado-n2-hh-0402:~$ gedit admin:///home

(gedit:12489): GVFS-WARNING **: 17:49:21.210: The peer-to-peer connection failed: Could not connect: Permission denied. Falling back to the session bus. Your application is probably missing --filesystem=xdg-run/gvfsd privileges.

** (gedit:12489): WARNING **: 17:49:21.219: Hit unhandled case 36 (GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Unix process subject does not have uid set) in parse_error.
corrado@corrado-n2-hh-0402:~$

Could not open the file “admin:///home”.
Unexpected error: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Unix process subject does not have uid set
```
the error is already known: [https://gitlab.freedesktop.org/polkit/polkit/-/issues/136](https://gitlab.freedesktop.org/polkit/polkit/-/issues/136)

---

### Post by PJSingh5000 on 2021-04-25
I'm experiencing this issue as well in Ubuntu 21.04.
Is there any work-around?

---

### Post by QIII on 2021-04-26
Moved to General Help since 21.04 has been released.

---

### Post by Impavidus on 2021-04-26
I've never used "gedit admin:///foo/bar". To edit files wich require root permission, you can use sudoedit:```
sudoedit file
```putting the name of the file you want to edit on the command line. This will ask for your password (just like sudo), then it will copy the file to a temporary location, run the default text editor to allow you to edit the file and, after you close the editor, will copy the modified file back. This way, the only tool which runs with root permissions is sudoedit itself.

The default text editor is defined in the environment variable EDITOR. To set it to gedit, add this line to your .bashrc:```
export EDITOR=gedit
```Open a new terminal or source your .bashrc to apply the changes.

---

### Post by PJSingh5000 on 2021-10-24
Is there a bug report for this?

---

