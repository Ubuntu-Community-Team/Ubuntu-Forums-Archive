---
title: "[SOLVED] Nothin but problems using firefox on ubuntu"
date: 2008-03-01
forum: General Help
---

### Post by faineant7698 on 2008-03-01
Is it just me or does firefox not like ubuntu or vise versa, if it's not one thing it's another with this program.  firefox constantly locks up and freezes making me force quit it everytime (especially on sites like veoh and youtube).  Now it refuses not to open new windows and full screen windows when links are clicked on.  I am now running fedora as well as ubuntu, and I don't have any problems like this with fedora only ubuntu.  Such a pain sometimes!  tried uninstalling firefox and reinstalling it but that didn't help, tried uninstalling reinstalling flash plugins and stuff but that didn't help.  Epiphany sometimes works a bit better but is often plagued by these same problems, so if anyone has any suggestions or ideas to fix these fun little problems with ubuntu and firefox just let me no please.](*,)

---

### Post by sstusick on 2008-03-01
This usually happens when viewing Flash video. The Flash software for Linux is very poor compared to the one that is provided for Windows.

---

### Post by faineant7698 on 2008-03-01
That makes sense but like I noted I don't experience these problems with fedora and even mandriva for that matter.  Seems like a problem more associated with ubuntu and debian based systems.  :confused:

---

### Post by sstusick on 2008-03-01
I've had the issue on every distro I've used... SuSE, Fedora, Ubuntu...

---

### Post by faineant7698 on 2008-03-01
What about other free flash players?  Is this a problem perhaps only with the adobe players and plugins?

---

### Post by sstusick on 2008-03-01
As far as I know, the issue is only with Adobe's software.

---

### Post by faineant7698 on 2008-03-01
hmmm I guess I'll try some other players and plugins then and see if that corrects the issue.  Has anyone tried gnash?  Just wondering how that one stacks up to adobe.:)

---

### Post by tad1073 on 2008-03-01
Try [Opera](http://my.opera.com/desktopteam/blog/2008/02/29/yet-another-snapshot-build)

---

### Post by sstusick on 2008-03-01
As far as the flash issue is concerned, I've had the same problem regardless of browser I was using, Opera, Firefox, Konqueror, Epiphany..

Hope it works for you, though.

---

### Post by baxterdog on 2008-03-01
The only problems I had with FF in Ubuntu (on a laptop no less) was the flash. Solved with flash problem threads;

Try;
[http://ubuntuforums.org/showthread.php?t=255422](http://ubuntuforums.org/showthread.php?t=255422)
[http://georgia.ubuntuforums.org/showthread.php?t=705538](http://georgia.ubuntuforums.org/showthread.php?t=705538)

No problems now. I found that the only plugin that really worked was the adobe non-free one.

youtube and all others should work fine if you're set up right, which can be tricky.

What I love, though, is that after all of that I had LEARNED something. Rather than just being exasperated after having to deal with getting under the hood of "another OS"

---

### Post by faineant7698 on 2008-03-01
Well nothing really much helping with this issue tried recommendations to no avail :( as far as opera it it gives a gray box when trying to look at a flash vid rather than the vid itself.  checked the directories and everything and it's pointed at the flash plugin but nothing.  Firefox is still mest up as well lol.

---

### Post by fragos on 2008-03-01
IMHO Firefox 2.0 problems aren't likely to be fixed.  Developers are apparently focused on Firefox 3.0.  For me, I've switched to Epiphany.  It also uses the Gecko rendering engine and it's so much faster without the freezes and crashes.  I miss my favorite extentions but Epiphany has some good pluses like performance and better integration with Gnome.  When 3.0 comes out, I'll consider using it.

---

### Post by faineant7698 on 2008-03-01
Found out what was wrong!  It seems that when I upgraded the flash player plugin a little while ago it looks like the old one didn't remove fully and the new one installed to a different directory.  So I had to go in and remove the old version from /usr/lib/firefox/plugins and copy the proper ones from /usr/lib/flashplugin-nonfree to the firefox plugins locations.  It might have been that the two set of plugins might have been fighting each other or the old plugins may have had some glitch in them.  Not really sure witch but the problem appears to be resolved now.  

TY for all the help and suggestions everyone :)

---

### Post by tad1073 on 2008-03-01
> **sstusick said:**
> As far as the flash issue is concerned, I've had the same problem regardless of browser I was using, Opera, Firefox, Konqueror, Epiphany..

Hope it works for you, though.

The newer snapshopst have functiong flash
just copy /usr/lib/flashplugin-nonfree/libflashplayer.so to /usr/lib/opera/plugins and use only /etc/lib/opera directory for your plugins in opera

---

