---
title: "Nautilus hangs after search on remote filesystem"
date: 2014-06-27
forum: General Help
---

### Post by Chris_Becker on 2014-06-27
Hi,

I have a reproducible problem, most probably a bug.

I connected to one of my webservers via Nautilus -> Connect to server.

The connection is a SSH (SFTP) connection.

```
gvfs-mount --list
``` shows, that everything went fine. I can see all my files.

When I'm in any folder, let's say / and then start tiping something on the keyboard, let's say 'etc', nautilus starts searching for everything containing etc instead of focusing the directory etc which I want to enter. When I the press ESC everything hangs and even unmounting using ```
gvfs-mount -u ...
``` doesn't work.

Any suggestions?

---

### Post by tgalati4 on 2014-06-27
Check your path statement.  If you have a directory on the remote tree, then that would be included in any command searches.  If your connection is slow, this could be painful.

```
echo $PATH
```

---

### Post by Chris_Becker on 2014-06-28
Thank you very much for your reply. :) My path does not contain any pathes on the remote filesystem.

For me it seems, that anything in Nautilus is wrong. Everytime I start tipping something on the keyboard Nautilus opens the search textbox and the text is automatically entered for a search.

When nautilus performs a search in / let's say for 'et' because I want to focus etc and I then press ESC, then I can't navigate through my server anymore.

---

### Post by tgalati4 on 2014-06-28
I use caja, which is a nautilus clone in Linux Mint MATE, and I don't seem to have that problem.  I'm currently using a version based on 12.10, so if you are running 14.04, then the behavior of nautilus may be a bug or a feature, depending on how much you like to wait.  It's probably not frozen, it just takes a really long time to perform some searches.

I do know if you have some preference settings that it will slow down remote access, such as preview icons "Always" vs "Local Files Only", this will attempt to parse icons for all files on a remote directory--which can take a long time on a remote share.

How large is the web directory that you are remotely mounted to?  Typically, if you are trying to remotely mount a web directory with ssh, you are performing maintenance on a website or updating content--and for that you would normally use the command line instead of nautilus.  Try a different file manager or come up with a command line workflow instead.

Also, I believe that any file mounted with *gvfs-mount* is automatically part of the root file tree and therefore your remote mount would be included in a root-level (/) search.  With a remote mount over a WAN, this could be slow.  Really, slow.  Lock-up-the-machine slow.

Try using a regular mount in [/etc/fstab]("https://help.ubuntu.com/community/Fstab") and see if nautilus behaves correctly.

---

