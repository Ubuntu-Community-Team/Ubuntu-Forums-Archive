---
title: "Ubuntu printing letter instead of A4"
date: 2007-05-21
forum: General Help
---

### Post by ianw1974 on 2007-05-21
For some bizarre reason, Ubuntu is continually defaulting to sending print jobs with letter, even though every single option for A4 is set.

Cups is configured for A4.
The application (OpenOffice) is also configured for A4.

I ran:

```
dpkg-reconfigure libpaper1
```

and made sure it was set to A4 and I also restarted cups afterwards. I even checked /etc/papersize and this is also set to A4. Yet the system continues to send in letter meaning I have to go to the printer and press buttons to force A4.

Any ideas on why this is happening and how I can fix it?  Incidently, cups prints the printer test perfectly fine without prompting.

I'm using Ubuntu 7.04 Feisty.

---

### Post by mitch.c on 2007-05-21
What is the output from:
```
$ paperconf
```
What happens when you print from apps other than OpenOffice.org?

---

### Post by ianw1974 on 2007-05-21
The output from paperconf:

```
ian@europa:~$ paperconf
a4
```

this is also the same when ran as root.  If I print for example with gedit, it works fine.

---

### Post by ianw1974 on 2007-05-21
I think I've fixed the openoffice issue, as I've now ensured that the locale is not default but UK and I think this might have done it.

Will have to check the other apps.

---

