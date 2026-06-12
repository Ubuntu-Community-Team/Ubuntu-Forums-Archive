---
title: "No automounting in Gnome and Policy Kit problems"
date: 2008-05-21
forum: General Help
---

### Post by rosciol on 2008-05-21
Hello,

I'm running Hardy and I seem to be having the exact same problem as Sam in this post:
[http://ubuntuforums.org/showthread.php?p=4701525](http://ubuntuforums.org/showthread.php?p=4701525)

That post was closed; unfortunately so, since it seems the problem (at least for me) didn't go away.

I am getting the same error messages Sam was getting:
```
Cannot mount volume.

Error org.freedesktop.DBus.Error.AccessDenied.

A security policy is in place the prevents this sender from sending this
message to this recipient, see message bus configuration file (rejected 
message had interface "org.freedesktop.Hal.Device.Volume" member "Mount" 
error name "(unset)" destination "org.freedesktop.Hal")
```

I tried accessing *System -> Administration -> Authorizations*, but it would not let me modify any of the values.  I pulled up a console and ran: ```
sudo polkit-gnome-authorization
```

This let me "modify" the entries; I put this in quotes because, even though I selected new values and clicked "modify", nothing actually changed.  I decided to check the errors in the terminal and the results were not encouraging:

```
[**on startup**]
polkit-read-auth-helper: needs to be setgid polkituser
polkit-read-auth-helper: needs to be setgid polkituser
polkit-read-auth-helper: needs to be setgid polkituser
polkit-read-auth-helper: needs to be setgid polkituser
polkit-read-auth-helper: needs to be setgid polkituser
polkit-read-auth-helper: needs to be setgid polkituser
polkit-read-auth-helper: needs to be setgid polkituser
polkit-read-auth-helper: needs to be setgid polkituser
[**after clicking "Mount filesystems from removeable drives"**]
[WARN  7887] polkit-session.c:285:polkit_session_get_ck_objref(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
[WARN  7887] polkit-session.c:321:polkit_session_get_ck_is_local(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
[WARN  7887] polkit-session.c:303:polkit_session_get_ck_is_active(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
polkit-read-auth-helper: needs to be setgid polkituser
polkit-read-auth-helper: needs to be setgid polkituser

** (polkit-gnome-authorization:7887): WARNING **: Error: code=3: uid 0 is
not authorized to read authorizations for uid -1 (requires 
org.freedesktop.policykit.read)
[**after clicking "edit"**]
polkit-read-auth-helper: needs to be setgid polkituser
polkit-read-auth-helper: needs to be setgid polkituser
polkit-read-auth-helper: needs to be setgid polkituser
[**after clicking "modify"**]
polkit-set-default-helper: needs to be setgid polkituser

** (polkit-gnome-authorization:7887): WARNING **: Error: code=8: 
NotAuthorizedToModifyDefaults: uid 0 is not authorized to modify defaults 
for implicit authorization for action org.freedesktop.hal.storage.mount-
removable (requires org.freedesktop.policykit.modify-defaults)
```

Clearly there are some permissions problems of some form.  However, as it does not specify *what* needs to have group *polkituser*, and I'm not familiar with the policy kit, I don't know what I should be changing to help fix this.

Of particular interest are the paragraphs that say that root is not authorized to view or modify defaults; I didn't really think that was possible for much of anything, let alone a policy kit.  If root can't do it, who can?

Could someone please shed some light on this subject?  It is, I suppose, more of a minor annoyance, since at this moment it only requires me to "sudo mount /dev/sdd1 /media/usb" or similar, but this is still a nice piece of functionality I'd like to have back.

Thanks in advance for any assistance.

- Michael

---

### Post by nutpants on 2008-05-29
im in the same boat..

so


BUMP...

nutz

---

### Post by Jeztastic on 2008-09-01
I have the same problem. Is there really no solution to this?

---

### Post by opscure on 2008-10-30
```
sudo gedit /etc/group
```
add your username after the line:
```
polkituser:x:122:
```

so it should look like:
```
polkituser:x:122:username
```

save and reboot.

---

### Post by Capa Pinbacker on 2009-01-04
I took the advice given here by reinstalling all installed packages with "policykit" in the name via Synaptic.  Permissions issues went away (Ubuntu 8.10).

[http://ubuntuforums.org/archive/index.php/t-718910.html](http://ubuntuforums.org/archive/index.php/t-718910.html)

I still used "sudo polkit-gnome-authorization" to set the authorizations.

---

