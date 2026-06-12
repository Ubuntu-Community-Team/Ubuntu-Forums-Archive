---
title: "ImageMagick won't let go of pdf files"
date: 2016-07-05
forum: General Help
---

### Post by tapasray on 2016-07-05
This is bizarre. I had to re-install Ubuntu 16.04 a few days ago. Since then, ImageMagick stays put as the default application for opening pdf files. No amount of trying to set Okular (which I want) or anything else through 'Properties' helps. Please help.

CORRECTION: It's Ubuntu, NOT Kubuntu.

---

### Post by coldraven on 2016-07-05
Have you tried right-clicking and select "Open with" > "Other application"? You might need to find out where okular is installed.

---

### Post by tapasray on 2016-07-05
It does open with Okular that way. But in 'properties', the opening value defaults to imagemagick and it's no use trying to change it to Okular or anything else. That just does not work.

I have now uninstalled imagemagick and that has solved the problem. only, this is not a real solution. So I'll see if a solution can be found before marking this thread as 'solved'.

---

### Post by &amp;KyT$0P# on 2016-07-05
What do you have in ~/.local/share/applications/mimeapps.list?

Add a line like this in alphabetical order in the "Default Applications" section:
```
application/pdf=okular.desktop
```

Make sure to also add "okular.desktop" semicolon-separated to any "application/pdf" entry in "Added Associations" section as well.

If you don't have a ~/.local/share/applications/mimeapps.list, or if it's empty, put this in it:
```
[Added Associations]
application/pdf=okular.desktop;

[Default Applications]
application/pdf=okular.desktop
```

You might need to log out and back in to see the effect of the change.

Does this help?

---

### Post by tapasray on 2016-07-06
Thanks, @halogen2, and apologies for the late response. Here's the result of my attempts --

```
xyz:~$ ~/.local/share/applications/mimeapps.list?
bash: /home/tapas/.local/share/applications/mimeapps.list?: No such file or directory
xyz:~$ /.local/share/applications/mimeapps.list?
bash: /.local/share/applications/mimeapps.list?: No such file or directory
xyz:~$ /.local/share/applications/mimeapps.list
bash: /.local/share/applications/mimeapps.list: No such file or directory
xyz:~$ .local/share/applications/mimeapps.list
bash: .local/share/applications/mimeapps.list: No such file or directory
xyz:~$[CODE]
```[/CODE]

---

### Post by &amp;KyT$0P# on 2016-07-06
mimeapps.list is not an executable file, it's a text file that you can edit as detailed above using your favorite text editor.

(For what it's worth, your first Terminal entry expands to the correct full path to the file, if you remove the ? on the end.)

---

### Post by vasa1 on 2016-07-06
> **halogen2 said:**
> ..., it's a text file that you can edit as detailed above using your favorite text editor.
...
+1.

@tapasray, 
I'd stick to editors such as Gedit or Mousepad or Geany when editing files which are "plain text" aka "ASCII text" to begin with. All these editors offer syntax highlighting for a variety of files.

In this specific case,
```
07:26 AM ~ $ file /home/vasa1/.local/share/applications/mimeapps.list
/home/vasa1/.local/share/applications/mimeapps.list: ASCII text
07:26 AM ~ $ 
```Avoid LibreOffice Writer or Abiword :)

---

### Post by tapasray on 2016-07-06
Thanks both of you you. Let's see ...

I searched Home and Computer for mimeapps and mimeapps.list, and got no hits.

I should mention that gscan2, which I think is an excellent app and use all the time, vanished after I removed imagemagick. After updating with Synaptic, imagemagick is back, and with it the old problem for which I started this thread. Then I installed gscan2 again, and it's working ... so far.

---

### Post by &amp;KyT$0P# on 2016-07-07
It won't be there if you've never define any custom associations.  So you can create a new text file named mimeapps.list in folder ~/.local/share/applications (creating those folders if they don't exist)

---

### Post by tapasray on 2016-07-08
Thank you. Will try this.

Hello! I have been trying, but haven't succeeded yet. Don't see any 'local' folder in 'Home'. Searching 'Computer' for 'local' brings up one such in /usr. That one has a 'share' folder, which does not have an 'applications' folder and will not let me create any new folder or document. Tried to become root user, following instructions people have posted on a couple of sites. Was able to (apparently) set a root password ... but then nothing happened.

---

### Post by vasa1 on 2016-07-11
Please post the output of ```
cd && ls -a
```

---

### Post by tapasray on 2016-07-11
@vasa1,

```
xyz:~$ cd && ls -a
.                 Export Pages Scanned Document.pdf  Pictures
..                .gconf                             .profile
.adobe            .gimp-2.8                          Public
.bash_history     .gksu.lock                         .sane
.bash_logout      .gnupg                             .sudo_as_admin_successful
.bashrc           .gscan2pdf                         Templates
.cache            .hplip                             .thumbnails
.config           .ICEauthority                      Videos
Desktop           .kde                               .Xauthority
.dmrc             .local                             .xsession-errors
Documents         .macromedia                        .xsession-errors.old
Downloads         .mozilla
examples.desktop  Music
xyz:~$ 


```

---

### Post by &amp;KyT$0P# on 2016-07-11
> Don't see any 'local' folder in 'Home'
Not "local" but ".local" (note that leading dot).  It's probably hidden by the file manager, so you'll need to either select to show hidden files & folders, or navigate there manually.

---

### Post by tapasray on 2016-07-12
ok, trying.

Ok, found .local ... it was indeed hidden. Created the mimeapps.list plain text file with - 

```
[Added Associations]
application/pdf=okular.desktop;

[Default Applications]
application/pdf=okular.desktop
```

in it.

But still can't set Okular as default.

---

### Post by QDR06VV9 on 2016-07-12
Has anyone suggested looking in "Settings"> Preferred Applications> and checking what is under Document Viewer yet?

---

### Post by tapasray on 2016-07-12
That I had tried after the 'Properties' route didn't work out. But there was no entry for pdf. The entries are Web, Mail, Calendar, Music, Video, and Photos. I have set Okular as default for Photos, thinking this might help, but it hasn't.

I should mention that there's no System Settings > Preferred Applications.
What I have is, System Settings > Details > Default Applications.

---

### Post by &amp;KyT$0P# on 2016-07-12
> **tapasray said:**
> ... still can't set Okular as default.
That *is* a way to set Okular as default.  The method works for me in Xubuntu 16.04...
You might need to log out and log back in for it to take effect.

---

### Post by tapasray on 2016-07-13
Tried. Does not work.

---

### Post by &amp;KyT$0P# on 2016-07-17
I found a mimeapps.list file in ~/.config as well, what if you try adding to that mimeapps.list file instead?

---

### Post by tapasray on 2016-07-24
Sorry, @halogen2. I wasn't well the last few days. Found that file and added those lines at the end. Restarted. Did not work.

I do not know whether this has anything with the Okular issue, but thought it might be useful here --

As VLC was not working, I opened Synaptic, searched for VLC, clicked 'Mark All Upgrades' and then clicked 'Apply'. Goetting a "Not all changes and updates succeeded" message with the following details.


```

Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 271020 files and directories currently installed.)
Preparing to unpack .../systemd-sysv_229-4ubuntu7_i386.deb ...
Unpacking systemd-sysv (229-4ubuntu7) over (229-4ubuntu6) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up systemd-sysv (229-4ubuntu7) ...
(Reading database ... 271020 files and directories currently installed.)
Preparing to unpack .../libpam-systemd_229-4ubuntu7_i386.deb ...
Unpacking libpam-systemd:i386 (229-4ubuntu7) over (229-4ubuntu6) ...
Preparing to unpack .../libsystemd0_229-4ubuntu7_i386.deb ...
Unpacking libsystemd0:i386 (229-4ubuntu7) over (229-4ubuntu6) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Setting up libsystemd0:i386 (229-4ubuntu7) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
(Reading database ... 271020 files and directories currently installed.)
Preparing to unpack .../systemd_229-4ubuntu7_i386.deb ...
Unpacking systemd (229-4ubuntu7) over (229-4ubuntu6) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for dbus (1.10.6-1ubuntu3) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up systemd (229-4ubuntu7) ...
addgroup: The group `systemd-journal' already exists as a system group. Exiting.
(Reading database ... 271020 files and directories currently installed.)
Preparing to unpack .../udev_229-4ubuntu7_i386.deb ...
Unpacking udev (229-4ubuntu7) over (229-4ubuntu6) ...
Preparing to unpack .../libudev1_229-4ubuntu7_i386.deb ...
Unpacking libudev1:i386 (229-4ubuntu7) over (229-4ubuntu6) ...
Processing triggers for systemd (229-4ubuntu7) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Setting up libudev1:i386 (229-4ubuntu7) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
(Reading database ... 271021 files and directories currently installed.)
Preparing to unpack .../base-files_9.4ubuntu4.2_i386.deb ...
Unpacking base-files (9.4ubuntu4.2) over (9.4ubuntu4.1) ...
Processing triggers for plymouth-theme-ubuntu-text (0.9.2-3ubuntu13.1) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for cracklib-runtime (2.9.2-1build2) ...
Processing triggers for install-info (6.1.0.dfsg.1-5) ...
Processing triggers for initramfs-tools (0.122ubuntu8.1) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-31-generic

```

---

### Post by vasa1 on 2016-07-24
> **tapasray said:**
> I do not know whether this has anything with the Okular issue, but thought it might be useful here --

As VLC was not working, I opened Synaptic, searched for VLC, clicked 'Mark All Upgrades' and then clicked 'Apply'. Goetting a "Not all changes and updates succeeded" message with the following details.
...
What about the **_entire_** output of plain old-fashioned *sudo apt-get update* and *sudo apt-get upgrade*?

---

### Post by tapasray on 2016-07-24
ok, will do that.

---

### Post by tapasray on 2016-07-24
For sudo apt-get update

```
Hit:1 http://security.ubuntu.com/ubuntu xenial-security InRelease
Get:2 http://in.archive.ubuntu.com/ubuntu xenial InRelease [247 kB]
Get:3 http://in.archive.ubuntu.com/ubuntu xenial-updates InRelease [95.7 kB]
Get:4 http://in.archive.ubuntu.com/ubuntu xenial-backports InRelease [92.2 kB]
Fetched 435 kB in 2s (182 kB/s)                               
Reading package lists... Done

```

For sudo apt-get upgrade

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  cups-browsed cups-core-drivers cups-daemon cups-filters-core-drivers
  cups-server-common hplip-data libcupscgi1 libcupsmime1 libfontembed1
  libgutenprint2 liblouisutdml-bin liblouisutdml-data liblouisutdml6 libqpdf17
  libqtassistantclient4 libwebpmux1 python3-notify2 python3-pexpect
  python3-pil python3-ptyprocess python3-pyqt4 python3-renderpm
  python3-reportlab python3-reportlab-accel python3-sip qpdf ssl-cert
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up cubemap (1.2.1-1) ...
Job for cubemap.service failed because the control process exited with error code. See "systemctl status cubemap.service" and "journalctl -xe" for details.
invoke-rc.d: initscript cubemap, action "start" failed.
dpkg: error processing package cubemap (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 cubemap
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by mc4man on 2016-07-24
cubemap package is broken, remove it
```
sudo apt purge cubemap
```
Post _complete_ results - 
```
cat .config/mimeapps.list
```

(-note: in ubuntu .local/share/applications/mimeapps.list is not used, if there delete it.

edit: bug cubemap - 
[https://bugs.launchpad.net/ubuntu/+source/cubemap/+bug/1598696](https://bugs.launchpad.net/ubuntu/+source/cubemap/+bug/1598696)

---

### Post by tapasray on 2016-07-24
ok ...

---

### Post by tapasray on 2016-07-24
```
xyz:~$ sudo apt purge cubemap
[sudo] password for tapas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  cups-browsed cups-core-drivers cups-daemon cups-filters-core-drivers
  cups-server-common hplip-data libcupscgi1 libcupsmime1 libfontembed1
  libgutenprint2 liblouisutdml-bin liblouisutdml-data liblouisutdml6 libqpdf17
  libqtassistantclient4 libwebpmux1 python3-notify2 python3-pexpect
  python3-pil python3-ptyprocess python3-pyqt4 python3-renderpm
  python3-reportlab python3-reportlab-accel python3-sip qpdf ssl-cert
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  cubemap*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 304 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 271239 files and directories currently installed.)
Removing cubemap (1.2.1-1) ...
Purging configuration files for cubemap (1.2.1-1) ...
Processing triggers for man-db (2.7.5-1) ...
xyz:~$ cat .config/mimeapps.list
[Default Applications]
image/jpeg=kde4-okularApplication_kimgio.desktop
image/avs=display-im6.q16.desktop
image/bie=display-im6.q16.desktop
image/x-ms-bmp=display-im6.q16.desktop
image/cmyk=display-im6.q16.desktop
image/dcx=display-im6.q16.desktop
image/eps=display-im6.q16.desktop
image/fax=display-im6.q16.desktop
image/fits=display-im6.q16.desktop
image/gif=kde4-okularApplication_kimgio.desktop
image/gray=display-im6.q16.desktop
image/pjpeg=eog.desktop
image/miff=display-im6.q16.desktop
image/mono=display-im6.q16.desktop
image/mtv=display-im6.q16.desktop
image/x-portable-bitmap=kde4-okularApplication_kimgio.desktop
image/pcd=display-im6.q16.desktop
image/pcx=display-im6.q16.desktop
image/pdf=display-im6.q16.desktop
image/x-portable-graymap=kde4-okularApplication_kimgio.desktop
image/pict=display-im6.q16.desktop
image/png=kde4-okularApplication_kimgio.desktop
image/x-portable-anymap=eog.desktop
image/x-portable-pixmap=kde4-okularApplication_kimgio.desktop
image/ps=display-im6.q16.desktop
image/rad=display-im6.q16.desktop
image/x-rgb=kde4-okularApplication_kimgio.desktop
image/rgba=display-im6.q16.desktop
image/rla=display-im6.q16.desktop
image/rle=display-im6.q16.desktop
image/sgi=display-im6.q16.desktop
image/sun-raster=display-im6.q16.desktop
image/targa=display-im6.q16.desktop
image/tiff=kde4-okularApplication_kimgio.desktop
image/uyvy=display-im6.q16.desktop
image/vid=display-im6.q16.desktop
image/viff=display-im6.q16.desktop
image/x-xbitmap=kde4-okularApplication_kimgio.desktop
image/x-xpixmap=kde4-okularApplication_kimgio.desktop
image/x-xwindowdump=display-im6.q16.desktop
image/x-icon=display-im6.q16.desktop
image/yuv=display-im6.q16.desktop
image/bmp=kde4-okularApplication_kimgio.desktop
image/x-dds=kde4-okularApplication_kimgio.desktop
image/x-eps=kde4-okularApplication_kimgio.desktop
image/x-exr=kde4-okularApplication_kimgio.desktop
image/x-hdr=kde4-okularApplication_kimgio.desktop
image/x-ico=kde4-okularApplication_kimgio.desktop
image/jp2=kde4-okularApplication_kimgio.desktop
image/x-pcx=kde4-okularApplication_kimgio.desktop
image/x-psd=kde4-okularApplication_kimgio.desktop
image/x-tga=kde4-okularApplication_kimgio.desktop
image/x-xcf=kde4-okularApplication_kimgio.desktop
image/x-gzeps=kde4-okularApplication_kimgio.desktop
image/x-bzeps=kde4-okularApplication_kimgio.desktop
image/jpg=eog.desktop
image/x-bmp=eog.desktop
image/x-gray=eog.desktop
image/x-icb=eog.desktop
image/x-png=eog.desktop
image/svg+xml=eog.desktop
image/svg+xml-compressed=eog.desktop
image/vnd.wap.wbmp=eog.desktop
audio/flac=vlc.desktop
application/pdf=kde4-okularApplication_pdf.desktop
application/pdf=kde4-okularApplication_pdf.desktop

[Added Associations]
image/avs=display-im6.q16.desktop;
image/bie=display-im6.q16.desktop;
image/x-ms-bmp=display-im6.q16.desktop;
image/cmyk=display-im6.q16.desktop;
image/dcx=display-im6.q16.desktop;
image/eps=display-im6.q16.desktop;
image/fax=display-im6.q16.desktop;
image/fits=display-im6.q16.desktop;
image/gif=display-im6.q16.desktop;kde4-okularApplication_kimgio.desktop;eog.desktop;
image/gray=display-im6.q16.desktop;
image/pjpeg=display-im6.q16.desktop;eog.desktop;
image/miff=display-im6.q16.desktop;
image/mono=display-im6.q16.desktop;
image/mtv=display-im6.q16.desktop;
image/x-portable-bitmap=display-im6.q16.desktop;kde4-okularApplication_kimgio.desktop;eog.desktop;
image/pcd=display-im6.q16.desktop;
image/pcx=display-im6.q16.desktop;
image/pdf=display-im6.q16.desktop;
image/x-portable-graymap=display-im6.q16.desktop;kde4-okularApplication_kimgio.desktop;eog.desktop;
image/pict=display-im6.q16.desktop;
image/png=display-im6.q16.desktop;kde4-okularApplication_kimgio.desktop;eog.desktop;
image/x-portable-anymap=display-im6.q16.desktop;eog.desktop;
image/x-portable-pixmap=display-im6.q16.desktop;kde4-okularApplication_kimgio.desktop;eog.desktop;
image/ps=display-im6.q16.desktop;
image/rad=display-im6.q16.desktop;
image/x-rgb=display-im6.q16.desktop;
image/rgba=display-im6.q16.desktop;
image/rla=display-im6.q16.desktop;
image/rle=display-im6.q16.desktop;
image/sgi=display-im6.q16.desktop;
image/sun-raster=display-im6.q16.desktop;
image/targa=display-im6.q16.desktop;
image/tiff=display-im6.q16.desktop;kde4-okularApplication_kimgio.desktop;eog.desktop;
image/uyvy=display-im6.q16.desktop;
image/vid=display-im6.q16.desktop;
image/viff=display-im6.q16.desktop;
image/x-xbitmap=display-im6.q16.desktop;kde4-okularApplication_kimgio.desktop;eog.desktop;
image/x-xpixmap=display-im6.q16.desktop;kde4-okularApplication_kimgio.desktop;eog.desktop;
image/x-xwindowdump=display-im6.q16.desktop;
image/x-icon=display-im6.q16.desktop;
image/yuv=display-im6.q16.desktop;
application/x-troff-man=gnome-software-local-file.desktop;
image/bmp=kde4-okularApplication_kimgio.desktop;eog.desktop;
image/x-ico=kde4-okularApplication_kimgio.desktop;eog.desktop;
image/x-pcx=kde4-okularApplication_kimgio.desktop;eog.desktop;
image/jpeg=display-im6.desktop;
image/jpg=eog.desktop;
image/x-bmp=eog.desktop;
image/x-gray=eog.desktop;
image/x-icb=eog.desktop;
image/x-png=eog.desktop;
image/svg+xml=eog.desktop;
image/svg+xml-compressed=eog.desktop;
image/vnd.wap.wbmp=eog.desktop;
inode/directory=vlc.desktop;
audio/flac=vlc.desktop;
application/pdf=kde4-okularApplication_pdf.desktop;evince.desktop;
application/pdf=okular.desktop;

[Removed Associations]
application/pdf=display-im6.desktop;

```

---

### Post by mc4man on 2016-07-24
You may have some conflicting entries & certainly some duped ones. To see if that's the issue - 
```
mv .config/mimeapps.list .config/mimeapps.list.bak
```
Then try to set pdf to a default of okular in the Properties > Open With on a pdf

---

### Post by tapasray on 2016-07-24
Nothing happens with that code. The prompt comes back.

```

xyz:~$ mv .config/mimeapps.list .config/mimeapps.list.bak
xyz:~$ 

```

---

### Post by &amp;KyT$0P# on 2016-07-24
> Nothing happens with that code. The prompt comes back.
That means the command worked :) For next time, if you want to see output, use [FONT=Courier New]mv -v[/FONT] instead of just [FONT=Courier New]mv[/FONT]

---

### Post by tapasray on 2016-07-24
Oh, ok! Let me try now ...

Yes! I could set Okular as the default program for pdf files.

Sincere thanks to all those who gave so much of their time to help. I really appreciate the trouble they took and their patience. Marking this thread as 'solved'.

---

### Post by mc4man on 2016-07-24
This issue was likely caused by use or repeated use of System Settings > Details > Default Applications. It's better to just set default app for any mimetype thru the file manger & stay away from the former.
I don't have the time or patience with this forums crappy performance to outline the particulars, you could glean the gist of it here - 
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1280794](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1280794)

---

