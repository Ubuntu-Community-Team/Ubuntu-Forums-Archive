---
title: "Texteditor deluxe"
date: 2007-07-19
forum: General Help
---

### Post by Helmi on 2007-07-19
Hi,

i'm looking for some advanced texteditor. I've seen a lot so far with different features, but i couldn't find one that has all this stuff:

[LIST]
[*]Syntax hilighting (at least html, css, php)
[*]input helpers (show open/close brackets that belong together...)
[*]integrated FTP (and probably SFTP/SCP)
[*]clean interface with at least switchable toolbars or none
[*]tabbed interface for multiple files
[/LIST]

the best i could find so far is bluefish but it has no ftp support. I'd like to directly edit files on the server without using the shell ;) Additionally it's synatx hilighting support is horrible.

Does anyone have a good idea?

P.S.: Forgot to say it should be Gnome-based ;)

---

### Post by dagnabit dang doohickey on 2007-07-19
Bluefish supports remote file access through gnome-vfs. I'm not a big fan of Bluefish for a bunch of reasons, but remote file access isn't one of them as it seems to handle that better than most.

You may want to look into [sshfs]("http://fuse.sourceforge.net/sshfs.html") for remote file access. It's fairly simple to set up and once you do, you'll be able to use any text editor you like.

My current favorite Linux text editor is [Geany]("http://geany.uvena.de/"). But when I'm doing some serious code cranking I fire up Textmate (with BBedit on the side for it's fantastic search/diff features) on the Mac. Nothing comes close for me on Linux. [edit: actually Geany looks very promising as something that may mature into a Textmate killer.]

Some sshfs links:
[http://myy.helia.fi/~karte/mount_sshfs.html]("http://myy.helia.fi/~karte/mount_sshfs.html")
[http://doc.gwos.org/index.php/Sshfs]("http://doc.gwos.org/index.php/Sshfs")
[http://ubuntuforums.org/showthread.php?t=103860]("http://ubuntuforums.org/showthread.php?t=103860")

Note: on some of these links you may see an instruction to change permissions of fusermount. Don't do that. If you add your user to the fuse group that kludge won't be necessary.

---

### Post by Helmi on 2007-07-21
hey thanks for your input.

yeah indeed textmate is probably the most advanced texteditor when it comes to features and usability.

Unfortunately it's mac only and i don't have one - so not worth a discussion. I'll look into sshfs. Bluefish is a nice editor but really only a nice and not a real good one. The syntax hilighting is horrible.

I'll also have a look at geany.

---

