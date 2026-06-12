---
title: "php debugger"
date: 2015-04-19
forum: General Help
---

### Post by yazvoprosywebw on 2015-04-19
1) Share how you use php debugger for ubuntu.


2) Is there a built-in text editor where php debugger.

---

### Post by pqwoerituytrueiwoq on 2015-04-19
You can use a editor like [geany]("apt:geany") that has decent syntax highlighting (so you can see your issues)
in your php server configs (this file: [FONT=courier new]/etc/php5/apache2/php.ini[/FONT] and/or [FONT=courier new]/etc/php5/cli/php.ini[/FONT])
set [FONT=courier new]display_errors[/FONT] to [FONT=courier new]On[/FONT], probably on line 479
then if this is a web server run this to apply the changes
```
sudo service apache2 reload
```
errors will now be printed on the web page instead of only in /var/log/apache2/error.log

---

### Post by Holger_Gehrke on 2015-04-19
I use php5-xdebug and the Eclipse PDT (php development tool). Source level debugging including step over and step into, conditional breakpoints, watch expressions ... Only downside to this setup: Eclipse is the poster child for resource devouring monster apps that make your machine feel like an old IBM PC ( no, not even an AT, an XT ...); and you might need to have two copies of your program (one in apache, one in your eclipse workspace) and God help you if they get out of sync ...

---

### Post by yazvoprosywebw on 2015-04-19
also want to use the [COLOR=#333333][FONT=Arial]XDebug[/FONT][/COLOR]. But after installing the instructions - [netbeans]("https://netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html"), I do not understand how to run it. How to open the interface.


What is the next step after installing the program - [netbeans]("https://netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html")?

---

### Post by yazvoprosywebw on 2015-04-19
> **Holger_Gehrke said:**
> I use php5-xdebug and the Eclipse PDT (php development tool). Source level debugging including step over and step into, conditional breakpoints, watch expressions ... Only downside to this setup: Eclipse is the poster child for resource devouring monster apps that make your machine feel like an old IBM PC ( no, not even an AT, an XT ...); and you might need to have two copies of your program (one in apache, one in your eclipse workspace) and God help you if they get out of sync ...

I also want to use the XDebug. But after installing the instructions - [netbeans]("https://netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html"), I do not understand how to run it. How to open the interface.


What is the next step after installing the program - [netbeans]("https://netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html")?
+

---

### Post by dragonfly41 on 2015-04-19
I'm now revisiting xdebug to run not in Eclipse (too bloated for me) but in Sublime Text 3 (evaluation free).

[http://www.sitepoint.com/debugging-xdebug-sublime-text-3/](http://www.sitepoint.com/debugging-xdebug-sublime-text-3/)

Until recently I  used Geany extensively but most of the examples I now see in Laravel5 framework seem to use either Sublime Text or Phpstorm.

I've also used Aptana Studio which seems lighter weight than Eclipse.

Also see the Firefox add-on ... [https://addons.mozilla.org/EN-uS/firefox/addon/the-easiest-xdebug/](https://addons.mozilla.org/EN-uS/firefox/addon/the-easiest-xdebug/)

[Later edit]

This is useful for viewing xdebug output logs ...

[https://naveensnayak.wordpress.com/2013/06/26/setting-up-kcachegrind-in-ubuntu/](https://naveensnayak.wordpress.com/2013/06/26/setting-up-kcachegrind-in-ubuntu/)


[and another edit]

Do take note that the netbeans tutorial is very old ..

> This tutorial shows how to configure the PHP development environment in the Ubuntu operating system (7.10 and later)

---

### Post by Holger_Gehrke on 2015-04-19
XDebug is a php module. You can install it using```

sudo apt-get install php5-xdebug
```
That should install the debugger module and a configuration snippet in /etc/php5/conf.d/. The options you can set there are documented on xdebug.org. The real problem - as I recall from doing it on Eclipse - is to get your IDE to talk to xdebug, and since I'm not using netbeans, I can't talk you through this.  But [https://rtcamp.com/tutorials/php/xdebug-netbeans/](https://rtcamp.com/tutorials/php/xdebug-netbeans/) seems like it's a starting point; looks a bit like the stuff I had to work out on Eclipse, although some of it looks like it expects a slightly ... different ... setup of apache than I use.

---

### Post by yazvoprosywebw on 2015-04-19
> **Holger_Gehrke said:**
> XDebug is a php module. You can install it using```

sudo apt-get install php5-xdebug
```
That should install the debugger module and a configuration snippet in /etc/php5/conf.d/. The options you can set there are documented on xdebug.org. The real problem - as I recall from doing it on Eclipse - is to get your IDE to talk to xdebug, and since I'm not using netbeans, I can't talk you through this. But [https://rtcamp.com/tutorials/php/xdebug-netbeans/](https://rtcamp.com/tutorials/php/xdebug-netbeans/) seems like it's a starting point; looks a bit like the stuff I had to work out on Eclipse, although some of it looks like it expects a slightly ... different ... setup of apache than I use.

1 step) i use [rtcamp.com/tutorials/php/xdebug-netbeans/]("https://rtcamp.com/tutorials/php/xdebug-netbeans/") and install: sudo apt-get install php5-xdebug

2 step) ```
Appendix 'vim' can be found in the following packages: * vim
* Vim-gnome
* Vim-tiny
* Vim-athena
* Vim-gtk
* Vim-nox
Try: sudo apt-get install <selected package>

```

what to do?

---

### Post by Holger_Gehrke on 2015-04-19
If you're not familiar with vim, you can use any editor you are familiar with instead of it. Use the keys "esc" ":" "q" "!" "enter" to exit vim. But before you create that file in another editor, take a look in '/etc/php5/' whether the directory 'fpm' and 'fpm/conf.d' actually exist. Depending on your configuration and Ubuntu version the file with the settings for xdebug might be in some other place. You should check your php.ini to see from where it includes configuration snippets. There should already be a minimal xdebug somewhere. On my system (Ubuntu 12.04, apache 2.22 with prefork mpm) the xdebug configuration sits in '/etc/php5/conf.d/xdebug.ini' and I think it got there during installation.

---

### Post by yazvoprosywebw on 2015-04-19
how to open the interface of the xdebug? Share a link to instructions

I can open gedit, firefox other applications, but how do I open xdebug?

---

### Post by Holger_Gehrke on 2015-04-19
> **yazvoprosywebw said:**
> how to open the interface of the [COLOR=#000000]xdebug[/COLOR]? Share a link to instructions

I can open gedit, firefox other applications, but how do I open [COLOR=#000000]xdebug?[/COLOR]

It doesn't have an interface per se, but while a php-script is running the debugger listens on the port set in the configuration for commands. That is why you need some client for the debugger. That means either an IDE that knows how to "talk" to xdebug or the command line client that is included with the source distribution of xdebug (I don't know whether there's a package of that, but I doubt it; it's mostly useless except as an example of how to communicate with the debugger).

---

### Post by scoon on 2015-04-20
> **yazvoprosywebw said:**
> how to open the interface of the xdebug? Share a link to instructions

I can open gedit, firefox other applications, but how do I open xdebug?

[http://xdebug.org/docs/]("http://xdebug.org/docs/")  is a link to the xdebug documents.  I use xdebug with eclipse and netbeans.  The documentation is complete and really should get you comfortable with using xdebug in whatever you decide to code with.

---

