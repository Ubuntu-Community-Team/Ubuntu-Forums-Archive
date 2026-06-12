---
title: "Using Kprinter with Firefox 3"
date: 2008-06-20
forum: General Help
---

### Post by kevin79 on 2008-06-20
I'm using the final release of Firefox 3 with Kubuntu Hardy 64bit. With FF 2.x, I was able to use Kprinter as my default printer, however, with FF 3, it doesn't work. Has anyone else had problems getting FF 3 to use Kprinter? Does anyone have it working? If so, what did you have to do to get it to work?

---

### Post by aavo on 2009-05-25
Here are the steps I took to make **kprinter** work with Firefox3:

1) The first step (inspired by a post from [http://www.linuxquestions.org/questions/linux-desktop-74/firefox-3-cannot-print-to-cups-printer-655002/](http://www.linuxquestions.org/questions/linux-desktop-74/firefox-3-cannot-print-to-cups-printer-655002/)):[INDENT]Edit the file **[FONT=Courier New]/etc/gtk-2.0/gtkrc[/FONT]** and add to the end the following line:
**[FONT=Courier New]gtk-print-backends = "lpr,file"[/FONT]**

This will make the **[FONT=Courier New]lpr[/FONT]** target appear in the Firefox print dialog.
[/INDENT]2) The second step is to switch the **[FONT=Courier New]lpr[/FONT]** command for **[FONT=Courier New]kprinter[/FONT]** command by executing:[INDENT][B][FONT=Courier New]cd `dirname \`which lpr\``
sudo mv lpr lpr.old
sudo ln -s `which kprinter` lpr[/FONT][/B]
[/INDENT]3) The third step is to get rid of the Firefox print dialog:[INDENT]Within Firefox, in [FONT=Courier New]**about:config**[/FONT] create a new Boolean option named:
[FONT=Courier New]**print.always_print_silent**[/FONT]
with value [FONT=Courier New]**true**.[/FONT]
[/INDENT]That's it. You should be done!
The only quirk I've found is that you cannot cancel the kprinter dialog - it will hang Firefox for some reason.

---

### Post by platinummonkey on 2010-04-09
[http://tamulug.tamu.edu/wiki/firefox_print_kerberos](http://tamulug.tamu.edu/wiki/firefox_print_kerberos)

this will still let your other programs print without double dialogs ;)

---

### Post by asaguiar on 2012-01-16
No need to change system files. It could affect badly other applications.

[http://asaguiar.net/modules.php?name=Reviews&rop=showcontent&id=65](http://asaguiar.net/modules.php?name=Reviews&rop=showcontent&id=65)

has a solution that avoids messing up directly with Firefox stuff and works smoothly just as if FF (all versions) had been written to KDE...

Alexandre

---

