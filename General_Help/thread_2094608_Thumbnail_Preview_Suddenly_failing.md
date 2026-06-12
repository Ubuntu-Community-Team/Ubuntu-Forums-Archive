---
title: "Thumbnail Preview Suddenly failing"
date: 2012-12-14
forum: General Help
---

### Post by Naeblis on 2012-12-14
Mu thumbnail previews were working fine a few days ago. But today when I logged in, I see that any .pdf, .png, or .jpg file thumbnail is not working properly.

I tried quite a few solutions, but none of them worked. These include: 

Deleting ```
.thumbnails/fail and .thumbnails/normal
```

Also tried this 
```
 sudo apt-get install libxine1-ffmpeg 
``` (This was already installed)

Log out/restarting after doing all of the above hasn't helped.

And a few other methods I found in threads referring to this site. 

Curiously, there are a few .png files in .thumbnails/normal now, just that they aren't being shown.

I'm using Ubuntu 11.04

Will appreciate any help I can get on this.

Thanks. :)

---

### Post by Naeblis on 2012-12-15
Bumping this. Would really appreciate any help guys. :)

---

### Post by Rexilion on 2012-12-15
Usually you get error and warning messages about this ~/.xsession-errors. Any clues in there?

---

### Post by Naeblis on 2012-12-16
There are LOTs of warnings about Audio control. Like this: 

```
** (gnome-settings-daemon:1896): WARNING **: Connection failed, reconnecting...

```


And after every few of them, there's this message, which I have no idea how to interpret.

```
** (gnome-settings-daemon:1896): WARNING **: Connection failed, reconnecting...

** (gnome-volume-control-applet:1916): WARNING **: Connection failed, reconnecting...
[2226:2226:1216/180818:ERROR:layout.cc(160)] Not implemented reached in ui::ScaleFactor ui::GetScaleFactorForNativeView(GtkWidget*)

** (gnome-volume-control-applet:1916): WARNING **: Connection failed, reconnecting...

** (gnome-settings-daemon:1896): WARNING **: Connection failed, reconnecting...
[2226:2226:1216/180824:ERROR:layout.cc(160)] Not implemented reached in ui::ScaleFactor ui::GetScaleFactorForNativeView(GtkWidget*)
```


Other than that, nothing. Grepping through the file about thumb, thumbnail etc didn't return anything either.

---

### Post by Rexilion on 2012-12-16
The thumbnailer communicates with gnome-settings-daemon for it's settings if I'm not mistaken.

Do you see any new errors appear if you:

- delete ~/.thumbnails
- open a directory containing images

?

---

### Post by Naeblis on 2012-12-17
These errors are logged when I `tail -f`ed the file, deleted .thumbnails, and browsed a directory with PDFs which should have thumbnails. 

```
(nautilus:1956): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1956): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1956): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1956): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1956): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1956): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

```

Along with a few gnome-settings-daemon errors as well.

---

### Post by Rexilion on 2012-12-18
[This link]("https://bugs.launchpad.net/ubuntu/+source/eog/+bug/754622") mentions the same error, yet no malfunctions.

Could you check if you have the same issue with a new and freshly created user?

---

### Post by Naeblis on 2012-12-20
Created a new user, and yes, the behavior persists. :(

---

### Post by Rexilion on 2012-12-20
Could you post the file '/var/log/dpkg.log' please?

---

### Post by Naeblis on 2012-12-22
Sorry for the delay. :)

Here's the file: 

```
2012-12-04 19:46:05 startup archives unpack
2012-12-04 19:46:12 install libbabl-0.0-0 0.0.22-1build1 0.0.22-1build1
2012-12-04 19:46:12 status half-installed libbabl-0.0-0 0.0.22-1build1
2012-12-04 19:46:12 status unpacked libbabl-0.0-0 0.0.22-1build1
2012-12-04 19:46:12 status unpacked libbabl-0.0-0 0.0.22-1build1
2012-12-04 19:46:13 startup packages configure
2012-12-04 19:46:13 configure libbabl-0.0-0 0.0.22-1build1 <none>
2012-12-04 19:46:13 status unpacked libbabl-0.0-0 0.0.22-1build1
2012-12-04 19:46:13 status half-configured libbabl-0.0-0 0.0.22-1build1
2012-12-04 19:46:13 status installed libbabl-0.0-0 0.0.22-1build1
2012-12-04 19:46:13 status triggers-pending libc-bin 2.13-0ubuntu13.2
2012-12-04 19:46:13 trigproc libc-bin 2.13-0ubuntu13.2 <none>
2012-12-04 19:46:13 status half-configured libc-bin 2.13-0ubuntu13.2
2012-12-04 19:46:15 status installed libc-bin 2.13-0ubuntu13.2
2012-12-04 23:04:49 startup packages remove
2012-12-04 23:04:49 status installed virtualbox-4.1 4.1.22-80657~Ubuntu~natty
2012-12-04 23:04:54 remove virtualbox-4.1 4.1.22-80657~Ubuntu~natty <none>
2012-12-04 23:04:54 status half-configured virtualbox-4.1 4.1.22-80657~Ubuntu~natty
2012-12-04 23:05:16 status half-installed virtualbox-4.1 4.1.22-80657~Ubuntu~natty
2012-12-04 23:05:16 status triggers-pending hicolor-icon-theme 0.12-1ubuntu1
2012-12-04 23:05:17 status half-installed virtualbox-4.1 4.1.22-80657~Ubuntu~natty
2012-12-04 23:05:17 status triggers-pending bamfdaemon 0.2.90-0ubuntu3
2012-12-04 23:05:17 status half-installed virtualbox-4.1 4.1.22-80657~Ubuntu~natty
2012-12-04 23:05:17 status triggers-pending desktop-file-utils 0.18-0ubuntu4
2012-12-04 23:05:17 status half-installed virtualbox-4.1 4.1.22-80657~Ubuntu~natty
2012-12-04 23:05:17 status triggers-pending python-gmenu 2.30.5-0ubuntu3
2012-12-04 23:05:17 status half-installed virtualbox-4.1 4.1.22-80657~Ubuntu~natty
2012-12-04 23:05:17 status triggers-pending shared-mime-info 0.90-1ubuntu3
2012-12-04 23:05:17 status half-installed virtualbox-4.1 4.1.22-80657~Ubuntu~natty
2012-12-04 23:05:18 status triggers-pending ureadahead 0.100.0-11
2012-12-04 23:05:18 status half-installed virtualbox-4.1 4.1.22-80657~Ubuntu~natty
2012-12-04 23:05:18 status config-files virtualbox-4.1 4.1.22-80657~Ubuntu~natty
2012-12-04 23:05:19 status config-files virtualbox-4.1 4.1.22-80657~Ubuntu~natty
2012-12-04 23:05:19 trigproc hicolor-icon-theme 0.12-1ubuntu1 <none>
2012-12-04 23:05:19 status half-configured hicolor-icon-theme 0.12-1ubuntu1
2012-12-04 23:05:25 status installed hicolor-icon-theme 0.12-1ubuntu1
2012-12-04 23:05:25 trigproc bamfdaemon 0.2.90-0ubuntu3 <none>
2012-12-04 23:05:25 status half-configured bamfdaemon 0.2.90-0ubuntu3
2012-12-04 23:05:25 status installed bamfdaemon 0.2.90-0ubuntu3
2012-12-04 23:05:26 trigproc desktop-file-utils 0.18-0ubuntu4 <none>
2012-12-04 23:05:26 status half-configured desktop-file-utils 0.18-0ubuntu4
2012-12-04 23:05:26 status installed desktop-file-utils 0.18-0ubuntu4
2012-12-04 23:05:26 trigproc python-gmenu 2.30.5-0ubuntu3 <none>
2012-12-04 23:05:26 status half-configured python-gmenu 2.30.5-0ubuntu3
2012-12-04 23:05:26 status installed python-gmenu 2.30.5-0ubuntu3
2012-12-04 23:05:27 status triggers-pending python-support 1.0.10ubuntu3
2012-12-04 23:05:27 trigproc shared-mime-info 0.90-1ubuntu3 <none>
2012-12-04 23:05:27 status half-configured shared-mime-info 0.90-1ubuntu3
2012-12-04 23:05:28 status installed shared-mime-info 0.90-1ubuntu3
2012-12-04 23:05:29 trigproc ureadahead 0.100.0-11 <none>
2012-12-04 23:05:29 status half-configured ureadahead 0.100.0-11
2012-12-04 23:05:29 status installed ureadahead 0.100.0-11
2012-12-04 23:05:29 trigproc python-support 1.0.10ubuntu3 <none>
2012-12-04 23:05:29 status half-configured python-support 1.0.10ubuntu3
2012-12-04 23:05:41 status installed python-support 1.0.10ubuntu3
2012-12-04 23:08:45 startup archives install
2012-12-04 23:08:46 install virtualbox-4.2 <none> 4.2.4-81684~Ubuntu~natty
2012-12-04 23:08:46 status half-installed virtualbox-4.2 4.2.4-81684~Ubuntu~natty
2012-12-04 23:08:49 status triggers-pending ureadahead 0.100.0-11
2012-12-04 23:08:49 status half-installed virtualbox-4.2 4.2.4-81684~Ubuntu~natty
2012-12-04 23:08:50 status triggers-pending shared-mime-info 0.90-1ubuntu3
2012-12-04 23:08:50 status half-installed virtualbox-4.2 4.2.4-81684~Ubuntu~natty
2012-12-04 23:08:50 status triggers-pending bamfdaemon 0.2.90-0ubuntu3
2012-12-04 23:08:50 status half-installed virtualbox-4.2 4.2.4-81684~Ubuntu~natty
2012-12-04 23:08:50 status triggers-pending desktop-file-utils 0.18-0ubuntu4
2012-12-04 23:08:50 status half-installed virtualbox-4.2 4.2.4-81684~Ubuntu~natty
2012-12-04 23:08:50 status triggers-pending python-gmenu 2.30.5-0ubuntu3
2012-12-04 23:08:50 status half-installed virtualbox-4.2 4.2.4-81684~Ubuntu~natty
2012-12-04 23:08:54 status triggers-pending hicolor-icon-theme 0.12-1ubuntu1
2012-12-04 23:08:55 status half-installed virtualbox-4.2 4.2.4-81684~Ubuntu~natty
2012-12-04 23:08:58 status unpacked virtualbox-4.2 4.2.4-81684~Ubuntu~natty
2012-12-04 23:08:58 status unpacked virtualbox-4.2 4.2.4-81684~Ubuntu~natty
2012-12-04 23:08:58 configure virtualbox-4.2 4.2.4-81684~Ubuntu~natty 4.2.4-81684~Ubuntu~natty
2012-12-04 23:08:58 status unpacked virtualbox-4.2 4.2.4-81684~Ubuntu~natty
2012-12-04 23:08:58 status unpacked virtualbox-4.2 4.2.4-81684~Ubuntu~natty
2012-12-04 23:08:58 status unpacked virtualbox-4.2 4.2.4-81684~Ubuntu~natty
2012-12-04 23:08:58 status unpacked virtualbox-4.2 4.2.4-81684~Ubuntu~natty
2012-12-04 23:08:58 status unpacked virtualbox-4.2 4.2.4-81684~Ubuntu~natty
2012-12-04 23:08:58 status half-configured virtualbox-4.2 4.2.4-81684~Ubuntu~natty
2012-12-04 23:09:48 status triggers-awaited virtualbox-4.2 4.2.4-81684~Ubuntu~natty
2012-12-04 23:09:48 status triggers-pending python-central 0.6.15ubuntu5
2012-12-04 23:09:49 status triggers-awaited virtualbox-4.2 4.2.4-81684~Ubuntu~natty
2012-12-04 23:09:49 trigproc ureadahead 0.100.0-11 0.100.0-11
2012-12-04 23:09:49 status half-configured ureadahead 0.100.0-11
2012-12-04 23:09:49 status installed ureadahead 0.100.0-11
2012-12-04 23:09:49 trigproc shared-mime-info 0.90-1ubuntu3 0.90-1ubuntu3
2012-12-04 23:09:49 status half-configured shared-mime-info 0.90-1ubuntu3
2012-12-04 23:09:50 status installed shared-mime-info 0.90-1ubuntu3
2012-12-04 23:09:51 trigproc bamfdaemon 0.2.90-0ubuntu3 0.2.90-0ubuntu3
2012-12-04 23:09:51 status half-configured bamfdaemon 0.2.90-0ubuntu3
2012-12-04 23:09:51 status installed bamfdaemon 0.2.90-0ubuntu3
2012-12-04 23:09:51 trigproc desktop-file-utils 0.18-0ubuntu4 0.18-0ubuntu4
2012-12-04 23:09:51 status half-configured desktop-file-utils 0.18-0ubuntu4
2012-12-04 23:09:51 status installed desktop-file-utils 0.18-0ubuntu4
2012-12-04 23:09:51 trigproc python-gmenu 2.30.5-0ubuntu3 2.30.5-0ubuntu3
2012-12-04 23:09:51 status half-configured python-gmenu 2.30.5-0ubuntu3
2012-12-04 23:09:52 status installed python-gmenu 2.30.5-0ubuntu3
2012-12-04 23:09:52 status triggers-pending python-support 1.0.10ubuntu3
2012-12-04 23:09:52 trigproc hicolor-icon-theme 0.12-1ubuntu1 0.12-1ubuntu1
2012-12-04 23:09:52 status half-configured hicolor-icon-theme 0.12-1ubuntu1
2012-12-04 23:09:52 status installed hicolor-icon-theme 0.12-1ubuntu1
2012-12-04 23:09:53 trigproc python-central 0.6.15ubuntu5 0.6.15ubuntu5
2012-12-04 23:09:53 status half-configured python-central 0.6.15ubuntu5
2012-12-04 23:09:53 status installed virtualbox-4.2 4.2.4-81684~Ubuntu~natty
2012-12-04 23:09:53 status installed python-central 0.6.15ubuntu5
2012-12-04 23:09:53 trigproc python-support 1.0.10ubuntu3 1.0.10ubuntu3
2012-12-04 23:09:53 status half-configured python-support 1.0.10ubuntu3
2012-12-04 23:09:55 status installed python-support 1.0.10ubuntu3
2012-12-06 16:43:53 startup archives unpack
2012-12-06 16:43:59 install w3m <none> 0.5.3-1
2012-12-06 16:43:59 status half-installed w3m 0.5.3-1
2012-12-06 16:43:59 status triggers-pending man-db 2.5.9-4
2012-12-06 16:44:00 status half-installed w3m 0.5.3-1
2012-12-06 16:44:00 status unpacked w3m 0.5.3-1
2012-12-06 16:44:00 status unpacked w3m 0.5.3-1
2012-12-06 16:44:00 trigproc man-db 2.5.9-4 2.5.9-4
2012-12-06 16:44:00 status half-configured man-db 2.5.9-4
2012-12-06 16:44:02 status installed man-db 2.5.9-4
2012-12-06 16:44:03 startup packages configure
2012-12-06 16:44:03 configure w3m 0.5.3-1 <none>
2012-12-06 16:44:03 status unpacked w3m 0.5.3-1
2012-12-06 16:44:04 status unpacked w3m 0.5.3-1
2012-12-06 16:44:04 status unpacked w3m 0.5.3-1
2012-12-06 16:44:04 status half-configured w3m 0.5.3-1
2012-12-06 16:44:05 status installed w3m 0.5.3-1
2012-12-11 22:40:01 startup archives unpack
2012-12-11 22:40:08 install libdb5.1 <none> 5.1.19-2ubuntu1
2012-12-11 22:40:08 status half-installed libdb5.1 5.1.19-2ubuntu1
2012-12-11 22:40:08 status unpacked libdb5.1 5.1.19-2ubuntu1
2012-12-11 22:40:09 status unpacked libdb5.1 5.1.19-2ubuntu1
2012-12-11 22:40:09 install python3.2-minimal <none> 3.2-1ubuntu1.2
2012-12-11 22:40:09 status half-installed python3.2-minimal 3.2-1ubuntu1.2
2012-12-11 22:40:09 status triggers-pending man-db 2.5.9-4
2012-12-11 22:40:10 status half-installed python3.2-minimal 3.2-1ubuntu1.2
2012-12-11 22:40:10 status unpacked python3.2-minimal 3.2-1ubuntu1.2
2012-12-11 22:40:10 status unpacked python3.2-minimal 3.2-1ubuntu1.2
2012-12-11 22:40:11 install python3.2 <none> 3.2-1ubuntu1.2
2012-12-11 22:40:11 status half-installed python3.2 3.2-1ubuntu1.2
2012-12-11 22:40:11 status half-installed python3.2 3.2-1ubuntu1.2
2012-12-11 22:40:12 status triggers-pending bamfdaemon 0.2.90-0ubuntu3
2012-12-11 22:40:12 status half-installed python3.2 3.2-1ubuntu1.2
2012-12-11 22:40:12 status triggers-pending desktop-file-utils 0.18-0ubuntu4
2012-12-11 22:40:12 status half-installed python3.2 3.2-1ubuntu1.2
2012-12-11 22:40:12 status triggers-pending python-gmenu 2.30.5-0ubuntu3
2012-12-11 22:40:12 status half-installed python3.2 3.2-1ubuntu1.2
2012-12-11 22:40:13 status unpacked python3.2 3.2-1ubuntu1.2
2012-12-11 22:40:13 status unpacked python3.2 3.2-1ubuntu1.2
2012-12-11 22:40:13 install python3-minimal <none> 3.2-1ubuntu1
2012-12-11 22:40:13 status half-installed python3-minimal 3.2-1ubuntu1
2012-12-11 22:40:13 status half-installed python3-minimal 3.2-1ubuntu1
2012-12-11 22:40:14 status unpacked python3-minimal 3.2-1ubuntu1
2012-12-11 22:40:14 status unpacked python3-minimal 3.2-1ubuntu1
2012-12-11 22:40:15 install python3 <none> 3.2-1ubuntu1
2012-12-11 22:40:15 status half-installed python3 3.2-1ubuntu1
2012-12-11 22:40:16 status half-installed python3 3.2-1ubuntu1
2012-12-11 22:40:17 status unpacked python3 3.2-1ubuntu1
2012-12-11 22:40:17 status unpacked python3 3.2-1ubuntu1
2012-12-11 22:40:17 trigproc man-db 2.5.9-4 2.5.9-4
2012-12-11 22:40:17 status half-configured man-db 2.5.9-4
2012-12-11 22:40:20 status installed man-db 2.5.9-4
2012-12-11 22:40:20 trigproc bamfdaemon 0.2.90-0ubuntu3 0.2.90-0ubuntu3
2012-12-11 22:40:20 status half-configured bamfdaemon 0.2.90-0ubuntu3
2012-12-11 22:40:21 status installed bamfdaemon 0.2.90-0ubuntu3
2012-12-11 22:40:21 trigproc desktop-file-utils 0.18-0ubuntu4 0.18-0ubuntu4
2012-12-11 22:40:21 status half-configured desktop-file-utils 0.18-0ubuntu4
2012-12-11 22:40:21 status installed desktop-file-utils 0.18-0ubuntu4
2012-12-11 22:40:21 trigproc python-gmenu 2.30.5-0ubuntu3 2.30.5-0ubuntu3
2012-12-11 22:40:21 status half-configured python-gmenu 2.30.5-0ubuntu3
2012-12-11 22:40:23 status installed python-gmenu 2.30.5-0ubuntu3
2012-12-11 22:40:23 status triggers-pending python-support 1.0.10ubuntu3
2012-12-11 22:40:23 trigproc python-support 1.0.10ubuntu3 1.0.10ubuntu3
2012-12-11 22:40:23 status half-configured python-support 1.0.10ubuntu3
2012-12-11 22:40:38 status installed python-support 1.0.10ubuntu3
2012-12-11 22:40:39 startup packages configure
2012-12-11 22:40:39 configure libdb5.1 5.1.19-2ubuntu1 <none>
2012-12-11 22:40:39 status unpacked libdb5.1 5.1.19-2ubuntu1
2012-12-11 22:40:39 status half-configured libdb5.1 5.1.19-2ubuntu1
2012-12-11 22:40:39 status installed libdb5.1 5.1.19-2ubuntu1
2012-12-11 22:40:39 status triggers-pending libc-bin 2.13-0ubuntu13.2
2012-12-11 22:40:39 configure python3.2-minimal 3.2-1ubuntu1.2 <none>
2012-12-11 22:40:39 status unpacked python3.2-minimal 3.2-1ubuntu1.2
2012-12-11 22:40:40 status unpacked python3.2-minimal 3.2-1ubuntu1.2
2012-12-11 22:40:40 status half-configured python3.2-minimal 3.2-1ubuntu1.2
2012-12-11 22:40:41 status installed python3.2-minimal 3.2-1ubuntu1.2
2012-12-11 22:40:41 configure python3.2 3.2-1ubuntu1.2 <none>
2012-12-11 22:40:41 status unpacked python3.2 3.2-1ubuntu1.2
2012-12-11 22:40:41 status half-configured python3.2 3.2-1ubuntu1.2
2012-12-11 22:40:42 status installed python3.2 3.2-1ubuntu1.2
2012-12-11 22:40:42 configure python3-minimal 3.2-1ubuntu1 <none>
2012-12-11 22:40:42 status unpacked python3-minimal 3.2-1ubuntu1
2012-12-11 22:40:42 status half-configured python3-minimal 3.2-1ubuntu1
2012-12-11 22:40:42 status installed python3-minimal 3.2-1ubuntu1
2012-12-11 22:40:42 configure python3 3.2-1ubuntu1 <none>
2012-12-11 22:40:42 status unpacked python3 3.2-1ubuntu1
2012-12-11 22:40:42 status half-configured python3 3.2-1ubuntu1
2012-12-11 22:40:43 status installed python3 3.2-1ubuntu1
2012-12-11 22:40:43 trigproc libc-bin 2.13-0ubuntu13.2 <none>
2012-12-11 22:40:43 status half-configured libc-bin 2.13-0ubuntu13.2
2012-12-11 22:40:45 status installed libc-bin 2.13-0ubuntu13.2
2012-12-13 11:31:15 startup archives unpack
2012-12-13 11:31:16 install pbuilder <none> 0.199+nmu1ubuntu1.1
2012-12-13 11:31:16 status half-installed pbuilder 0.199+nmu1ubuntu1.1
2012-12-13 11:31:16 status triggers-pending doc-base 0.9.5ubuntu2
2012-12-13 11:31:16 status half-installed pbuilder 0.199+nmu1ubuntu1.1
2012-12-13 11:31:16 status triggers-pending man-db 2.5.9-4
2012-12-13 11:31:17 status half-installed pbuilder 0.199+nmu1ubuntu1.1
2012-12-13 11:31:17 status unpacked pbuilder 0.199+nmu1ubuntu1.1
2012-12-13 11:31:17 status unpacked pbuilder 0.199+nmu1ubuntu1.1
2012-12-13 11:31:17 trigproc doc-base 0.9.5ubuntu2 0.9.5ubuntu2
2012-12-13 11:31:17 status half-configured doc-base 0.9.5ubuntu2
2012-12-13 11:31:18 status installed doc-base 0.9.5ubuntu2
2012-12-13 11:31:18 trigproc man-db 2.5.9-4 2.5.9-4
2012-12-13 11:31:18 status half-configured man-db 2.5.9-4
2012-12-13 11:31:19 status installed man-db 2.5.9-4
2012-12-13 11:31:20 startup packages configure
2012-12-13 11:31:20 configure pbuilder 0.199+nmu1ubuntu1.1 <none>
2012-12-13 11:31:20 status unpacked pbuilder 0.199+nmu1ubuntu1.1
2012-12-13 11:31:20 status unpacked pbuilder 0.199+nmu1ubuntu1.1
2012-12-13 11:31:20 status unpacked pbuilder 0.199+nmu1ubuntu1.1
2012-12-13 11:31:21 status half-configured pbuilder 0.199+nmu1ubuntu1.1
2012-12-13 11:31:21 status installed pbuilder 0.199+nmu1ubuntu1.1
2012-12-14 17:02:27 startup packages remove
2012-12-14 17:02:27 status installed libavutil50 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:27 status installed libavutil50 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:27 status installed libavutil50 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:27 status installed libavutil50 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:27 status installed libavutil50 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:28 status installed libavutil50 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:28 status installed libavutil50 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:28 status installed libavutil50 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:28 status installed libavutil50 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:28 status installed libavutil50 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:28 status installed libavutil50 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:28 status installed libavutil50 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:28 status installed libavutil50 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:28 status installed libavutil50 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:29 status installed libavutil50 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:29 status installed libavutil50 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:35 remove libavutil50 4:0.6.6-0ubuntu0.11.04.1 <none>
2012-12-14 17:02:35 status half-configured libavutil50 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:35 status half-installed libavutil50 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:36 status triggers-pending libc-bin 2.13-0ubuntu13.2
2012-12-14 17:02:36 status config-files libavutil50 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:36 status config-files libavutil50 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:36 trigproc libc-bin 2.13-0ubuntu13.2 <none>
2012-12-14 17:02:36 status half-configured libc-bin 2.13-0ubuntu13.2
2012-12-14 17:02:37 status installed libc-bin 2.13-0ubuntu13.2
2012-12-14 17:02:38 startup archives unpack
2012-12-14 17:02:38 install libavutil-extra-50 <none> 4:0.6.6-1ubuntu1
2012-12-14 17:02:38 status half-installed libavutil-extra-50 4:0.6.6-1ubuntu1
2012-12-14 17:02:39 status unpacked libavutil-extra-50 4:0.6.6-1ubuntu1
2012-12-14 17:02:39 status unpacked libavutil-extra-50 4:0.6.6-1ubuntu1
2012-12-14 17:02:40 startup packages configure
2012-12-14 17:02:40 configure libavutil-extra-50 4:0.6.6-1ubuntu1 <none>
2012-12-14 17:02:40 status unpacked libavutil-extra-50 4:0.6.6-1ubuntu1
2012-12-14 17:02:41 status half-configured libavutil-extra-50 4:0.6.6-1ubuntu1
2012-12-14 17:02:42 status installed libavutil-extra-50 4:0.6.6-1ubuntu1
2012-12-14 17:02:42 status triggers-pending libc-bin 2.13-0ubuntu13.2
2012-12-14 17:02:42 trigproc libc-bin 2.13-0ubuntu13.2 <none>
2012-12-14 17:02:42 status half-configured libc-bin 2.13-0ubuntu13.2
2012-12-14 17:02:42 status installed libc-bin 2.13-0ubuntu13.2
2012-12-14 17:02:43 startup archives unpack
2012-12-14 17:02:44 install libopenjpeg2 <none> 1.3+dfsg-4
2012-12-14 17:02:44 status half-installed libopenjpeg2 1.3+dfsg-4
2012-12-14 17:02:44 status unpacked libopenjpeg2 1.3+dfsg-4
2012-12-14 17:02:44 status unpacked libopenjpeg2 1.3+dfsg-4
2012-12-14 17:02:45 startup packages remove
2012-12-14 17:02:45 status installed libavcodec52 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:45 status installed libavcodec52 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:45 status installed libavcodec52 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:45 status installed libavcodec52 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:46 status installed libavcodec52 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:46 status installed libavcodec52 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:46 status installed libavcodec52 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:46 status installed libavcodec52 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:46 status installed libavcodec52 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:46 status installed libavcodec52 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:46 status installed libavcodec52 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:46 status installed libavcodec52 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:46 status installed libavcodec52 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:46 status installed libavcodec52 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:46 status installed libavcodec52 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:47 status installed libavcodec52 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:47 remove libavcodec52 4:0.6.6-0ubuntu0.11.04.1 <none>
2012-12-14 17:02:47 status half-configured libavcodec52 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:47 status half-installed libavcodec52 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:47 status triggers-pending libc-bin 2.13-0ubuntu13.2
2012-12-14 17:02:48 status config-files libavcodec52 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:48 status config-files libavcodec52 4:0.6.6-0ubuntu0.11.04.1
2012-12-14 17:02:48 trigproc libc-bin 2.13-0ubuntu13.2 <none>
2012-12-14 17:02:48 status half-configured libc-bin 2.13-0ubuntu13.2
2012-12-14 17:02:48 status installed libc-bin 2.13-0ubuntu13.2
2012-12-14 17:02:49 startup archives unpack
2012-12-14 17:02:49 install libavcodec-extra-52 <none> 4:0.6.6-1ubuntu1
2012-12-14 17:02:49 status half-installed libavcodec-extra-52 4:0.6.6-1ubuntu1
2012-12-14 17:02:50 status unpacked libavcodec-extra-52 4:0.6.6-1ubuntu1
2012-12-14 17:02:50 status unpacked libavcodec-extra-52 4:0.6.6-1ubuntu1
2012-12-14 17:02:51 startup packages configure
2012-12-14 17:02:51 configure libopenjpeg2 1.3+dfsg-4 <none>
2012-12-14 17:02:51 status unpacked libopenjpeg2 1.3+dfsg-4
2012-12-14 17:02:51 status half-configured libopenjpeg2 1.3+dfsg-4
2012-12-14 17:02:51 status installed libopenjpeg2 1.3+dfsg-4
2012-12-14 17:02:51 status triggers-pending libc-bin 2.13-0ubuntu13.2
2012-12-14 17:02:51 configure libavcodec-extra-52 4:0.6.6-1ubuntu1 <none>
2012-12-14 17:02:51 status unpacked libavcodec-extra-52 4:0.6.6-1ubuntu1
2012-12-14 17:02:51 status half-configured libavcodec-extra-52 4:0.6.6-1ubuntu1
2012-12-14 17:02:52 status installed libavcodec-extra-52 4:0.6.6-1ubuntu1
2012-12-14 17:02:52 trigproc libc-bin 2.13-0ubuntu13.2 <none>
2012-12-14 17:02:52 status half-configured libc-bin 2.13-0ubuntu13.2
2012-12-14 17:02:52 status installed libc-bin 2.13-0ubuntu13.2
2012-12-14 17:02:53 startup archives unpack
2012-12-14 17:02:53 install cabextract <none> 1.3-1
2012-12-14 17:02:53 status half-installed cabextract 1.3-1
2012-12-14 17:02:54 status triggers-pending man-db 2.5.9-4
2012-12-14 17:02:54 status half-installed cabextract 1.3-1
2012-12-14 17:02:54 status unpacked cabextract 1.3-1
2012-12-14 17:02:54 status unpacked cabextract 1.3-1
2012-12-14 17:02:54 install libfaac0 <none> 1.26-0.1ubuntu2
2012-12-14 17:02:54 status half-installed libfaac0 1.26-0.1ubuntu2
2012-12-14 17:02:55 status unpacked libfaac0 1.26-0.1ubuntu2
2012-12-14 17:02:55 status unpacked libfaac0 1.26-0.1ubuntu2
2012-12-14 17:02:55 install libquicktime1 <none> 2:1.1.5-1ubuntu3
2012-12-14 17:02:55 status half-installed libquicktime1 2:1.1.5-1ubuntu3
2012-12-14 17:02:56 status unpacked libquicktime1 2:1.1.5-1ubuntu3
2012-12-14 17:02:56 status unpacked libquicktime1 2:1.1.5-1ubuntu3
2012-12-14 17:02:56 install libmjpegtools-1.9 <none> 1:1.9.0-0.5ubuntu4
2012-12-14 17:02:56 status half-installed libmjpegtools-1.9 1:1.9.0-0.5ubuntu4
2012-12-14 17:02:57 status unpacked libmjpegtools-1.9 1:1.9.0-0.5ubuntu4
2012-12-14 17:02:57 status unpacked libmjpegtools-1.9 1:1.9.0-0.5ubuntu4
2012-12-14 17:02:57 install gstreamer0.10-plugins-bad-multiverse <none> 0.10.21-1
2012-12-14 17:02:57 status half-installed gstreamer0.10-plugins-bad-multiverse 0.10.21-1
2012-12-14 17:02:57 status unpacked gstreamer0.10-plugins-bad-multiverse 0.10.21-1
2012-12-14 17:02:57 status unpacked gstreamer0.10-plugins-bad-multiverse 0.10.21-1
2012-12-14 17:02:58 install gstreamer0.10-plugins-ugly-multiverse <none> 0.10.17-1
2012-12-14 17:02:58 status half-installed gstreamer0.10-plugins-ugly-multiverse 0.10.17-1
2012-12-14 17:02:58 status unpacked gstreamer0.10-plugins-ugly-multiverse 0.10.17-1
2012-12-14 17:02:58 status unpacked gstreamer0.10-plugins-ugly-multiverse 0.10.17-1
2012-12-14 17:02:58 install libmp4v2-0 <none> 1:1.6dfsg-0.2ubuntu9
2012-12-14 17:02:58 status half-installed libmp4v2-0 1:1.6dfsg-0.2ubuntu9
2012-12-14 17:02:59 status unpacked libmp4v2-0 1:1.6dfsg-0.2ubuntu9
2012-12-14 17:02:59 status unpacked libmp4v2-0 1:1.6dfsg-0.2ubuntu9
2012-12-14 17:02:59 install ttf-mscorefonts-installer <none> 3.3ubuntu3
2012-12-14 17:02:59 status half-installed ttf-mscorefonts-installer 3.3ubuntu3
2012-12-14 17:03:09 status triggers-pending fontconfig 2.8.0-2.1ubuntu3
2012-12-14 17:03:09 status half-installed ttf-mscorefonts-installer 3.3ubuntu3
2012-12-14 17:03:10 status unpacked ttf-mscorefonts-installer 3.3ubuntu3
2012-12-14 17:03:10 status unpacked ttf-mscorefonts-installer 3.3ubuntu3
2012-12-14 17:03:10 install ubuntu-restricted-addons <none> 7
2012-12-14 17:03:10 status half-installed ubuntu-restricted-addons 7
2012-12-14 17:03:10 status unpacked ubuntu-restricted-addons 7
2012-12-14 17:03:10 status unpacked ubuntu-restricted-addons 7
2012-12-14 17:03:11 install ubuntu-restricted-extras <none> 43
2012-12-14 17:03:11 status half-installed ubuntu-restricted-extras 43
2012-12-14 17:03:11 status unpacked ubuntu-restricted-extras 43
2012-12-14 17:03:11 status unpacked ubuntu-restricted-extras 43
2012-12-14 17:03:12 install icedtea-6-plugin <none> 1.2-2ubuntu0.11.04.3
2012-12-14 17:03:12 status half-installed icedtea-6-plugin 1.2-2ubuntu0.11.04.3
2012-12-14 17:03:12 status unpacked icedtea-6-plugin 1.2-2ubuntu0.11.04.3
2012-12-14 17:03:12 status unpacked icedtea-6-plugin 1.2-2ubuntu0.11.04.3
2012-12-14 17:03:12 install icedtea6-plugin <none> 6b21.2-2ubuntu0.11.04.3
2012-12-14 17:03:12 status half-installed icedtea6-plugin 6b21.2-2ubuntu0.11.04.3
2012-12-14 17:03:13 status unpacked icedtea6-plugin 6b21.2-2ubuntu0.11.04.3
2012-12-14 17:03:13 status unpacked icedtea6-plugin 6b21.2-2ubuntu0.11.04.3
2012-12-14 17:03:13 trigproc man-db 2.5.9-4 2.5.9-4
2012-12-14 17:03:13 status half-configured man-db 2.5.9-4
2012-12-14 17:03:14 status installed man-db 2.5.9-4
2012-12-14 17:03:14 trigproc fontconfig 2.8.0-2.1ubuntu3 2.8.0-2.1ubuntu3
2012-12-14 17:03:14 status half-configured fontconfig 2.8.0-2.1ubuntu3
2012-12-14 17:03:16 status installed fontconfig 2.8.0-2.1ubuntu3
2012-12-14 17:03:17 startup packages configure
2012-12-14 17:03:17 configure cabextract 1.3-1 <none>
2012-12-14 17:03:17 status unpacked cabextract 1.3-1
2012-12-14 17:03:18 status half-configured cabextract 1.3-1
2012-12-14 17:03:18 status installed cabextract 1.3-1
2012-12-14 17:03:18 configure libfaac0 1.26-0.1ubuntu2 <none>
2012-12-14 17:03:18 status unpacked libfaac0 1.26-0.1ubuntu2
2012-12-14 17:03:18 status half-configured libfaac0 1.26-0.1ubuntu2
2012-12-14 17:03:18 status installed libfaac0 1.26-0.1ubuntu2
2012-12-14 17:03:18 status triggers-pending libc-bin 2.13-0ubuntu13.2
2012-12-14 17:03:18 configure libquicktime1 2:1.1.5-1ubuntu3 <none>
2012-12-14 17:03:18 status unpacked libquicktime1 2:1.1.5-1ubuntu3
2012-12-14 17:03:18 status half-configured libquicktime1 2:1.1.5-1ubuntu3
2012-12-14 17:03:18 status installed libquicktime1 2:1.1.5-1ubuntu3
2012-12-14 17:03:18 configure libmjpegtools-1.9 1:1.9.0-0.5ubuntu4 <none>
2012-12-14 17:03:18 status unpacked libmjpegtools-1.9 1:1.9.0-0.5ubuntu4
2012-12-14 17:03:19 status half-configured libmjpegtools-1.9 1:1.9.0-0.5ubuntu4
2012-12-14 17:03:19 status installed libmjpegtools-1.9 1:1.9.0-0.5ubuntu4
2012-12-14 17:03:19 configure gstreamer0.10-plugins-bad-multiverse 0.10.21-1 <none>
2012-12-14 17:03:19 status unpacked gstreamer0.10-plugins-bad-multiverse 0.10.21-1
2012-12-14 17:03:19 status half-configured gstreamer0.10-plugins-bad-multiverse 0.10.21-1
2012-12-14 17:03:19 status installed gstreamer0.10-plugins-bad-multiverse 0.10.21-1
2012-12-14 17:03:19 configure gstreamer0.10-plugins-ugly-multiverse 0.10.17-1 <none>
2012-12-14 17:03:19 status unpacked gstreamer0.10-plugins-ugly-multiverse 0.10.17-1
2012-12-14 17:03:19 status half-configured gstreamer0.10-plugins-ugly-multiverse 0.10.17-1
2012-12-14 17:03:19 status installed gstreamer0.10-plugins-ugly-multiverse 0.10.17-1
2012-12-14 17:03:19 configure libmp4v2-0 1:1.6dfsg-0.2ubuntu9 <none>
2012-12-14 17:03:19 status unpacked libmp4v2-0 1:1.6dfsg-0.2ubuntu9
2012-12-14 17:03:20 status half-configured libmp4v2-0 1:1.6dfsg-0.2ubuntu9
2012-12-14 17:03:20 status installed libmp4v2-0 1:1.6dfsg-0.2ubuntu9
2012-12-14 17:03:20 configure ttf-mscorefonts-installer 3.3ubuntu3 <none>
2012-12-14 17:03:20 status unpacked ttf-mscorefonts-installer 3.3ubuntu3
2012-12-14 17:03:20 status unpacked ttf-mscorefonts-installer 3.3ubuntu3
2012-12-14 17:03:20 status half-configured ttf-mscorefonts-installer 3.3ubuntu3
2012-12-14 17:06:56 status installed ttf-mscorefonts-installer 3.3ubuntu3
2012-12-14 17:06:56 configure ubuntu-restricted-addons 7 <none>
2012-12-14 17:06:56 status unpacked ubuntu-restricted-addons 7
2012-12-14 17:06:56 status half-configured ubuntu-restricted-addons 7
2012-12-14 17:06:56 status installed ubuntu-restricted-addons 7
2012-12-14 17:06:56 configure ubuntu-restricted-extras 43 <none>
2012-12-14 17:06:56 status unpacked ubuntu-restricted-extras 43
2012-12-14 17:06:57 status half-configured ubuntu-restricted-extras 43
2012-12-14 17:06:57 status installed ubuntu-restricted-extras 43
2012-12-14 17:06:57 configure icedtea-6-plugin 1.2-2ubuntu0.11.04.3 <none>
2012-12-14 17:06:57 status unpacked icedtea-6-plugin 1.2-2ubuntu0.11.04.3
2012-12-14 17:06:57 status half-configured icedtea-6-plugin 1.2-2ubuntu0.11.04.3
2012-12-14 17:06:58 status installed icedtea-6-plugin 1.2-2ubuntu0.11.04.3
2012-12-14 17:06:58 configure icedtea6-plugin 6b21.2-2ubuntu0.11.04.3 <none>
2012-12-14 17:06:58 status unpacked icedtea6-plugin 6b21.2-2ubuntu0.11.04.3
2012-12-14 17:06:58 status half-configured icedtea6-plugin 6b21.2-2ubuntu0.11.04.3
2012-12-14 17:06:58 status installed icedtea6-plugin 6b21.2-2ubuntu0.11.04.3
2012-12-14 17:06:58 trigproc libc-bin 2.13-0ubuntu13.2 <none>
2012-12-14 17:06:58 status half-configured libc-bin 2.13-0ubuntu13.2
2012-12-14 17:06:58 status installed libc-bin 2.13-0ubuntu13.2
2012-12-14 17:07:28 startup packages remove
2012-12-14 17:07:28 status installed ubuntu-restricted-extras 43
2012-12-14 17:07:29 remove ubuntu-restricted-extras 43 <none>
2012-12-14 17:07:29 status half-configured ubuntu-restricted-extras 43
2012-12-14 17:07:29 status half-installed ubuntu-restricted-extras 43
2012-12-14 17:07:29 status config-files ubuntu-restricted-extras 43
2012-12-14 17:07:29 status config-files ubuntu-restricted-extras 43
2012-12-14 17:07:29 status config-files ubuntu-restricted-extras 43
2012-12-14 17:07:29 status not-installed ubuntu-restricted-extras <none>
2012-12-14 18:18:38 startup archives unpack
2012-12-14 18:18:38 install ri1.9.1 <none> 1.9.2.0-2
2012-12-14 18:18:38 status half-installed ri1.9.1 1.9.2.0-2
2012-12-14 18:18:38 status triggers-pending man-db 2.5.9-4
2012-12-14 18:18:38 status half-installed ri1.9.1 1.9.2.0-2
2012-12-14 18:18:47 status unpacked ri1.9.1 1.9.2.0-2
2012-12-14 18:18:47 status unpacked ri1.9.1 1.9.2.0-2
2012-12-14 18:18:47 trigproc man-db 2.5.9-4 2.5.9-4
2012-12-14 18:18:47 status half-configured man-db 2.5.9-4
2012-12-14 18:18:48 status installed man-db 2.5.9-4
2012-12-14 18:18:49 startup packages configure
2012-12-14 18:18:49 configure ri1.9.1 1.9.2.0-2 <none>
2012-12-14 18:18:49 status unpacked ri1.9.1 1.9.2.0-2
2012-12-14 18:18:49 status half-configured ri1.9.1 1.9.2.0-2
2012-12-14 18:18:49 status installed ri1.9.1 1.9.2.0-2
2012-12-19 02:31:44 startup archives unpack
2012-12-19 02:31:51 upgrade google-chrome-stable 23.0.1271.64-r165188 23.0.1271.97-r171054
2012-12-19 02:31:51 status half-configured google-chrome-stable 23.0.1271.64-r165188
2012-12-19 02:31:52 status unpacked google-chrome-stable 23.0.1271.64-r165188
2012-12-19 02:31:52 status half-installed google-chrome-stable 23.0.1271.64-r165188
2012-12-19 02:31:52 status triggers-pending man-db 2.5.9-4
2012-12-19 02:31:52 status half-installed google-chrome-stable 23.0.1271.64-r165188
2012-12-19 02:31:52 status triggers-pending bamfdaemon 0.2.90-0ubuntu3
2012-12-19 02:31:53 status half-installed google-chrome-stable 23.0.1271.64-r165188
2012-12-19 02:31:53 status triggers-pending desktop-file-utils 0.18-0ubuntu4
2012-12-19 02:31:53 status half-installed google-chrome-stable 23.0.1271.64-r165188
2012-12-19 02:31:53 status triggers-pending python-gmenu 2.30.5-0ubuntu3
2012-12-19 02:31:53 status half-installed google-chrome-stable 23.0.1271.64-r165188
2012-12-19 02:32:00 status half-installed google-chrome-stable 23.0.1271.64-r165188
2012-12-19 02:32:00 status unpacked google-chrome-stable 23.0.1271.97-r171054
2012-12-19 02:32:00 status unpacked google-chrome-stable 23.0.1271.97-r171054
2012-12-19 02:32:00 upgrade heroku-toolbelt 2.33.0 2.33.5
2012-12-19 02:32:00 status half-configured heroku-toolbelt 2.33.0
2012-12-19 02:32:00 status unpacked heroku-toolbelt 2.33.0
2012-12-19 02:32:00 status half-installed heroku-toolbelt 2.33.0
2012-12-19 02:32:01 status half-installed heroku-toolbelt 2.33.0
2012-12-19 02:32:01 status unpacked heroku-toolbelt 2.33.5
2012-12-19 02:32:01 status unpacked heroku-toolbelt 2.33.5
2012-12-19 02:32:01 upgrade heroku 2.33.0 2.33.5
2012-12-19 02:32:01 status half-configured heroku 2.33.0
2012-12-19 02:32:01 status unpacked heroku 2.33.0
2012-12-19 02:32:01 status half-installed heroku 2.33.0
2012-12-19 02:32:02 status half-installed heroku 2.33.0
2012-12-19 02:32:04 status unpacked heroku 2.33.5
2012-12-19 02:32:04 status unpacked heroku 2.33.5
2012-12-19 02:32:05 upgrade google-talkplugin 3.9.1.0-1 3.10.2.0-1
2012-12-19 02:32:05 status half-configured google-talkplugin 3.9.1.0-1
2012-12-19 02:32:05 status unpacked google-talkplugin 3.9.1.0-1
2012-12-19 02:32:05 status half-installed google-talkplugin 3.9.1.0-1
2012-12-19 02:32:07 status half-installed google-talkplugin 3.9.1.0-1
2012-12-19 02:32:07 status unpacked google-talkplugin 3.10.2.0-1
2012-12-19 02:32:07 status unpacked google-talkplugin 3.10.2.0-1
2012-12-19 02:32:08 upgrade postgresql-9.1 9.1.6-1~natty1 9.1.7-0ppa1~natty.1
2012-12-19 02:32:08 status half-configured postgresql-9.1 9.1.6-1~natty1
2012-12-19 02:32:10 status unpacked postgresql-9.1 9.1.6-1~natty1
2012-12-19 02:32:10 status half-installed postgresql-9.1 9.1.6-1~natty1
2012-12-19 02:32:12 status half-installed postgresql-9.1 9.1.6-1~natty1
2012-12-19 02:32:12 status unpacked postgresql-9.1 9.1.7-0ppa1~natty.1
2012-12-19 02:32:12 status unpacked postgresql-9.1 9.1.7-0ppa1~natty.1
2012-12-19 02:32:12 upgrade postgresql-client-9.1 9.1.6-1~natty1 9.1.7-0ppa1~natty.1
2012-12-19 02:32:12 status half-configured postgresql-client-9.1 9.1.6-1~natty1
2012-12-19 02:32:12 status unpacked postgresql-client-9.1 9.1.6-1~natty1
2012-12-19 02:32:13 status half-installed postgresql-client-9.1 9.1.6-1~natty1
2012-12-19 02:32:14 status half-installed postgresql-client-9.1 9.1.6-1~natty1
2012-12-19 02:32:14 status unpacked postgresql-client-9.1 9.1.7-0ppa1~natty.1
2012-12-19 02:32:14 status unpacked postgresql-client-9.1 9.1.7-0ppa1~natty.1
2012-12-19 02:32:14 trigproc man-db 2.5.9-4 2.5.9-4
2012-12-19 02:32:14 status half-configured man-db 2.5.9-4
2012-12-19 02:32:17 status installed man-db 2.5.9-4
2012-12-19 02:32:17 trigproc bamfdaemon 0.2.90-0ubuntu3 0.2.90-0ubuntu3
2012-12-19 02:32:17 status half-configured bamfdaemon 0.2.90-0ubuntu3
2012-12-19 02:32:17 status installed bamfdaemon 0.2.90-0ubuntu3
2012-12-19 02:32:17 trigproc desktop-file-utils 0.18-0ubuntu4 0.18-0ubuntu4
2012-12-19 02:32:17 status half-configured desktop-file-utils 0.18-0ubuntu4
2012-12-19 02:32:17 status installed desktop-file-utils 0.18-0ubuntu4
2012-12-19 02:32:17 trigproc python-gmenu 2.30.5-0ubuntu3 2.30.5-0ubuntu3
2012-12-19 02:32:17 status half-configured python-gmenu 2.30.5-0ubuntu3
2012-12-19 02:32:18 status installed python-gmenu 2.30.5-0ubuntu3
2012-12-19 02:32:18 status triggers-pending python-support 1.0.10ubuntu3
2012-12-19 02:32:18 trigproc python-support 1.0.10ubuntu3 1.0.10ubuntu3
2012-12-19 02:32:18 status half-configured python-support 1.0.10ubuntu3
2012-12-19 02:32:32 status installed python-support 1.0.10ubuntu3
2012-12-19 02:32:33 startup packages configure
2012-12-19 02:32:33 configure google-chrome-stable 23.0.1271.97-r171054 <none>
2012-12-19 02:32:33 status unpacked google-chrome-stable 23.0.1271.97-r171054
2012-12-19 02:32:35 status half-configured google-chrome-stable 23.0.1271.97-r171054
2012-12-19 02:32:37 status installed google-chrome-stable 23.0.1271.97-r171054
2012-12-19 02:32:37 configure heroku 2.33.5 <none>
2012-12-19 02:32:37 status unpacked heroku 2.33.5
2012-12-19 02:32:37 status half-configured heroku 2.33.5
2012-12-19 02:32:38 status installed heroku 2.33.5
2012-12-19 02:32:38 configure heroku-toolbelt 2.33.5 <none>
2012-12-19 02:32:38 status unpacked heroku-toolbelt 2.33.5
2012-12-19 02:32:38 status half-configured heroku-toolbelt 2.33.5
2012-12-19 02:32:38 status installed heroku-toolbelt 2.33.5
2012-12-19 02:32:38 configure google-talkplugin 3.10.2.0-1 <none>
2012-12-19 02:32:38 status unpacked google-talkplugin 3.10.2.0-1
2012-12-19 02:32:38 status half-configured google-talkplugin 3.10.2.0-1
2012-12-19 02:32:38 status installed google-talkplugin 3.10.2.0-1
2012-12-19 02:32:38 configure postgresql-client-9.1 9.1.7-0ppa1~natty.1 <none>
2012-12-19 02:32:38 status unpacked postgresql-client-9.1 9.1.7-0ppa1~natty.1
2012-12-19 02:32:38 status half-configured postgresql-client-9.1 9.1.7-0ppa1~natty.1
2012-12-19 02:32:39 status installed postgresql-client-9.1 9.1.7-0ppa1~natty.1
2012-12-19 02:32:39 configure postgresql-9.1 9.1.7-0ppa1~natty.1 <none>
2012-12-19 02:32:39 status unpacked postgresql-9.1 9.1.7-0ppa1~natty.1
2012-12-19 02:32:39 status half-configured postgresql-9.1 9.1.7-0ppa1~natty.1
2012-12-19 02:32:42 status installed postgresql-9.1 9.1.7-0ppa1~natty.1

```

---

### Post by Rexilion on 2012-12-23
Could you provide a date where you are sure it worked and a date of the moment when you are confident it failed to work?

I'm suspecting an update broke something somewhere =) .

---

### Post by Naeblis on 2012-12-23
Can't be really accurate. I think I waited a few days before making this thread. But I think I can be reasonably sure that everything was fine around 2 weeks ago. That would be December 9. I made this thread 1 week ago, so I suppose December 16 can be taken as the date on which I'm confident stuff wasn't working. 

Side note: I notice that when I open a folder where there are files which should have thumbnails, the processor activity goes up.

---

### Post by Rexilion on 2012-12-25
> **Naeblis said:**
> Side note: I notice that when I open a folder where there are files which should have thumbnails, the processor activity goes up.

Kewl, could you fire up 'top' in another terminal and figure out where what process is doing that? It should appear at the top.

---

### Post by Naeblis on 2012-12-25
It's nautilus.

---

### Post by Rexilion on 2012-12-26
I checked launchpad, couldn't directly see a bug relating to your experience. Maybe open a new one? Make sure to mention that you tried to delete ~/.thumbnails and tried it with a 'fresh' user.

---

### Post by Naeblis on 2012-12-26
I'll do that. Thanks for all the help! :)

---

