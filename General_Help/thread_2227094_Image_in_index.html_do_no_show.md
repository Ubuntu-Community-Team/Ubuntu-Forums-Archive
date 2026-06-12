---
title: "Image in index.html do no show"
date: 2014-05-30
forum: General Help
---

### Post by transition_code on 2014-05-30
[COLOR=#000000][FONT=Verdana]I've created two virtual hosts as instructed in "Configuring Name-based Virtual Hosts" in "[https://library.linode.com/hosting-website#sph_configuring-name-based-virtual-hosts](https://library.linode.com/hosting-website#sph_configuring-name-based-virtual-hosts)" document. As per "[https://library.linode.com/web-servers/apache/2.2-2.4-upgrade](https://library.linode.com/web-servers/apache/2.2-2.4-upgrade)" I added the following instruction: <Directory /path/toMy/public/website/> Require all granted </Directory>
to each virtual host configuration file with the correct path.
My first site, [http://gouro.us](http://gouro.us) seems to read the index.html but does not load/show the included image???
My second site, [http://transition.blue](http://transition.blue), I have a Forbidden You don't have permission to access / on this server. error. 
If i put the <Directory instructions in apache2.conf instead then the second site display 
Index of /
[ICO]	Name	Last modified	Size	Description
[TXT]	transition.html	2014-05-27 18:05	 21K	
[DIR]	transition_fichiers/	2014-05-27 18:07	 -	
It does not load/display the html file. 
Thank you in advance.[/FONT][/COLOR]

---

### Post by mcduck on 2014-05-30
Check that all files have ownership & permissions that allow Apache to access them. (It's running as it's own user, not as you or root, so depending on your setup you need to have read access for *group* or *others*).

Also it seems to me that the image on the gouro.us site is outside of your configured web root directory, which is not allowed. Move it anywhere inside the website directory and things should work.

---

