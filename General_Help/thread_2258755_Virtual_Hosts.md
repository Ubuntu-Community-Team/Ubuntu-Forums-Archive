---
title: "Virtual Hosts"
date: 2014-12-30
forum: General Help
---

### Post by DiogoSaraiva on 2014-12-30
Hi,

Anyone can tell me what is the easiest way to configure the following:

/var/www/html/example1 > example1.no-ip.org
/var/www/html/example2 > example2.no-ip.org
/var/www/html/example3 > example3.no-ip.org

**example1 requires cgi-bin**, so "/usr/lib/cgi-bin/" will be common to all 3 sites?
or will I have "/usr/lib/cgi-bin/example1", "/usr/lib/cgi-bin/example2"... too?

Sorry for be boring and Thank you very much
and have a happy new year...

---

### Post by TheFu on 2014-12-30
[https://httpd.apache.org/docs/current/vhosts/examples.html](https://httpd.apache.org/docs/current/vhosts/examples.html) explains how to use virtualhosts.
Normally, you would create a new file for each v-host in the sites-available/ directory, then symlink those to the sites-enabled/ directory.

Each is separate, so the cgi-bin/ directory will be separate.

When using virtual-hosts under apache, the /usr/lib/ areas are generally ignore completely.

Of course, you can do whatever you like - apache configurations are very flexible.  I generally place virtual-hosts in different directories with whatever files they need (cgi, static, mod_perl, whatever) and tell apache through each individual site config file where to point.

---

### Post by DiogoSaraiva on 2014-12-30
I see that document and I don't understand how I do... Should I not use bind9???
I already added a configuration like this:
```


Listen 80
<VirtualHost *:80>
    DocumentRoot /var/www/example1
    ServerName example1.noip.org
  
</VirtualHost>


<VirtualHost *:80>
    DocumentRoot /var/www/example2
    ServerName example2.noip.org

</VirtualHost>

```

and created /var/www/example2 and /var/www/example1
but gives me a error when I restart apache:

[FONT=Menlo]----------------[/FONT]
[FONT=Menlo](98)Address already in use: AH00072: make_sock: could not bind to address [::]:80[/FONT]
[FONT=Menlo]                                                                                                     [[COLOR=#c33720]fail[/COLOR]][/FONT]
[FONT=Menlo] [COLOR=#afad24]*[/COLOR] The apache2 instance did not start within 20 seconds. Please read the log files to discover problems

----------------

[/FONT]
I don't find the log files...


[FONT=Menlo]

[/FONT]
Help me please....
Thanks

---

### Post by nerdtron on 2014-12-30
That error is not a problem of the config. It can't bind to port 80 since that port is in use by another program.
What is the output of.
```
 sudo service apache2 status
sudo netstat -tulpn
```

---

### Post by DiogoSaraiva on 2014-12-30
Now its runing whell because I delleted that info: 

```

Listen 80
<VirtualHost *:80>
    DocumentRoot /var/www/example1
    ServerName example1.noip.org
  
</VirtualHost>




<VirtualHost *:80>
    DocumentRoot /var/www/example2
    ServerName example2.noip.org


</VirtualHost>


```
however here is output of two codes you asked me:

```

[FONT=Menlo][COLOR=#34bd26]**diogosaraiva@Ubuntu**[/COLOR]:[COLOR=#5330e1]**~**[/COLOR]$ sudo service apache2 status[/FONT]
[FONT=Menlo] * apache2 is running[/FONT]
[FONT=Menlo][COLOR=#34bd26]**diogosaraiva@Ubuntu**[/COLOR]:[COLOR=#5330e1]**~**[/COLOR]$ sudo netstat -tulpn[/FONT]
[FONT=Menlo]Ligações de Internet Activas (só servidores)[/FONT]
[FONT=Menlo]Proto Recv-Q Send-Q Endereço Local          Endereço Remoto         Estado       PID/Program name[/FONT]
[FONT=Menlo]tcp        0      0 0.0.0.0:7300            0.0.0.0:*               ESCUTA      1176/perl       [/FONT]
[FONT=Menlo]tcp        0      0 192.168.1.104:27754     0.0.0.0:*               ESCUTA      1176/perl       [/FONT]
[FONT=Menlo]tcp        0      0 127.0.1.1:53            0.0.0.0:*               ESCUTA      1459/dnsmasq    [/FONT]
[FONT=Menlo]tcp        0      0 0.0.0.0:22              0.0.0.0:*               ESCUTA      925/sshd        [/FONT]
[FONT=Menlo]tcp        0      0 127.0.0.1:631           0.0.0.0:*               ESCUTA      2395/cupsd      [/FONT]
[FONT=Menlo]tcp        0      0 127.0.0.1:6010          0.0.0.0:*               ESCUTA      3403/1          [/FONT]
[FONT=Menlo]tcp6       0      0 :::80                   :::*                    ESCUTA      4372/apache2    [/FONT]
[FONT=Menlo]tcp6       0      0 :::22                   :::*                    ESCUTA      925/sshd        [/FONT]
[FONT=Menlo]tcp6       0      0 ::1:631                 :::*                    ESCUTA      2395/cupsd      [/FONT]
[FONT=Menlo]tcp6       0      0 ::1:6010                :::*                    ESCUTA      3403/1          [/FONT]
[FONT=Menlo]udp        0      0 0.0.0.0:53688           0.0.0.0:*                           485/avahi-daemon: r[/FONT]
[FONT=Menlo]udp        0      0 0.0.0.0:631             0.0.0.0:*                           1078/cups-browsed[/FONT]
[FONT=Menlo]udp        0      0 0.0.0.0:5353            0.0.0.0:*                           485/avahi-daemon: r[/FONT]
[FONT=Menlo]udp        0      0 0.0.0.0:22518           0.0.0.0:*                           1018/dhclient   [/FONT]
[FONT=Menlo]udp        0      0 127.0.1.1:53            0.0.0.0:*                           1459/dnsmasq    [/FONT]
[FONT=Menlo]udp        0      0 0.0.0.0:68              0.0.0.0:*                           1018/dhclient   [/FONT]
[FONT=Menlo]udp6       0      0 :::5353                 :::*                                485/avahi-daemon: r[/FONT]
[FONT=Menlo]udp6       0      0 :::40762                :::*                                485/avahi-daemon: r[/FONT]
[FONT=Menlo]udp6       0      0 :::10077                :::*                                1018/dhclient   [/FONT]

```

Thanks

---

### Post by TheFu on 2014-12-30
Logs are in /var/log/ somewhere - apache generally has a subdirectory.

There can only be one "Listen 80" anywhere in the apache config files.  Where it is by default depends on the apache release you are using. Think ubuntu switched from 2.2 to 2.4 so many things have changed.  What version are you trying to make work?  Remove the listen in the v-hosts file so the other one doesn't see any conflict.

Besides that you'll need settings for other directories and to make cgi-bin work.  It is a security thing not to allow scripts to run automatically from any directory without explicitly asking.

If you don't want the default website - remove the link in sites-enabled/*default.

So ... for example.... 1 vhost here:

/etc/apache2/sites-available$ more 003-nepal.conf 
```
<VirtualHost *:8181>
        ServerAdmin webmaster@localhost
        ServerName nepal.example.com
        DocumentRoot /var/www/vhosts/nepal.example.com
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/vhosts/nepal.example.com/ >
                Options +Indexes +FollowSymLinks +MultiViews +Includes
                AllowOverride None
                Order allow,deny
                allow from all
                DirectoryIndex index.html

        </Directory>

        ScriptAlias /cgi-bin/ /var/www/vhosts/nepal.example.com/cgi-bin/
        <Directory "/var/www/vhosts/nepal.example.com/cgi-bin/">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
</VirtualHost>

```
For another virtualhost - copy that and change all the "nepal" things to some other name.
You probably want to listen on port 80, not 8181 - I use a reverse proxy on another machine to control access and prevent access from some parts of the nasty internet.

Hope this all makes sense.  A concrete example usually helps.

---

### Post by DiogoSaraiva on 2014-12-31
So what I should do its create a file: /etc/apache2/sites-available/example1.conf or should be 001-example.conf?? 001-example.conf 002-otherexample.conf, etc,... for each virtual host?

with that info

only that?
Thanks

---

### Post by dragonfly41 on 2014-12-31
I have recently had to setup some virtualhosts (in localhost development) so I can give you some notes I took along the way.

Run this command to check your apache2 version

apache2 -v

If apache 2.4 check on apache site the differences in configuration migrating from apache 2.2 > apache 2.4.

Depending on version of apache2 installed your DocumentRoot might now be /var/www/html and not /var/www

In /etc/apache2/sites-available/
create a config file with multiple virtualhosts as below ... examples.conf

note: you have the option of creating one file for each virtual host.
example1.conf
example2.conf etc.

```

<VirtualHost *:80>
ServerName example1.noip.org
DocumentRoot "/var/www/html/example1"
DirectoryIndex index.html index.php

<Directory  "/var/www/html/example1">
    Options Indexes FollowSymLinks MultiViews Includes
    AddDefaultCharset UTF-8
    AllowOverride none      
    Require all granted
</Directory>

    ErrorLog /var/log/apache2/example1.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel debug
</VirtualHost>

# ======================================

<VirtualHost *:80>
ServerName example2.noip.org
DocumentRoot "/var/www/html/example2"
DirectoryIndex index.html index.php

<Directory  "/var/www/html/example2">
    Options Indexes FollowSymLinks MultiViews Includes
    AddDefaultCharset UTF-8
    AllowOverride none      
    Require all granted
</Directory>

    ErrorLog /var/log/apache2/example2.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel debug
</VirtualHost>


```


Note that the configuration line

          Require all granted

is used in apache2 version 2.4 and replaces older configuration syntax (see apache2 docs)

          Order allow,deny
          allow from all


check virtualhost configuration
apachectl -S     

check virtualhost syntax
apachectl -t   


To enable the site(s) in /etc/apache2/sites-available
run this command ...

sudo a2ensite examples.conf

this creates symlink in sites-enabled folder

sudo a2dissite examples.conf disables the virtual hosts.

Use a2ensite and a2dissite rather than deleting configuration files in folders.

Finally if testing in localhost mode add virtualhost ServerName(s) to 
/etc/hosts

127.0.0.1 localhost
127.0.0.1 example1.noip.org
127.0.0.1 example2.noip.org

Make sure that DocumentRoot (and below) has apache ownership
www-data:www-data

After any editing of virtualhost configurations they can be loaded with this command

sudo service apache2 reload

or a server restart ...

sudo service apache2 restart

...

---

### Post by TheFu on 2014-12-31
I've told you how I do it, not what you should do.  You should do what you think works best for your needs.  There are many reasons to be different and Linux is very flexible.  For example, on my newer systems, just because the default location for DocumentRoot has moved, it is easier for me to change that back to the old location than move stuff to the new default location.  Just because something is a default, that doesn't mean it is a good idea for every situation.  Only you and your brain can decide that AND take responsibility if it doesn't work as intended.

---

### Post by DiogoSaraiva on 2014-12-31
I got it working:

```

<VirtualHost *:80>
    ServerAdmin cr7akg@cr7akg.com
    ServerName dxc-cr7akg.ddns.net
    ServerName dxcluster.cr7akg.com
    DocumentRoot "/var/www/dxcluster"
    <Directory />
            Options FollowSymLinks
            AllowOverride None
    </Directory>
    <Directory "/var/www/dxcluster" >
            Options +Indexes +FollowSymLinks +MultiViews +Includes
            AllowOverride None
            Order allow,deny
            allow from all
            DirectoryIndex index.html
            
    </Directory>
    
    ScriptAlias /cgi-bin/ /var/www/dxcluster/cgi-bin/
    <Directory "/var/www/dxcluster/cgi-bin/">
            AllowOverride None
            Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
            Order allow,deny
            Allow from all
    </Directory>


    ErrorLog ${APACHE_LOG_DIR}/dxcluster-error.log
    
    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn


    CustomLog ${APACHE_LOG_DIR}/dxcluster-access.log combined
    
</VirtualHost>

```

this file in "[COLOR=#000000]/etc/apache2/sites-available/"
and I issued the command "[/COLOR][COLOR=#000000]sudo a2ensite dxcluster.conf"
and then "[/COLOR]sudo service apache2 restart"

unfortunately this is not working:
[http://dxcluster.cr7akg.com/cgi-bin/spider.cgi](http://dxcluster.cr7akg.com/cgi-bin/spider.cgi)

and I don know why, because I already in java configuration put my site in white list but when I click in connect does nothing....
you can try with my login:
login: cr7akg
no enter passwd

Thanks

---

### Post by TheFu on 2014-12-31
CGI doesn't care which language a program is written in.  Java will be **extremely slow** due to the high startup costs of a process in java.

Which version of apache you are running?  Some settings have chnged.
Be certain to carefully read what @dragonfly41 wrote and make those changes, if needed, for your situation.

---

### Post by dragonfly41 on 2014-12-31
(1) what is output from this command .. apache2 -v

(2) what does your log file show .. 
ErrorLog ${APACHE_LOG_DIR}/dxcluster-error.log

you could try setting log file to debug mode.

---

### Post by DiogoSaraiva on 2014-12-31
my apache is 2.4.7
I think that the problem is not from apache but from the applets (are not signed, are old...)
you can take a look:
[http://dxcluster.cr7akg.com/client/](http://dxcluster.cr7akg.com/client/)
and
cgi file is here:
```

[FONT=Menlo]#!/usr/bin/perl[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]# cluster-web.pl - perl login script for cluster web interface.[/FONT]
[FONT=Menlo]# @author Ian Norton [/FONT]
[FONT=Menlo]# - Based on clx-web by DL6DBH (ftp://clx.muc.de/pub/clx/clx-java_10130001.tgz)[/FONT]
[FONT=Menlo]# - Modified by PA4AB[/FONT]
[FONT=Menlo]# @version 0.2 beta.  20020519.[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]# Work out the hostname of this server.[/FONT]
[FONT=Menlo]use Sys::Hostname;[/FONT]
[FONT=Menlo]my $HOSTNAME = hostname();[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]# Please note that the HOSTNAME MUST be resolvable from the user end. Otherwise the[/FONT]
[FONT=Menlo]# web interface will NOT work.[/FONT]
[FONT=Menlo]# Uncomment and set the hostname manually here if the above fails.[/FONT]
[FONT=Menlo]# $HOSTNAME = "dxcluster.cr7akg.com" ;[/FONT]
[FONT=Menlo]$PORT = "7300" ;[/FONT]
[FONT=Menlo]$NODECALL = "CR7AKG-2" ;[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]# Send text/html header to the browser.[/FONT]
[FONT=Menlo]print "Content-type: text/html\n\n";[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]# Get the parameters passed to the script.[/FONT]
[FONT=Menlo]read (STDIN, $post_data, $ENV{CONTENT_LENGTH});[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]$callstart = index($post_data, "=") + 1 ;[/FONT]
[FONT=Menlo]$callend = index($post_data, "&") ;[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]$call = substr($post_data, $callstart, $callend - $callstart), [/FONT]
[FONT=Menlo]$password = substr($post_data, index($post_data, "=", $callend) + 1, length($post_data)) ;[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]# Print the page header.[/FONT]
[FONT=Menlo]#print("Callsign : $call") ;[/FONT]
[FONT=Menlo]#print("Password : $password") ;[/FONT]
[FONT=Menlo]print <<'EOF';[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0//EN">[/FONT]
[FONT=Menlo]<HTML LANG="EN">[/FONT]
[FONT=Menlo]    <HEAD>[/FONT]
[FONT=Menlo]        <TITLE>CR7AKG - DX Cluster Web Interface.</TITLE>[/FONT]
[FONT=Menlo]        <META HTTP-EQUIV="content-type" CONTENT="text/html; charset=ISO-8859-1">[/FONT]
[FONT=Menlo]        <META NAME="Author" CONTENT="Ian Norton.">[/FONT]
[FONT=Menlo]        <META NAME="DESCRIPTION" CONTENT="DX Cluster web interface">[/FONT]
[FONT=Menlo]    </HEAD>[/FONT]

[FONT=Menlo]<BODY BGCOLOR="#FFFFFF" LINK="#008080" ALINK="#000099" VLINK="#000099">         [/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]    <H1>[/FONT]
[FONT=Menlo]    <CENTER>[/FONT]
[FONT=Menlo]        <FONT FACE="arial, helvicta" COLOR="#008080" SIZE=+2>[/FONT]
[FONT=Menlo]        <B><BR>CR7AKG - DX Cluster Web Interface.</B><BR>[/FONT]
[FONT=Menlo]EOF[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]        print("Welcome!<BR>") ;[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]print <<'EOF';[/FONT]
[FONT=Menlo]        </FONT>[/FONT]
[FONT=Menlo]    </CENTER>[/FONT]
[FONT=Menlo]    </H1>[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]<BR CLEAR="ALL">[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]<HR>[/FONT]
[FONT=Menlo]EOF[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]if($ENV{CONTENT_LENGTH} > 0)[/FONT]
[FONT=Menlo]    {[/FONT]
[FONT=Menlo]    # Callsign is set - print the whole <APPLET> stuff....[/FONT]
[FONT=Menlo]    # print("Callsign is $call<BR>\n") ;[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]    print("<CENTER>\n") ;[/FONT]
[FONT=Menlo]    print("    <APPLET CODE=\"spiderclient.class\" CODEBASE=\"/client/\" width=800 height=130>\n") ;[/FONT]
[FONT=Menlo]    print("        <PARAM NAME=\"CALL\" VALUE=\"$call\">\n") ;[/FONT]
[FONT=Menlo]    print("        <PARAM NAME=\"PASSWORD\" VALUE=\"$password\">\n") ;[/FONT]
[FONT=Menlo]    print("        <PARAM NAME=\"HOSTNAME\" VALUE=\"$HOSTNAME\">\n") ;[/FONT]
[FONT=Menlo]    print("        <PARAM NAME=\"PORT\" VALUE=\"$PORT\">\n") ;[/FONT]
[FONT=Menlo]    print("        <PARAM NAME=\"NODECALL\" VALUE=\"$NODECALL\">\n") ;[/FONT]
[FONT=Menlo]    print("    </APPLET>\n") ;[/FONT]
[FONT=Menlo]    print("</CENTER>\n") ;[/FONT]
[FONT=Menlo]    }[/FONT]
[FONT=Menlo]else[/FONT]
[FONT=Menlo]    {[/FONT]
[FONT=Menlo]    # Callsign isn't set - print the login page.[/FONT]
[FONT=Menlo]    print <<'EOF';[/FONT]
[FONT=Menlo]    <CENTER>[/FONT]
[FONT=Menlo]    <FORM METHOD=POST>[/FONT]
[FONT=Menlo]        <STRONG>Please enter your callsign: </STRONG><BR>[/FONT]
[FONT=Menlo]        <INPUT name="call" size=10><BR>[/FONT]
[FONT=Menlo]        <STRONG>Please enter your password: </STRONG><BR>[/FONT]
[FONT=Menlo]        <INPUT name="password" size=10 TYPE=PASSWORD><BR>[/FONT]
[FONT=Menlo]        <INPUT type=submit value="Click here to Login">[/FONT]
[FONT=Menlo]    </FORM>[/FONT]
[FONT=Menlo]    <BR>If you do not have a password set - don't enter one :)[/FONT]
[FONT=Menlo]    </CENTER>[/FONT]
[FONT=Menlo]EOF[/FONT]
[FONT=Menlo]    }[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]print <<'EOF';[/FONT]
[FONT=Menlo]<HR>[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]<ADDRESS>[/FONT]
[FONT=Menlo]<A HREF="telnet://dxcluster.cr7akg.com:7300">Connect via Telnet</A>: telnet dxcluster.cr7akg.com 7300[/FONT]
[FONT=Menlo]</HTML>[/FONT]
[FONT=Menlo]<ADDRESS>[/FONT]
[FONT=Menlo]<A HREF="http://www.cr7akg.com/">CR7AKG HomePage</A>[/FONT]
[FONT=Menlo]</HTML>[/FONT]
[FONT=Menlo]<ADDRESS>[/FONT]
[FONT=Menlo]<A HREF="http://www.dxcluster.org/">Spider HomePage</A>[/FONT]
[FONT=Menlo]</HTML>[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]EOF[/FONT]


```

---

### Post by dragonfly41 on 2014-12-31
Since you are using apache 2.4.7 you will need to replace
[INDENT]Order allow,deny
allow from all
[/INDENT]

with ...
[INDENT]Require all granted
[/INDENT]

and then check again your virtualhosts ...

check virtualhost configuration
apachectl -S

check virtualhost syntax
apachectl -t 


and .. sudo service apache2 restart

Do you have ownership ... www-data:www-data .. throughout DocumentRoot?

Is perl script executable?

Can you run perl script on command line?

More info here ...

[http://perlmaven.com/perl-cgi-script-with-apache2](http://perlmaven.com/perl-cgi-script-with-apache2)

---

### Post by DiogoSaraiva on 2014-12-31
yes the script is executable, at least in the site:
[http://dxcluster.cr7akg.com/cgi-bin/spider.cgi](http://dxcluster.cr7akg.com/cgi-bin/spider.cgi)

```

[COLOR=#5330E1][FONT=Menlo][COLOR=#34bd26]**diogosaraiva@Ubuntu**[/COLOR][COLOR=#000000]:[/COLOR]**/var/www/dxcluster/cgi-bin**[COLOR=#000000]$ apachectl -S[/COLOR][/FONT][/COLOR]
[FONT=Menlo]VirtualHost configuration:[/FONT]
[FONT=Menlo]*:80                   is a NameVirtualHost[/FONT]
[FONT=Menlo]         default server Ubuntu (/etc/apache2/sites-enabled/000-default.conf:1)[/FONT]
[FONT=Menlo]         port 80 namevhost Ubuntu (/etc/apache2/sites-enabled/000-default.conf:1)[/FONT]
[FONT=Menlo]         port 80 namevhost cr7akg.ddns.net (/etc/apache2/sites-enabled/cr7akg.conf:1)[/FONT]
[FONT=Menlo]         port 80 namevhost dxcluster.cr7akg.com (/etc/apache2/sites-enabled/dxcluster.conf:1)[/FONT]
[FONT=Menlo]ServerRoot: "/etc/apache2"[/FONT]
[FONT=Menlo]Main DocumentRoot: "/var/www"[/FONT]
[FONT=Menlo]Main ErrorLog: "/var/log/apache2/error.log"[/FONT]
[FONT=Menlo]Mutex default: dir="/var/lock/apache2" mechanism=fcntl [/FONT]
[FONT=Menlo]Mutex mpm-accept: using_defaults[/FONT]
[FONT=Menlo]Mutex watchdog-callback: using_defaults[/FONT]
[FONT=Menlo]PidFile: "/var/run/apache2/apache2.pid"[/FONT]
[FONT=Menlo]Define: DUMP_VHOSTS[/FONT]
[FONT=Menlo]Define: DUMP_RUN_CFG[/FONT]
[FONT=Menlo]Define: ENABLE_USR_LIB_CGI_BIN[/FONT]
[FONT=Menlo]User: name="www-data" id=33 not_used[/FONT]
[FONT=Menlo]Group: name="www-data" id=33 not_used[/FONT]
[COLOR=#5330E1][FONT=Menlo][COLOR=#34bd26]**diogosaraiva@Ubuntu**[/COLOR][COLOR=#000000]:[/COLOR]**/var/www/dxcluster/cgi-bin**[COLOR=#000000]$ apachectl -t[/COLOR][/FONT][/COLOR]
[FONT=Menlo]Syntax OK[/FONT]
[COLOR=#5330E1][FONT=Menlo][COLOR=#34bd26]**diogosaraiva@Ubuntu**[/COLOR][COLOR=#000000]:[/COLOR]**/var/www/dxcluster/cgi-bin**[COLOR=#000000]$[/COLOR][/FONT][/COLOR]

```

"[COLOR=#000000]Do you have ownership ... www-data:www-data .. throughout DocumentRoot?
[/COLOR]
How I know? I didn't understanded.
This Ubuntu is only mine... is this what you want know...

Thanks

---

### Post by dragonfly41 on 2014-12-31
First, on the subject of using /var/www as DocumentRoot instead of 2.4 change to /var/www/html

read this .. [http://askubuntu.com/questions/448944/where-to-place-my-local-website-starting-with-the-2-4-7-version-of-apache2](http://askubuntu.com/questions/448944/where-to-place-my-local-website-starting-with-the-2-4-7-version-of-apache2)

particularly since you have 000-default.conf enabled.

You might prefer to move to new DocumentRoot /var/www/html and edit your virtualhost files again.

i.e. move /var/www/<contents> to /var/www/html/<contents>

...

Second, apache2 uses www-data as ownership of DocumentRoot.  You should be able to search "www-data" to find how to change ownership.

See reference to www-data in your posted output (last post) from command [COLOR=#5330E1][FONT=Menlo][COLOR=#000000].. apachectl -S[/COLOR][/FONT][/COLOR]
..

Third, you have not posted the error log output as requested.

...

[later edit]

Often I use an editor .. geany .. in sudo mode and when I save edited files into DocumentRoot I have to always reset ownership to www-data:www-data instead of root:root.

I use Krusader as my file manager (it is in repo) and I can just right click on a file and choose Properties > Permissions and then set to
User:   www-data
Group: www-data

Under Krusader > Tools there is "Start Root Mode Krusader".

---

### Post by Lars Noodén on 2014-12-31
> **DiogoSaraiva said:**
> Do you have ownership ... www-data:www-data .. throughout DocumentRoot?


There is a user and group "www-data" it is sometimes mistakenly granted to web directories.  If that happened, then it had to be undone, but if you didn't change the ownership of the directories, then that is nothing to worry about.  The user/group exists to limit access for the web server processes.  The web server processes should (most of the time) get only read access to the web pages and only specific files or directories 

Though the CGI scripts could be moved outside the DocumentRoot.  If you have web pages in /var/www/dxcluster/html/ then you could have scripts in /var/www/dxcluster/cgi-bin/ and not have a directory "/var/www/dxcluster/html/cgi-bin" because that would give read access to your scripts to the public.

---

### Post by DiogoSaraiva on 2014-12-31
> **dragonfly41 said:**
> First, on the subject of using /var/www as DocumentRoot instead of 2.4 change to /var/www/html

read this .. [http://askubuntu.com/questions/448944/where-to-place-my-local-website-starting-with-the-2-4-7-version-of-apache2](http://askubuntu.com/questions/448944/where-to-place-my-local-website-starting-with-the-2-4-7-version-of-apache2)

particularly since you have 000-default.conf enabled.

You might prefer to move to new DocumentRoot /var/www/html and edit your virtualhost files again.

i.e. move /var/www/<contents> to /var/www/html/<contents>



I disabled the 000-default.conf:

```

[FONT=Menlo][COLOR=#34bd26]**diogosaraiva@Ubuntu**[/COLOR]:[COLOR=#5330e1]**~**[/COLOR]$ sudo a2dissite 000-default.conf[/FONT]
[FONT=Menlo]Site 000-default disabled.[/FONT]
[FONT=Menlo]To activate the new configuration, you need to run:[/FONT]
[FONT=Menlo]  service apache2 reload[/FONT]
[FONT=Menlo][COLOR=#34bd26]**diogosaraiva@Ubuntu**[/COLOR]:[COLOR=#5330e1]**~**[/COLOR]$ sudo service apache2 restart[/FONT]
[FONT=Menlo] * Restarting web server apache2                                                                            [ OK ] [/FONT]
[COLOR=#34BD26][FONT=Menlo]**diogosaraiva@Ubuntu**[COLOR=#000000]:[/COLOR][COLOR=#5330e1]**~**[/COLOR][COLOR=#000000]$ [/COLOR][/FONT][/COLOR]

```

> **dragonfly41 said:**
> 
[COLOR=#000000]Third, you have not posted the error log output as requested.[/COLOR]

sorry here is:

```

[FONT=Menlo][COLOR=#34bd26]**diogosaraiva@Ubuntu**[/COLOR]:[COLOR=#5330e1]**/**[/COLOR]$ cat /var/log/apache2/dxcluster-error.log[/FONT]
[FONT=Menlo][Wed Dec 31 14:14:26.978738 2014] [cgi:error] [pid 4075] [client 85.240.233.8:63522] script not found or unable to stat: /var/www/dxcluster/cgi-bin/spider.cgi, referer: http://dxcluster.cr7akg.com/english.html[/FONT]
[FONT=Menlo][Wed Dec 31 15:37:49.929439 2014] [cgi:error] [pid 4077] [client 85.240.233.8:59004] attempt to invoke directory as script: /var/www/dxcluster/cgi-bin/[/FONT]

```
the first error was my mistake, i forget to create the file spider.cgi
the second was me too attempting to access [http://dxcluster.cr7akg.com/cgi-bin/](http://dxcluster.cr7akg.com/cgi-bin/) 

> **dragonfly41 said:**
> 
[COLOR=#000000]Often I use an editor .. geany .. in sudo mode and when I save edited files into DocumentRoot I have to always reset ownership to www-data:www-data instead of root:root.[/COLOR]

I use geany too... but over ssh (ssh **-Y** diogosaraiva@Ubuntu) I use often ssh to control my ubuntu...

ownership =~= permissions???

If yes can I issue a command:

sudo chown -R www-data:www-data {directory}

I will do that, its ok??

Thanks

---

### Post by dragonfly41 on 2014-12-31
> sudo chown -R www-data:www-data {directory}

That works for me .. but in localhost development mode ..

for production setup read earlier post from Lars Noodén

> There is a user and group "www-data" it is sometimes mistakenly granted  to web directories.  If that happened, then it had to be undone,

I understand from above that more security tweaks are needed for usage on remote server. Perhaps someone else can advise .. or read up on permissions/ownership of DocumentRoot.

Does your cgi perl script work in command line .. not through remote server?

---

### Post by DiogoSaraiva on 2014-12-31
Hi,
I got all working, thank you very much to all...
I created a jar file with the content of "client" folder with "jar cvf spiderclient * " and signed it with "sudo jarsigner -keystore ~/.myKeyStore spiderclient.jar DiogoSaraiva"

previous commands was:
[FONT=Menlo]keytool -genkey -keystore ~/.myKeyStore -alias DiogoSaraiva
[/FONT]
[FONT=Menlo]keytool -selfcert -keystore ~/.myKeyStore -alias DiogoSaraiva[/FONT]


Now its running, only need add my site in java security exception list... (white list)

Thanks to all....
and a happy new year...

---

