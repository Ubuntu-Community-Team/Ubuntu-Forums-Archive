---
title: "Apache and cgisock"
date: 2007-10-22
forum: General Help
---

### Post by smbogan on 2007-10-22
I have the Ubuntu 7.10 server version installed.  I'm trying to get Apache to allow public_html directories to have cgi access (mainly to set up eRuby)

I have the public_html directory working, and it hosts .html files.  I've enabled the mods for cgi, userdir, rewrite, action, and possibly someothers along the way.

Basically, if I leave out an .htaccess file it serves the .rhtml file as a download with the contents of the file.  If I use the .htaccess file (below) as given by eruby, my browser is served a copy of the cgi script itself.

I'm pretty new to Linux administration, as I've only been familiar with the user side before.  Any help is apprecited.

Smbogan

My userdir.conf contains:
-------------------------
```
<IfModule mod_userdir.c>
        UserDir public_html
        UserDir disabled root

        <Directory /home/*/public_html>
                #AllowOverride FileInfo AuthConfig Limit
                AllowOverride All
                Options MultiViews Indexes SymLinksIfOwnerMatch Includes ExecCG
        </Directory>
</IfModule>
```
-------------------------

and my local .htaccess contains (as given by eruby's website):
-------------------------
```
DirectoryIndex index.rhtml index.html index.htm
AddHandler rubypage .rhtml
Action rubypage /eruby.cgi
```
--------------------------

---

