---
title: "CGI problem"
date: 2005-06-26
forum: General Help
---

### Post by dfghost on 2005-06-26
I have a cgi problem.  I went into /etc/apache2 and edited the apache2.conf so that i could run cgi outside of the cgi-bin.  I then restarted the server and made this cgi:

#!/usr/bin/perl

##########################################
#Web counter created and copywrited by webmaster: -DF-Gh0sT#
##########################################
print "Content-type: text/html\n\n";

open (COUNT, "counter.dat");
$hitcount = <COUNT>;
close COUNT;

$hitcount = $hitcount + 1;

open (COUNT, "> counter.dat");
flock(COUNT, 2);
print COUNT "$hitcount";
close COUNT;

print "$hitcount";

exit;


When i run the cgi in the terminal, it runs fine.  I sudo vi the counter.dat file and it increments perfectly.

But, then i want to put this little counter into an html using this simple .html file:

<html>
<body>
<font color="#FF0000">
<!--#include virtual="counter.cgi"-->
</font>
</body>
</html>

then i visited the test.html file on the internet on a remote computer and nothing happened.  The screen is blank, and the counter.dat file didn't increment at all.

Any suggestions on how i could run the cgi in an html and actually get it to increment the counter.dat file and then show the results?

Thank's in advance.

---

### Post by intangible on 2005-06-27
Make sure in the apache config that in the settings for the directory of the test.html file (which may be cgi-bin for you) that **Options IncludesNoEXEC** is set.

Also, make sure that whatever user the webserver is running as (nobody?) has rights to write to "counter.dat" (maybe *chmod 777 counter.dat*).

Also, when you open a file, put an || on the end so it will give you an error message if it cannot open the file:

open (COUNT, "> counter.dat") || die "Unable to open counter file, error message: $!" ;

---

### Post by dfghost on 2005-06-28
I found the problem, i think.  I need to enable SSI to allow a browser to call the .cgi file.  I've tried many ways of doing this, but none seem to work.  Here they are

NOTE: edits made to the httpd.conf file

<Directory "/var/www">
Options +Includes
AddType text/html .html
AddOutputFilter INCLUDES .html
AddHandler server-parsed .html
</Directory>

I then restarted my server, /etc/init.d/apache2 restart returned a fail, and tried a variety of html files with include calls to cgi's and pl's, but none worked.  I then tried the same above, but with .shtml instead of .html.  That didn't work either.  All i got from some .shtml pages were downloads, they didn't execute.  And all of my permissions for all the files i tried are 777.

Am i doing something wrong here, or what?  Thanks, for the comment though.

---

### Post by intangible on 2005-06-29
Have you just tried this in your page to see if anything shows up?
```

<!--#echo var="DATE_LOCAL" -->

```

---

### Post by dfghost on 2005-06-29
Absolutely nothing happens.  Still blank

I even put a <p>whatever</p> in there to be sure that even plain text shows up, and it does.  Below that line, nothing.

---

### Post by intangible on 2005-06-29
Does the <!-- line still show or is it blank where it was?

---

### Post by dfghost on 2005-06-29
blank, show's up in source, but no where on the actual page.

[Here's a link to the actual page if you want](http://69.105.151.49/test.html)

---

### Post by intangible on 2005-06-30
When I go there, I see <!--#echo var="DATE_LOCAL" --> still.  Looks like it's not even running the includes option on the page.  If you want to PM me your full apache configuration, I'm sure I can get it working for you.

---

### Post by dfghost on 2005-06-30
I'm at work right now, so i'll send it to ya in bout 30min.  Also, why do all of my web pages look different on other computers.  Is it cause i'm accessing my server from my own network and it behaves differently, or is it because of different setups.

And as far as you being able to see the <!--#blah --> include code on the page, are u using ubuntu to browse it, IE on windows, or firefox on either?  That might be why i can't see it, cause my server's GUI is really hard to get, since it's looked up and stowed away with just an ethernet and a power cord hooked up to it.  So, i just use windows.  Anyway, sorry for the long explanation, i'll pm u in a bit.  Thank's for the help!!! really appreciated!!!

---

### Post by intangible on 2005-06-30
Got it.  PMed this as well.

You don't need all that stuff that you have in httpd.conf
**sudo a2enmod include** Enables the Includes Module
**sudo gedit /etc/apache2/sites-available/default**
Find the "Options" line for **<Directory /var/www>**, and just add **Includes** to it.
**sudo /etc/init.d/apache2 force-reload**

You should name the file with **.shtml** so the server doesn't have to parse all html pages for SSI (This setup only works with shtml files)

Try this in a file name "**test.shtml**" to make sure it works:
```
<pre><!--#printenv--></pre>
```

---

### Post by dfghost on 2005-06-30
Thank you so so so very much.  I used to not like ubuntu, probably because I could never get alot of things to work on it, but i guess all you need is someone that knows what they're doing, namely: YOU!  Thanks abunch.  The only problem is that my cgi program isn't working, although that's probably an error on my part, the IP code and pre code you gave worked fine.  I'll try a cgi i got from a friend that i know works.

Thanks again, you've been great, 1 million e-props.   :)  :razz:

---

### Post by Milambar on 2006-09-27
Sorry to resurect this old thread...

I am having the exact same problems as described here. It doesn't seem that the "include" module is distributed anymore, its not in /etc/apache2/mods-availiable, nor is it on any of the repo's.

Whats the fix for dapper drake?

---

### Post by {Rm}Gh0sT on 2006-09-29
I'm dfghost btw.  Dapper's installation of this works just fine.

**sudo vi /etc/apache2/sites-enabled/000-default** and add **Includes** under the <Directory /var/www/> at the end of the line, after Multiviews.

**sudo a2enmod include**.

**sudo /etc/init.d/apache2 restart**.

**sudo ln -s /usr/lib/cgi-bin/ /var/www/cgi-bin/** -- this will give you a cgi-bin in your /var/www/ directory.  And make sure to set proper permissions and file owners for cgi-bin.

Then to test, just vi index.shtml and put:

<html>
<body>
<!--#echo var="DATE_LOCAL" -->
</body>
</html>

And that should do it [nothing's changed from intangible's method]  Anyway, if this still doesn't work - which it should, I just did it on my laptop 2 minutes ago for ya - then E-mail me @ [email]bancrofj@uci.edu[/email] and we'll go from there.

---

