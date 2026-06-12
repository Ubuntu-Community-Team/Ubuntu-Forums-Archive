---
title: "Perl/Tk"
date: 2005-05-06
forum: General Help
---

### Post by Gmini on 2005-05-06
Hello,

I've made a program in Perl/Tk (I installed perl-tk with Synaptic)
I've got this error :

Tk::Error: Can't locate auto/Tk/Listbox/itemconfigu.al in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.4 /usr/local/share/perl/5.8.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl5/Tk/Derived.pm line 467

When I use this line in my code :

$buffer->itemconfigure(0,-foreground =>'yellow',-background => 'black',-selectbackground =>'black') ;

I try my program on ActivePerl (Windows) and it works fine ! I don't understand... :-| 

Please, can anyone help me ?

---

### Post by jdodson on 2005-05-06
[QUOTE=Gmini]Hello,

I've made a program in Perl/Tk (I installed perl-tk with Synaptic)
I've got this error :

Tk::Error: Can't locate auto/Tk/Listbox/itemconfigu.al in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.4 /usr/local/share/perl/5.8.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl5/Tk/Derived.pm line 467

When I use this line in my code :

$buffer->itemconfigure(0,-foreground =>'yellow',-background => 'black',-selectbackground =>'black') ;

I try my program on ActivePerl (Windows) and it works fine ! I don't understand... :-| 

Please, can anyone help me ?[/QUOTE]

right.  basically you just dont have the itemconfu.al or whatever perl module loaded.  not a big deal to fix, just synaptic search for perl tk and either install everything(which could be too much) OR search around for the module you need, ASSuming that its listed in synaptic, which it might not be.

you could google around to see if that minor module is a part of a larger TK package.  if it is, you might find that in synaptic.

---

