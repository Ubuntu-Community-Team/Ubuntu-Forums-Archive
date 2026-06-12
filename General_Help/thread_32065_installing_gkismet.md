---
title: "installing gkismet"
date: 2005-05-05
forum: General Help
---

### Post by psilo on 2005-05-05
I've been using Ubuntu for all of about 4 hours now.  I'm having a problem installing gkismet.  I couldn't find it in Synaptic so I figured I'd give it a shot on my own and, of course, it didn't work.  When I ran make install one of the first lines to scroll across my screen was:

[INDENT]perl or Gtk module does not seem to be installed, gkismet probably will not work, installing anyway...[/INDENT] 

When I tried to run it, I got:

[INDENT]Can't locate Gnome.pm in @INC (@INC contains: /usr/local/lib/gkismet /etc/perl /usr/local/lib/perl/5.8.4 /usr/local/share/perl/5.8.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/local/lib/gkismet/GKismetApplication.pm line 27.
BEGIN failed--compilation aborted at /usr/local/lib/gkismet/GKismetApplication.pm line 27.
Compilation failed in require at /usr/local/bin/gkismet line 25.
BEGIN failed--compilation aborted at /usr/local/bin/gkismet line 25.[/INDENT] 

I went searching thru Synaptic for perl and Gtk module and got tons of results.  I have no idea which one(s) I'm supposed to install to get gkismet to work.

Other than that, Ubuntu seems to work beautifully on my laptop.  Even suspend works!

---

### Post by poofyhairguy on 2005-05-06
[QUOTE=psilo]I've been using Ubuntu for all of about 4 hours now.  I'm having a problem installing gkismet.  I couldn't find it in Synaptic so I figured I'd give it a shot on my own and, of course, it didn't work.  When I ran make install one of the first lines to scroll across my screen was:

[INDENT]perl or Gtk module does not seem to be installed, gkismet probably will not work, installing anyway...[/INDENT] 

When I tried to run it, I got:

[INDENT]Can't locate Gnome.pm in @INC (@INC contains: /usr/local/lib/gkismet /etc/perl /usr/local/lib/perl/5.8.4 /usr/local/share/perl/5.8.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/local/lib/gkismet/GKismetApplication.pm line 27.
BEGIN failed--compilation aborted at /usr/local/lib/gkismet/GKismetApplication.pm line 27.
Compilation failed in require at /usr/local/bin/gkismet line 25.
BEGIN failed--compilation aborted at /usr/local/bin/gkismet line 25.[/INDENT] 

I went searching thru Synaptic for perl and Gtk module and got tons of results.  I have no idea which one(s) I'm supposed to install to get gkismet to work.

Other than that, Ubuntu seems to work beautifully on my laptop.  Even suspend works![/QUOTE]


I figured it out tonight. You need the 

libgnome-perl

package....

---

### Post by psilo on 2005-05-06
That did the trick.  Thanks.

---

### Post by alanhaggai on 2008-02-24
Thank you very much. :D

---

### Post by fackie on 2008-07-11
Hi there,

This thread is probably way outdated and maybe that is the reason why I cannot get my problem resolved.

I too am getting the above issues when installing gkismet.

When running the recommended command, I get the following:

# sudo apt-get install libgnome-perl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libgnome-perl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libgnome-perl has no installation candidate

So I guess this package would probably be deprecated by now. Any idea what has superseded it?

I am running Hardy 8.04.

Thanks,

fck

---

