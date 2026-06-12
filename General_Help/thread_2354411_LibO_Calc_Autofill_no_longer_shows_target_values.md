---
title: "LibO Calc Autofill no longer shows target values?"
date: 2017-03-02
forum: General Help
---

### Post by 2CV67 on 2017-03-02
Hi!
I asked this question already on Ask.LibO but got no response, so please excuse cross-posting here!

For as long as I can remember (In Excel & OOo Calc, long before LibO arrived...) using the "Autofill" method for filling cells (dragging bottom right handle) has shown a "Target Value" as the dragging continued & before releasing the mouse button.

This was doubly usefull: 
1. It provided a reminder/indication as to whether the values were incrementing or not. 
2. It enabled dragging to stop when the desired target was reached.

I recently upgraded to LibO 5.2.2.2 & this vital indication has disappeared. 
Is this a Bug or an "Improvement"?

Can I get the function back somehow?

Thanks!

---

### Post by vasa1 on 2017-03-02
> **2CV67 said:**
> ...
I recently upgraded to LibO 5.2.2.2 & this vital indication has disappeared. 
...
I have 
```
Version: 5.2.4.2
Build ID: 1:5.2.4~rc2-0ubuntu1~xenial2
CPU Threads: 2; OS Version: Linux 4.4; UI Render: default; VCL: gtk2; 
```
With that version, in **gtk2** mode, I see a sort of bubble showing the value. (gtk3 mode is a bit high on resources for me.)

I didn't notice whether what you want was present or not in earlier versions of LibO.

---

### Post by 2CV67 on 2017-03-03
Yes - that bubble is what I am looking for.
It has been present in every version of OOo Calc & LibO Calc I have (since 2004?).
I just checked & it is present in LibO4.2.8.2 which I have in Ubuntu 14.04LTS on another partition.
It appears in every tutorial I have looked at.

I think (but am not 100% sure) it was still present when I upgraded from 16.04 to 16.10 with LibO 5.2....(never checked exact reference) last month.

It certainly is no longer present in my new version:
```
Version: 5.2.2.2
Build ID: 1:5.2.2-0ubuntu2
CPU Threads: 4; OS Version: Linux 4.8; UI Render: default; 
Locale: en-GB (en_GB.UTF-8); Calc: group
```

The actual autofill still works, including incrementing (or not - if using Ctrl), just no target value before releasing the button.

Any ideas?

Maybe I should do a Bug Report...

---

### Post by vasa1 on 2017-03-03
> **2CV67 said:**
> ...
Any ideas?

Maybe I should do a Bug Report...
No harm in filing a bug!

BTW do you have *libreoffice-gtk2* or *libreoffice-gtk3* installed?

---

### Post by 2CV67 on 2017-03-03
Good question!

Synapt shows me I have:
```
libreoffice-gtk
libreoffice-gtk2
libreoffice-gtk3
```
all marked as "installed" (green square).

I have no idea how to interpret that...

---

### Post by vasa1 on 2017-03-03
> **2CV67 said:**
> Good question!

Synapt shows me I have:
```
libreoffice-gtk
libreoffice-gtk2
libreoffice-gtk3
```
all marked as "installed" (green square).

I have no idea how to interpret that...

Well, those are supposed to ensure that LibO "integrates" with the environment. On some systems, these components aren't installed by default and then things don't look pretty.

```
apt search libreoffice | grep integration

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

  office productivity suite -- GNOME integration
  office productivity suite -- GTK+ integration
  office productivity suite -- GTK+ 2 integration
  office productivity suite -- GTK+ 3.0 integration
  office productivity suite -- KDE integration
```

---

### Post by 2CV67 on 2017-03-03
Produces almost the same result for me:

```
apt search libreoffice | grep integration

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

  office productivity suite -- GNOME integration
  office productivity suite -- GTK+ 2 integration
  office productivity suite -- GTK+ 3 integration
  office productivity suite -- KDE integration

```
But I am out of my depth here...

---

### Post by 2CV67 on 2017-11-20
Since LibO 5.3.1.2 (installed Sept 20) the targets are back.
Great relief!

---

