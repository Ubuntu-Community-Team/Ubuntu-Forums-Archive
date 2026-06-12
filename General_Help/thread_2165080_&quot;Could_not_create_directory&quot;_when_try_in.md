---
title: "&quot;Could not create directory&quot; when try install wordpress theme."
date: 2013-08-03
forum: General Help
---

### Post by Greg_Lafrance on 2013-08-03
[COLOR=#333333][FONT=Helvetica Neue]When installing a wordpress theme I get a message "Could not create directory": [/FONT][/COLOR]

[COLOR=#333333][FONT=Helvetica Neue]Installing Theme: Responsive 1.9.3.5 [/FONT][/COLOR]

[COLOR=#333333][FONT=Helvetica Neue]Downloading install package from [http://wordpress.org/themes/download/responsive.1.9.3.5.zip…](http://wordpress.org/themes/download/responsive.1.9.3.5.zip…) [/FONT][/COLOR]

[COLOR=#333333][FONT=Helvetica Neue]Unpacking the package… [/FONT][/COLOR]

[COLOR=#333333][FONT=Helvetica Neue]Could not create directory. /srv/www/wp-content/mysite.com/upgrade[/FONT][/COLOR]

---

### Post by lisati on 2013-08-03
I've seen similar messages before on Wordpress sites I've run: they usually mean that Wordpress needs write permissions on the folder where it's putting the files.

By the way, did you reinstall Wordpress after asking the question in your [other thread]("http://ubuntuforums.org/showthread.php?t=2165041&p=12743924#post12743924"), or is this a fresh install in another location?

---

### Post by Greg_Lafrance on 2013-08-03
I uninstalled and re-installed many times, just trying to get beyond an ftp credentials issue. 

[COLOR=#333333][FONT=Helvetica Neue]Someone suggested adding this to wp-config.php: [/FONT][/COLOR]

[COLOR=#333333][FONT=Helvetica Neue]define('FS_METHOD','direct'); 

That helped with the ftp credentials issue, but now I have the issue for this post.
[/FONT][/COLOR]

---

