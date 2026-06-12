---
title: "UTF-8 font encoding problems: US layout"
date: 2007-07-04
forum: General Help
---

### Post by chatko on 2007-07-04
Hi guys,

I think I've got UTF-8 font encoding problems which are causing me much grief.

I've installed feist fawn server edition and added xubuntu-desktop.  After reboot I get to the session login screen and if i log into the xubuntu desktop I get the following messages: (the gnome failsafe works fine)

.xsession-error log:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "chatko"
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/startxfce4: X server already running on display :0
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: This build doesn't include support for XF86Misc extension
** Message: Querying Xkb extension
** Message: Xkb extension found
Warning:          No symbols defined for <SYRQ> (keycode 92)
Warning:          No symbols defined for <II65> (keycode 101)
Warning:          No symbols defined for <BRK> (keycode 114)

I also get these "symbols" anytime I use synaptic package manager or apt install. 

For example:

Selecting previously deselected package tea-data.
(Reading database ... 99471 files and directories currently installed.)
Unpacking tea-data (from .../tea-data_14.2.4-2ubuntu1_all.deb) ...
Selecting previously deselected package tea.
Unpacking tea (from .../tea_14.2.4-2ubuntu1_i386.deb) ...
Setting up gnome-session (2.18.0-0ubuntu3) ...
/usr/share/gconf/schemas/gnome-session.schemas:1049: parser error : Input is not proper UTF-8, indicate encoding !
Bytes: 0xEE 0x29 0xBA 0xEE
            \ufffd)\ufffd\ufffd\ufffdF\ufffd\ufffd\u076d.2^\ufffd/
                            ewP\ufffd\ufffd\ufffdJ\ufffd\ufffd\ufffd}\ufffd\ufffd\ufffd+\ufffd\ufffdl\ufffd)\ufffd\ufffd\W\u4bb9\ufffd$\ufffd\ufffdG
                                                            \ufffd1QP\ufffd\ufffd(\ufffd\ufffd\ufffd[\ufffd\ufffd^
            ^
/usr/share/gconf/schemas/gnome-session.schemas:1049: parser error : PCDATA invalid Char value 21
            \ufffd)\ufffd\ufffd\ufffdF\ufffd\ufffd\u076d.2^\ufffd/
                            ewP\ufffd\ufffd\ufffdJ\ufffd\ufffd\ufffd}\ufffd\ufffd\ufffd+\ufffd\ufffdl\ufffd)\ufffd\ufffd\W\u4bb9\ufffd$\ufffd\ufffdG
                                                            \ufffd1QP\ufffd\ufffd(\ufffd\ufffd\ufffd[\ufffd\ufffd^
                    ^


Video card is geforce2 MX 400
Keyboard was auto detected to "us"
I have already set color depth to 16.

Any ideas of what I could try? Thanks

---

