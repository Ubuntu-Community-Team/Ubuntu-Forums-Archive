---
title: "Saving PHP files properly"
date: 2008-01-05
forum: General Help
---

### Post by RyuKokoro on 2008-01-05
Hi,

I had a quick scout round and didn't find another topic about this so I'm posting a new one.

Anyways, here's the deal:

I'm currently working on a website and I'm using simple PHP includes:

```


<?php

include('header.html');

if(!$_SERVER['QUERY_STRING']) { ?>

<MAIN CONTENT PAGE>

<? } elseif ($_SERVER['QUERY_STRING'] == "Page2") { ?>

<ANOTHER PAGE>

<? } elseif ($_SERVER['QUERY_STRING'] == "Page3") { ?>

<AND ANOTHER PAGE>

<? }  

include('footer.html'); ?>


```

Anyhow, I saved the files I needed and uploaded them all fine and that but when I try to access them I get an error 500 Internal Server Error. I have a feeling it's something to do with the way both Bluefish and Gedit are saving the PHP files and the formatting therein is stopping the server from parsing the index.php correctly. What I need to know is, how do I save PHP files properly in Ubuntu so they parse properly? I know it's not an error on the server itself because all the PHP stuff I've uploaded already from when I had WinXP work fine. I'm pretty sure it's not my FTP program either but for the record, I'm using gFTP.

Thanks in advance for any help! :)

---

### Post by p_quarles on 2008-01-05
Just a few questions first:
1) What kind of server? Apache? IIS? Other?

2) What are your privileges on the server?

3) Do you have a PHP parser installed on your desktop machine? (I ask because if you do, it's easy to make a test file).

---

### Post by RyuKokoro on 2008-01-05
1) Apache. It's a friend's webspace.

2) I can upload PHP files and they will work providing they're formatted correctly (like they were when I was on Windows XP and I used Notepad to write them and save them with no formatting whatsoever.) I can also CHMOD my files however I like.

3) No, installing PHP is a bit of a ball-ache and I really can't be arsed if I'm completely honest.

Anyway, I'm 99% sure the problem lies in the way my HTML editor is saving the files. Said HTML editor being Bluefish.

---

### Post by p_quarles on 2008-01-05
Bluefish and Gedit are just plain text editors, so I don't see how they could be to blame. 

Installing PHP is a pain? Since when? Open a terminal, and run this:
```
sudo aptitude install libapache2-mod-php5
```This will install several apps, which you can easily remove later. Once that's done, create the test file:
```
sudo sh -c "echo '<?php phpinfo(); ?>' > info.php"
```Now, upload the "info.php" file to the server, navigate to it, and see if it works properly. 

To remove everything you just installed:
```
sudo aptitude remove libapache2-mod-php5
```

---

### Post by RyuKokoro on 2008-01-05
Ahh, installing PHP was a pain on Windows, I just presumed it'd be the same on Linux (which I've not long had installed.) But yeah, thanks forthe help, I'll try that and report back! :)

---

### Post by RyuKokoro on 2008-01-05
Right, I tried doing what you said and it didn't work. What's more, I tried uploading an untouched index.php file to another site I have that I created when I had windows and now that's broken too. In the server-side window on gFTP, the PHP files that are fine have an icon that looks like a page but the ones I've uploaded today have an icon that looks like the end of an RJ45 cable. I really haven't got a clue what's going on cos the CHMODs are fine too. HTML files are fine when I upload them, the server loads them properly no problem. It's just PHP files that I've sent since I've had Ubuntu.

---

### Post by p_quarles on 2008-01-05
Strange. :confused:

Do you have shell (i.e., SSH) access to the server? If so, log in and run this:
```
ls -l ~/info.php
```
I'm not really sure what the problem is here, but the results of that command may lead to the answer.

---

### Post by RyuKokoro on 2008-01-05
Strange is right.

Unfortunately, I don't have shell access cos it's not my webspace, I'm just loaning the space of a friend. All I have is FTP.

---

### Post by p_quarles on 2008-01-05
> **RyuKokoro said:**
> Strange is right.

Unfortunately, I don't have shell access cos it's not my webspace, I'm just loaning the space of a friend. All I have is FTP.
Yeah, I'm not sure that it's possible to check file permissions via FTP. Wish I could help more, but this one has me stumped. 

Anyway, this is kind of shot in the dark, but maybe worth a try. Copy the test file to your web directory (this is under the assumption that you haven't uninstalled PHP yet):
```
sudo cp info.php /var/www/
```
Then, point your browser to:
```
http://localhost/info.php
```
If the default PHP version information page shows up, then the problem is either with the server or with the transfer. If it doesn't, then it's likely a problem with the Ubuntu installation on your comp.

---

### Post by RyuKokoro on 2008-01-05
Cheers, one question though. How would I navigate to a specific folder on localhost? e.g., /home/dan/Documents.

EDIT: In fact, scratch that, there's a copy in the localhost home folder. It doesn't work, it asks me what program I'd like to use to open it instead.

---

### Post by p_quarles on 2008-01-05
> **RyuKokoro said:**
> Cheers, one question though. How would I navigate to a specific folder on localhost? e.g., /home/dan/Documents
```
cd /home/dan/Documents
```

---

### Post by RyuKokoro on 2008-01-05
That wouldn't work in a web browser though, that'd only work in Terminal. Anyway, as I editted in my last post, I had a copy of info.php in the localhost home folder already. When I try to go to it, I get asked which program I'd like to open it with.

---

### Post by p_quarles on 2008-01-05
> **RyuKokoro said:**
> That wouldn't work in a web browser though, that'd only work in Terminal. Anyway, as I editted in my last post, I had a copy of info.php in the localhost home folder already. When I try to go to it, I get asked which program I'd like to open it with.
It won't work in your home folder -- you need to copy it to the /var/www folder (see the first command in post #9 of this thread). If that doesn't work, post the output of this:
```
cat /etc/apache2/apache2.conf
```

---

### Post by RyuKokoro on 2008-01-05
Apache doesn't seem to be working properly, does it need some initial configuring? I've copied the whole website folder to /var/www/ like you said and the folder's shown up in Firefox. When I click on it though, I get told it's a PHTML file and asked what I'd like to open it with.

---

### Post by p_quarles on 2008-01-05
Honestly, I can't remember how much initial configuration is involved. That's why I asked for the output of 
```
cat /etc/apache2/apache2.conf
```
That'll allow me to compare your configuration with mine. ;)

---

### Post by RyuKokoro on 2008-01-05
```
#
# Based upon the NCSA server configuration files originally by Rob McCool.
#
# This is the main Apache server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See http://httpd.apache.org/docs/2.2/ for detailed information about
# the directives.
#
# Do NOT simply read the instructions in here without understanding
# what they do.  They're here only as hints or reminders.  If you are unsure
# consult the online docs. You have been warned.  
#
# The configuration directives are grouped into three basic sections:
#  1. Directives that control the operation of the Apache server process as a
#     whole (the 'global environment').
#  2. Directives that define the parameters of the 'main' or 'default' server,
#     which responds to requests that aren't handled by a virtual host.
#     These directives also provide default values for the settings
#     of all virtual hosts.
#  3. Settings for virtual hosts, which allow Web requests to be sent to
#     different IP addresses or hostnames and have them handled by the
#     same Apache server process.
#
# Configuration and logfile names: If the filenames you specify for many
# of the server's control files begin with "/" (or "drive:/" for Win32), the
# server will use that explicit path.  If the filenames do *not* begin
# with "/", the value of ServerRoot is prepended -- so "/var/log/apache2/foo.log"
# with ServerRoot set to "" will be interpreted by the
# server as "//var/log/apache2/foo.log".
#

### Section 1: Global Environment
#
# The directives in this section affect the overall operation of Apache,
# such as the number of concurrent requests it can handle or where it
# can find its configuration files.
#

#
# ServerRoot: The top of the directory tree under which the server's
# configuration, error, and log files are kept.
#
# NOTE!  If you intend to place this on an NFS (or otherwise network)
# mounted filesystem then please read the LockFile documentation (available
# at <URL:http://httpd.apache.org/docs-2.1/mod/mpm_common.html#lockfile>);
# you will save yourself a lot of trouble.
#
# Do NOT add a slash at the end of the directory path.
#
ServerRoot "/etc/apache2"

#
# The accept serialization lock file MUST BE STORED ON A LOCAL DISK.
#
#<IfModule !mpm_winnt.c>
#<IfModule !mpm_netware.c>
LockFile /var/lock/apache2/accept.lock
#</IfModule>
#</IfModule>

#
# PidFile: The file in which the server should record its process
# identification number when it starts.
#
PidFile /var/run/apache2.pid

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
KeepAliveTimeout 15

##
## Server-Pool Size Regulation (MPM specific)
## 

# prefork MPM
# StartServers: number of server processes to start
# MinSpareServers: minimum number of server processes which are kept spare
# MaxSpareServers: maximum number of server processes which are kept spare
# MaxClients: maximum number of server processes allowed to start
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

# worker MPM
# StartServers: initial number of server processes to start
# MaxClients: maximum number of simultaneous client connections
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadsPerChild: constant number of worker threads in each server process
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_worker_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

User www-data
Group www-data

#
# AccessFileName: The name of the file to look for in each directory
# for additional configuration directives.  See also the AllowOverride
# directive.
#

AccessFileName .htaccess

#
# The following lines prevent .htaccess and .htpasswd files from being 
# viewed by Web clients. 
#
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>

#
# DefaultType is the default MIME type the server will use for a document
# if it cannot otherwise determine one, such as from filename extensions.
# If your server contains mostly text or HTML documents, "text/plain" is
# a good value.  If most of your content is binary, such as applications
# or images, you may want to use "application/octet-stream" instead to
# keep browsers from trying to display binary files as though they are
# text.
#
DefaultType text/plain


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
ErrorLog /var/log/apache2/error.log

#
# LogLevel: Control the number of messages logged to the error_log.
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
#
LogLevel warn

# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

# Include all the user configurations:
Include /etc/apache2/httpd.conf

# Include ports listing
Include /etc/apache2/ports.conf

#
# The following directives define some format nicknames for use with
# a CustomLog directive (see below).
#
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

#
# ServerTokens
# This directive configures what you return as the Server HTTP response
# Header. The default is 'Full' which sends information about the OS-Type
# and compiled in modules.
# Set to one of:  Full | OS | Minor | Minimal | Major | Prod
# where Full conveys the most information, and Prod the least.
#
ServerTokens Full

#
# Optionally add a line containing the server version and virtual host
# name to server-generated pages (internal error documents, FTP directory 
# listings, mod_status and mod_info output etc., but not CGI generated 
# documents or custom error documents).
# Set to "EMail" to also include a mailto: link to the ServerAdmin.
# Set to one of:  On | Off | EMail
#
ServerSignature On



#
# Customizable error responses come in three flavors:
# 1) plain text 2) local redirects 3) external redirects
#
# Some examples:
#ErrorDocument 500 "The server made a boo boo."
#ErrorDocument 404 /missing.html
#ErrorDocument 404 "/cgi-bin/missing_handler.pl"
#ErrorDocument 402 http://www.example.com/subscription_info.html
#

#
# Putting this all together, we can internationalize error responses.
#
# We use Alias to redirect any /error/HTTP_<error>.html.var response to
# our collection of by-error message multi-language collections.  We use 
# includes to substitute the appropriate text.
#
# You can modify the messages' appearance without changing any of the
# default HTTP_<error>.html.var files by adding the line:
#
#   Alias /error/include/ "/your/include/path/"
#
# which allows you to create your own set of files by starting with the
# /usr/share/apache2/error/include/ files and copying them to /your/include/path/, 
# even on a per-VirtualHost basis.  The default include files will display
# your Apache version number and your ServerAdmin email address regardless
# of the setting of ServerSignature.
#
# The internationalized error documents require mod_alias, mod_include
# and mod_negotiation.  To activate them, uncomment the following 30 lines.

#    Alias /error/ "/usr/share/apache2/error/"
#
#    <Directory "/usr/share/apache2/error">
#        AllowOverride None
#        Options IncludesNoExec
#        AddOutputFilter Includes html
#        AddHandler type-map var
#        Order allow,deny
#        Allow from all
#        LanguagePriority en cs de es fr it nl sv pt-br ro
#        ForceLanguagePriority Prefer Fallback
#    </Directory>
#
#    ErrorDocument 400 /error/HTTP_BAD_REQUEST.html.var
#    ErrorDocument 401 /error/HTTP_UNAUTHORIZED.html.var
#    ErrorDocument 403 /error/HTTP_FORBIDDEN.html.var
#    ErrorDocument 404 /error/HTTP_NOT_FOUND.html.var
#    ErrorDocument 405 /error/HTTP_METHOD_NOT_ALLOWED.html.var
#    ErrorDocument 408 /error/HTTP_REQUEST_TIME_OUT.html.var
#    ErrorDocument 410 /error/HTTP_GONE.html.var
#    ErrorDocument 411 /error/HTTP_LENGTH_REQUIRED.html.var
#    ErrorDocument 412 /error/HTTP_PRECONDITION_FAILED.html.var
#    ErrorDocument 413 /error/HTTP_REQUEST_ENTITY_TOO_LARGE.html.var
#    ErrorDocument 414 /error/HTTP_REQUEST_URI_TOO_LARGE.html.var
#    ErrorDocument 415 /error/HTTP_UNSUPPORTED_MEDIA_TYPE.html.var
#    ErrorDocument 500 /error/HTTP_INTERNAL_SERVER_ERROR.html.var
#    ErrorDocument 501 /error/HTTP_NOT_IMPLEMENTED.html.var
#    ErrorDocument 502 /error/HTTP_BAD_GATEWAY.html.var
#    ErrorDocument 503 /error/HTTP_SERVICE_UNAVAILABLE.html.var
#    ErrorDocument 506 /error/HTTP_VARIANT_ALSO_VARIES.html.var



# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

```

---

### Post by p_quarles on 2008-01-05
Okay, it looks like that file is missing the settings that will allow it to read PHP files. At the moment, I think I've had a few too many "beverages" to give you the best advice. I'll get back to you later tomorrow and try to suggest ways of reconfiguring it.

---

### Post by RyuKokoro on 2008-01-05
Alright dude, cheers for all the help. I'll just get on with content writing tonight then! Thanks again. :)

---

### Post by p_quarles on 2008-01-06
No problem. Hope we can get this at least partially resolved. 

Add the following line to your apache2.conf file:
```
AddType application/x-httpd-php .php .phtml .php3
```
Now, restart Apache:
```
sudo /etc/init.d/apache2 restart
```
And point your browser to localhost/info.php. If it's still not working properly, post the output of the following commands:
```
ps aux | grep apache
```
and
```
dpkg --get-selections apache2 libapache2-mod-php5
```

---

### Post by RyuKokoro on 2008-01-06
That's cracked it! It's working both locally and remotely. Cheers, mate. You are, without a doubt, a legend.

Case closed, lol.

---

