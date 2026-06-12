---
title: "Bus error
Can't start VirtualBox and OpenOffice Bus error (core dumped)"
date: 2008-03-27
forum: General Help
---

### Post by ev0 on 2008-03-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/207551](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/207551) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi all,

The other day my Gutsy froze and I had to press the hard reset button to reboot the machine. And once it's restarted I can't start VirtualBox or Open Office anymore.

By typing the command
"oowriter" at a console, I get this error message:

/usr/lib/openoffice/program/soffice: line 361: 19804 Bus error
(core dumped) "$sd_prog/$sd_binary" "$@"

And by starting VirtualBox, here's the error dialog in the attachment: Failed to create VirtualBox COM object.

By typing /usr/lib/virtualbox/./VBoxSVC in the console, the only message I get is: "Bus error (core dumped)"
I've reinstalled VirtualBox 1.5.6 from the virtual box repo, installed 1.5.0 from ubuntu repo, and still the same problem persists. Any help would be very very much appreciated!! Thanks!!

---

