---
title: "gnomebaker does not start"
date: 2007-04-12
forum: General Help
---

### Post by NT4.0 on 2007-04-12
My gnomebaker does not want to start. I ran it from the command line and the output was


(gnomebaker:5523): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
GTK Accessibility Module initialized

GThread-ERROR **: GThread system may only be initialized once.
aborting...
Aborted

I restored the system partition from older backups twice -- did not help. As I have a separate /home partition, I thought the problem should be in the config files in my home directory. Any advice?

---

### Post by zvacet on 2007-04-12
> Locale not supported by C library

[http://easylinux.info/wiki/Ubuntu_Edgy#How_to_add_locales_to_Ubuntu_the_command_line_way]("http://easylinux.info/wiki/Ubuntu_Edgy#How_to_add_locales_to_Ubuntu_the_command_line_way")

---

### Post by NT4.0 on 2007-04-13
>     * Open up a terminal 

    * Generate a /var/lib/locales/supported.d/local from /usr/share/i18n/SUPPORTED: 

cat /usr/share/i18n/SUPPORTED | grep "en\|ru" > /var/lib/locales/supported.d/local

This example shows all Russian (ru) and English (en) locales being chosen. Look through /usr/share/i18n/SUPPORTED to find the ones for you, then put them in a list, replacing en\|ru and separating each language with a \| (backslash, bar). If you only want one language, just put it in quotes.

    * Then regenerate all of the locales: 

dpkg-reconfigure locales

    * Then set your locale: 

update-locale LANG=en_US.UTF-8

In this step, make sure to choose the language and country that you would like your computer to think it is in. Here, I choose en_US, the United States version of English. Once again, look at your /var/lib/locales/supported.d/local or /usr/share/i18n/SUPPORTED for the one right for you. You may also want to research locales, using the Internet. 

Can't find the program "update-locale," it is not a dpkg option, nor is it in the repositories.

Still can't run gnomebaker, while another user on this system can.

---

### Post by NT4.0 on 2007-04-15
Solved!

[http://www.mail-archive.com/universe-bugs@lists.ubuntu.com/msg06806.html](http://www.mail-archive.com/universe-bugs@lists.ubuntu.com/msg06806.html)

> 
[Bug 34158] Re: Gnomebaker doesn't start. It fails with a GThread-ERROR

Chrissss
Mon, 21 Aug 2006 06:55:37 -0700

You can "solve" the problem by disabling the accessibility support.

I and many people turn this on, because after you disabled the option
/apps/metacity/general/reduced_resources in gconf (to get rid of the -
sorry - crappy animation when you minimize/maximize windows), you only
see a wire-frame, when you move a windows around. With the accessibility
support turned on, windows stay "whole" again while moving them.

[http://www.ubuntuforums.org/showpost.php?p=1283681&postcount=2:](http://www.ubuntuforums.org/showpost.php?p=1283681&postcount=2:)

--
The problem is gnomebaker is not getting along with the accessibility
module. If accessibility support is not a requirement for you, it can be
disabled with the gconf-editor. The relevant key
is /desktop/gnome/interface/accessibility. Uncheck the box and then
restart your session. 
--

-- 
Gnomebaker doesn't start. It fails with a GThread-ERROR
[https://launchpad.net/bugs/34158](https://launchpad.net/bugs/34158)

---

