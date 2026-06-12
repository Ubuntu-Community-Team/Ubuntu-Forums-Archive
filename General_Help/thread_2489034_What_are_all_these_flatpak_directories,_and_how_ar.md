---
title: "What are all these flatpak directories, and how are they mounted?"
date: 2023-07-16
forum: General Help
---

### Post by Paddy Landau on 2023-07-16
I don't know a good place to ask this question, so if you do know a better place, please point me there!

flatpak mounts folders on the RAM disk in [FONT=courier new]/run/user/$UID/doc/*name-of-app*/[/FONT]. Each time you use a flatpak after booting, it seems to create a new subfolder.

Some of those folders are persistent across reboots, so they accumulate — and some of them are even invalid!

Those same folders are also listed under [FONT=courier new]/run/user/$UID/doc/[/FONT], so they are available from both places.

For example, here is the listing for Calibre: 8 folders, and another 6 invalid folders.
```
$ [COLOR=#0000cd]ls -l /run/user/1000/doc/by-app/com.calibre_ebook.calibre/[/COLOR]
ls: /run/user/1000/doc/by-app/com.calibre_ebook.calibre/cafec96: No such file or directory
ls: /run/user/1000/doc/by-app/com.calibre_ebook.calibre/9e2e1d26: No such file or directory
ls: /run/user/1000/doc/by-app/com.calibre_ebook.calibre/f94591ca: No such file or directory
ls: /run/user/1000/doc/by-app/com.calibre_ebook.calibre/a8c433ce: No such file or directory
ls: /run/user/1000/doc/by-app/com.calibre_ebook.calibre/c55794c5: No such file or directory
ls: /run/user/1000/doc/by-app/com.calibre_ebook.calibre/bf4588b8: No such file or directory
total 0
drwx------ 2 paddy paddy 0 Jan  1  1970 51fd1a84
drwx------ 2 paddy paddy 0 Jan  1  1970 57e7149d
drwx------ 2 paddy paddy 0 Jan  1  1970 9e2e1d26
drwx------ 2 paddy paddy 0 Jan  1  1970 a8c433ce
drwx------ 2 paddy paddy 0 Jan  1  1970 bf4588b8
drwx------ 2 paddy paddy 0 Jan  1  1970 c55794c5
drwx------ 2 paddy paddy 0 Jan  1  1970 cafec96
drwx------ 2 paddy paddy 0 Jan  1  1970 f94591ca
```
You can see those same folders included in the list of all folders:
```
$ [COLOR=#0000cd]ls -l /run/user/1000/doc/[/COLOR]
ls: /run/user/1000/doc/8f267d36: No such file or directory
ls: /run/user/1000/doc/cafec96: No such file or directory
ls: /run/user/1000/doc/9e2e1d26: No such file or directory
ls: /run/user/1000/doc/f94591ca: No such file or directory
ls: /run/user/1000/doc/a8c433ce: No such file or directory
ls: /run/user/1000/doc/c55794c5: No such file or directory
ls: /run/user/1000/doc/bf4588b8: No such file or directory
ls: /run/user/1000/doc/f991313f: No such file or directory
total 0
drwx------  2 paddy paddy 0 Jan  1  1970 116ee15
drwx------  2 paddy paddy 0 Jan  1  1970 17a1f69b
drwx------  2 paddy paddy 0 Jan  1  1970 2f6cb0a6
drwx------  2 paddy paddy 0 Jan  1  1970 33a89951
drwx------  2 paddy paddy 0 Jan  1  1970 38160461
drwx------  2 paddy paddy 0 Jan  1  1970 44386810
drwx------  2 paddy paddy 0 Jan  1  1970 48e9cdf3
drwx------  2 paddy paddy 0 Jan  1  1970 49dd1348
drwx------  2 paddy paddy 0 Jan  1  1970 4d3106b8
drwx------  2 paddy paddy 0 Jan  1  1970 501d3fee
drwx------  2 paddy paddy 0 Jan  1  1970 51fd1a84
drwx------  2 paddy paddy 0 Jan  1  1970 57e7149d
drwx------  2 paddy paddy 0 Jan  1  1970 58cec66f
drwx------  2 paddy paddy 0 Jan  1  1970 6685ee83
dr-x------+ 2 paddy paddy 0 Jan  1  1970 7535b4c9
drwx------  2 paddy paddy 0 Jan  1  1970 8f267d36
dr-x------+ 2 paddy paddy 0 Jan  1  1970 90cb5787
drwx------  2 paddy paddy 0 Jan  1  1970 98fa3a32
drwx------  2 paddy paddy 0 Jan  1  1970 9e2e1d26
drwx------  2 paddy paddy 0 Jan  1  1970 a01d3ff
drwx------  2 paddy paddy 0 Jan  1  1970 a39fc69c
drwx------  2 paddy paddy 0 Jan  1  1970 a8c433ce
drwx------  2 paddy paddy 0 Jan  1  1970 bb00b10c
drwx------  2 paddy paddy 0 Jan  1  1970 bf4588b8
dr-x------  2 paddy paddy 0 Jan  1  1970 by-app
drwx------  2 paddy paddy 0 Jan  1  1970 c55794c5
drwx------  2 paddy paddy 0 Jan  1  1970 cafec96
drwx------  2 paddy paddy 0 Jan  1  1970 d07077f
drwx------  2 paddy paddy 0 Jan  1  1970 f94591ca
drwx------  2 paddy paddy 0 Jan  1  1970 f991313f
```
Those folders are also visible in Nautilus, with Nautilus showing a red cross on the invalid folders.

I have three questions about these folders.

[LIST=1]
[*]The folders aren't symbolic links, nor are they listed in [FONT=courier new]mount[/FONT]. So, how are they mounted in both places (i.e. under both …[FONT=courier new]/doc/[/FONT] and …[FONT=courier new]/doc/by-app/*name-of-app*/[/FONT])? What mysterious (to me) mechanism is used to create the equivalence?
[*]What are those invalid folders?
[*]Why does flatpak maintain some of these folders (both valid and invalid) across reboots, even though they remain unused and thus accumulate so many?
[/LIST]
Thank you

---

### Post by #&amp;thj^% on 2023-07-16
Paddy that's a big ask, but I can shed some light but not all. (Keep that in mind please)

Flatpak packages are installed to /var/lib/flatpak/app or ~/.local/share/flatpak/app
When you install a Flatpak package, it gets installed in /var/lib/flatpak. All the installed files, metadata, application files, and runtime files are contained in this directory. Also, the user installation directory contains Flatpak data – that is – ~/.local/share/flatpak >> "flatpak uninstall --unused" which removes runtimes and extensions not used by installed applications. This is a small clean-up
ie:
```
flatpak uninstall --unused
Nothing unused to uninstall

```

This command will clean a lot more, 
A sample ran on mine:
```
sudo flatpak repair 
[2/41] Verifying flathub:runtime/org.freedesktop.Platform.GL.default/x86_64/21.0[7/41] Verifying flathub:runtime/org.freedesktop.Platform.ffmpeg-full/x86_64/22.[9/41] Verifying flathub:runtime/org.freedesktop.Platform.GL.nvidia-535-54-03/x8[15/41] Verifying flathub:app/com.github.micahflee.torbrowser-launcher/x86_64/st[23/41] Verifying flathub:runtime/org.freedesktop.Platform.GL.default/x86_64/22.[34/41] Verifying flathub:runtime/org.freedesktop.Platform.openh264/x86_64/2.2.0[38/41] Verifying flathub:runtime/org.telegram.desktop.webview.Locale/x86_64/sta[40/41] Verifying flathub:runtime/org.freedesktop.Platform.GL.default/x86_64/22.08-extra…
Checking remotes...
Pruning objects
Erasing .removed

``` 
by deleting the apps, Flatpak just became aware of all that garbage. 

Flatpak doesn't automatically remove a runtime after the last application that depended on it was uninstalled. This may be an issue for some users because these runtimes can take a lot of disk space.

Flatpak applications depend on runtimes, a set of essential libraries and services like Dbus, GLib, Gtk3, PulseAudio and so on. Thanks to these runtimes, application authors can bundle the libraries specific to the application without having to worry about low-level dependencies.

Each runtime is used by multiple applications, keeping the applications small in size, but there's one problem. After you uninstall all the application that depend on a particular runtime, the runtime itself is not removed. And that can be a problem because these runtimes can be very large - for example:


While Flatpak doesn't auto remove unused runtimes, there is a way to remove them, similar to apt autoremove or dnf / yum autoremove:
```

flatpak uninstall --unused
```

This command should list all unused Flatpak runtimes, and offer to uninstall them from your system.


There's no need to append --user to this command if you have installed Flatpak applications for your user only. The flatpak uninstall --unused command removes both system and user runtimes that are no longer needed.

And Next here is I learned that /run/user/1000/doc is the temporary directory for storing file used by running applications, and they still remain.

Just remove ~/.local/share/flatpak/db and restart. The system will recreate ~/.local/share/flatpak/db and start to populate /run/user/1000/doc/ on the go, again, as document portal demands go on....

---

### Post by Paddy Landau on 2023-07-16
> **1fallen said:**
> Paddy that's a big ask, but I can shed some light but not all. (Keep that in mind please)
@1fallen, that's brilliant, thank you! It explains a lot.

I followed your procedures, and it did indeed clean up everything. Quite a few unused flatpaks were uninstalled, and my [FONT=courier new]…/doc[/FONT] folder is clear. So nice :)

You twice specified the same command, [FONT=courier new]flatpak uninstall --unused[/FONT]. That was for the purposes of explanation, right?

Thank you again.

Now, to satisfy my curiosity, I want to find out how we get a folder in two places at the same time without mounts or symbolic links! And, how it's possible for a folder to be invalid.

---

### Post by Holger_Gehrke on 2023-07-16
Another way to remove the portal 'files' (actually it's a fuse (file system in user-space) that is used by both flatpak and snap to access files) is to call the method "Delete(id)" from the Interface "org.freedesktop.portal.Documents" on the name "org/freedesktop/portal/Documents" on the dbus. One can probably coble together a dbus-send invocation that does this, but I'm lazy and use 'd-feet' (a GUI for dbus). The "id" you have to pass as a parameter is not the actual filename but the 8-digit hexadecimal code that's used as a directory name. That allows you to be a bit more selective about removing these than just removing the database.

Holger

---

### Post by #&amp;thj^% on 2023-07-16
Just saw this
> **Holger_Gehrke said:**
> Another way to remove the portal 'files' (actually it's a fuse (file system in user-space) that is used by both flatpak and snap to access files) is to call the method "Delete(id)" from the Interface "org.freedesktop.portal.Documents" on the name "org/freedesktop/portal/Documents" on the dbus. One can probably coble together a dbus-send invocation that does this, but I'm lazy and use 'd-feet' (a GUI for dbus). The "id" you have to pass as a parameter is not the actual filename but the 8-digit hexadecimal code that's used as a directory name. That allows you to be a bit more selective about removing these than just removing the database.

Holger
+1 Great info Holger
> **Paddy Landau said:**
> 
You twice specified the same command, [FONT=courier new]flatpak uninstall --unused[/FONT]. That was for the purposes of explanation, right?

Thank you again.



Yes. explanation purposes only, is it overboard?
I can remove one of those in my first reply if it is confusing. (Or just Note that here)

---

### Post by Paddy Landau on 2023-07-16
> **Holger_Gehrke said:**
> … actually it's a fuse…
Thank you! I'll make a note of this.
> **1fallen said:**
> Yes. explanation purposes only, is it overboard?
No, not overboard. I was checking that you hadn't accidentally typed one thing and meant another (something that I do too often).

---

