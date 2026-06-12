---
title: "How to lock keyboard/mouse?"
date: 2008-06-30
forum: General Help
---

### Post by p.becks on 2008-06-30
Hello,

I am looking for a way to lock the keyboard/mouse in Ubuntu WITHOUT loosing the view on the desktop (so NO screensaver should start to run!)

(in Windows Xp i´ve got toddler-trap which i sortha like what i am looking for)

Anyone?:)

---

### Post by Rhubarb on 2008-06-30
After having a look through the Ubuntu repositories, I can't find / don't know of any programs that is equivalent to this.
Best of luck.

---

### Post by ajmorris on 2008-06-30
hi there,
i havnt tried all these, so dunno which ones blank out the screen, but here is a list of some of the screen locking apps:

xtrlock
xautolock
slock
alock
vlock

Hopefully one of those doesnt blank out the screen,

AJ

---

### Post by p.becks on 2008-06-30
Hello,

I found that this perl-script works best for my needs.



#!/bin/env perl


use warnings;

use strict;

use Data::Dumper;

my $datemod="2006/05/25";

my $defaultpassword="end";

my $progname=$0;

$progname =~ s%.*/%%g;



sub usage($)

{

  my ($exitcode)=@_;



  print STDERR <<END_OF_USAGE ;

usage for $progname

$progname [-xy=XX,YY]

			  [-p|password thepassword]

			  [-stars|-visible|-visible=maxlen]

			  [-message]

			  [-help]



$progname was written by:Chris Sincock 

(this version $datemod)

Copyright (C) 2006 Chris Sincock



This is free software; see the GNU GPL license for copying conditions.

There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR

A PARTICULAR PURPOSE





If you specify -password or -stars it will default to not telling you

 what password to type

If you don't specify -password or -stars or -vis, it will tell you

 what password to type and the password will be $defaultpassword



You can clear whatever has already been typed by hitting <Return>

END_OF_USAGE



  exit($exitcode);

}





my $password=$defaultpassword;

my $message="Type the password to quit\n:";

my $true=1;

my $false=0;

my $noshow=$true;

my $maxshownlength=30;

my $defaults_changed=$false;

my $defaults_changed_vis=$false;



my @startpos=(0,0);



while (@ARGV)

{

  my $arg=shift @ARGV;

  if($arg =~ /^-xy=(\d+),(\d+)$/i)

  {

    @startpos=($1,$2);

  }

  elsif($arg =~ /^(-|--)(h|help|usage|[?])$/i)

  {

    usage(0);

  }

  elsif($arg =~ /^(-|--)(p|pass|password)$/i)

  {

    if(!@ARGV)

    {

      print STDERR "missing argument\n";

      usage(-1);

    }

    $password=shift @ARGV;

    $defaults_changed=$true;

  }

  elsif($arg =~ /^(-|--)(s|stars)$/i)

  {

    $noshow="stars";

    $defaults_changed=$true;

  }

  elsif($arg =~ /^(-|--)(v|vis|visible)(=(\d+)|)$/i)

  {

    $noshow=$false;

    if(length($4))

    {

      $maxshownlength=$4;

    }

    $defaults_changed=$true;

    $defaults_changed_vis=$true;

  }

  elsif($arg =~ /^(-|--)(m|msg|message)$/i)

  {

    if(!@ARGV)

    {

      print STDERR "missing argument\n";

      usage(-1);

    }

    $message=shift @ARGV;

    if(length($message))

    {

      $message.="\n";

    }

    $defaults_changed=$true;

  }

  else

  {

    usage(-1);

  }

}

if(!$defaults_changed)

{

  $noshow=$false;

}

if((!$defaults_changed || $defaults_changed_vis))

{

  $message="Type '$password' to quit\n";

}



use Gtk2 -init;

my $w  = new Gtk2::Window -popup;

my $l  = new Gtk2::Label $message;

my $eb = new Gtk2::EventBox;

my $gdkwin;

my $grabstatus;

my $typed="";



sub do_grab()

{

  $grabstatus= Gtk2::Gdk->keyboard_grab(

      $gdkwin,$true,Gtk2::Gdk::X11->get_server_time($gdkwin) );

  if($grabstatus ne "success")

  {

    $l->set_text("keyboard grab failed");

  }

}



sub do_ungrab()

{

  Gtk2::Gdk->keyboard_ungrab(Gtk2::Gdk::X11->get_server_time($gdkwin));

}



sub do_keypress(@)

{

  my ($widg,$evt)=@_;

  my $kv = $evt->keyval;

  my $cs = Gtk2::Gdk->keyval_name($kv);



  if($cs =~ /Return|Enter/)

  {

    if($typed eq $password)

    {

      do_ungrab();

      Gtk2->main_quit;

    }

    else

    {

      $typed="";

    }

  }

  elsif(length($cs) == 1 && $cs =~ /[[:print:]]/)

  {

    $typed .= $cs;

  }

  my $showtyped=$typed;

  if($noshow eq "stars")

  {

    $showtyped =~ s/[^*]/*/g;

  }

  elsif($noshow)

  {

    $showtyped="";

  }

  if(length($showtyped) > $maxshownlength)

  {

    $showtyped=substr($showtyped,0,$maxshownlength);

  }

  $l->set_text($message.$showtyped);

}

$w->add($eb);

$eb->add($l);

$w->add_events( [ qw(key_press_mask) ]);

$w->signal_connect('key_press_event', \&do_keypress);

$w->signal_connect('realize', sub { $w->window->move(@startpos); });

$w->signal_connect('map', sub { $gdkwin=$w->window; do_grab(); });

$w->show_all;

Gtk2->main;


I renamed it Babylock.pl but it had a different name.

---

### Post by p.becks on 2008-06-30
Tried it some more... I didn´t like it. I can still start up things with the mouse...

---

### Post by howaboutthisone on 2008-07-12
> **p.becks said:**
> Tried it some more... I didn´t like it. I can still start up things with the mouse...

Hi,
I am the author of the program which was pasted in above. It's called lock-keyboard-for-baby, and it now has mouse locking support (thanks to a patch someone sent me). 
So you could get the current version and try the '-withmouse' option.
The URL with the new version is: [http://frobland.jamfisted.net/lock-keyboard-for-baby.htm](http://frobland.jamfisted.net/lock-keyboard-for-baby.htm)

however keep in mind it's a not written with security in mind, just protection from babies.

cheers

---

### Post by williamts99 on 2011-02-14
I use xtrlock with a keyboard shortcut, see my post #4 [http://ubuntuforums.org/showthread.php?p=10457105](http://ubuntuforums.org/showthread.php?p=10457105)

---

