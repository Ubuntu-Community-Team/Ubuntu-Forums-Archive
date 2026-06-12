---
title: "problems to install gkismet"
date: 2005-05-15
forum: General Help
---

### Post by tontonrico on 2005-05-15
Hello,

I want to use gkismet as frontend to Kismet. On the Warty there was no problem to install and use it, but I can not succeed on my Hoary.

Here after the error messages I have at the install :

"perl or Gtk module does not seem to be installed, gkismet probably will not work"

and of course, when I want to start gkismet :

"Can't locate Gtk.pm in @INC (@INC contains: /usr/local/lib/gkismet /etc/perl /usr/local/lib/perl/5.8.4 /usr/local/share/perl/5.8.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/local/lib/gkismet/PacketBox.pm line 27."

It seems there are some missing packages but I do not know which...

Could you please help me to find these packages ?!

Thanks in advance.

---

### Post by syltty on 2005-05-15
apf-file gives these packages with Gtk.pm:

$ apt-file search Gtk.pm

dbishell: usr/share/perl5/DBIShell/Gtk.pm
dbishell: usr/share/perl5/DBIShell/Gtk.pm
dbishell: usr/share/perl5/DBIShell/Gtk.pm
fvwm: usr/share/fvwm/perllib/FVWM/Module/Gtk.pm
fvwm: usr/share/fvwm/perllib/FVWM/Module/Gtk.pm
fvwm: usr/share/fvwm/perllib/FVWM/Module/Gtk.pm
fvwm-gnome: usr/share/fvwm/perllib/FVWM/Module/Gtk.pm
fvwm-gnome: usr/share/fvwm/perllib/FVWM/Module/Gtk.pm
fvwm-gnome: usr/share/fvwm/perllib/FVWM/Module/Gtk.pm
glade-perl: usr/share/perl5/Glade/PerlUIGtk.pm
glade-perl: usr/share/perl5/Glade/PerlUIGtk.pm
glade-perl: usr/share/perl5/Glade/PerlUIGtk.pm
libgtk-perl: usr/lib/perl5/Gtk.pm
libgtk-perl: usr/lib/perl5/Gtk.pm
libgtk-perl: usr/lib/perl5/Gtk.pm
libpoe-perl: usr/share/perl5/POE/Loop/Gtk.pm
libpoe-perl: usr/share/perl5/POE/Loop/Gtk.pm
libpoe-perl: usr/share/perl5/POE/Loop/Gtk.pm

try if sudo apt-get install libgtk-perl helps

---

### Post by tontonrico on 2005-05-15
[QUOTE=syltty]apf-file gives these packages with Gtk.pm:

$ apt-file search Gtk.pm

dbishell: usr/share/perl5/DBIShell/Gtk.pm
dbishell: usr/share/perl5/DBIShell/Gtk.pm
dbishell: usr/share/perl5/DBIShell/Gtk.pm
fvwm: usr/share/fvwm/perllib/FVWM/Module/Gtk.pm
fvwm: usr/share/fvwm/perllib/FVWM/Module/Gtk.pm
fvwm: usr/share/fvwm/perllib/FVWM/Module/Gtk.pm
fvwm-gnome: usr/share/fvwm/perllib/FVWM/Module/Gtk.pm
fvwm-gnome: usr/share/fvwm/perllib/FVWM/Module/Gtk.pm
fvwm-gnome: usr/share/fvwm/perllib/FVWM/Module/Gtk.pm
glade-perl: usr/share/perl5/Glade/PerlUIGtk.pm
glade-perl: usr/share/perl5/Glade/PerlUIGtk.pm
glade-perl: usr/share/perl5/Glade/PerlUIGtk.pm
libgtk-perl: usr/lib/perl5/Gtk.pm
libgtk-perl: usr/lib/perl5/Gtk.pm
libgtk-perl: usr/lib/perl5/Gtk.pm
libpoe-perl: usr/share/perl5/POE/Loop/Gtk.pm
libpoe-perl: usr/share/perl5/POE/Loop/Gtk.pm
libpoe-perl: usr/share/perl5/POE/Loop/Gtk.pm

try if sudo apt-get install libgtk-perl helps[/QUOTE]


Thanks, 

It is solved : I installed some (or lot of :-)) missing "devel" packages and it works correctly now.

See you

---

### Post by v1s on 2006-09-20
I belive this is the package needed:

# sudo apt-get install libgnome-perl

---

