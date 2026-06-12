---
title: "HOWTO: Importing email into Thunderbird"
date: 2005-09-14
forum: General Help
---

### Post by wombat20 on 2005-09-14
About time I posted something useful.   ;-) 

You may be frustrated by how Thunderbird appears to only want to import mail from other applications already running in the same OS.  That's not much good if you're migrating from Windows or OSX as many here are.

Most mail programs seem to either store email in the mbox format or are able to export in this format.  If not I guess you can try to import to one which does.

Thunderbird thankfully has an extension to allow you to import .mbox files directly rather than selecting from a list of inappropriate programs (I only see Netscape Communicator 4.x which I don't even have).

The following allows you to import .mbox files from anywhere on your system.  In my case it also worked for .txt files which I assume must've been in the mbox format.

[Thunderbird mbox importer extension](http://www.extensionsmirror.nl/index.php?showtopic=2074)

This works for email exported from Demon Internet's Turnpike 6 for Windows and will probably do the job in most other cases.

Hope that helps someone.   :grin:

---

### Post by editrix on 2005-10-19
Hi Wombat:

It wouldn't install for me. Said it's incompatible with Thunderbird. Could that be because I'm still on Hoary?

---

### Post by aysiu on 2005-10-19
When I first migrated to Linux, I just copied my C:\Documents and Settings\Username\Application Data\Thunderbird folder to my /home/username/.mozilla-thunderbird folder, and it worked like a charm.

---

### Post by editrix on 2005-10-19
[QUOTE=aysiu]When I first migrated to Linux, I just copied my C:\Documents and Settings\Username\Application Data\Thunderbird folder to my /home/username/.mozilla-thunderbird folder, and it worked like a charm.[/QUOTE]

Darn! It didn't work for me. Maybe because I used TBird before I tried it? Or maybe I need to (Gasp!) reboot? What happened? You just fired up TBird in Ubuntu, and it was all there? Special folders and everything?

I read someplace about creating symlinks between the Win & Lin versions, too, but I don't know enough about symlinks to even create one.

Edit: Got this from Linux Questions.org

"There is a profile folder in windows:
c:\Documents and Settings\<<username>>\Application Data\Thunderbird\

In Linux,
put the contents of /home/<<username>>/.thunderbird/ into a new folder in the same location and name it "old".
Then copy the contents of the profile folder from windows to the above path in linux and voila! It worked!"

(I'm pasting the info here to spare others the work I'm going through. Hopefully, keep all possible solutions in one place.)

---

### Post by wombat20 on 2005-10-20
[QUOTE=editrix]Hi Wombat:
It wouldn't install for me. Said it's incompatible with Thunderbird. Could that be because I'm still on Hoary?[/QUOTE]

No, I did it in Hoary (now upgraded).  As with all Thunderbird extensions, make sure you save it on your disk (it's a .xpi file), then go Tools -> Extensions in Thunderbird.  I often get an error when I absent mindedly try to open it from within Firefox.

---

