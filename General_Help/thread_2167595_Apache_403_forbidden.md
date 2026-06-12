---
title: "Apache 403 forbidden"
date: 2013-08-14
forum: General Help
---

### Post by andrewgerm on 2013-08-14
Good day all
I've been puzzling over this issue for several days now, and while I've found many solutions online (including these forums) none of those have worked for me yet.

The issue is, I have a few sites in folders below /var/www
The one main site in particular runs off a MySQL database, with rewritten URLs. The CSS and most of the images / graphics are not loading. The only images that are loaded are those that are from files manipulated by a script, and displayed as thumbnails.

I have my log level set to debug, but see no errors in either the access.log or error.log files. If I view the page source, and then follow a link to e.g. one of the CSS files, I get a 403 forbidden error.

The directories are owned by www-data, and this is the user / group apache is running under.
I am able to access the files in question via SMB. Sever name has been set, as well as setting allowoveride, not allowing multiviews (although I've tried this both ways). As an experiment, with the same issues, I copied all directories to the /home/sername/www and had the same results.

My first venture into a headless server, so while learning a ton, I guess I've missed something too. I am doing everything via SSH.
Any suggestions would be greatly appreciated!!

---

### Post by zero2xiii on 2013-08-14
Hay,

One thing I have found with designing and hosting my own website was that you actually need to make images "executable" to be able to display properly. There is a different term used by web developers but essentially it is the exc flag that needs to be set (for everyone).

Try that and see if that solves your issue.

EDIT:
Folders, not files. See here for my thread on a similar issue:
[http://ubuntuforums.org/showthread.php?t=2131374&p=12584098#post12584098](http://ubuntuforums.org/showthread.php?t=2131374&p=12584098#post12584098)

> oh, that's a good point, you need to have execute permission on directories to be able to access their contents. You shouldn't need execute permission on the images though.

 (permissions on directories are slightly different from the ones used on files, the "execute" is often called "search permission" as it's required to access the inode information of files and subdirectories. For example read permission allows you to list a directory's contents, but to cd into it or access the files using many tools you also need the execute bit to be set. And it also needs to be set for all the parent directories as well...)

---

### Post by Skateinmars on 2013-08-14
My guess is a permission problem.
If you've already checked the owner of the files then take a look at their rights.

To be sure of the problem you can also change the log verbosity for apache : [http://httpd.apache.org/docs/2.2/en/logs.html](http://httpd.apache.org/docs/2.2/en/logs.html)
You could then look at /var/log/apache and see what exactly is going wrong.

---

### Post by andrewgerm on 2013-08-14
Thank you both for the replies. I have read through the links too, to be sure.
I do believe it is a permissions issue, but to trace it seems to be the issue.

To the best I can see, www-data owns the /var/www directory, and all those inside.
Permissions on all files are set to 775, also to the best of my knowledge.
Files have Owner RWE, Goups has RWE and public has RE

No CSS, direct image loads, or direct photo loads (as in not shown in an altered state by my thumbnail scripts) are showing.

I have the Apache log level set to debug, but have not seen any errors in the error or access logs.
About all I'm seeing is a few zlib items and their compression levels.

The only way to see the 403 is to view the source, and then click on the css reference in the source.

---

### Post by Habitual on 2013-08-14
rwx NOT RW"E". ;)
[http://www.cyberciti.biz/faq/apache-403-forbidden-error-and-solution/](http://www.cyberciti.biz/faq/apache-403-forbidden-error-and-solution/)

---

### Post by andrewgerm on 2013-08-14
@Habitual

Thank you for the link (and syntax correction, noted!!) :)
To the best of what I can see, everything from that link is in order. And have set my apache2.conf log level to debug as well as in the site config, and no errors in there at all.

All file and directory permissions seem in place.
Directories are owned by www-data (which apache runs under) with drwxrwxr-x
And files are all owned by www-data with rwxrwxr-x

Altering the AllowOverride to match those in the link did cause a 500 error. Leaving it as 'AllowOverride all' continues to work as before.

Still no CSS or other files loading though.

---

### Post by Habitual on 2013-08-15
> **andrewgerm said:**
> Good day all
I've been puzzling over this issue for several days now, and while I've found many solutions online (including these forums) none of those have worked for me yet.

The issue is, I have a few sites in folders below /var/www
The one main site in particular runs off a MySQL database, with rewritten URLs. The CSS and most of the images / graphics are not loading. The only images that are loaded are those that are from files manipulated by a script, and displayed as thumbnails.

I have my log level set to debug, but see no errors in either the access.log or error.log files. If I view the page source, and then follow a link to e.g. one of the CSS files, I get a 403 forbidden error.

The directories are owned by www-data, and this is the user / group apache is running under.
I am able to access the files in question via SMB. Sever name has been set, as well as setting allowoveride, not allowing multiviews (although I've tried this both ways). As an experiment, with the same issues, I copied all directories to the /home/sername/www and had the same results.

My first venture into a headless server, so while learning a ton, I guess I've missed something too. I am doing everything via SSH.
Any suggestions would be greatly appreciated!!

andrewgerm:

No worries.
Generally speaking it is good practice to use
755 for directories and
644 for files.

does the apache error log(s) file show any 503 errors?

```
zgrep 503 /var/log/apache/*
```
should show them.

you said 
[QUOTE=andrewgerm]The directories are owned by www-data[/QUOTE] but are the files below them owned by www-data as well?
and
[QUOTE=andrewgerm]The one main site in particular runs off a MySQL database, with  rewritten URLs. The CSS and most of the images / graphics are not  loading[/QUOTE]
is this a wordpress site?

---

### Post by andrewgerm on 2013-08-15
@Habitual
A big thank you, once again.

I tried you command to find the 403 errors (I tried both ways, but guess it should be 403 and not 503?)
Nothing on either 403 or 503, although some old entries from way back, I did browse the site just prior to running the command, as I had changed the log reporting level from warn to debug this week (these errors are from last week).

```
tail -f /var/log/apache2/error.log
```
This gives entries showing that the various JS and CSS files are being deflated by mod-deflate.

As mentioned though, if I view the site code, and click on a link to a CSS file, this is when the 403 is displayed.

This site will have WordPress integrated, but currently it is the propriety code (excluding WordPress, etc.) that is accessing the MySQL.

Both directories and files are owned by www-data. My username (not running as root) is in the www-data group as well.

Still puzzling over things. A big thank you again :)

---

### Post by Habitual on 2013-08-15
> **andrewgerm said:**
> if I view the site code, and click on a link to a CSS file, this is when the 403 is displayed.


andrewgerm:

Can you clarify the above snippet? It sounds like the site displays fine, but some CSS element when viewed as "site code" contains a reference
to a resource that is giving you the 403?

something like right-mouse click (on my own site) > "View Page Source" in Firefox...shows me...?
```

<script type="text/javascript">
//<=!=[=C=D=A=T=A=[
try{if (!window.CloudFlare) { var CloudFlare=[{verbose:0,p:0,byc:0,owlid:"cf",mirage:{responsive:0,lazy:0},mirage2:0,oracle:0,paths:{cloudflare:"/cdn-cgi/nexp/abv=833003145/"},atok:"440f09720223f72397ee1138ab381fa1",zone:"bournetoraiseshell.com",rocket:"a",apps:{}}];document.write('<script type="text/javascript" src="//ajax.cloudflare.com/cdn-cgi/nexp/abv=340409193/cloudflare.min.js"><'+'\/script>')}}catch(e){};
//]=]=>
</script>
<link rel="canonical" href="http://www.bournetoraiseshell.com/">
<link rel="search" href="http://www.bournetoraiseshell.com/search.php" title="Advanced Search">
<link rel="stylesheet" type="text/css" href="http://www.bournetoraiseshell.com/layout/professional/style.css">
```
and I this were your "site code" and clicked something similar to 
[http://www.bournetoraiseshell.com/layout/professional/style.css](http://www.bournetoraiseshell.com/layout/professional/style.css)
you get a 403?

Good catch on the [45]03 error detail.

output of these 2 commands please?
```
ls -ld /var/www/*
find `pwd` /var/www/ -name .htaccess

```

Suggestion: Quit messing with user group permissions at this time
YOU don't "need" to be in any additional groups to isolate and troubleshoot this permissions error.

---

### Post by andrewgerm on 2013-08-16
@habitual

Thank you again for the reply.

Apologies. I'll try clarify what I meant about the CSS. If I load the site over the local network, the pages are showing, and grabbing the relevant data from MySQL. The site colours, formatting and images (those of the menu, logo, etc.) are not showing. Only images that are generated on-the-fly via a script are showing up. I am using Chromium, so right clicking and selecting view source displays the page code. From the source view, I can click on the links to the CSS files, and that is when I am seeing the 403 Forbidden error.

Following your link to the CSS file, is what I would expect to see, yes. I have my CSS and JS laid out for easy reading when developing, but once ready to publish, I min them.

Out put from the commands:
ls -ld /var/www/*
```
-rwxrwxr-x  1 www-data www-data   22 Jul 30 18:21 /var/www/info.phpdrwxrwxr-x 18 www-data www-data 4096 Jul 30 18:23 /var/www/samdb
drwxrwxr-x  3 www-data www-data 4096 Jul 30 18:24 /var/www/samdb-admin
drwxrwxr-x  6 www-data www-data 4096 Jul 30 18:24 /var/www/samdb-emailed
drwxrwxr-x  2 www-data www-data 4096 Jul 30 18:24 /var/www/test
drwxrwxr-x  3 www-data www-data 4096 Jul 30 18:24 /var/www/videolist

```

find 'pwd' /var/www/ -name .htaccess
/var/www/samdb/.htaccess
[/CODE]



The site in question is the /var/www/samdb site. Others are just code portions, testing, etc.

And staying away from user-groups :)

The index is specified in the .htaccess. This entire site worked correctly prior, but with a massive server failure on my development server, I have had to restore everything to a new machine.

Apache enabled site conf, for reference:
```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	ServerName SAMDB-Dev


	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks
		AllowOverride all
		Order allow,deny
		allow from all
	</Directory>


	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>


	ErrorLog ${APACHE_LOG_DIR}/error.log


	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel debug


	CustomLog ${APACHE_LOG_DIR}/access.log combined


	Alias /doc/ "/usr/share/doc/"
	<Directory "/usr/share/doc/">
		Options Indexes MultiViews FollowSymLinks
		AllowOverride None
		Order deny,allow
		Allow from all
	</Directory>


</VirtualHost>
```


The info.php file contains only the phpinfo(); function, and loads. When loading the default address for the server over the network, I see the directory listing of folders, and can successfully navigate each. Mod-rewrite is also working as it should.

A huge thank you, once again. I'm glad to see I'm only one of many having this issue, but unfortunately none of the current proposed solutions has worked (else I'm missing something that's probably obvious). First foray into a headless server :)

---

### Post by Lars Noodén on 2013-08-16
> **andrewgerm said:**
> Out put from the commands:
ls -ld /var/www/*
```
-rwxrwxr-x  1 www-data www-data   22 Jul 30 18:21 /var/www/info.php
drwxrwxr-x 18 www-data www-data 4096 Jul 30 18:23 /var/www/samdb
drwxrwxr-x  3 www-data www-data 4096 Jul 30 18:24 /var/www/samdb-admin
drwxrwxr-x  6 www-data www-data 4096 Jul 30 18:24 /var/www/samdb-emailed
drwxrwxr-x  2 www-data www-data 4096 Jul 30 18:24 /var/www/test
drwxrwxr-x  3 www-data www-data 4096 Jul 30 18:24 /var/www/videolist

```

No files or directories should be owned by the user www-data or in the group www-data.  Their purpose is to provide an unprivileged user and group for the web server processes.  That purpose is defeated if httpd serves up files and directories writeable to www-data.   Using www-data for files and directories gives the web server permission to write those files and directories.  That permission extends to unwanted guests who figure out how to get the web server to write or execute these files.  If that happens it is game over and the server is owned.  

To prevent such risk, the files and directories should be owned by some other user and group than www-data.  The default is user root and group root.  But if you are the only user on that server, you can own the files yourself.  

All that's needed for httpd to serve these files to the public is for the directories and files to be readable by the web server (httpd).  That can be done with 775, 755, or 555 for the directories and 664, 644, or 444 for the files.

---

### Post by andrewgerm on 2013-08-16
@Lars

Thank you for that. I had been following several forum posts (not from these forums, as this was when they were down) to try resolve the original issue, and most were saying to do this. I didn't recall needing to do that last time, but as mentioned, I was running via GUI.

I assume it would then be save to remove myself from the www-data group, and to take ownership of the files? Should I do these are root, or as my own user? I am the only user on the server for most things. Any other access / use of the server is just viewing of served web pages, and items accessing and using the DB.

Thanks for that.

---

### Post by Lars Noodén on 2013-08-16
It would be fine to remove yourself from the group www-data.  That group can be empty or have just the user www-data.  As for the files and directories under /var/www, if you are the only user of that machine, then it is fine if you take ownership of them.  If you are sharing with other users then some work with groups is needed.  But if you are the only user then [chown](http://manpages.ubuntu.com/manpages/raring/en/man1/chown.1.html) is enough.  

Also when passing data to or from the database, always assume that the incoming data is 'tainted' or insecure and must be cleaned.  That is to say process it in such a way that it is rendered harmless before passing it on to the system or the database.  Perl and a few others can track tainted variables, if the right mode or modules are used.  It may go without saying, but things that go without saying all too often go unsaid.  ;)

---

### Post by andrewgerm on 2013-08-16
@Lars

Thank you again. I took ownership with my username.
The 403 still persists, so taking a big guess here that it may be config related, and not permissions?

I hear you on the 'never trust user input' and that was something I spent a lot of time on initially. The site in question is running php, so spent a lot of time reading up on other users comments on cleaning that data.

---

### Post by Lars Noodén on 2013-08-16
It's looking like it might be a configuration problem.  What do the error logs have to say?  You could try opening up a terminal and using [tail](http://manpages.ubuntu.com/manpages/raring/en/man1/tail.1.html) to watch the logs live as you bring up the error in your browser.

```

tail -f /var/log/apache2/error.log 

```

The logs should tell you one way or another whether it was "client denied by server configuration" or "file permissions deny server access"

Edit: I see that was asked already.  Can you post the exact error message from the log?

---

### Post by andrewgerm on 2013-08-16
@Lars
Thank you again.

This is the output of the tail -f /var/log/apache2/error.log. Updated from the previous one in an earlier post.
My warn level is set to debug.

```
[Fri Aug 16 17:05:27 2013] [debug] mod_deflate.c(615): [client 192.168.0.6] Zlib: Compressed 12476 to 3803 : URL /samdb/index.php, referer: http://samdb-dev.local/samdb/user/182[Fri Aug 16 17:05:28 2013] [debug] mod_deflate.c(615): [client 192.168.0.6] Zlib: Compressed 304 to 229 : URL /samdb/css/default.css, referer: http://samdb-dev.local/samdb/
[Fri Aug 16 17:05:28 2013] [debug] mod_deflate.c(615): [client 192.168.0.6] Zlib: Compressed 315 to 238 : URL /samdb/css/jquery.bubblepopup.css, referer: http://samdb-dev.local/samdb/
[Fri Aug 16 17:05:28 2013] [debug] mod_deflate.c(615): [client 192.168.0.6] Zlib: Compressed 311 to 234 : URL /samdb/css/jquery.twitter.css, referer: http://samdb-dev.local/samdb/
[Fri Aug 16 17:05:28 2013] [debug] mod_deflate.c(615): [client 192.168.0.6] Zlib: Compressed 317 to 240 : URL /samdb/js/jquery.bubblepopup.min.js, referer: http://samdb-dev.local/samdb/
[Fri Aug 16 17:05:28 2013] [debug] mod_deflate.c(615): [client 192.168.0.6] Zlib: Compressed 314 to 237 : URL /samdb/js/jquery.tagcloud.min.js, referer: http://samdb-dev.local/samdb/
[Fri Aug 16 17:05:28 2013] [debug] mod_deflate.c(615): [client 192.168.0.6] Zlib: Compressed 305 to 231 : URL /samdb/js/jquery.min.js, referer: http://samdb-dev.local/samdb/
[Fri Aug 16 17:05:28 2013] [debug] mod_deflate.c(615): [client 192.168.0.6] Zlib: Compressed 303 to 229 : URL /samdb/js/homepage.js, referer: http://samdb-dev.local/samdb/
[Fri Aug 16 17:05:28 2013] [debug] mod_deflate.c(615): [client 192.168.0.6] Zlib: Compressed 305 to 228 : URL /samdb/images/samdb.png, referer: http://samdb-dev.local/samdb/



```

---

### Post by Lars Noodén on 2013-08-16
Thanks.  I'm not seeing an error in that part of that log.  Do you have multiple error logs set up for the multiple virtual hosts?

---

### Post by Habitual on 2013-08-16
andrewgerm:

I'm bowing out here as Lars and others are more qualified than I am to troubleshoot this issue on your OS.
I was merely looking for the obvious. ;)

Peace.

---

### Post by Lars Noodén on 2013-08-16
Can you give an example of a URL which works but has a corresponding CSS link (or other) that fails with a 403?

Also, I see .htaccess mentioned above.   Later, if you have no special reasons for keeping a separate .htaccess file, it would help to move its contents back into the corresponding .conf file in /etc/apache2/sites-available/  One reason is that it simplifies maintenance and debugging by keeping the vhost's configurations all in the same place.  The .htaccess files are useful when sharing administration of a site without giving full access to the main configuration file, but if it's just you taking care of the site then .htaccess just means more pieces to keep track of.  

@Habitual: many eyes make all bugs shallow

---

### Post by andrewgerm on 2013-08-16
@Habitual
A big thank you. I thought I had gone through all the obvious, but you made many suggestions that I wouldn't have thought of. I thank you!!!

@Lars
Thank you again too.
Not too sure what you are looking for with the URL. Every page on the site is missing the 'appearance' from not loading CSS files. On each page, if I click 'view source' and then click on the URL for a CSS file in that source, I get the 403.

The URLs for the CSS are correct, once loaded.
E.g. going to [http://dev.local/samdb](http://dev.local/samdb) will load the site, minus CSS
Then, view source and following those will lead to [http://dev.local/samdb/css](http://dev.local/samdb/css)
I have all CSS files under a directory below the main site, so these are correct.

As mentioned, the site was working on the previous server, which sadly died suddenly one morning.

This is the development server, for all my sites, and several client sites. As mentioned, I'm in the process of restoring all the sites. The .htaccess would need to remain as is, due to rewritten URLs, and for it to be uploaded to a hosting server when edited.

---

### Post by Habitual on 2013-08-16
> **Lars Noodén said:**
> @Habitual: many eyes make all bugs shallow

;)

---

### Post by Lars Noodén on 2013-08-16
Thanks.  About the URLs, I was looking for the site structure.  The errors have to be going somewhere to some log file.  

Can you hunt for the log files using [find](http://manpages.ubuntu.com/manpages/raring/en/man1/find.1.html)?

```

find /var/www/ -name .htaccess -exec grep -i log {} \;
find /etc/apache2/ -name *.conf -exec grep -i errorlog {} \;

```

If we can find where the errors are getting logged, we can read the exact error message and, hopefully, thus fix it.

---

### Post by andrewgerm on 2013-08-16
@Lars

Once again, thank you!!

The first command returned nothing.
The second returned:

```
# ErrorLog: The location of the error log file.# If you do not specify an ErrorLog directive within a <VirtualHost>
ErrorLog ${APACHE_LOG_DIR}/error.log



```

I have not changed the location of any log file for Apache, and do see the error.log file adding entries, etc. whenever I view the site (the zlib entries). The access.log doesn't show any errors either, just the browser type, etc. that I'm using now on the remote PC.

My distro is Ubuntu x64 13.04, with all latest updates, if that says anything.
Logs are under /var/log/apache2

---

### Post by Lars Noodén on 2013-08-16
Just to go back to the permissions question again, the top level directories looked ok, but then again they are also serving the web pages correctly.  However, the subdirectories are not serving the css correctly, but strangely not producing an error in the logs.  What happens if you touch up the read permissions for the subdirectories and their files?

```

find /var/www/ -type d -exec chmod 755 {} \;
find /var/www/ -type f -exec chmod 644 {} \;

```

I'm still puzzled as to where the errors are getting logged.  The grep should have produced something like this:

```

$ find /etc/apache2/ -name *.conf -exec grep -i errorlog {} \;
# ErrorLog: The location of the error log file.
# If you do not specify an ErrorLog directive within a <VirtualHost>
ErrorLog ${APACHE_LOG_DIR}/error.log
		ErrorLog ${APACHE_LOG_DIR}/error.log
	ErrorLog ${APACHE_LOG_DIR}/error.log
	ErrorLog ${APACHE_LOG_DIR}/error.log

```

---

### Post by andrewgerm on 2013-08-16
@Lars

First two commands took about 10 secs to run each. I saw no output.
I'm running all this via SSH, just btw.

I reran the command, just in-case I had done something stupid again.
Output:
```
# ErrorLog: The location of the error log file.# If you do not specify an ErrorLog directive within a <VirtualHost>
ErrorLog ${APACHE_LOG_DIR}/error.log

```

This does appear to be where I've been looking at the log file all along.

---

### Post by Lars Noodén on 2013-08-16
Running via ssh is the same as running in a local terminal.  So that's all good.

You're also looking in the right place for the error logs, according to the configuration file.  

But I'm stumped as to where the 403 error is coming from and why it is not getting logged in the log file.  Without the relevant log messages I am unable to even speculate as to the source of the 403 error.   On my spare machine I tried running apache2 in debug mode (-X) where it does not detach and become a daemon, but that provided no additional data.  All the errors still went to the log file anyway.

---

### Post by andrewgerm on 2013-08-16
@Lars
I think what I'm going to try this weekend, is move the site off the server, and place it back on, and start at the beginning with file and directory permissions.

My knowledge pales to most others here, but from experience on other systems, well, I'd like to almost say, perhaps a permission has got 'stuck' somehow, and although displaying one way, is actually another. I"m sure that doesn't make too much sense, but then again, computers like to keep things mysterious :)

Thank you again!!

---

### Post by andrewgerm on 2013-08-18
@Habitual & @Lars

First, again, a big thank you for all the information you both provided. It was most invaluable in my troubleshooting process, and I learnt quite a bit doing all of this remotely via SSH.

I have actually solved my problem, so I post this in the hopes of saving others the many days of fiddling that it has taken me. As per my previous post, I pulled the entire site down from the server to the local machine, deleted it on the server, and then uploaded it again.

This did not solve the process, but I have had a few issues with public hosts and .htaccess files for clients. I checked to be sure this had uploaded, and then opened the site again. To my dismay, everything as it was. I checked the log files, and NO error messages, even when set to debug level. The only messages there were from zlib. In an attempt to eliminate every possible avenue, I decided to go disable this. I opened .htaccess, and right at the top I have a few lines of regex to stop external sites hotlinking to large files (like sound and video) on the site, and using up all the bandwidth, and in a very noob mistake, this was set to the main live server (correctly) but having replaced the development server here at the office, I had not changed the name for the code that covers the local network.

Changing this expression to the new server name works, and the site now loads properly!!

Thank you again, and I hope this mistake of mine can indeed help others!!

---

### Post by Habitual on 2013-08-18
Well, *actually,* I was going to suggest next (before I bowed out) to rename the sole .htaccess file even for like 1 minute and retry the procedure again.
Also remember andrewgerm, that .htaccess files are hierarchical, so directives in an htaccess above it can over-ride directrive in one below it.

/var/www/.htaccess has a badly formed rewrite rule, for example...
can over-ride or cause nasty side-effects on another htaccess entry in say /var/www/somesite/.htaccess

Also, .htaccess is for use for those who don't have access to the httpd.conf file.
So now you know.

Good job! and +1

Now [B]make a backup!
[/B]```
tar -pczf /root/www_archive.tar.gz /var/www/*
```

---

### Post by andrewgerm on 2013-08-19
@Habitual

Thank you. I had actually considered removing .htaccess myself, but as the site uses rewrites for a lot of the URLs (to personalise URLs per-person) it would have been quite a task. I did comment out everything other than rewrites, but I missed the rewrite that looked for host name.

I do need to use .htaccess, as all the sites I develop are then uploaded to production servers, most of which are in shared hosting environments where the only means it a .htaccess. There isn't a root .htaccess, just one per site directory (with a few in subfolders when items such as Wordpress or a cart have been added).

Ubuntu 13.04 doesn't seem to have an http.conf file, however there is a /etc/apache2/apache.conf file.
The only change here was to alter the log level.

Thank you for the backup command line. I will be using that from the remote machine (also running Ubuntu 13.04).
In the past I would just create an archive from the Windows desktop GUI.

Now, to automate all that, and do the final tasks (including slow network performance).

Thank you both @Lars and @Habitual!!
Will go try mark this thread solved!!

---

### Post by Habitual on 2013-08-19
Andrew:

I predict you'll do just fine doing sysadmin work.
Glad it worked out.

Have a Great Day!

---

