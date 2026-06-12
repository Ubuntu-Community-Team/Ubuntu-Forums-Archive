---
title: "Unable to change php version using phpbrew and linuxbrew"
date: 2014-03-07
forum: General Help
---

### Post by jason58 on 2014-03-07
Greetings!

I installed Ubuntu 12.04 and updated php to the latest 5.5 ([https://launchpad.net/~ondrej/+archive/php5](https://launchpad.net/~ondrej/+archive/php5)).

I've since learned this isn't the best way to go, as I discovered methods like linuxbrew and phpbrew for handling multiple versions of php -- which would be awesome.

Now I'm trying to get this going, but have the strange issue where I do "phpbrew use 5.4.20" and pear says it's using 5.4.20, if I do phpversion() from a script, it still says I'm using 5.5.8-3+sury.org~precise+2. I've been able to get along up to this point, but now I'm not sure how to troubleshoot this.

I did notice that, at the end of installing 5.4.20 ($ phpbrew install 5.4.20 +default) I was given "sh: 1: pear: not found". Strange thing is, when I check ($ pear version) it says php is 5.4.20.


Very strange. Any help is greatly appreciated!
[COLOR=#444444][FONT=Open Sans]
~Jason[/FONT][/COLOR]

---

### Post by dragonfly41 on 2014-03-07
I can think of one possibility .. you might have multiple versions of php.ini stored .. 
or even multiple versions of php ..

Try sudo updatedb

and after that (this command will take some minutes to complete without any action seen in the terminal)

run .. sudo locate php.ini

---

### Post by jason58 on 2014-03-07
Thanks Dragonfly41,

I did that and it returned the following:
```
/etc/php5/apache2/php.ini/etc/php5/cli/php.ini
/home/jason/.phpbrew/build/php-5.4.20/php.ini-development
/home/jason/.phpbrew/build/php-5.4.20/php.ini-production
/home/jason/.phpbrew/php/php-5.4.20/etc/php.ini
/usr/share/php5/php.ini-development
/usr/share/php5/php.ini-production
/usr/share/php5/php.ini-production.cli
```

Does that provide any insight?

---

### Post by dragonfly41 on 2014-03-07
Sorry I've been busy and I've just returned to the forum ..

as I guessed you have these active php.ini files

/etc/php5/apache2/php.ini ... used by your server
/etc/php5/cli/php.ini     ... used by php command line for scripts

/home/jason/.phpbrew/php/php-5.4.20/etc/php.ini

I would run phpinfo() in your server docbase to see the php.ini path you are using.

---

### Post by jason58 on 2014-03-12
I found the tentative solution on stack overflow [1]. The reason I can't try this solution is that (according to another source [2]), that isn't supported on apache 2.4.6. Bummer.

Is it possible to manually re-direct apache to the other location? You were right that I have two php.ini locations.

Open to better solutions, too! :)

[1]: [http://stackoverflow.com/questions/20584156/tell-apache-to-use-a-specific-php-version-installed-using-phpbrew](http://stackoverflow.com/questions/20584156/tell-apache-to-use-a-specific-php-version-installed-using-phpbrew)
[2]: [http://stackoverflow.com/questions/18566774/how-to-intstall-apxs-module-on-apache-2-4-6](http://stackoverflow.com/questions/18566774/how-to-intstall-apxs-module-on-apache-2-4-6)

---

### Post by dragonfly41 on 2014-03-12
I'm sorry but I'm not well read on this topic and  don't understand what you are trying to do.

What is apxs module used for?

What are your operational needs?   Why phpbrew?

Hopefully others will step in to help you .. but you need to clarify what you're doing.

---

### Post by jason58 on 2014-03-13
Hi dragonfly41,

Sorry, I didn't explain myself well.

As you pointed out, I have two versions of php running on my machine &#8212; the cli and apache versions. Sure enough, when I run phpinfo(), the server is using the apache2/php.ini version, and phpbrew is controlling the cli version. From what I understand, the way to run this is to use the apxs module, which is an APache eXtenSible module, which would (if I understand correctly), allows phpbrew to redirect apache2 to a different php.ini.


The reason I'm doing all this because, as a web developer, it's extremely useful to me if I can precisely match the version of php the remote server is running to make sure there's no unexpected bugs due to a difference in php versions. I did some research and understood that phpbrew, running on top of homebrew (linuxbrew fork for us), was a great way to do this.


Hope this makes sense! If I'm still unclear please let me know. Thanks!

---

### Post by dragonfly41 on 2014-03-13
I haven't had much need for dynamic switching of php versions ...   I would hazard a guess that you might do this by using a bash script to change aliases to different php.ini files ...

However I found this thread ..

[http://stackoverflow.com/questions/524508/how-can-one-run-multiple-versions-of-php-5-x-on-a-development-lamp-server](http://stackoverflow.com/questions/524508/how-can-one-run-multiple-versions-of-php-5-x-on-a-development-lamp-server)

one suggestion is to run different PHP versions using fast cgi on different ports

or even multiple virtual server instances

or using phpfarm ..  [http://cweiske.de/tagebuch/Introducing%20phpfarm.htm](http://cweiske.de/tagebuch/Introducing%20phpfarm.htm)

and in ubuntu ... [http://dbforch.wordpress.com/2010/05/21/apache2-fastcgi-multiple-php-versions-ubuntulucid-10-04/](http://dbforch.wordpress.com/2010/05/21/apache2-fastcgi-multiple-php-versions-ubuntulucid-10-04/)


But I might be way off target here.

---

### Post by dragonfly41 on 2014-03-13
[color=maroon]

Are you aware of Composer for php dependency management?

[http://www.slideshare.net/Seldaek/dependency-management-with-composer](http://www.slideshare.net/Seldaek/dependency-management-with-composer)

here you can specify the exact php version needed to run a package.

[www.Laravel.com](www.Laravel.com) (which I use for php development) uses composer extensively.

[/color]

---

