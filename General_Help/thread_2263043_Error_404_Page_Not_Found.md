---
title: "Error 404 Page Not Found"
date: 2015-01-29
forum: General Help
---

### Post by faridzul2 on 2015-01-29
Hello and Good Day

Hi There
Im new user here.. and im using ubuntu 14.04 LTS

ok here is my problem
i already installed apache2 and mysql and configured apache2 to my document root on 000-default.conf
but i still cant access to my website.. is there any problem that can help me with this..also do i need to configured on default-ssl.conf also? 

Below here is my 000-default.conf

```
<VirtualHost *:80>
    # The ServerName directive sets the request scheme, hostname and port that
    # the server uses to identify itself. This is used when creating
    # redirection URLs. In the context of virtual hosts, the ServerName
    # specifies what hostname must appear in the request's Host: header to
    # match this virtual host. For the default virtual host (this file) this
    # value is not decisive as it is used as a last resort host regardless.
    # However, you must set it for any further virtual host explicitly.
    #ServerName www.example.com

    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/mybooking

    # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
    # error, crit, alert, emerg.
    # It is also possible to configure the loglevel for particular
    # modules, e.g.
    #LogLevel info ssl:warn

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined

    # For most configuration files from conf-available/, which are
    # enabled or disabled at a global level, it is possible to
    # include a line for only one particular virtual host. For example the
    # following line enables the CGI configuration for this host only
    # after it has been globally disabled with "a2disconf".
    #Include conf-available/serve-cgi-bin.conf
</VirtualHost>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
```



and this is my apache2.conf also i make change with this.. 

```
# This is the main Apache server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See http://httpd.apache.org/docs/2.4/ for detailed information about
# the directives and /usr/share/doc/apache2/README.Debian about Debian specific
# hints.
#
#
# Summary of how the Apache 2 configuration works in Debian:
# The Apache 2 web server configuration in Debian is quite different to
# upstream's suggested way to configure the web server. This is because Debian's
# default Apache2 installation attempts to make adding and removing modules,
# virtual hosts, and extra configuration directives as flexible as possible, in
# order to make automating the changes and administering the server as easy as
# possible.

# It is split into several files forming the configuration hierarchy outlined
# below, all located in the /etc/apache2/ directory:
#
#    /etc/apache2/
#    |-- apache2.conf
#    |    `--  ports.conf
#    |-- mods-enabled
#    |    |-- *.load
#    |    `-- *.conf
#    |-- conf-enabled
#    |    `-- *.conf
#     `-- sites-enabled
#         `-- *.conf
#
#
# * apache2.conf is the main configuration file (this file). It puts the pieces
#   together by including all remaining configuration files when starting up the
#   web server.
#
# * ports.conf is always included from the main configuration file. It is
#   supposed to determine listening ports for incoming connections which can be
#   customized anytime.
#
# * Configuration files in the mods-enabled/, conf-enabled/ and sites-enabled/
#   directories contain particular configuration snippets which manage modules,
#   global configuration fragments, or virtual host configurations,
#   respectively.
#
#   They are activated by symlinking available configuration files from their
#   respective *-available/ counterparts. These should be managed by using our
#   helpers a2enmod/a2dismod, a2ensite/a2dissite and a2enconf/a2disconf. See
#   their respective man pages for detailed information.
#
# * The binary is called apache2. Due to the use of environment variables, in
#   the default configuration, apache2 needs to be started/stopped with
#   /etc/init.d/apache2 or apache2ctl. Calling /usr/bin/apache2 directly will not
#   work with the default configuration.


# Global configuration
#

#
# ServerRoot: The top of the directory tree under which the server's
# configuration, error, and log files are kept.
#
# NOTE!  If you intend to place this on an NFS (or otherwise network)
# mounted filesystem then please read the Mutex documentation (available
# at <URL:http://httpd.apache.org/docs/2.4/mod/core.html#mutex>);
# you will save yourself a lot of trouble.
#
# Do NOT add a slash at the end of the directory path.
#
#ServerRoot "/etc/apache2"

#
# The accept serialization lock file MUST BE STORED ON A LOCAL DISK.
#
Mutex file:${APACHE_LOCK_DIR} default

#
# PidFile: The file in which the server should record its process
# identification number when it starts.
# This needs to be set in /etc/apache2/envvars
#
PidFile ${APACHE_PID_FILE}

#
# Timeout: The number of seconds before receives and sends time out.
#
Timeout 300

#
# KeepAlive: Whether or not to allow persistent connections (more than
# one request per connection). Set to "Off" to deactivate.
#
KeepAlive On

#
# MaxKeepAliveRequests: The maximum number of requests to allow
# during a persistent connection. Set to 0 to allow an unlimited amount.
# We recommend you leave this number high, for maximum performance.
#
MaxKeepAliveRequests 100

#
# KeepAliveTimeout: Number of seconds to wait for the next request from the
# same client on the same connection.
#
KeepAliveTimeout 5


# These need to be set in /etc/apache2/envvars
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}

#
# HostnameLookups: Log the names of clients or just their IP addresses
# e.g., www.apache.org (on) or 204.62.129.132 (off).
# The default is off because it'd be overall better for the net if people
# had to knowingly turn this feature on, since enabling it means that
# each client request will result in AT LEAST one lookup request to the
# nameserver.
#
HostnameLookups Off

# ErrorLog: The location of the error log file.
# If you do not specify an ErrorLog directive within a <VirtualHost>
# container, error messages relating to that virtual host will be
# logged here.  If you *do* define an error logfile for a <VirtualHost>
# container, that host's errors will be logged there and not here.
#
ErrorLog ${APACHE_LOG_DIR}/error.log

#
# LogLevel: Control the severity of messages logged to the error_log.
# Available values: trace8, ..., trace1, debug, info, notice, warn,
# error, crit, alert, emerg.
# It is also possible to configure the log level for particular modules, e.g.
# "LogLevel info ssl:warn"
#
LogLevel warn

# Include module configuration:
IncludeOptional mods-enabled/*.load
IncludeOptional mods-enabled/*.conf

# Include list of ports to listen on
Include ports.conf


# Sets the default security model of the Apache2 HTTPD server. It does
# not allow access to the root filesystem outside of /usr/share and /var/www.
# The former is used by web applications packaged in Debian,
# the latter may be used for local directories served by the web server. If
# your system is serving content from a sub-directory in /srv you must allow
# access here, or in any related virtual host.
<Directory />
    Options FollowSymLinks
    AllowOverride None
    Require all denied
</Directory>

<Directory /usr/share>
    AllowOverride None
    Require all granted
</Directory>

<Directory /var/www/>
    Options Indexes FollowSymLinks
    AllowOverride All
    Require all granted
</Directory>

#<Directory /srv/>
#    Options Indexes FollowSymLinks
#    AllowOverride None
#    Require all granted
#</Directory>




# AccessFileName: The name of the file to look for in each directory
# for additional configuration directives.  See also the AllowOverride
# directive.
#
AccessFileName .htaccess

#
# The following lines prevent .htaccess and .htpasswd files from being
# viewed by Web clients.
#
<FilesMatch "^\.ht">
    Require all denied
</FilesMatch>


#
# The following directives define some format nicknames for use with
# a CustomLog directive.
#
# These deviate from the Common Log Format definitions in that they use %O
# (the actual bytes sent including headers) instead of %b (the size of the
# requested file), because the latter makes it impossible to detect partial
# requests.
#
# Note that the use of %{X-Forwarded-For}i instead of %h is not recommended.
# Use mod_remoteip instead.
#
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %O" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
IncludeOptional conf-enabled/*.conf

# Include the virtual host configurations:
IncludeOptional sites-enabled/*.conf

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
```

[[img]http://www.hostpic.org/images/1501291242270101.png[/img]](http://www.hostpic.org/view.php?filename=1501291242270101.png)


[[IMG]http://www.hostpic.org/images/1501291240050100.png[/IMG]]("http://www.hostpic.org/view.php?filename=1501291240050100.png")

---

### Post by Peptid on 2015-01-29
Hi,

I am not an expert, but just out of curiousity, could you please try accessing 127.0.0.1/installation/index.php?

---

### Post by faridzul2 on 2015-01-29
as you can see at my picture.. already access 127.0.0.1installation/index.php but still no effect.. still error

---

### Post by Holger_Gehrke on 2015-01-29
> **faridzul2 said:**
> as you can see at my picture.. already access 127.0.0.1installation/index.php but still no effect.. still error

No, the picture shows you trying to access 'http://127.0.0.1/mybooking/installation/index.php'. Since you've configured '/var/www/mybooking' as DokumentRoot, accessing 'http://127.0.0.1' is the same as going to '/var/www/mybooking'. He wants you to try it without the 'mybooking' part in the url

---

### Post by yancek on 2015-01-29
Can you access the Apache index.html page from a browser:  [http://localhost](http://localhost)  you should get the Its working  or the Server is Alive and working.
Does the php page you are pointing to open in gedit as shown in your post?  If that's the case, your php configuration is not right and you will need to modify those entries in the apache configuration files.  After making any changes, did you restart apache?

Some info on what to look for at the site below:

[http://stackoverflow.com/questions/6245895/apache2-on-ubuntu-php-files-downloading](http://stackoverflow.com/questions/6245895/apache2-on-ubuntu-php-files-downloading)

---

### Post by Holger_Gehrke on 2015-01-29
Obviously, *something* **is** working. That error page in the picture is certainly not the stock error page, which I have in front of me in an other tab, delivered from my local apache.

---

### Post by faridzul2 on 2015-01-29
> **yancek said:**
> Can you access the Apache index.html page from a browser:  [http://localhost](http://localhost)  you should get the Its working  or the Server is Alive and working.
Does the php page you are pointing to open in gedit as shown in your post?  If that's the case, your php configuration is not right and you will need to modify those entries in the apache configuration files.  After making any changes, did you restart apache?

Some info on what to look for at the site below:

[http://stackoverflow.com/questions/6245895/apache2-on-ubuntu-php-files-downloading](http://stackoverflow.com/questions/6245895/apache2-on-ubuntu-php-files-downloading)



first its said its working on this... then i configured document root and goes to localhost/mybooking/installation/index.html

---

### Post by faridzul2 on 2015-01-29
> **Holger_Gehrke said:**
> No, the picture shows you trying to access 'http://127.0.0.1/mybooking/installation/index.php'. Since you've configured '/var/www/mybooking' as DokumentRoot, accessing 'http://127.0.0.1' is the same as going to '/var/www/mybooking'. He wants you to try it without the 'mybooking' part in the url

so what should i do.. where i wanna configured on this?

---

### Post by lisati on 2015-01-29
> **faridzul2 said:**
> so what should i do.. where i wanna configured on this?

Have you tried [noparse]http://127.0.0.1/installation/index.php[/noparse] as suggested?

---

### Post by faridzul2 on 2015-01-29
yes i tried so many times , even restart the apache2 and mysql still error on my pages.. but the icon as you can see the mouse is appear..

---

### Post by yancek on 2015-01-29
If you got the Its working for Apache message then it is the configuration of php that is the problem.  You're going to the page and instead of the php file being parsed and producing output it is opening in a text editoro.  Go to the stackoverflow link I posted above and look for the php entries you need in the apache config files.  I haven't used apache/php on Ubuntu so I can't be any more specific.

---

### Post by SeijiSensei on 2015-01-29
The most common reason why PHP files are not parsed on an Ubuntu server is that libapache2-mod-php5 is not installed.

---

