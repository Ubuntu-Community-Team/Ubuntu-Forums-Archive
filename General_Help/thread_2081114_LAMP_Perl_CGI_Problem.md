---
title: "LAMP Perl CGI Problem"
date: 2012-11-06
forum: General Help
---

### Post by Randy Schilling on 2012-11-06
I installed  libapache2-mod-perl2 and tried to configure my vhost to run 
simple perl a  file.
My default vhost file seemed to come from my installation of Apache 
configured for cgi scripts.   It contained out of the package (within <VirtualHost> ...</VirtualHost>) the following code:
```

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

```I placed a simple test file perltest.pl in /usr/lib/cgi-bin/.
The file is executable by all (chmod a+x perltest.pl).
I did a $apachectl configtest and a  $apachectl restart.
I entered  [http://rjs357.com/cgi-bin/perltest.pl](http://rjs357.com/cgi-bin/perltest.pl) 
in my browser and it responded with 

"Internal Server Error ...
The server encountered an internal error or misconfiguration..."

My error.log file reports:

[Mon Nov 05 23:13:13 2012] [error] [client 67.167.150.157] (8)Exec format error: exec of '/usr/lib/cgi-bin/perltest.pl' failed
[Mon Nov 05 23:13:13 2012] [error] [client 67.167.150.157] Premature end of script headers: perltest.pl
(The funny face is suppose to be 8 in (). Don't know what's going on here.)

Where have I gone wrong?

Thanks and grateful to have this forum, Randy

---

### Post by Lars Noodén on 2012-11-06
Ok. You made the CGI executable, that eliminates one possible source of the error.  Can you run the script via the shell?  

The next most likely thing is the [media type](http://en.wikipedia.org/wiki/Internet_media_type).  That must be the absolute very first thing that any script outputs to the web server.  Other things can come after, but it must be the first.

```

#!/usr/bin/perl                                                                 

use strict;
use warnings;

my $title=qq(It Works!);

**print qq(Content-type: text/html\n\n);**

print <<EOHTML
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta name="generator" content=
"HTML Tidy for Linux (vers 25 March 2009), see www.w3.org" />
<title>$title</title>
</head>
<body>
<h1>$title</h1>
Tue Nov  6 15:37:50 EET 2012
</body>
</html>
EOHTML

```

The type can also be "application/xhtml+xml" for HTML.

The utility [tidy](http://tidy.sourceforge.net/) can also be of help as you work.

---

### Post by Lars Noodén on 2012-11-06
If it was programming errors that caused the trouble, you can also use the module [CGI::Carp](http://search.cpan.org/~lds/CGI.pm-3.08/CGI/Carp.pm) to help debug.  It will send the errors to the web server properly.  However, while CGI::Carp is being used, it is a very good idea to have the script behind a password or otherwise blocked from the public.  Otherwise, it might give too many hints about weaknesses that can be exploited to then get local access to the server.  

```

#!/usr/bin/perl                                                                

use strict;
use warnings;
use CGI::Carp qw(fatalsToBrowser);

print qq(Content-type: text/plain\n\n);

print qq(Hello, World\n);

# here is some nonsense
xyzzy

```

---

### Post by Lars Noodén on 2012-11-06
mod_perl isn't actually needed to run plain perl CGI scripts.  You can run perl CGI scripts without it installed: perl itself is pre-installed on most systems including Linux and BSD.  mod_perl is really an accelerator to keep perl and various perl modules pre-loaded in memory.  It's very useful for sites with heavy traffic, but not necessarily needed at the beginning.

```

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        **PerlModule ModPerl::Registry**
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
                [b]SetHandler perl-script
                PerlHandler ModPerl::Registry
                PerlSendHeader On[/b]
        </Directory>
...
[b]
        <Location /perl-status>
                SetHandler perl-script
                PerlHandler +Apache2::Status
                order deny,allow
                deny from all
                allow from 127.0.0.1
        </Location>
[/b]

```

To get the status check [http://127.0.0.1/perl-status](http://127.0.0.1/perl-status) and see which modules are loaded with [http://127.0.0.1/perl-status?isa_tree](http://127.0.0.1/perl-status?isa_tree)

There is a lot of material for mod_perl, but most of it is written for Apache 1.3, and Ubuntu (and the world) has since moved on to 2.x.

---

### Post by Randy Schilling on 2012-11-06
Thanks Lars,

Your script is significantly different what I found in previous references .
(I don't know any perl code, just trying to get my system working for now.)
I ran the following from bash:
```
$ /usr/lib/cgi-bin/perltest.pl 
```Bash returned  "unknown mime type" warning and other errors.
I replaced the content of perltesl.pl with your code.
When I ran the script again I expected my browser to respond but instead
bash returned the following to the shell:
```

Content-type: text/html

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta name="generator" content=
"HTML Tidy for Linux (vers 25 March 2009), see www.w3.org" />
<title>It Works!</title>
</head>
<body>
<h1>It Works!</h1>
Tue Nov  6 15:37:50 EET 2012
</body>
</html>

```This is what I've tried so far.
I'll be looking into the rest of your suggestions.

Thanks - Randy

---

### Post by Lars Noodén on 2012-11-06
Yes, that's the output you should get if you run it from the shell.  If you call it via the cgi directory on the web server, you will get a web page.  (Secret: it's really the same text.)

---

### Post by Randy Schilling on 2012-11-06
I followed up on your mod-perl post and added that code to both my
default and rjs35 vurtual hosts.

[http://localhost/perl-status?isa_tree](http://localhost/perl-status?isa_tree) shows this:

```


       Embedded Perl version **v5.14.2** for **Apache/2.2.22** process **17046**,
      running since Tue Nov  6 09:09:37 2012     
 APR 	DynaLoader Apache2::Const 	ModPerl::Const 		DynaLoader Apache2::Log::Request 	Apache2::Log Apache2::Log::Server 	Apache2::Log Carp 	Exporter File::Basename 	Exporter File::Spec::Functions 	Exporter File::Spec 	File::Spec::Unix IO::File 	IO::Handle 	IO::Seekable 	Exporter ModPerl::Const 	DynaLoader ModPerl::Registry 	ModPerl::RegistryCooker 

```

Aside: I've been running bash as root but when I restart Apache as user rjs 
I get this error:
```

/usr/sbin/apachectl: 87: ulimit: error setting limit (Operation not permitted)
httpd not running, trying to start
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
Action 'restart' failed.
The Apache error log may have more information.


```Got to go to work.  I'll get back to this thread later.
Thanks - Randy

---

### Post by Lars Noodén on 2012-11-06
The error shows a problem with your web server's configuration.  You'll have to debug it with [apache2ctl configtest](http://manpages.ubuntu.com/manpages/precise/en/man8/apache2ctl.8.html)

Edit: actually at second look, it doesn't.

---

### Post by Randy Schilling on 2012-11-07
The  perl script you gave me is working through both my sites, localhost and rjs357.com,
using the following virtual host configuration code (also from you):
```

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        PerlModule ModPerl::Registry
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
                SetHandler perl-script
                PerlHandler ModPerl::Registry
                PerlSendHeader On
        </Directory>
        <Location /perl-status>
                SetHandler perl-script
                PerlHandler +Apache2::Status
                order deny,allow
                deny from all
                allow from 127.0.0.1
        </Location>

```If I follow our thread correctly, under this code, the perl module
is not active.   Is this correct and should we now try to use the perl module
with this script? (I'm surprised that it works through rjs357.com with the code
```

                deny from all
                allow from 127.0.0.1

```
Secondly, I'm still concerned with the following error  message which comes up
when I try to restart apache as an ordinary user,

```

/usr/sbin/apache2ctl: 87: ulimit: error setting limit (Operation not permitted)
/usr/sbin/apache2ctl: 87: ulimit: error setting limit (Operation not permitted)
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
Action 'start' failed.

```

Since the are no errors when I restart as root, doesn't this suggest that I have a
permission problem some where in my configuration?
There is a thread on this error,
[http://ubuntuforums.org/showthread.php?t=1981187](http://ubuntuforums.org/showthread.php?t=1981187),
but they do not come up with a  solution.
They relate the problem to upgrading to Ubuntu 12.04 with an active Apache server;
whereas I started with 12.04 and am building a server.
I think that I have been restarting apache as root right from the beginning 
of my work with servers and not until today did I try starting it as an ordinary user.
This means that the problem could have been there from the beginning and
I can't relate it to a particular change that I made to my configuration.

Should I just settle for restarting apache as root?

Thanks so much for your help.  Randy

---

### Post by Lars Noodén on 2012-11-07
> **Randy Schilling said:**
> 
Should I just settle for restarting apache as root?


If you want Apache to listen on ports 80 and 443 then you will have to as root, usually using sudo.  Root privilege is needed to bind to ports below 1024.  If it's a pain to keep typing the password, you can modify sudoers to allow a specific group special permissions.  This grants special permissions to users in the group "webmasters"

```

%webmasters ALL=(ALL) NOPASSWD: /usr/sbin/apache2ctl, /usr/sbin/a2enmod, /usr/sbin/a2dismod

```

mod_perl is an accelerator and not needed to run perl scripts themselves.  If you follow the instructions above in the eariler post, it will improve the performance of your scripts by keeping perl and the modules you use (e.g. CGI, Carp, etc.) in RAM.  From what I gather there are also advanced uses where you can keep persistent database connections.

---

### Post by Randy Schilling on 2012-11-07
Thanks Lars,

Using sudo is not a problem.  I've gotten use to it long ago and generally know
when its necessary or not.  I read something that left me with the impression
that sudo was not necessary to start Apache (lots of disinfor out there).
Now that I know better its ok.

Thanks again for tuning in and staying with me on this.  Randy

---

