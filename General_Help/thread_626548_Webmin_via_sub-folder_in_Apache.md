---
title: "Webmin via sub-folder in Apache"
date: 2007-11-29
forum: General Help
---

### Post by super_czar on 2007-11-29
I have a KUbuntu server running as a torrent downloader + CGI-Proxy + NAS server 

The KDE environment is disabled on the server as it runs headless 

I usually adminster the server using Webmin from within the home network but I also need access to it from outside

Since I have torrentflux and CGI proxy running under sub-folders in apache, I want to add webmin under a subfolder under apache (also because all ports but 80/443 are blocked from my workplace)

SO I followed this guide 

> **Webmin In A Sub-Directory Via A Proxy**
If you just want Webmin to be accessible via an URL subdirectory (like /webmin) on an Apache server without going to the trouble of configuring Apache to run the CGI scripts directly, there is a simpler method that can be used. This is also useful if your system is only accessible on port 80, and you want access to both Webmin and a normal website. The steps to follow are :

   1. Make sure mod_proxy is installed on your Apache webserver.

   2. Add the following directives to the Apache configuration file:
      ProxyPass /webmin/ [http://localhost:10000/](http://localhost:10000/)
      ProxyPassReverse /webmin/ [http://localhost:10000/](http://localhost:10000/)
      <Proxy *>
      allow from all
      </Proxy>

   3. Add the lines webprefix=/webmin and webprefixnoredir=1 to /etc/webmin/config.

   4. In /etc/webmin/config, add the line referer=apachehost, where apachehost is the hostname from the URL used to access Webmin via Apache. If the referer line already has some hosts listed, add apachehost to it.

   5. Re-start Apache to apply the configuration.

All requests to /webmin on the Apache server will then be passed through to the Webmin server on localhost port 10000. All features should work fine, including themes, with the exception of IP access control (because as far as Webmin is concerned, all connections will be coming from localhost).

But there is no webmin folder under apache (on localhost) that I can see :(

- I installed mod_proxy and loaded it(shows up in running mods)
- I added the conf file edits to /etc/apache2/apache2.conf
- Step 3 verbatim
- I wasnt sure abt step 4 (hostname from the URL used to access Webmin via Apache?) so I simply added the line as-is to the etc/webmin/config file
- restarted apache 
But no-go :(

For now, I have port mapped 443 ->10000 (default webmin port) on my router so I can access webmin by using [https://mydomain](https://mydomain) but all modules aren't accessible (e.g file download) because they
need a direct port forwarding

what could I be doing wrong here?



In addition, there is another method described on thwe webmin apache guide:

[http://www.webmin.com/apache.html](http://www.webmin.com/apache.html)
ut Iam afraid I don't clearly understand all the steps:

1- Where and how do I create the alias in step 1..I presume this means /var/www/webmin should alias to the local webmin folder...Am I right?

2- Step 3: . "Add a <Directory> section to Apache for /usr/local/webmin."
How do i do this ?


> 
Apache In A Sub-Directory
In Webmin versions 0.965 and above, it is possible to run Webmin under Apache in a subdirectory rather than at the top level of a virtual server. This means that Webmin could be accessed at a URL like [http://www.yourdomain.com/webmin/](http://www.yourdomain.com/webmin/) . The steps to take to set this up are :

   1. Create a new Alias that maps some URL path like /webmin to the directory where Webmin is installed, such as /usr/local/webmin.

   2. Add the line webprefix=/webmin to /etc/webmin/config.

   3. Add a <Directory> section to Apache for /usr/local/webmin.

   4. In the directory section, configure Apache to treat all files with the .cgi extension as CGI programs, with the AddHandler cgi-script .cgi directive.

   5. Add the directives DirectoryIndex index.cgi and Options ExecCGI to the directory section.

   6. Webmin CGI programs have their config directory passed to them in the WEBMIN_CONFIG, WEBMIN_VAR and MINISERV_CONFIG environment variables. For Apache to do this, you need to add the directives

      SetEnv WEBMIN_CONFIG /etc/webmin
      SetEnv WEBMIN_VAR /var/webmin
      SetEnv SERVER_ROOT /usr/local/webmin
      SetEnv MINISERV_CONFIG /etc/webmin/miniserv.conf

   7. Password-protect the virtual server by putting directives like AuthName Webmin
      AuthType basic
      AuthUserFile /etc/webmin/htusers
      require valid-user
      Inside the <Directory> section. The file /etc/webmin/htusers must contains users who match up with those in /etc/webmin/webmin.acl.

   8. Make all the Webmin programs owned by root and setuid with the commands
      chown -R root:root /usr/local/webmin
      chmod -R 6755 /usr/local/webmin

   9. Add the -U flag to the perl line in all the Webmin scripts. This can be easily done with the following command run from the webmin directory
      find . -name "*.cgi" -o -name "*.pl" | perl perlpath.pl "/usr/bin/perl -U" -
      This assumes that Perl is installed as /usr/bin/perl on your system.

  10. Configure Webmin to use the 'Default Webmin Theme', as Apache cannot support Webmin's theming system.

  11. Make sure that the setuid scripts cannot be run by other users on your system, by setting the permissions on /usr/local/webmin to 700 and changing its ownership to the user your webserver runs as. Otherwise any user would be able to execute any command as root by running some of the scripts

---

