---
title: "Rlogin not able to open a window"
date: 2008-03-22
forum: General Help
---

### Post by anthony_molg on 2008-03-22
Hello 
   I just built a Ubuntu Server to replace a very old Red Hat one. I have been able to get every thing running on the Ubuntu one but rlogin to one of our other servers. When you rlogin to this server there is a start up script that opens a window. But the window never opens on the Ubuntu computer. 


The startup script is in perl and below is the part in question

```
#  Declare perl modules used by this script
use Tk;			# perlTk module
use Sys::Hostname;      # module for system hostname 
use strict;		# enforces good programming practice

#**********************************************************************
#	Declare all 'global' variables here
#**********************************************************************

$main::userhost;        # user's system name
my $hostname =  hostname;

my @radio_text;		# contains array of radio button text entries
$radio_text[0] = 'A';
$radio_text[1] = 'B';
$radio_text[2] = 'C';
$radio_text[3] = 'Exit out of this menu';

# declare font ot be used in displaying text within the main window canvas
my $listfont = "-misc-fixed-medium-r-normal--14-110-100-100-c-70-iso8859-1";
#**********************************************************************

# capture user and host information
# check to insure user is logged in as `*remoteuser*`

&check_user;
$main::userhost = &set_display;
 $ENV{DISPLAY}=$main::userhost.":0.0";
 print "DISPLAY environment variable now set to $main::userhost \n";
print "DISPLAY environment variable now set to $ENV{DISPLAY}\n";
```

This is what i get when i rlogin

```
*"localuser"*@*"localcomputer"*:~$ rlogin "*remote_computer*" -l *"REMOTE_USER"*
*"REMOTE_USER"*@*"remote_computer"*'s password: 
Last login: Sat Mar 22 05:19:32 2008 from *"localcomputer"*
-bash: [: =: unary operator expected
username:* "REMOTE_USER"* is configured to use the XXX Administrator tool 
remort term = xterm 
remote host =  
DISPLAY environment variable now set to  
DISPLAY environment variable now set to :0.0
couldn't connect to display ":0.0" at /usr/lib/perl5/site_perl/5.8.6/i386-linux-thread-multi/Tk/MainWindow.pm line 55.
MainWindow->new(-title,XXX Administration Application Menu         Revision 1.2,-foreground,black,-background,light grey) at /home/*"REMOTE_USER"/"REMOTE_USER"*_startup.pl line 79
[*"REMOTE_USER"*@*"remote_computer*" ~]$ 
```

I changed user and computer names, for security. I am pretty new to Ubuntu, so i am sure it is something pretty simple. Thanks for the help.

---

### Post by anthony_molg on 2008-03-24
Could somebody point me to some reading material that might get me going??? Is there a Ubuntu for Dummies??? Do i need to install something to get rlogin to run?  Thanks

---

