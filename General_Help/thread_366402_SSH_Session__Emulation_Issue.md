---
title: "SSH Session / Emulation Issue"
date: 2007-02-20
forum: General Help
---

### Post by Strider on 2007-02-20
Hi all,

I recently installed ubuntu server and setup SSH for remote access.  I'm using SecureCRT to connect via SSH.  I can connect fine.  My emulation is set to Linux with ANSI Colors.  Almost everything is displayed properly and working but I have two issues:

1) When editing a file in vi and I'm in insert mode, any attempts to move the arrow keys just puts a character on a new line and does not move the cursor.

2) The attach image shows an issue displaying ansi characters on the display for pstree output.  

I've changed emulation to vt100, vt220, etc and ran pstree as a test to see if it works but nothing seems to fix the problem.

Way back when I remember doing something to fix a similar issue on a different distro of linux but I don't remember anymore.

Has anyone ran into these issues and if so, any solutions/workarounds?  A little annoying at times and I know this can be fixed.

I've also tried using Putty but got the same results so I'm looking at something on the system itself.

Thanks in advance.


**Update: Resolution**
I fixed the issue.  If anyone is interested in it, I had to set the Character encoding on my terminal emulator (SecureCRT in this case) to UTF-8.  All seems to work now! :guitar: 

-Mike

---

