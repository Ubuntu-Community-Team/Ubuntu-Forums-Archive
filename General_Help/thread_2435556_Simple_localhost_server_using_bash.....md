---
title: "Simple localhost server using bash...."
date: 2020-01-22
forum: General Help
---

### Post by Furycd001 on 2020-01-22
HI Guys..

I'm looking to start a simple localhost server from within a directory on my system & have all the files & folders from within that directory accessible to all other devices connected to the same network. Is this at all possible using only bash  ?? I found [**"THIS"**]("https://github.com/benrady/shinatra") but it doesn't seem to work for me. I also found [**"THIS LIST"**]("https://gist.github.com/willurd/5720255") over on GitHub, but there is no bash native listed & the busybox one runs, but does nothing([see this screenshot]("http://i.imgur.com/VroLNzV.png")). Any help is very much appreciated. Thanks....

---

### Post by TheFu on 2020-01-22
> **jonny6 said:**
> HI Guys..

I'm looking to start a simple localhost server from within a directory on my system & have all the files & folders from within that directory accessible to all other devices connected to the same network. Is this at all possible using only bash  ?? I found [**"THIS"**]("https://github.com/benrady/shinatra") but it doesn't seem to work for me. I also found [**"THIS LIST"**]("https://gist.github.com/willurd/5720255") over on GitHub, but there is no bash native listed & the busybox one runs, but does nothing([see this screenshot]("http://i.imgur.com/VroLNzV.png")). Any help is very much appreciated. Thanks....

Dude.  Use ssh and sftp.  There are ssh/sftp/scp/rsync clients for every OS that has networking.  Don't try to reinvent the wheel, badly.  Every networked system needs ssh.
Every Linux file manager has built-in support for sftp.  On Windows, use WinSCP or Filezilla.

If that doesn't work for the edge cases, something like nextcloud might fit, but it isn't trivial to setup.

If the files are media - music, video, then something like miniDLNA or Plex would allow streaming from pretty much any device.

If you insist on using tiny web servers, hacked in a scripting language, most will have file-size limits and all will need to run on a high-port ... so set it up above port 1024.

---

### Post by Furycd001 on 2020-01-23
> **TheFu said:**
> Dude.  Use ssh and sftp.  There are ssh/sftp/scp/rsync clients for every OS that has networking.  Don't try to reinvent the wheel, badly.  Every networked system needs ssh.
Every Linux file manager has built-in support for sftp.  On Windows, use WinSCP or Filezilla.

If that doesn't work for the edge cases, something like nextcloud might fit, but it isn't trivial to setup.

If the files are media - music, video, then something like miniDLNA or Plex would allow streaming from pretty much any device.

If you insist on using tiny web servers, hacked in a scripting language, most will have file-size limits and all will need to run on a high-port ... so set it up above port 1024.

Thank you very much for replying. I'll look into ssh or ftp :)

---

### Post by TheFu on 2020-01-23
> **jonny6 said:**
> Thank you very much for replying. I'll look into ssh or ftp :)

Forget FTP, that protocol should have died in 2002. Use sftp, which is part of openssh-server.  When you install that, you get sftp for free, with all the same security that ssh provides.

Someone will probably mention that on an internal LAN, security doesn't matter.  Security always matters these days. Best to get into the habit of using secure protocols, always.

ssh is how the Unix world communicates and has been since the mid-1990s.

ssh is enough for
[LIST]
[*]    secure remote access to files via **sftp**
[*]    secure remote filesystem access via **sshfs**
[*]    secure remote CLI/shell access to systems with plain ssh
[*]    secure remote desktops via **x2go**/freenx
[*]    secure remote file replication with **rsync** (ssh is the default rsync tunnel protocol)
[*]    secure port forwarding of selected ports
[*]    secure remote editing with **vim**/gvim and other editors
[*]    pseudo-VPN with **sshuttle**  
[/LIST]
Master ssh, rsync, and a backup tool like rdiff-backup.

---

### Post by kevdog on 2020-01-23
@TheFu

Curious about the rdiff-backup.  I thought many had moved up to borg or something similar?

Never head about sshuttle.  I guess I learn something new everyday.

---

### Post by TheFu on 2020-01-23
> **kevdog said:**
>  
Curious about the rdiff-backup.  I thought many had moved up to borg or something similar?

Never head about sshuttle.  I guess I learn something new everyday.

I learn multiple new things daily. Some are even useful.
I looked at borg last year and decided, for some reason, it wasn't worth changing for me. Thought it was still beta code?  I don't mention backup tools that I don't have direct experience using. That should not be surprising. I almost didn't mention any backup tool, but almost all Unix F/LOSS tools for backups are based on librsync, which embeds ssh tunnels into their solution, it sorta fit.

I love me some versioned backups.

Been using rdiff-backup here for desktop and server backups for almost a decade now.  About once a year, either something bad or stupid happens, so some kind of restore is needed.  rdiff-backup has always been there working when needed.  In that decade, a backup set has become corrupted about 3 times, but the tool notifies about that.  There is only 1 issue that I'd like handled better in rdiff-backup - sparse file handling.  Most people know zero about sparse files, so it isn't an issue for them.

My point in providing the list is mostly for people coming from Windows.  Most have no idea about ssh and don't realize the 50 things it can do, all with ssh-keys for authentication and recognized encryption security. Too much?

This entire thread could have gone down the "I only want tiny autoindex web server solutions" path too.  In some environments, adding **any** more software just isn't possible/allowed.  So having an existing scripted language, 1-line solution, might be the only possible answer. Most places I've worked, we always had NFS to share files across all the different workstations and servers.  I have that at home too.

---

