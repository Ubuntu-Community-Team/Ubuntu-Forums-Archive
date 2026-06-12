---
title: "How to open the editor from flatpak version of FileZilla"
date: 2022-08-29
forum: General Help
---

### Post by Paddy Landau on 2022-08-29
I wonder if someone has managed to solve the problem of opening the editor from the flatpak version of FileZilla?

I use gedit, but from searching the net, it seems that this problem is common to other editors as well.

Specifically, in FileZilla:

[LIST]
[*]Edit > Settings > File editing > Use custom editor > [FONT=courier new]/usr/bin/gedit[/FONT]
[/LIST]
This doesn't work. FileZilla complains, because (due to flatpak) it can't see [FONT=courier new]/usr/[/FONT]. The official flatpak way to overcome this is to reference [FONT=courier new]/run/host[/FONT] as follows.

[LIST]
[*]Edit > Settings > File editing > Use custom editor > [FONT=courier new]/run/host/usr/bin/gedit[/FONT]
[/LIST]
This is flatpak's official way to get around flatpak's restriction. Although FileZilla can now see gedit, it still doesn't work. Because…

When trying to edit a file, the following error occurs:
```
/run/host/usr/bin/gedit: error while loading shared libraries: libgedit-41.so: cannot open shared object file: No such file or directory
```
The problem is that [FONT=courier new]libgedit-41.so[/FONT] is in [FONT=courier new]/usr/lib/x86_64-linux-gnu/gedit/[/FONT], and so when accessed from flatpak, gedit needs to reference [FONT=courier new]/run/host/usr/lib/x86_64-linux-gnu/gedit/[/FONT] instead.

I have no idea how to get around this problem.

Would you know how?

---

### Post by vanadium on 2022-08-29
<snip> question was not well understood.

---

### Post by Paddy Landau on 2022-08-29
> **vanadium said:**
> ```

flatpak run <application name>

```
will always do it, where <application name> is a name such as "org.gnome.gedit" for gedit.

You can see the names of your installed applications in the output of "flatpak list".
Thanks, but gedit is installed from the standard repositories. I don't have the flatpak version installed.

Do you suggest that I change to the flatpak version of gedit? I could do so. Nevertheless, it would be good to have an answer that doesn't involve flatpak, because, as I say, other people have the same problem with other editors.

---

### Post by vanadium on 2022-08-29
Sorry, my bad, I will read your original question more carefully now ;)

It looks like the "flatpak spawn" command allows to run an application outside the sandbox or in the host, with the "--host" option. That requires access to the org.freedesktop.Flatpak D-Bus interface, something that eventually can be set using Flatseal or "flatpak override"

For those that do not already know, man pages for all these flatpak commands are available, e.g. "man flatpak-spawn" or "man flatpak-override".

---

### Post by Paddy Landau on 2022-08-29
> **vanadium said:**
> … "flatpak spawn" command… That requires access to the org.freedesktop.Flatpak D-Bus interface
Thank you for this. I was blissfully unaware of the spawn command.

My confusion now is how to grant access to the org.freedesktop.Flatpak D-Bus interface. I tried this in Flatseal:

[LIST]
[*]Turn on both *D-Bus session bus* and *D-Bus system bus*.
[*]Add org.freedesktop.Flatpak to both *System Bus > Talks* and *Session Bus > Talks*.
[/LIST]
I had FileZilla call gedit with:
```
/run/host/usr/bin/flatpak spawn --host /usr/bin/gedit
```
But, that fails for the same reason when accessing flatpak itself!
```
/run/host/usr/bin/flatpak: error while loading shared libraries: libdconf.so.1: cannot open shared object file: No such file or directory
```
I am at a complete loss how to proceed. Are you able to advise, please?

---

### Post by HermanAB on 2022-08-29
I think that for your use case, it would be better not to use the flatpack version of Filezilla, but rather ye gud olde version.

---

### Post by Paddy Landau on 2022-08-29
> **HermanAB said:**
> I think that for your use case, it would be better not to use the flatpack version of Filezilla, but rather ye gud olde version.
That might indeed turn out to be the case, yes. Still, I would love to find a solution to this, because it would teach me more about the flatpak security model, as well as making it easier to keep FileZilla up to date.

---

### Post by Paddy Landau on 2022-08-29
I've found some more detail now that I know what to look for, but I'm still confused.

I've added [FONT=courier new]org.freedesktop.Flatpak[/FONT] override, which can be done either in Flatseal > Session Bus > Talks, or via the CLI:
```
flatpak --user override --talk-name=org.freedesktop.Flatpak org.filezillaproject.Filezilla
```
But, this has changed nothing. I still get exactly same error messages.

EDIT: I also tried changing FileZilla to call [FONT=courier new]/run/host/usr/bin/flatpak --spawn /run/host/usr/bin/gedit[/FONT], but that also did nothing.

I've run out of ideas. I'm at a total loss on this one.

---

### Post by Paddy Landau on 2022-08-29
I managed to figure it out! With a lot of help :)

There were two things conspiring to confuse me.

[LIST]
[*]There is no such flatpak command *spawn*, so [FONT=courier new]flatpak spawn[/FONT] isn't allowed. But, the command [FONT=courier new]flatpak-spawn[/FONT] doesn't exist, except for the brief moment when calling an app from within flatpak itself.
[*]When you enter the required command ([FONT=courier new]flatpak-spawn …[/FONT]) into FileZilla, FileZilla helpfully checks that the command exists — but, of course, [FONT=courier new]flatpak-spawn[/FONT] doesn't yet exist, so FileZilla refuses to accept the command.
[/LIST]
I created a workaround. For anyone else wanting a solution, here it is:

[LIST=1]
[*]Add access to the D-Bus Session [FONT=courier new]org.freedesktop.Flatpak[/FONT] override. Either:
[LIST]
[*]Flatseal > FileZilla > Session Bus > Talks > add [FONT=courier new]org.freedesktop.Flatpak[/FONT]
or:
[*]```
flatpak --user override --talk-name=org.freedesktop.Flatpak org.filezillaproject.Filezilla
```
[/LIST]

[*]Create a custom script to call gedit as follows using the override. The shebang is necessary; I don't know why, but when I don't use it, the command fails. I placed the script in [FONT=courier new]~/bin/geditfilezilla[/FONT]
```
#!/usr/bin/env bash
flatpak-spawn --host gedit "${@}"
```
[*]FileZilla > Edit > Settings > File editing > Use custom editor > [FONT=courier new]/home/paddy/bin/geditfilezilla[/FONT] (change the path as required).
[/LIST]
And that works!

Thank you, @vanadium, for pointing me in the right direction!

---

