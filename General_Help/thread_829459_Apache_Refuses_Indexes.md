---
title: "Apache Refuses Indexes"
date: 2008-06-14
forum: General Help
---

### Post by codeking on 2008-06-14
I'm trying to set up Apache, but it doesn't allow directory indexes.  Every time I try to access a folder without a index.[html, php, etc] file, instead of giving me the index, it says 403 forbidden.  I've done google searches, but all of that is caused by not having "Options Indexes," and I do.  Here's my directory options from the httpd.conf file.

```
DocumentRoot "/media/Shared/Websites"

#
# Each directory to which Apache has access can be configured with respect
# to which services and features are allowed and/or disabled in that
# directory (and its subdirectories). 
#
# First, we configure the "default" to be a very restrictive set of 
# features.  
#
<Directory />
    Options FollowSymLinks
    AllowOverride None
    #XAMPP
    #Order deny,allow
    #Deny from all
</Directory>

#
# Note that from this point forward you must specifically allow
# particular features to be enabled - so if something's not working as
# you might expect, make sure that you have specifically enabled it
# below.
#

#
# This should be changed to whatever you set DocumentRoot to.
#
<Directory "/media/Shared/Websites">
    #
    # Possible values for the Options directive are "None", "All",
    # or any combination of:
    #   Indexes Includes FollowSymLinks SymLinksifOwnerMatch ExecCGI MultiViews
    #
    # Note that "MultiViews" must be named *explicitly* --- "Options All"
    # doesn't give it to you.
    #
    # The Options directive is both complicated and important.  Please see
    # http://httpd.apache.org/docs/2.2/mod/core.html#options
    # for more information.
    #
    #Options Indexes FollowSymLinks
    # XAMPP
    Options All


    #
    # AllowOverride controls what directives may be placed in .htaccess files.
    # It can be "All", "None", or any combination of the keywords:
    #   Options FileInfo AuthConfig Limit
    #
    #AllowOverride None
    # since XAMPP 1.4:
    AllowOverride All


    #
    # Controls who can get stuff from this server.
    #
    Order allow,deny
    Allow from all

</Directory>
```

---

### Post by Joeb454 on 2008-06-14
```
chmod o+rx /var/www/<your directory>
```

That may fix it :)

---

### Post by spiderbatdad on 2008-06-14
```
    #AllowOverride None
    # since XAMPP 1.4:
   ** AllowOverride All**

```

This would be requiring .htaccess authentication. Changing it to None would set the directory to open access.

---

