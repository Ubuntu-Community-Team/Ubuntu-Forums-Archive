---
title: "Word Perfect 2000 and FontTastic"
date: 2007-08-18
forum: General Help
---

### Post by profeXorGeek on 2007-08-18
I am trying to install WordPerfect 2000 on Ubuntu Dapper Drake for a friend. Why not use open office? Because he has lots of existing files in WP with columns and other things that don't translate well.

I couldn't install the program from the CD. Kept giving me 'Permission Denied' errors,even as root. I finally copied the CD to a temp folder, chmod the setup file to be executable and got it to install.

However, there were only two install modes: automatic and manual. Manual doesn't work and Automatic doesn't give you any feedback about errors or failures.

When I try to launch wordperfect after installing it says that no instance of Fonttastic font server is running. It tries to start one, fails. I try to start one, fail. I try to start one as root: cannot access display (because the display is running under my friend's username). I try to start one as super-user (sudo vs su -), fails. Says port is already in use.

ps -ef shows me that an instance of the font server is already running. Hence the port in use errors. However, WP apparently cannot see this instance.

Does anyone have any ideas why the font server is running but not detected by WP? Every program in this corel suite requires the font server and will not start without it. I have been all over Google and these forums and have tried all relevant tips. Please let me know if you have any suggestions.

Much thanks

---

### Post by HermanAB on 2007-08-18
Hmm, you'll have better luck with Wordperfect on Windoze on Qemu, Virtualbox or VMware.

---

