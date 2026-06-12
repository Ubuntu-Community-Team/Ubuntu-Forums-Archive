---
title: "installing SugareCRM."
date: 2007-12-28
forum: General Help
---

### Post by strip21 on 2007-12-28
Dear All

I have setup and installed a Server 7.10 and put a GUI on it so i just makes it easyer. (i love making life easyer). Now i have been given the job of installing SugarCRM. (open source customer relationship management). 

This needs Apache server PHP and MySQL. This i have installed (LAMP). I do get "It works" when i go to the web page. So i guess the web server is working. As for PHP or MySQL im have no i dear. All the install doc said is....


  Copying Sugar Files to the Web Server
    After you download Sugar, you need to unzip the files and set permissions.
    1. Locate your webroot directory on your Web server. This is the directory on your
        web server where publicly accessible files are made available by your Web server.
        Common locations for Web root includes:
        /var/www/html/ (Linux/Apache)
        C:\Inetpub\wwwroot\ (Windows/IIS)
        C:\Program Files\Apache Group\Apache\htdocs\ (Windows/Apache)
        /Library/Web server/Documents/ (MacOS X/Apache)
    2. Unzip the Sugar zip file into your webroot. A directory is automatically created
        within webroot.
    3. Rename this directory at any time.
    4. Set permissions on the Sugar files. The following directories, all subdirectories,
        and files must be made writable by your Web server user:
            cache
            custom
            data
            modules
            config.php
        The system user that your Web server uses to access files in your Webroot varies
        depending on your operating system configuration. Common Web server users
        include:
            apache (Linux/Apache)
            nobody (Linux/Apache)
            IUSR_computerName (Windows/IIS)
If you are unsure of your Web server user, consult your system administrator.

now i have copied the SugarCRM to the 

**/var/www/apache2-default/SuagerCE-full-5.0.0**

and all i keep getting is firefox keeps asking to download the install.php file. I have logged in as "root" and changed all the file permissions so that everbody can access this path/directory. 

Is there a way of checking that PHP is there and that MySQL is there? Is this something to do with a Apache Server or is it a Sugar issue. 

Any comments would be nice, thanks

poor old admin

---

### Post by strip21 on 2008-01-03
i have now have this working. 

It was Apache 2.2.4 and PHP 5.2.3-1 not talking. Once i have reinstalled them both and sorted out the password for MySQL. i still can not open the install.php file. i opened the directory and as if by magic all is now working. 
So im not sure if it was the reinstalling or if it was me just opening up the location and not the file that made it install. 

This also worked for Joomla too. I now have a CRM and a CMS working and thats a 1st for me.

---

### Post by mcginnis_john on 2008-01-30
strip21,

Nothing personal there fella but why work so hard?? If you don't mind running 6.06 LTS there is already a .deb for sugarcrm! From a standing start with the plain vanilla LTS installed. At command line --

```
deb http://archive.canonical.com/ubuntu dapper-commercial main

apt-get update

apt-get install sugarcrm
```

apt will work out all the dependencies (at least it did for me.) And of course you could do the same thing in the Adept Manger GUI. Just open repositories and do an add with the deb line above. Then do a fetch updates. after that. Filter on 'sugarcrm'. 

Downside? Well the biggest is that its version 4.5.0.

---

