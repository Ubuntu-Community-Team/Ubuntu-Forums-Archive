---
title: "PHP Files"
date: 2008-06-05
forum: General Help
---

### Post by andrecamp on 2008-06-05
Everytime I try to run a PHP web page on my computer, it doesn;t open in Firefox and it asks me to download the file.

On windows I was able to open PHP files in Firefox. What do I do now though?

---

### Post by deadtom on 2008-06-05
Is this one particular page that keeps doing it to you or just php sites in general?
Usually that is a server side problem where either php is not installed correctly or MIME types are not set correctly.

---

### Post by andrecamp on 2008-06-05
General PHP problem

---

### Post by deadtom on 2008-06-05
Hmmm...  well this site is php. Are you viewing/posting using a different browser?
In that case there is some kind of MIME problem with firefox. Rename your .mozilla folder to something else and let firefox generate a new one and see if it continues to do it. If it keeps doing it then uninstall-reinstall firefox. If not then the problem was some corruption in your firefox profile.

---

### Post by indytim on 2008-06-06
How are you trying to open the file?

You should be able to open them within your browser via:
[http://localhost/somefile.php](http://localhost/somefile.php)

IndyTim

---

### Post by andrecamp on 2008-06-06
Well I store all my websites on my external harddrive. When I try to open them, they don't work. It wants me to download it. 

And I don't know where any programs on Ubuntu are stored. I have been using Ubuntu for only 2 weeks.

---

### Post by deadtom on 2008-06-06
PHP scripts are run server side, not from your browser. To function properly the files must reside on a server running PHP. If you're simply trying to access the files from a hard disk, your browser will see them as nothing more than a file to download.

---

### Post by deadtom on 2008-06-06
I use my laptop as a work environment for my web sites. I've got apache2 with libapache2-mod-php5 installed on the laptop. I turn the server on from init.d when I want to play with the scripts and shut it off when I'm done. Works really slick.

---

### Post by fragos on 2008-06-06
Synaptics-> Edit menu-> Mark Packages by Task-> LAMP Server. This will give a the web server Apache2, MySQL and PHP. Place your web sites in /var/www and you can access them as "localhost". You may need to do a small amount of Apache2 configuration to get PHP to run.

---

### Post by andrecamp on 2008-06-06
Wow, in Windows I was able to run them in Firefox by just clicking on it... :S

---

### Post by indytim on 2008-06-07
Alternative to Frago's method:
```

$ sudo tasksel

```

IndyTim

---

### Post by id1337x on 2008-06-07
*Wow, in Windows I was able to run them in Firefox by just clicking on it... :S*

What? Can you be more specific please? Are you running these files on the client-side and what server is installed? What server did you have on Windows? Apache????

---

### Post by _DD_ on 2008-06-07
> **andrecamp said:**
> Wow, in Windows I was able to run them in Firefox by just clicking on it... :S

I can be pretty certain you couldn't. The pages have to be requested and then all the dynamic stuff parsed by PHP and outputted to plain (X)HTML before your browser can read them. Firefox has no way to parse (execute) PHP.

---

### Post by Old Marcus on 2008-06-07
You could, but the php wouldn't work, since there was no way of executing it.

---

### Post by fragos on 2008-06-07
PHP only runs on the server by design and you should be glad of it. PHP can read and write to the disk on the machine it runs on. Would you want sites you surf to write to your PC's disk? Do you want malware to have stealth open season on your PC? If PHP ran in your PC it's because there was a web server installed in it and not because of the infinite infalable wisdom of the evil empire.

---

### Post by andrecamp on 2008-06-07
The PHP pages I am trying to open don't even have any PHP script. They are HTML pages with .php at the end of the name.

I was able to run these pages in Firefox while I was using Windows. Obviously I wasn't able to run PHP on Windows, but I should have been more clear still. Sorry about that.

---

### Post by fragos on 2008-06-07
No problem the entire client server thing in the web world can be very confusing unless you'd actually hand coded the with all the various markup and scripting languages. If you're curious to learn a little more without converting to total geek, check my free tutorial at [http://FragosTech.com](http://FragosTech.com).

---

### Post by andrecamp on 2008-06-10
I don't really want to install a server on my computer. I just want firefox to run these practically HTML files which are in PHP format. 

The pages I am trying to run don't even have any PHP code but they only are in PHP format. 

I was able to run these pages on Windows Firefox easily so is there a way I can run it on Ubuntu without install a whole bunch of stuff and reading LONG tutorials.

Also, Frago, if you have a tutorial, can you please send me a direct link please? :)

---

### Post by fragos on 2008-06-10
PHP is a server side language by design. Anything is posible in the world of software but that doesn't mean it's worth doing. The server is an easy install. Here's a link to the tutorial on site development [http://fragostech.com/HTML/HTML-1.html](http://fragostech.com/HTML/HTML-1.html). There are also other parts of the site of interest for people with web sites. They can be found in [http://fragostech.com/coach.html](http://fragostech.com/coach.html).

---

### Post by chex_m8 on 2008-06-11
if they don't have any php scripts why don't you just change then to html files. problem solved.

---

### Post by Kinnza on 2008-06-11
hey
listen, im not sure how you got it to work on windows
but i tried it (yes i even opened the explorer for that),
and it asks me to download it

im pretty sure you have a php server on windows as well

---

### Post by andrecamp on 2008-06-29
It never work in Internet Explorer. I

When I opened a PHP file in Firefox or even Opera it showed perfectly fine. 
To get it to work in IE I had to select view in IE from Dreamweaver to get it to show properly.

However, when I ran the PHP files on my Windows Computer, the php scripts never ran. The page show fine though.

That is all I want to happen in Ubuntu.

---

### Post by fragos on 2008-06-29
PHP doesn't execute in your browser. If you request a PHP page it's executed on the server and an HTML page is created and sent to the browser. Normally an HTML FORM is used and the results are passed to the server where the PHP is run to process the user input. It's posible to run a server on your PC with the browser. When you address "localhost" in your browser it looks for the server on your PC. This is a simplification but is how it works, regardless of Windows, Linux, Mac or whatever......

---

### Post by Umang on 2008-06-29
I think you're talking of an HTML page with a .php extension. Just change the .php extension to .htm, right click the file, open with Firefox. (If you haven't made Firefox the default application to open .htm files with as yet, otherwise you can just double click it).

---

### Post by fragos on 2008-06-29
If you place an .html after .php It ships the file as html and the browser displays the PHP code as text. It won't execute. This is becoming a waste of my time -- you don't want my help.

---

### Post by Master Chief on 2008-07-08
> **andrecamp said:**
> Everytime I try to run a PHP web page on my computer, it doesn;t open in Firefox and it asks me to download the file.

On windows I was able to open PHP files in Firefox. What do I do now though?

I've done some reading and it seems that you don't want/have Apache installed and that you want Mozilla Firefox to serve the files with a .php file extension as text/html 

Check /etc/mime.types for this line:

[COLOR="SeaGreen"]text/html					html htm shtml[/COLOR]

and change it to:

[COLOR="SeaGreen"]text/html					html htm shtml[/COLOR] [COLOR="Red"]php[/COLOR]

Now, normally you would have the following lines in /etc/mime.types:

application/x-httpd-php				phtml pht [COLOR="Red"]php[/COLOR]
application/x-httpd-php-source			phps
application/x-httpd-php3			php3
application/x-httpd-php3-preprocessed		php3p
application/x-httpd-php4			php4

And if you have these, remove [COLOR="Red"]php[/COLOR] from the first line.

Oh, edit can be done with:

```
sudo gedit /etc/mime.types
```

Note: This is a complete and ugly workaround but hey, if this makes you happy ;)

---

