---
title: "Where to start troubleshooting test website on localhost"
date: 2013-03-26
forum: General Help
---

### Post by nickdc on 2013-03-26
My partner's small live website (we're happy to post the url, but is that within forum rules? It's not a commercial site) is hosted remotely and was designed and set up professionally (by a relative of a friend). Having moved house and operating systems I'm trying to set up a mirror test site locally on her pc so she can add artwork etc, as she used to do in Windows. I've installed and configured apache2 and php5, but not all the links work locally. There is a range of images, displayed dynamically via various different links on different pages, which won't display, a 404 Not Found page displaying instead. As a stopgap, so my partner can get on, we've installed Windows XP in a VirtualBox and replicated the setup she used before, using XAMPP. This works fully, so is OK, but not ideal. The guy who set up the site says he thinks it may be to do with software versions: he's had the same problem using the current Windows version of XAMPP (1.8.1) with the site but it works fine with the original version (1.7.0). He points out that the versions of Apache and PHP in the current XAMMP package are v2.4.3 and v5.4.7 respectively, while in the older package that works they are v2.2.11 and v5.2.8 respectively. He's not really into linux so isn't able to help much further. I've tried to find those earlier version to install, but have run aground: a) I'm not sure the Win versions correspond to the Linux versions of Apache and PHP; b) I can't find the exact version matches; c) the earlier versions I have found would require installing and configuring from scratch and I'm not yet confident doing that, especially with such complex applications; d) it may be a load of trouble for nothing, as the problem might be resolved much more simply by tweaking some configurations; and e) on principle I prefer not to be reliant on ageing applications. I'd be hugely grateful for any suggestions how I might start troubleshooting the issue?

---

### Post by SeijiSensei on 2013-03-26
Do the linked graphics use relative or absolute URL addresses?  I avoid relative addressing as much as possible and prefer "/images/blue.gif" over "images/blue.gif" or "../images/blue.gif".  Permissions may also be an issue.  Directories containing websites need, at a minimum, to allow the www-data that Apache runs as to list the directory ("x") and read the files therein ("r").  The files themselves need at least "r" permissions.

Take a look in /var/log/apache2/error.log to see a more extensive error than just the 404 you get now.  Usually Apache will tell you when it cannot locate a file or if there is a permissions problem denying access.

---

### Post by nickdc on 2013-03-26
Thank you so much, SeijiSensei, for picking this up. Yes, there's a lot in the error log, and I'm out of my depth here. I've copied the last part of it, all of which has the same time stamp so presumably is all related to the last page I requested and didn't get. What do you make of it?

```
[Tue Mar 26 13:17:00 2013] [error] [client 127.0.0.1] PHP Notice:  Undefined variable: REQUEST_URI in /home/nick/public_html/artwork/redirects.php on line 7, referer: http://localhost/artworkGallery.php
[Tue Mar 26 13:17:00 2013] [error] [client 127.0.0.1] PHP Notice:  Undefined variable: DOCUMENT_ROOT in /home/nick/public_html/artwork/redirects.php on line 7, referer: http://localhost/artworkGallery.php
[Tue Mar 26 13:17:00 2013] [error] [client 127.0.0.1] PHP Notice:  Undefined variable: HTTP_SERVER_VARS in /home/nick/public_html/artwork/redirects.php on line 17, referer: http://localhost/artworkGallery.php
[Tue Mar 26 13:17:00 2013] [error] [client 127.0.0.1] PHP Notice:  Use of undefined constant startElemHandler - assumed 'startElemHandler' in /home/nick/public_html/php/xmlParser.php on line 24, referer: http://localhost/artworkGallery.php
[Tue Mar 26 13:17:00 2013] [error] [client 127.0.0.1] PHP Notice:  Use of undefined constant endElemHandler - assumed 'endElemHandler' in /home/nick/public_html/php/xmlParser.php on line 24, referer: http://localhost/artworkGallery.php
```

---

### Post by nickdc on 2013-03-26
SOLVED.  I just needed to turn on "register_globals" and "register_long_arrays" in the php.ini file. The former is off by default and the latter was off, even though the accompanying comment says it is on by default! Anyway, everything now works.

---

### Post by SeijiSensei on 2013-03-26
l suggest you consider rewriting the code to avoid needing register_globals. Read the [appropriate section]("http://php.net/manual/en/security.globals.php") of the PHP manual to learn why.

---

### Post by nickdc on 2013-03-27
> **SeijiSensei said:**
> l suggest you consider rewriting the code to avoid needing register_globals. Read the [appropriate section]("http://php.net/manual/en/security.globals.php") of the PHP manual to learn why.

Thanks. Yes, I've read that, and though I don't fully understand all the code-speak I get the drift. The problem is: I'm not the one writing the code! But I'm in touch with the guy who is and have sent the link you posted. I've also pointed out that I'm in luck that the repository PHP version is 5.3.10, so I've been able to turn register_globals back on, but in due course there will be an update and our problem will resurface. I imagine he will want to start writing his code differently in order to future-proof his work.

---

### Post by SeijiSensei on 2013-03-27
It's mostly a matter of using the defined globals like $_REQUEST['varname'] rather than simply $varname to capture the URL query string parameters or the data POSTed by an HTML form.  So if the form has a "telno" field for telephone numbers, rather than coding
```

echo $telno;

```
to display the number, he would need to first pull the variable out of the PHP global like this:
```

$telno=$_REQUEST['telno'];
echo $telno;

```

I generally use the $_REQUEST global which includes both GETs and POSTs, but you can also be a bit more security conscious and use the $_GET and $_POST globals for data specific to each type of request.

If he uses arrays in the form, as I do, the arrays will also be in the globals.  As an example, have him look at the form on [this page](http://www.cfmr.com/index.php?go=join) which puts all the person's data into an array called "registrant".  Then there will be a corresponding entry, $_REQUEST['registrant'], which is a PHP array that contains the complete record of entries for that person.  He can then extract the array from the global just like the "telno" example above.

"register_globals" has been deprecated for a very long time now.  The PHP developers have kept it around to protect people like your friend, but I'm glad to see it go away finally in 5.4.

---

### Post by nickdc on 2013-03-27
Well thanks for that. I don't think it's forms that have been the problem. As far as I remember there's only one form on the site (it's a tiny site) which is a simple contact form. The problem was about the failure of links which should have called up pages containing images. The same pages and their images could be called either from a single "artworks" page, which had links to them all, or from other pages which had links just to specific groups of them. I've been assuming the globals and variables stuff has related to this issue of which pages are called from where - but maybe I'm completely wrong; as I've said, I've not yet sussed out how to read the code properly. I was going to post an example, but I can't find individual php files/pages that correspond to the links that didn't work, and I can't see the links on, say, the index page php file. But I'm relying on a very rudimentary knowledge of html and no knowledge at all of php. From looking at the index file, it appears that everything is somehow generated dynamically, so presumably that's where the variables come in. There's one file, "redirects.php" that may throw some light on it:

```
<?php /* alistapart.com/articles/succeed */

include("../php/xmlParser.php");
include("artwork.php");

// 1. check to see if a "real" file exists..
if(file_exists($DOCUMENT_ROOT.$REQUEST_URI)
and ($SCRIPT_FILENAME!=$DOCUMENT_ROOT.$REQUEST_URI)
and ($REQUEST_URI!="/")){
$url=$REQUEST_URI;
include($DOCUMENT_ROOT.$url);
exit();
}

// 2. if not, go ahead and check for dynamic content.
// Get URL and only use end file name
$expl = explode("/",$HTTP_SERVER_VARS["REQUEST_URI"]);
$UserRequest = $expl[ count($expl)-1 ];

// Check to see if such exists in xml, if not then 404 (if just '/' then also 404)
$artworks = artworksList("artworks.xml");

if( !in_array($UserRequest, $artworks)  ) {// || ("" == $UserRequest)
    header("HTTP/1.1 404 Not Found");
    exit("404 Error");
} else if ("" == $UserRequest) {
    header("HTTP/1.1 404 Not Found");
    exit("404 Error - No index page");
}

// 3. Now create page

$artworkInfoArray = artworkInfo($UserRequest, 'artworks.xml');

artwork($artworkInfoArray, $UserRequest);

?>
```

Do you spot something here that would not work without register_globals on?

---

### Post by SeijiSensei on 2013-03-28
All those server-based globals like "$REQUEST_URI" need to be replaced with references to the global $_SERVER array like $_SERVER['REQUEST_URI'].  I think $HTTP_SERVER_VARS has been replaced by $_SERVER as well.

I'd also be careful about constructs like "$DOCUMENT_ROOT.$REQUEST_URI".  A snoop could browse for files by crafting an appropriate URI.  What if the URI contains "../../etc/passwd" for instance?  

The rule-of-thumb is never trust the input your script receives.

---

### Post by nickdc on 2013-03-28
That's helpful. I hear what you're saying. Still waiting to hear back from the guy who wrote the code!

---

