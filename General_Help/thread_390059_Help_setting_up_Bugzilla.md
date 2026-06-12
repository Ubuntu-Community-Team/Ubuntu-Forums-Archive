---
title: "Help setting up Bugzilla"
date: 2007-03-21
forum: General Help
---

### Post by edmicman on 2007-03-21
How the heck are you supposed to install and setup Bugzilla?  I'm on a 6.10 server install (set up as LAMP) - text only interface.  I've got to say that trying to get bugzilla set up and installed has been one of the biggest PsITA that I've tried yet.

I originally tried installing from "apt-get install bugzilla" and wrestled with that for awhile.  After finally getting my password stuff straightened out I was able to access the bugzilla install via a browser, but the default setups from the package were screwy.  So I wanted to start over and install by hand from scratch.

I downloaded the latest Bugzilla RC1 files, and they are in my /var/www/bugzilla directory.  I'm having a heck of a time getting the Perl modules to install for it and am about at wits end.  I'm running ./checksetup.pl and it shows this:

```
COMMANDS TO INSTALL:

    libwww-perl: /usr/bin/perl -MCPAN -e 'install LWP::UserAgent'
        GDGraph: /usr/bin/perl -MCPAN -e 'install GD::Graph'
     GDTextUtil: /usr/bin/perl -MCPAN -e 'install GD::Text'
    Template-GD: /usr/bin/perl -MCPAN -e 'install Template::Plugin::GD::Image'
             GD: /usr/bin/perl -MCPAN -e 'install GD'
Email-MIME-Attachment-Stripper: /usr/bin/perl -MCPAN -e 'install Email::MIME::Attachment::Stripper'
    Email-Reply: /usr/bin/perl -MCPAN -e 'install Email::Reply'
      perl-ldap: /usr/bin/perl -MCPAN -e 'install Net::LDAP'
    HTML-Parser: /usr/bin/perl -MCPAN -e 'install HTML::Parser'
  HTML-Scrubber: /usr/bin/perl -MCPAN -e 'install HTML::Scrubber'
       XML-Twig: /usr/bin/perl -MCPAN -e 'install XML::Twig'
          Chart: /usr/bin/perl -MCPAN -e 'install Chart::Base'
     PerlMagick: /usr/bin/perl -MCPAN -e 'install Image::Magick'
    PatchReader: /usr/bin/perl -MCPAN -e 'install PatchReader'
      SOAP-Lite: /usr/bin/perl -MCPAN -e 'install SOAP::Lite'
       mod_perl: /usr/bin/perl -MCPAN -e 'install mod_perl2'
```

The bugzilla documentation says something about running 
```
perl -MCPAN -e 'install "Bundle::Bugzilla"'
```

to install the needed modules.  When I do that, it goes through a bunch of stuff, but when I rerun the checksetup.pl script, nothing has changed.  If I do individual lines I get:
```
perl -MCPAN -e 'install LWP::UserAgent'
Can't locate object method "install" via package "LWP::UserAgent" at -e line 1.
```

If I keep retrying it, sometimes it will go.  But then the module installs are littered with
```
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
```

and they fail.  Nothing seems to be working.  

Granted, I consider myself a novice at best when it comes to linux in general, but I'm fairly familiar with installing web scripts on a lamp setup, though it's usually PHP/MySQL scripts.  But I would think this would be similar.  Any help or advice would be greatly appreciated!

---

### Post by edmicman on 2007-03-22
Bump?

---

### Post by darkdigger on 2007-04-15
I'm going through the same thing right now. I'm installing from 3.0RC1 and it requires a boat load of modules. You can actually install most of the required modules through apt.

To find out the name of the library you need to install, just type:
```
apt-cache search *libraryname* perl
```

That will spit out a list of matching libraries. Once you've found the library that matches the one required in the list given to you by checksetup.pl, you can install it with:
```
sudo apt-get install *packagename*
```

I've gotten them all to install with the exception of 'Email::Send.' I use the command the checksetup.pl script gives, but it terminates at the end everytime with the same error (on all the modules I try it with also)

```
    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
```

I thought I just needed to install *make*, so I went ahead and did so, but it gives the same error still. Anybody got anymore help on this?

---

### Post by Reza_Sho on 2008-06-04
I just had same issue and it was making me crazy

sudo cpan

install Bundle::CPAN 

It fixed all the issues

---

