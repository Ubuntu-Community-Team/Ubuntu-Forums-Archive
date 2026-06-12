---
title: "Hitherto unposted error"
date: 2007-05-09
forum: General Help
---

### Post by winit_gal on 2007-05-09
Hey,

I'm new to Ubuntu, so I'm completely unfamiliar with how to go about troubleshooting this error. Hopefully you'll be able to help me out.
Here are the screens I get on every attempted boot:
<IMG SRC="http://i41.photobucket.com/albums/e260/BugJar/wubierror1.jpg">
<IMG SRC="http://i41.photobucket.com/albums/e260/BugJar/wubierror2.jpg">

It hangs at "loading..." for quite some time, and never progresses past the last image. 

Thanks! =)

---

### Post by ago on 2007-05-10
can you type 

more /tmp/zenigata.log

and see if there are relevant errors

---

### Post by winit_gal on 2007-05-10
"permission denied" 

Followed by nothing. =\

---

### Post by ago on 2007-05-10
ls /tmp/

(it's LS lower case) do you see zenigata.log?

---

### Post by winit_gal on 2007-05-10
Yes, I do.

---

### Post by ago on 2007-05-10
do you see 

ls /host

---

### Post by winit_gal on 2007-05-10
Hm, no I don't think so. When I type that it just goes back to (initramfs).

---

### Post by ago on 2007-05-10
cat /tmp/zenigat.log 

use shift+pgup to scroll

---

### Post by winit_gal on 2007-05-10
"No such file or directory".

---

### Post by ago on 2007-05-10
did you put a space after cat?

---

### Post by winit_gal on 2007-05-10
yep, definitely; when I mistype it precurses everything with "bin/sh"
whereas the "no such file or directory" error came after cat: [the path] no such...

---

### Post by ago on 2007-05-10
didn't you say that you could see zenigata.log under tmp?

---

### Post by winit_gal on 2007-05-10
Yes I can see it, but not view it, I guess. =( is it hopeless?

---

### Post by ago on 2007-05-10
If you can see it you should be able to read it using the commands "more" and "cat"

---

### Post by winit_gal on 2007-05-10
Ah, okay here we go (thanks for the walkthrough, it was just my incompetence stopping it from working), it tells me:

failed to mount /dev/sda1 : operation not supported
Mount denied because NTFS logfile is unclean

There's also a msg + echo "could not find host"

"could not find host folder, please check the boot parameters"

If I'm not transcribing the right bits, let me know and I can take more screen caps.

---

### Post by ago on 2007-05-11
Run wubi and reinstall. When you reboot, the first time select windows. Shutdown. Restart and select Ubuntu.

---

### Post by winit_gal on 2007-05-11
Thank you very much! =) That worked like a charm and it's up and running. 
Although- I can't seem to connect to my wireless network; it detects it (among others), and prompts me for my WEP key, notifies me that I have a percentage of connectablility, but then fails to load pages. 
All my other machines [OSX + WinXP + NT]  can connect to the network. The Ubuntu machine can also connect, but only when booted in Windows.

---

