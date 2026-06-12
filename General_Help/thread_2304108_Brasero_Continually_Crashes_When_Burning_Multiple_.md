---
title: "Brasero Continually Crashes When Burning Multiple Disks 14.04.3"
date: 2015-11-24
forum: General Help
---

### Post by coljohnhannibalsmith on 2015-11-24
Hello,

Whenever I use Brasero, I have to exit and relaunch it to burn multiple discs; otherwise I get a copy error. The error always happens during the final creating checksum phase. While some of the created discs appear to work correctly, I don't feel I can really trust these. To me, the failure looks like a buffer getting full, that doesn't properly clear unless I quit the app. This happens on both of my DELL laptops, 1545 & 5520 Inspirons.

Thanks, Hannibal

---

### Post by Sweet_Baby_Jamie on 2015-11-24
I'm still kinda new yet, but when Brasero kept doing that for me I tried **Xfburn** and it has worked alot more reliably.  The only other Linux user I know loves K3B which is reliable for him.  It brings in alot of KDE stuff when installed, but Xfburn doesn't.

---

### Post by coljohnhannibalsmith on 2015-11-24
> **Sweet_Baby_Jamie said:**
> I'm still kinda new yet, but when Brasero kept doing that for me I tried **Xfburn** and it has worked alot more reliably.  The only other Linux user I know loves K3B which is reliable for him.  It brings in alot of KDE stuff when installed, but Xfburn doesn't.

Thanks for the reply. I've installed it; and I will give it a try. One observation; it doesn't have disk copy capability.

Thanks, Hannibal

---

### Post by Sweet_Baby_Jamie on 2015-11-25
I would bet that **K3B** has all the bells and whistles you want, if Xfburn doesn't.

---

### Post by scdbackup on 2015-11-25
Hi,

besides the GUI, the dependencies, and the supported use cases,
K3B and Xfburn also differ by their burn backends.

K3B uses mkisofs/genisoimage for ISO 9660, cdrecord/wodim for CD,
and growisofs for DVD (and BD ?).
Xfburn uses libisofs for ISO 9660 and libburn for CD, DVD, BD.
Brasero can use either of those backends.

Normally all the backends are supposed to do a proper job.
If burner or media are on the edge of failure, their subtle
differences might decide about success, though.


> disk copy capability

If you mean copying or cloning of optical media, then Xfburn
might do the job for single-session data media, if you choose
the from-drive as "image" with the use case of image burning.

If you want to copy such a medium to an image file on hard disk,
use some shell command like

  dd if=/dev/sr0 of="$HOME"/image_of_sr0 bs=2048

to create file  "$HOME"/image_of_sr0 .
This can then be burned as image to another optical mediumi
of sufficient capacity.

With multi-session media or multi-track media or audio CD,
i am not aware that Xfburn would ask libburn to create an
according structure on the target medium.
Afaik it does not offer to add sessions to appendable media.


Have a nice day :)

Thomas

---

### Post by coljohnhannibalsmith on 2015-11-26
> **scdbackup said:**
> Hi,

besides the GUI, the dependencies, and the supported use cases,
K3B and Xfburn also differ by their burn backends.

K3B uses mkisofs/genisoimage for ISO 9660, cdrecord/wodim for CD,
and growisofs for DVD (and BD ?).
Xfburn uses libisofs for ISO 9660 and libburn for CD, DVD, BD.
Brasero can use either of those backends.

Thomas

How do I reconfigure Brasero to use libisofs for ISO 9660 and libburn for CD, DVD, BD?

Thanks, Hannibal

---

### Post by scdbackup on 2015-11-26
Hi,

Disclaimer:
I am really not an expert for operating the GUI frontends,
but rather backend programmer of libburn and libisofs.

The problem you report with Brasero does not look like a backend
problem. Afaik, Brasero does not use the checksum facility of
libisofs but rather does its own computations.

On Debian Jessie, Menu bar "Edit" has only one item "Plugins"
which pops up a window with a check list. About in the middle
of the list there are "genisoimage", "growisofs", "libburn",
"libisofs". At the end of the list is "wodim" (cdrecord clone).
"cdrdao" probably does the CD cloning.
They all are checked in my installation. Dunno which one has
precedence. Probably you would have to disable some.

With Ubuntu, chances are high that Brasero already uses libburn.
Messages in Brasero log files tell which is in effect.
One can see in the web about any combinations of one of
BraseroGenisoimage , BraseroLibisofs
and one of
   BraseroGrowisofs, BraseroLibburn, BraseroWodim

Like
  ```

  BraseroGenisoimage stderr: /usr/bin/genisoimage: Warning: Directory loop
  BraseroWodim stdout: Starting new track at sector:
  BraseroGrowisofs stderr: /dev/sr0: "Current Write Speed" is 6.1x1352KBps.
  BraseroLibburn Setting burnproof 1
  BraseroLibisofs creating volume

```

Paragraph "Reporting Bugs" in
  [https://wiki.gnome.org/Apps/Brasero](https://wiki.gnome.org/Apps/Brasero)
says one shall run it by

  ```
brasero -g --brasero-media-debug > log 2>&1
```

to get a file named "log". That's obviously what my indirect users
post when they call for help. Very verbous.
Exercise one burn session and then look in file "log" for above
line starts.


Have a nice day :)

Thomas

---

### Post by coldraven on 2015-11-27
> **Sweet_Baby_Jamie said:**
> I would bet that **K3B** has all the bells and whistles you want, if Xfburn doesn't.

+1 for K3B

---

### Post by coljohnhannibalsmith on 2015-11-27
> **coldraven said:**
> +1 for K3B

Thank you. I am using k3b; but it often has the same problem that I've been experiencing in Brasero. So far xfburn has not displayed this bahavior. This has been happening on both of my DELL laptops.

Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2015-12-02
xfburn is the best backend I've ever used, kudos devs. So far, it appears to be absolutely bug free.

---

