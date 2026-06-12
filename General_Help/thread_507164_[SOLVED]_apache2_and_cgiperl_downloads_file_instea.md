---
title: "[SOLVED] apache2 and cgi/perl: downloads file instead of executing it"
date: 2007-07-22
forum: General Help
---

### Post by unebaguettesvp on 2007-07-22
so, i have apache2 running perfectly with php5 and mysql. everything works great. now, i'm trying to get perl to work. when i go to [http://localhost/cgi-bin/test.cgi](http://localhost/cgi-bin/test.cgi), it tries to download the file instead of executing it. here are my settings:

/etc/apache2/apache.conf:

```

#
# Based upon the NCSA server configuration files originally by Rob McCool.
#
# This is the main Apache server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See <URL:http://httpd.apache.org/docs-2.1/> for detailed information about
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

TypesConfig /etc/mime.types

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

# Include generic snippets of statements
Include /etc/apache2/conf.d/

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

<IfModule alias_module>
    #
    # Aliases: Add here as many aliases as you need (with no limit). The format is 
    # Alias fakename realname
    #
    # Note that if you include a trailing / on fakename then the server will
    # require it to be present in the URL.  So "/icons" isn't aliased in this
    # example, only "/icons/".  If the fakename is slash-terminated, then the 
    # realname must also be slash terminated, and if the fakename omits the 
    # trailing slash, the realname must also omit it.
    #
    # We include the /icons/ alias for FancyIndexed directory listings.  If
    # you do not use FancyIndexing, you may comment this out.
    #
    Alias /icons/ "/usr/share/apache2/icons/"

    <Directory "/usr/share/apache2/icons">
        Options Indexes MultiViews
        AllowOverride None
        Order allow,deny
        Allow from all
    </Directory>

</IfModule>

#
# Directives controlling the display of server-generated directory listings.
#
<IfModule mod_autoindex.c>

    #
    # IndexOptions: Controls the appearance of server-generated directory
    # listings.
    #
    IndexOptions FancyIndexing VersionSort HTMLTable NameWidth=*

    #
    # AddIcon* directives tell the server which icon to show for different
    # files or filename extensions.  These are only displayed for
    # FancyIndexed directories.
    #
    AddIconByEncoding (CMP,/icons/compressed.gif) x-compress x-gzip

    AddIconByType (TXT,/icons/text.gif) text/*
    AddIconByType (IMG,/icons/image2.gif) image/*
    AddIconByType (SND,/icons/sound2.gif) audio/*
    AddIconByType (VID,/icons/movie.gif) video/*

    AddIcon /icons/binary.gif .bin .exe
    AddIcon /icons/binhex.gif .hqx
    AddIcon /icons/tar.gif .tar
    AddIcon /icons/world2.gif .wrl .wrl.gz .vrml .vrm .iv
    AddIcon /icons/compressed.gif .Z .z .tgz .gz .zip
    AddIcon /icons/a.gif .ps .ai .eps
    AddIcon /icons/layout.gif .html .shtml .htm .pdf
    AddIcon /icons/text.gif .txt
    AddIcon /icons/c.gif .c
    AddIcon /icons/p.gif .pl .py
    AddIcon /icons/f.gif .for
    AddIcon /icons/dvi.gif .dvi
    AddIcon /icons/uuencoded.gif .uu
    AddIcon /icons/script.gif .conf .sh .shar .csh .ksh .tcl
    AddIcon /icons/tex.gif .tex
    AddIcon /icons/bomb.gif core

    AddIcon /icons/back.gif ..
    AddIcon /icons/hand.right.gif README
    AddIcon /icons/folder.gif ^^DIRECTORY^^
    AddIcon /icons/blank.gif ^^BLANKICON^^

    #
    # DefaultIcon is which icon to show for files which do not have an icon
    # explicitly set.
    #
    DefaultIcon /icons/unknown.gif

    #
    # AddDescription allows you to place a short description after a file in
    # server-generated indexes.  These are only displayed for FancyIndexed
    # directories.
    # Format: AddDescription "description" filename
    #
    #AddDescription "GZIP compressed document" .gz
    #AddDescription "tar archive" .tar
    #AddDescription "GZIP compressed tar archive" .tgz

    #
    # ReadmeName is the name of the README file the server will look for by
    # default, and append to directory listings.
    #
    # HeaderName is the name of a file which should be prepended to
    # directory indexes. 
    ReadmeName README.html
    HeaderName HEADER.html

    #
    # IndexIgnore is a set of filenames which directory indexing should ignore
    # and not include in the listing.  Shell-style wildcarding is permitted.
    #
    IndexIgnore .??* *~ *# RCS CVS *,v *,t 
</IfModule>

<IfModule mod_mime.c>

    #
    # AddType allows you to add to or override the MIME configuration
    # file mime.types for specific file types.
    #
    #AddType application/x-gzip .tgz
    #
    # AddEncoding allows you to have certain browsers uncompress
    # information on the fly. Note: Not all browsers support this.
    # Despite the name similarity, the following Add* directives have
    # nothing to do with the FancyIndexing customization directives above.
    #
    #AddEncoding x-compress .Z
    #AddEncoding x-gzip .gz .tgz
    #
    # If the AddEncoding directives above are commented-out, then you
    # probably should define those extensions to indicate media types:
    #
    AddType application/x-compress .Z
    AddType application/x-gzip .gz .tgz

    #
    # DefaultLanguage and AddLanguage allows you to specify the language of 
    # a document. You can then use content negotiation to give a browser a 
    # file in a language the user can understand.
    #
    # Specify a default language. This means that all data
    # going out without a specific language tag (see below) will 
    # be marked with this one. You probably do NOT want to set
    # this unless you are sure it is correct for all cases.
    #
    # * It is generally better to not mark a page as 
    # * being a certain language than marking it with the wrong
    # * language!
    #
    # DefaultLanguage nl
    #
    # Note 1: The suffix does not have to be the same as the language
    # keyword --- those with documents in Polish (whose net-standard
    # language code is pl) may wish to use "AddLanguage pl .po" to
    # avoid the ambiguity with the common suffix for perl scripts.
    #
    # Note 2: The example entries below illustrate that in some cases 
    # the two character 'Language' abbreviation is not identical to 
    # the two character 'Country' code for its country,
    # E.g. 'Danmark/dk' versus 'Danish/da'.
    #
    # Note 3: In the case of 'ltz' we violate the RFC by using a three char
    # specifier. There is 'work in progress' to fix this and get
    # the reference data for rfc1766 cleaned up.
    #
    # Catalan (ca) - Croatian (hr) - Czech (cs) - Danish (da) - Dutch (nl)
    # English (en) - Esperanto (eo) - Estonian (et) - French (fr) - German (de)
    # Greek-Modern (el) - Hebrew (he) - Italian (it) - Japanese (ja)
    # Korean (ko) - Luxembourgeois* (ltz) - Norwegian Nynorsk (nn)
    # Norwegian (no) - Polish (pl) - Portugese (pt)
    # Brazilian Portuguese (pt-BR) - Russian (ru) - Swedish (sv)
    # Simplified Chinese (zh-CN) - Spanish (es) - Traditional Chinese (zh-TW)
    #
    AddLanguage ca .ca
    AddLanguage cs .cz .cs
    AddLanguage da .dk
    AddLanguage de .de
    AddLanguage el .el
    AddLanguage en .en
    AddLanguage eo .eo
    AddLanguage es .es
    AddLanguage et .et
    AddLanguage fr .fr
    AddLanguage he .he
    AddLanguage hr .hr
    AddLanguage it .it
    AddLanguage ja .ja
    AddLanguage ko .ko
    AddLanguage ltz .ltz
    AddLanguage nl .nl
    AddLanguage nn .nn
    AddLanguage no .no
    AddLanguage pl .po
    AddLanguage pt .pt
    AddLanguage pt-BR .pt-br
    AddLanguage ru .ru
    AddLanguage sv .sv
    AddLanguage zh-CN .zh-cn
    AddLanguage zh-TW .zh-tw
</IfModule>

<IfModule mod_negotiation.c>
    #
    # LanguagePriority allows you to give precedence to some languages
    # in case of a tie during content negotiation.
    #
    # Just list the languages in decreasing order of preference. We have
    # more or less alphabetized them here. You probably want to change this.
    #
    LanguagePriority en ca cs da de el eo es et fr he hr it ja ko ltz nl nn no pl pt pt-BR ru sv zh-CN zh-TW

    #
    # ForceLanguagePriority allows you to serve a result page rather than
    # MULTIPLE CHOICES (Prefer) [in case of a tie] or NOT ACCEPTABLE (Fallback)
    # [in case no accepted languages matched the available variants]
    #
    ForceLanguagePriority Prefer Fallback

</IfModule>

<IfModule mod_mime.c>
    #
    # Specify a default charset for all pages sent out. This is
    # always a good idea and opens the door for future internationalisation
    # of your web site, should you ever want it. Specifying it as
    # a default does little harm; as the standard dictates that a page
    # is in iso-8859-1 (latin1) unless specified otherwise i.e. you
    # are merely stating the obvious. There are also some security
    # reasons in browsers, related to javascript and URL parsing
    # which encourage you to always set a default char set.
    #
    #AddDefaultCharset ISO-8859-1

    #
    # Commonly used filename extensions to character sets. You probably
    # want to avoid clashes with the language extensions, unless you
    # are good at carefully testing your setup after each change.
    # See http://www.iana.org/assignments/character-sets for the
    # official list of charset names and their respective RFCs.
    #
    AddCharset us-ascii    .ascii .us-ascii
    AddCharset ISO-8859-1  .iso8859-1  .latin1
    AddCharset ISO-8859-2  .iso8859-2  .latin2 .cen
    AddCharset ISO-8859-3  .iso8859-3  .latin3
    AddCharset ISO-8859-4  .iso8859-4  .latin4
    AddCharset ISO-8859-5  .iso8859-5  .cyr .iso-ru
    AddCharset ISO-8859-6  .iso8859-6  .arb .arabic
    AddCharset ISO-8859-7  .iso8859-7  .grk .greek
    AddCharset ISO-8859-8  .iso8859-8  .heb .hebrew
    AddCharset ISO-8859-9  .iso8859-9  .latin5 .trk
    AddCharset ISO-8859-10  .iso8859-10  .latin6
    AddCharset ISO-8859-13  .iso8859-13
    AddCharset ISO-8859-14  .iso8859-14  .latin8
    AddCharset ISO-8859-15  .iso8859-15  .latin9
    AddCharset ISO-8859-16  .iso8859-16  .latin10
    AddCharset ISO-2022-JP .iso2022-jp .jis
    AddCharset ISO-2022-KR .iso2022-kr .kis
    AddCharset ISO-2022-CN .iso2022-cn .cis
    AddCharset Big5        .Big5       .big5 .b5
    AddCharset cn-Big5     .cn-big5
    # For russian, more than one charset is used (depends on client, mostly):
    AddCharset WINDOWS-1251 .cp-1251   .win-1251
    AddCharset CP866       .cp866
    AddCharset KOI8      .koi8
    AddCharset KOI8-E      .koi8-e
    AddCharset KOI8-r      .koi8-r .koi8-ru
    AddCharset KOI8-U      .koi8-u
    AddCharset KOI8-ru     .koi8-uk .ua
    AddCharset ISO-10646-UCS-2 .ucs2
    AddCharset ISO-10646-UCS-4 .ucs4
    AddCharset UTF-7       .utf7
    AddCharset UTF-8       .utf8
    AddCharset UTF-16      .utf16
    AddCharset UTF-16BE    .utf16be
    AddCharset UTF-16LE    .utf16le
    AddCharset UTF-32      .utf32
    AddCharset UTF-32BE    .utf32be
    AddCharset UTF-32LE    .utf32le
    AddCharset euc-cn      .euc-cn
    AddCharset euc-gb      .euc-gb
    AddCharset euc-jp      .euc-jp
    AddCharset euc-kr      .euc-kr
    #Not sure how euc-tw got in - IANA doesn't list it???
    AddCharset EUC-TW      .euc-tw
    AddCharset gb2312      .gb2312 .gb
    AddCharset iso-10646-ucs-2 .ucs-2 .iso-10646-ucs-2
    AddCharset iso-10646-ucs-4 .ucs-4 .iso-10646-ucs-4
    AddCharset shift_jis   .shift_jis .sjis

    #
    # AddHandler allows you to map certain file extensions to "handlers":
    # actions unrelated to filetype. These can be either built into the server
    # or added with the Action directive (see below)
    #
    # To use CGI scripts outside of ScriptAliased directories:
    # (You will also need to add "ExecCGI" to the "Options" directive.)
    #
    AddHandler cgi-script .cgi .pl

    #
    # For files that include their own HTTP headers:
    #
    #AddHandler send-as-is asis

    #
    # For server-parsed imagemap files:
    #
    #AddHandler imap-file map

    #
    # For type maps (negotiated resources):
    # (This is enabled by default to allow the Apache "It Worked" page
    #  to be distributed in multiple languages.)
    #
    AddHandler type-map var

    #
    # Filters allow you to process content before it is sent to the client.
    #
    # To parse .shtml files for server-side includes (SSI):
    # (You will also need to add "Includes" to the "Options" directive.)
    #
    AddType text/html .shtml
    AddOutputFilter INCLUDES .shtml
</IfModule>

#
# Action lets you define media types that will execute a script whenever
# a matching file is called. This eliminates the need for repeated URL
# pathnames for oft-used CGI file processors.
# Format: Action media/type /cgi-script/location
# Format: Action handler-name /cgi-script/location
#
Action cgi-script "/usr/bin/perl"
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

<IfModule mod_setenvif.c>
    #
    # The following directives modify normal HTTP response behavior to
    # handle known problems with browser implementations.
    #
    BrowserMatch "Mozilla/2" nokeepalive
    BrowserMatch "MSIE 4\.0b2;" nokeepalive downgrade-1.0 force-response-1.0
    BrowserMatch "RealPlayer 4\.0" force-response-1.0
    BrowserMatch "Java/1\.0" force-response-1.0
    BrowserMatch "JDK/1\.0" force-response-1.0

    #
    # The following directive disables redirects on non-GET requests for
    # a directory that does not include the trailing slash.  This fixes a 
    # problem with Microsoft WebFolders which does not appropriately handle 
    # redirects for folders with DAV methods.
    # Same deal with Apple's DAV filesystem and Gnome VFS support for DAV.
    #
    BrowserMatch "Microsoft Data Access Internet Publishing Provider" redirect-carefully
    BrowserMatch "MS FrontPage" redirect-carefully
    BrowserMatch "^WebDrive" redirect-carefully
    BrowserMatch "^WebDAVFS/1.[012]" redirect-carefully
    BrowserMatch "^gnome-vfs/1.0" redirect-carefully
    BrowserMatch "^XML Spy" redirect-carefully
    BrowserMatch "^Dreamweaver-WebDAV-SCM1" redirect-carefully
</IfModule>

<IfModule mod_status.c>
    #
    # Allow server status reports generated by mod_status,
    # with the URL of http://servername/server-status
    # Change the ".example.com" to match your domain to enable.
    #
    <Location /server-status>
        SetHandler server-status
        Order deny,allow
        Deny from all
        Allow from localhost
    </Location>
</IfModule>

ExtendedStatus On

<IfModule mod_info.c>
    #
    # Allow remote server configuration reports, with the URL of
    #  http://servername/server-info (requires that mod_info.c be loaded).
    # Change the ".example.com" to match your domain to enable.
    #
    <Location /server-info>
        SetHandler server-info
        Order deny,allow
        Deny from all
        Allow from localhost
    </Location>
</IfModule>

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

```

/etc/apache2/sites-enabled/default:
```

NameVirtualHost *
<VirtualHost *>
	ServerAdmin admin@localhost
	
	DocumentRoot /data/Websites/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /data/Websites/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ "/data/Websites/cgi-bin/"
	<Directory "/data/Websites/cgi-bin/">
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
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

test.cgi:
```

#!/usr/bin/perl
print "Content-type: text/html\n\n";
print "Hello, World.";

```

test.cgi and cgi-bin are both owned by my username and the group is too.

running sudo a2enmod says that the cgi cgid and perl modules are all enabled. and yes, i have restarted the apache server.

if i do a whereis perl, i get:

perl: /usr/bin/perl /etc/perl /usr/lib/perl /usr/X11R6/bin/perl /usr/bin/X11/perl /usr/share/perl /usr/share/man/man1/perl.1.gz

any ideas? i THINK i went through all the posts on this board regarding this issue and i'm still having problems.

thanks in advance!

---

### Post by unebaguettesvp on 2007-07-23
sorry for the bump. any ideas?

---

### Post by unebaguettesvp on 2007-07-23
one more bump. please help!

---

### Post by Billy the Kid on 2007-07-23
Do you have mod-perl installed and configured correctly?
Is the perl script given executable privileges?  Try chmod a+x script.pl

---

### Post by unebaguettesvp on 2007-08-03
mod_perl is installed. libapache2-mod-perl2 is installed in synaptic package manager. using a2enmod, perl is enabled. i can also see it in the directory mods-enabled.

however, i don't think it is configured correctly which is why i think i'm having this problem.

the perl script was given executable privileges.

---

### Post by unebaguettesvp on 2007-08-04
sorry for the bump

---

### Post by spur on 2007-08-06
I am having exactly the same prob. I'm using feisty. Did you find a solution?

---

### Post by tr333 on 2007-08-07
You don't need mod_perl installed to use Perl CGI scripts on apache, but they might run faster if you do.  Have you checked the apache logs to see if they tell you anything of interest?

```
/var/log/apache2/error.log
/var/log/apache2/access.log
```

Some more things to try:

Make sure that you have the shebang line at the top of each perl script.
```
#!/usr/bin/perl -wT
```

Make sure that each perl script has execute permissions on it.
```
chmod +x cgifile.cgi
```

---

### Post by tr333 on 2007-08-07
Try running the following test script and see if it gives any output.

```
#!/usr/bin/perl -wT

use strict;
use warnings;

use CGI qw(:all -debug);
use CGI::Carp qw(fatalsToBrowser warningsToBrowser);

print header,
start_html("Test CGI Script"),
p("This is a test CGI script"),
end_html;

exit 0;
```

Place this script in your cgi-bin directory and set the execute permissions with "chmod a+x test.cgi".

If this has problems running, you should see the errors in either the log file at /var/log/apache2/error.log or directly in the browser window.

---

### Post by spur on 2007-08-07
Yes I have the 'she-bang' line and the permissions set to execute etc.
I have started using eclipse with epic for perl as I can test all my perl with it without using apache at all.
I spent two days trying different things and always ended up with the same result. I am beginning too think there is a bug of some kind. I did remember to restart apache when I changed something as well.The error logs tell me nothing as they just repeat the error message (permission denied) or say nothing (as an offer to download is not seen as an error).
I saved your script as test.pl and it worked.
The permissions are the same as my hello-world.pl which gets the download dialog.
The script I have been trying to get to go is 
> 
#!/usr/local/bin/perl

print "Content-type:text/html\n\n";
print "<html><h1>Hello World!</h1></html>";
If I run this in Eclipse I get the desired result.

---

### Post by spur on 2007-08-07
The end results.Attachments
your test script
your script with my 'hello-world' result (download window' overlaid.
'hello-world run through eclipse.

---

### Post by tr333 on 2007-08-07
The sample code you gave in your test script uses "/usr/local/bin/perl" for the perl path.  On my system, the perl path is located at "/usr/bin/perl".  You might want to check if you have the correct perl path in the scripts.

> #!/usr/local/bin/perl

print "Content-type:text/html\n\n";
print "<html><h1>Hello World!</h1></html>";

---

### Post by spur on 2007-08-07
I don't know how that crept in and I had never checked it. I just copy and pasted my original that I initially tried to configure with from my zip drive. I changed it and it works. Thanks for spotting that. I will have to determine if that happened when I ran it through Eclipse.
Update. I found about half of my files had the extra /local/ in the she-bang line.
[img]http://jumi.lut.fi/~junousia/hymiot/think/vaikeapaatos.gif[/img]
Also when I make my zip my cgi-bin even with the proper she-bang line I get the download. I think that is because it is directing to the root of the zip drive first(for the perl). The / for the zip and not my hard disk. Please, how would I direct to the hard disk root?

---

### Post by unebaguettesvp on 2007-08-08
My error.log file says:

[Tue Aug 07 21:00:06 2007] [error] [client 127.0.0.1] (13)Permission denied: exec of '/data/Websites/cgi-bin/printenv.cgi' failed

Should I change my User and Group setting? It's currently set at www-data.

---

### Post by spur on 2007-08-08
I would leave the group settings as is. Ensure you have permissions of 755 and executable set on the file. You can check this by right clicking and going to permissions. You need user read and w rite and group and others read and the box for make executable ticked.
Also check were your Perl is.
See what you get by using > which perl on the command line. Your she-bang line should direct there if its a perl script your using.

---

### Post by unebaguettesvp on 2007-08-08
I tried changing the User AND Group settings to 'philip'. That's my username. That didn't work.

I did a chmod 0777 to the file and the directory it is in. No luck.

I did a chown philip:philip to the file and directory it is in. No luck.

The user philip CAN execute the command /usr/bin/perl /thefile

What's the deal?

---

### Post by unebaguettesvp on 2007-08-08
which perl points to /usr/bin/perl and my shebang line is pointing to #!/usr/bin/perl -wT

My above post should say philip : philip. I guess the colon plus a p points to a smiley face?

---

### Post by spur on 2007-08-08
I'm wondering about the '.cgi' ending. I have not used it only'.pl'. If your system is not configure to see '.cgi' as perl it could be the cause of your trouble. What happens if you use '.pl'

---

### Post by unebaguettesvp on 2007-08-08
Yeah, I get the same error. I created an AddHandler in apache.conf for cgi and pl.

---

### Post by spur on 2007-08-08
Reducing this one thing at a time. Your permissions seam ok. Your add handler seems ok.
What about your ScriptAlias?
What about your perl installation, is it where you expect it to be?

---

### Post by unebaguettesvp on 2007-08-08
This is in the file /etc/apache2/sites-available/default

```

	ScriptAlias /cgi-bin/ "/data/Websites/cgi-bin/"
	<Directory "/data/Websites/cgi-bin/">
		AllowOverride Options
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

```

This is from the file /etc/apache2/apache2.conf

```

<IfModule mod_mime.c>
    ...........................
    AddHandler cgi-script .cgi .pl
    ...........................
</IfModule>

Action cgi-script /usr/bin/perl

```

Everything seems to be fine!

The perl installation is fine. It's under /usr/bin/perl. I can execute the Hello, World example from a command line just fine. Just not through the browser.

Any other ideas? Thanks for your help!!!! Did you get yours to work?

---

### Post by bukwirm on 2007-08-08
You need to print a header (with the CGI::header function) before you print anything else.

```
#!/usr/local/bin/perl

use CGI qw(:all -debug);

print header('text/html');
print start_html();
print h1('Hello World!') ;
print end_html();
```

You might look at the [documentation for the CGI module]("http://search.cpan.org/~lds/CGI.pm-3.29/CGI.pm"), if you haven't already.

---

### Post by tr333 on 2007-08-08
> **unebaguettesvp said:**
> I did a chmod 0777 to the file and the directory it is in. No luck.

You should never chmod any directory or file to 0777 if it will be accessible from a cgi-script.

---

### Post by spur on 2007-08-08
Unebaguettesvp said
>  Any other ideas? Thanks for your help!!!! Did you get yours to work?
Yes, with the help of tr333.
I am using Eclipse for my perl stuff as I can test it through the IDE so life is a little simpler.
I can't see what would be making yours not work so I hope someone else can steer you in the right direction.

---

### Post by unebaguettesvp on 2007-08-09
bukwirm-
i tried your script and i still had no luck. my cgi test script has this as the first line:

print "Content-type: text/html\n\n";

i don't think it's an issue with the script just the settings within apache.

tr333-
the only reason why i gave that directory and the files in it full access was because i was really pissed at this not working. i wanted to give it complete access. plus, my webserver will not be accessible from the outside. this is only for my own personal use.


any other ideas anyone?

---

### Post by spur on 2007-08-09
Just to try and pin it down a bit more. Have you tried a .pl file or just the .cgi? 
Also not likely to be but could be do you have maybe (no offense intended) a spelling mistake in your shebang line?
Also I think I have my AddHandler line in a different place to you.
The Bukwirm script has "/usr/local/bin/perl"  if you copy and paste you might not have noticed the 'local' and you probably don't need it. :)

---

### Post by unebaguettesvp on 2007-08-10
I've tried both .cgi and .pl. Neither seem to work.
Yeah, I looked at the shebang line a million times already. But everything is as it should be.
Do you think you could post your AddHandler, Action, and ScriptAlias lines and where they should be? Also, can you post the cgi-bin <Directory segment with the ExecCGI? Thanks!
Yeah, I tried executing a script in a command prompt using /usr/local/bin/perl. It didn't work because it's not installed in that directory. However, /usr/bin/perl worked perfectly.

I'm going try reinstalling the mod_perl again this weekend. Thanks for your help.

---

### Post by spur on 2007-08-10
The attachment is my apache .conf that has all the lines for you to compare. I put them all in one. I did that after I got some advice on this forum and it did make a difference. My system is feisty.

---

### Post by bdean42 on 2007-08-17
i don't know if this is useful to anyone or not. i'm using feisty and had similar problems with the test script from this thread. however looking at my default virtual host i noticed that the cgi-bin directory is pointing to /usr/lib/cgi-bin which doesn't exist.

i'm thinking this must be the default in the feisty packages because i don't remember ever setting it up like this. anyway, after creating the /usr/lib/cgi-bin directory and putting test.pl in it, it worked fine (note that i did have to change the handler in /etc/apache2/apache2.conf for cgi to have both .cgi and .pl extensions).

---

### Post by unebaguettesvp on 2007-11-05
i finally figured out what the problem was this weekend. i had to do a clean install of gutsy and that meant reinstalling apache, php, mysql, and the libapache2-modperl? package.

so, again, i tried to get the cgi-bin to work and i was still running into the same errors. then i thought to just use the default cgi-bin directory (/usr/lib/cgi-bin). so, i restored the default settings and it worked!!!

i guess my problem was that the cgi-bin directory that i wanted to use was inside the website directory (/data/Websites/cgi-bin was in /data/Websites with all the other sites). i guess that doesn't work. i tried to get it to work by setting permissions and all, but nothing did the trick.

thanks again for any help!

---

