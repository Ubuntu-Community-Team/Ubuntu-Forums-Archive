---
title: "Apache/php query"
date: 2008-04-19
forum: General Help
---

### Post by Ludek on 2008-04-19
Hello All,

Firstly my setup here: Ubuntu 7.1, Apache 2.2, php 5.2, mySQL 5.

I'm trying to teach myself php and set up Apache, mySql and php to that end. All the elements seem to be installed OK and and now I'm slowly working my way through my text book.

A small problem has arisen however: when I upload a page that refers to another page (data from a form being passed to the page that will handle the data for example) the page loads OK and then a few seconds later I get an error <The URL is not valid and can't be loaded> and the whole things hangs. This occurs without me actually clicking through to the handling page.

If I click on the submit button page info is passed and I get the result OK but then a few seconds later on comes the error again.

That's in Firefox, in Opera the page disappears altogether and I get an error page.

When I upload a 'stand alone' page ie one that doesn't refer to anything else - no problems.

Any clues anyone?

Thanks in advance,

Ludek

---

### Post by edward4130 on 2008-04-19
Sounds like you either do not have the PHP loaded properly on the server, or you need to check the syntax on your PHP inclues on the testing pages.  Try to test the pages on a server you know has a working PHP on it to narrow it donw if you can.  Next check examples of a working PHP config file from someone on here.  I do not have php running on mine in any normal way,  (Mythweb mediaserver) the location shold be at "etc/apache2/mods-enabled" not"etc/apache2/mods-disabled"

---

### Post by fragos on 2008-04-19
There a configuration change required to get PHP to work. I unforyunately don't recall what it is but now you know what to look for. Cnfiguration of Apache and Apache2 differs so be careful what instructions you follow. Apache2 is the default install with Ubuntu.

---

