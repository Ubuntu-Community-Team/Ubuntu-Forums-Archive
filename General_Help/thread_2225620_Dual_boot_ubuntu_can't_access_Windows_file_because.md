---
title: "Dual boot ubuntu can't access Windows file because &quot;Windows is hibernated&quot;"
date: 2014-05-22
forum: General Help
---

### Post by fernandojosecabral on 2014-05-22
I use a dual boot linux mint with windows 8. Normally I mount the windows drive C: and manipulate de files from linux. Only on rare occasions I have to resort to Windows.
Now, I've got stormed from a blue sky: linux refuses to mount the windows hard disk with the message "Windows is hibernated, refused to mount" (full message below).

Machine is an HP Envy with UEFI. Bios is operating in legacy mode. I have disabled fast boot. It was working and stopped working even thou I have not changed anything
after install ubuntu.

Now, I have tried everything I could think of. I have reboot and shut windows down half a dozen times. But is alwas comes back as "hibernated".
Any hints on how to get rid of this for ever?

```

Error mounting /dev/sda4 at /media/fernando/E46468D66468AD4C: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda4" "/media/fernando/E46468D66468AD4C"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

```

---

### Post by sudodus on 2014-05-22
This link explained to me how to find the setting to really shut down Windows 8, hidden deep down in the menu stack

[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

---

### Post by fernandojosecabral on 2014-05-22
[SOLVED] 

Thank you for the hint. It did work (even thou the procedure is still more circunvoluted than described in the article, because
it requires administrative rights, and to get administrative right in Windows 8 is quite round about -- at least it was for me).

> **sudodus said:**
> This link explained to me how to find the setting to really shut down Windows 8, hidden deep down in the menu stack

[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

---

### Post by sudodus on 2014-05-22
I'm glad you fixed the problem with administrative permissions :KS

If your problem is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED.

---

### Post by oldfred on 2014-05-22
You mean Windows does not use something simple like sudo to grant Administrative rights? :)

       [URL="http://xkcd.com/149/"]http://xkcd.com/149/
[/URL]But the above has never worked for me. And forum rules may restrict me from usual response I get. :)

---

### Post by fernandojosecabral on 2014-05-22
> **oldfred said:**
> You mean Windows does not use something simple like sudo to grant Administrative rights? :)

       [URL="http://xkcd.com/149/"]http://xkcd.com/149/
[/URL]But the above has never worked for me. And forum rules may restrict me from usual response I get. :)

I understand. Oh, how well I do! (I am talking about the usual responses you get).

---

