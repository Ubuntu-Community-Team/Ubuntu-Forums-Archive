---
title: "VirtualBox"
date: 2007-01-26
forum: General Help
---

### Post by superami on 2007-01-26
Summary:
I'm having keyboard issues running a WinXP guest PC inside Ubuntu.  My
custom german/dvorak keyboard layout is leaking into the guest PC, but
not fully.  All the letters, numbers, and control type keys are coming
through, but most of the punctuation and umlauted letters are either on
the wrong key or acted as if they were the key directly above the tab key.

How I got Here:
Yesterday using my WinXP partition I installed VirtualBox 1.3.2 and
proceeded to install and setup a WinXP guest OS with my standard
settings.  This included German Keyboard for the install and a custom
German/Dvorak once logged in as me.  Everything worked and I was really
happy.  I also installed the VirtualPC extensions on the guest PC.

Today I install VirtualBox on Ubunt Edgy Eft 6.10.  The install and
booting of the guest WinXP image from yesterday worked.  But when I went
to login instead of the keyboard being the German default as it was when
I hosted in WinXP, it was already a partial of my custom layout.  Once
logged in the layout got even screwier. Changing the layout inside the
guest PC between standard greman and german/dvorak caused the keyboard
to get shuffled, but I was unable to get a standard German layout, or my
custom dvorak layout working 100%.  I even tried switching the Ubuntu
host PC and WinXP guest PC layouts both the english, but it didn't
correct the problem.  I also tried uninstalling the virtualpc
extensions, but this didn't fix the problem either.

Does anyone have any ideas?

I really need to be able to get this to work in Ubuntu.
I have tried Qemu, but its simply too slow, and I like the idea of a virtual machine with near full speed in both Windows and Linux, as I work in a Windows office.

---

