---
title: "permeo socks client"
date: 2007-02-26
forum: General Help
---

### Post by rowdy15 on 2007-02-26
Hello everyone,
I am an absolute NOOB at ubuntu (well Linux in general) but I have quite a specific question
that may or may not be answerable on this forum..........


I have installed a "permeo security socks client" on Ubuntu 6.10 (Edgy Eft) which will hopefully help me to use other programs at the university that I attend.

I quite simply want to know if it is possible to find out all the commands that will help me use the  "permeo security socks client" because at the moment the socks client which is installed and going, however I don't know how to tell the socks client when im in at university or when i am at home, as this is imperative for the use and access of other programs to the internet.........

I have the writing from a file below that may be the manual of some sort but I can't work out how to deduce what it is saying...........it does say at one point about being able to list the clients commands but i don't know how to do this have a look and see if you can make sense of it 

.TH clientproxy 1 "29 Aug 2002"
.SH NAME
clientproxy - Dynamically socks-enables applications 
.SH SYNOPSIS
clientproxy \fI options program-name\fP
.SH DESCRIPTION
clientproxy ensures that the linker uses the Permeo shared library when you link at runtime. clientproxy only works if you dynamically link, and the operating system supports all the clientproxy features.
.PP
The Security Driver requires a license key in its settings file. The install script sets the key in INSTALLDIR/etc/clientproxy.conf. The Driver settings file serves a crucial role in ensuring that socks-enabled applications work as expected. Please refer to the clientproxy.conf(5) man page for additional information about the Driver's settings file.
.PP
.SH WARNINGS
clientproxy searches for its settings file in the file identified in the --filename command line option. When you omit the command line option, clientproxy searches for the file in the path that the CLIENTPROXY_CONF environment variable defines. When it fails to locate its settings file, clientproxy fails to run.
.PP
.SH ENVIRONMENT
clientproxy supports one environment variable:
.PP
.RS 5
CLIENTPROXY_CONF=\fIpath\fP
.RE
.PP
\fIpath\fP specifies the Driver settings file. You must specify the Driver's settings file with this variable, or the --filename command line option. clientproxy does not run when it fails to find its settings file.
.PP
.SH OPTIONS
.TP
-f |--filename
Specify the Driver's settings file. When you omit this option, the Driver searches the value of the CLIENTPROXY_CONF environment variable for the settings file. The Driver fails to start when it cannot find its settings file.
.TP
-h |--help
Displays a list of clientproxy command line options.
.TP
-n | --normal
Forces clientproxy to load the normal library.
.PP
.RS
clientproxy attempts to identify threaded applications. If it identifies a non-threaded application as threaded, use --normal to force clientproxy to load the normal library.
.PP
--normal and --threaded are mutually exclusive.
.RE
.TP
-ping | --ping \fIhost\fP
Uses clientproxy's built-in, socks-enabled ping program to contact \fIhost\fP. Use IP address or hostname to specify \fIhost\fP.
.TP
-t | --threaded
Forces clientproxy to load the threaded library. 
.PP
.RS
clientproxy attempts to identify threaded applications. If it fails to identify a threaded application as threaded, use --threaded to force clientproxy to load the threaded library.
.PP
--normal and --threaded are mutually exclusive.
.RE
.TP
-trace | --traceroute \fIhost\fP
Uses clientproxy's built-in, socks-enabled traceroute program to display the routers between the Driver and \fIhost\fP. Use IP address or hostname to specify \fIhost\fP.
.TP
-v | --version
Prints the clientproxy version number
.PP
.SH SEE ALSO
clientproxy.conf.(5)
libplugins.conf(5)
.PP
.SH AUTHOR
Permeo Development Team
.br
Send comments to [email]support@permeo.com[/email]


this post may be a long shot but hopefully someone will know what to do

cheers:) 

Rowdy15

---

### Post by Brunellus on 2007-02-27
I'm shunting this to general help.

---

### Post by rowdy15 on 2007-02-27
Hey Brunellus,

thanks a bunch, cos I know this is probably a bit more of a random question, so thanks

Cheers

Rowdy15

---

