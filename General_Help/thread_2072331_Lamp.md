---
title: "Lamp"
date: 2012-10-17
forum: General Help
---

### Post by Randy Schilling on 2012-10-17
Where can I go to get my LAMP installation and configuration questions answered?

---

### Post by Lars Noodén on 2012-10-17
Installation is easy.

```

sudo apt-get update
sudo apt-get install lamp-server^

```

Note that the caret (^) is needed.

When you have an idea of what you want to use your LAMP server for you can look for tutorials and howtos and/or ask here in the forums.  

One place to start, after installation, would be here:
[https://help.ubuntu.com/community/ApacheMySQLPHP#After_installing_PHP](https://help.ubuntu.com/community/ApacheMySQLPHP#After_installing_PHP)

How do you plan to use the setup?  CMS?  Static pages?

---

### Post by Randy Schilling on 2012-10-18
I plan to setup a web page for a Coppermine Photo Gallery and another one to 
advertise my math tutoring service.  I hope to expand the latter web page to a forum,
likely modeled after this forum, where people can go to get there math questions
answered.  The first problem one encounters is providing people with a way of entering
mathematical notation.   I think I can do better than what's already out there because I have an idea for simplify communication of mathematical notation.

My first reference for this LAMP project was Linux Bible.  I looked at 
  [https://help.ubuntu.com/12.04/serverguide/httpd.html](https://help.ubuntu.com/12.04/serverguide/httpd.html).
Then I looked at Apache Cookbook and Apache: The Definitive Guide.
All these seemed either out-of-date or short on details, at least for someone with
my background.  Now I'm following the Apache Documentation
[http://httpd.apache.org/docs/2.4/install.html](http://httpd.apache.org/docs/2.4/install.html)
and building Apache from source code (versus binaries).  This source, combined with what I've learned and tried previously, and things finally seem to be clicking.

I'll look at your suggestions too.   Thanks and many kind regards - Randy

---

### Post by SlugSlug on 2012-10-18
phpbb is easy to use web forum software

---

### Post by Lars Noodén on 2012-10-18
With planning two sites, one of the first things to look at and set up will be [name-based virtual hosts](http://httpd.apache.org/docs/2.2/vhosts/name-based.html).

---

### Post by Randy Schilling on 2012-10-18
Mr. Nooden,

Yes. I am working toward setting up name-based virtual hosting, Chapter 4
of "Apache: The Definitive Guide" and your reference.  Thanks.

I have two questions below.

I installed apache2 by downloading source code and the commands
$ ./confiure
$ make
$ make install.
The setup you get is different from what is described in the reference
[https://help.ubuntu.com/community/ApacheMySQLPHP;](https://help.ubuntu.com/community/ApacheMySQLPHP;)
for instance, there is no directory /etc/apache2.

This has been a big problem when it comes to references.  They're
installation dependent.  Instructions that apply to say a distribution-based
installation such as
$apt-get install apache2
do not have an obvious carry-over to a source-based installation.

I started with a distribution-based installation, ran into trouble, and 
started over using source code because  this is what was recommended
by Apache: The Definitive Guide and [http://httpd.apache.org/docs/2.4/](http://httpd.apache.org/docs/2.4/).
All in all, I'm more comfortable so far with the documentation that comes
with the src-based installation.

Can I install php5 as described in
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
even though I installed Apache in a different way?

I tested my src-based installation by starting apache,
/usr/local/apache2/bin/apachectl -k start,
and the response was this message:
AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message.
This is not surprising because the ServerName directive is commented in my file
/usr/local/apache2/conf/httpd.conf
I added the directive 
ServerName localhost
and got a clean restart of apache.

But I wonder what is the proper choice for ServerName?
Should I get a domain name, say rjs.com, from say GoDaddy.com
and then use this in my ServerName directive,
ServerName rjs.com?

Thanks for your help and I hope you have time to stick with this. 
I thinks with some getting started help, I'll eventually be able to get 
things on my own.

Randy

---

### Post by Lars Noodén on 2012-10-18
Maintaining a package manually by building from source is a lot of work and can lead to redundancies and incompatibilities.  I'd strongly recommend using the package manager instead, it *will* save you a lot of work and trouble.  Back when Apache first came out, building from source was necessary. Now it just gets in the way as the package manager does such a good job of handling the details.

About the server name, you'll have to have a hostname or two in DNS matching your IP number.  Whether you do that by running dnsmasq locally or on your router or by buying a domain depends on how much of an investment you want to make in your project just now.  

But the exact warning message you are getting right now is just a warning and won't actually affect the operation of the server just now.

---

### Post by Randy Schilling on 2012-10-20
Mr. Nooden,

I started with the package-based installation, $apt-get install apache2,
but removed it and went to a src-based installation because much of the 
reference material that I had did not seem to apply.  For instance,
I could not find the executable httpd and could not perform the simple,
but reassuring sanity checks such as $httpd -l.
I believe you're right though and by the time I understand things a bit better,
I will end up with a package-based installation.

I got a src-based apache2/php5/mysql setup working, finally.  It took some time
and that explains the delay in getting back to you.  By the way, my best reference 
for the scr-based installation is this: [http://dan.drydog.com/apache2php.html](http://dan.drydog.com/apache2php.html).
"Working" here means I was able to carry out those sanity checks and I was
able to bring up the php information page, <?php phpinfo(); ?>, in my browser
using [http://localhost/phpinfo.php](http://localhost/phpinfo.php).

My problem now is setting up a web-site.  

Would you please add more detail to this paragraph:

About the server name, you'll have to have a hostname or two in DNS matching your IP number. Whether you do that by running dnsmasq locally or on your router or by buying a domain depends on how much of an investment you want to make in your project just now.

What is "the server name?"
Is [www.rjs.com]("http://www.rjs.com") an example of a "hostname?"
(As you can see, I'm still struggling with terminology.)

I understand something of a correspondence between hostname (I guess) and IP addresses.
The DNS translates hostnames into IP addresses.  Is this correct?

I would like to setup a very simple and inexpensive site for now, just a very simple
index.html file that comes up in my browsere under something like 
httpd://www.rjs.com/index.html.
This would be a great achievement for me.  With it I would have a working example
to build upon and experiment with.

The paragraph suggest that "dnsmasq locally" and "dnsmasq on router" are options to 
buying a domain from GoDaddy or some other company.  Is this correct?

I'm pretty sure I don't have a router and that would leave me with the setting up 
a dnsmasq locally.  If this is all correct, I will begin looking into doing that.

Thanks and very grateful to have this forum, Randy

---

### Post by Lars Noodén on 2012-10-21
Another reason for using the package manager to install things is that they will end up in the normal place for Ubuntu.  Then it will be possible for them to give relevant answers.  If you compile from source and look for the binaries, they could be just about anywhere depending on what your settings were at compile time.  

Server name would be like [www.rjs.com](www.rjs.com) or [www.google.com](www.google.com) or similar.  It is simply there to stand in place of the ip address it represents.  Without it, you would have to type in the ip address to reach a server.  Also, multiple host names can stand for the same ip address and vice versa.  And yes, the translation is done by DNS.

Using dnsmasq locally would be a temporary alternative to buying 
a domain at a registrar like gandi.net or others.  There are many to choose from so you can find one with good prices and a good reputation.  dnsmasq would only work locally on your LAN but would be enough to get started with.  However, if it is too complex, you can always use plain ip addresses while you get used to working with Apache.

---

### Post by Randy Schilling on 2012-10-22
Mr. Nooden,

I know you prefer the package-based setup but would you please 
see this src-based setup through just a little bit further?  
Conversion table:                                                                      
location for web documents(src setup):     /usr/local/apache2/htdocs     
............................................(package setup):  /var/www (I think.)
location of configuration files(src setup):  /usr/local/apache2/conf         
...............................................(package setup):   /etc/apache2/conf.d
main configuration file(src setup):                              http.conf                               
.................................(package setup):  apache2.conf

My main confiuration document, /usr/local/apache2/conf/httpd.conf, 
has these setting (and many more, indicated by ...),
...
ServerName localhost
<Directory />
    AllowOverride none
    Require all denied
</Directory>
DocumentRoot /usr/local/apache2/htdocs
DirectoryIndex index.html
...
When I enter the url [http://localhost](http://localhost) into my browser
the index.html file in DocumentRoot comes up, as it should.
I created a file phpinfo.php, containing <?php phpinfo(); ?>,
added it to DocumentRoot,
and the url [http://localhost/phpinf.php](http://localhost/phpinf.php) works as well.



I setup another web site as follows.
I got a domain name, rjs357.com and  I changed an ip address 
in GoDaddy's zone editor to the ip address of my pc.
I created a directory /usr/local/apache2/htdocs/rjs357 and added 
an index.html and a phpinfo.php file to this new directory.
I created a file /usr/local/apache2/conf/rjs357.conf with content

<VirtualHost *:80>
    ServerName [www.rjs357.com]("http://www.rjs357.com")
    ServerAdmin [EMAIL="rjschilling@comcast.net"]rjschilling@comcast.net[/EMAIL]
    DocumentRoot /usr/local/apache2/htdocs/rjs357
    #<Directory "/usr/local/apache2/htdocs"></Directory>
     DirectoryIndex index.html
     ErrorLog logs/error_log
     # Redirect permanent /foo [http://www.example.com/bar](http://www.example.com/bar)
     # Alias /webpath /full/filesystem/path
</VirtualHost>

and  added the line Include /usr/local/apache2/conf/rjs357.conf
to my main configuration file.  
I restarted apache, apachectl -k restart (having set the appropriate PATH).

The url [http://rjs357.com/](http://rjs357.com/) brings up the correct index.html and
[http://rjs357.com/phpinfo.php](http://rjs357.com/phpinfo.php) contains the correct information as well.

But now when I try the url [http://localhost](http://localhost) what comes up is the
new index.html, instead of the old original.

What confuses me more is this.  
I commented the line Include /usr/local/apache2/conf/rjs357.conf
out of my main configuration file, thinking that this will
take my system back to its original state.
That didn't happen.
When I try the url [http://localhost](http://localhost) what comes up is the
new index.html, instead of the old original, again!

Thanx and grateful for you help, Randy

---

### Post by Lars Noodén on 2012-10-22
Do you have two <VirtualHost *:80></VirtualHost> entries?  You will need one for each virtual host that you set up, even if one is 'default'.

Edit: In Apache2 those are usually separate files, one for each virtual host.

---

### Post by Randy Schilling on 2012-10-22
No, I have just one <VirtualHost *:80>  ...  </VirtualHost>, that for rjs357 and it is located in
rjs357.conf which is "Included" by my main configuration file.
It is my understanding that settings made outside any <VirtualHost *:80>  ...  </VirtualHost>
sections define the 'default'.

In rjs357.conf,  I changed one line of the virtual host directive,
<VirtualHost *:80>                  to            <VirtualHost 67.167.150.157:80>,
where 67.167.150.157 is the IP of my pc, and things worked as I expected they should:
The urls [http://localhost](http://localhost) and [http://rjs357.com](http://rjs357.com) bring up the content of the expected
index.html in my browser.
[http://localhost/phpinfo.php](http://localhost/phpinfo.php) and [http://rjs357.com/phpinfo.php](http://rjs357.com/phpinfo.php) also work.

This change was based on intuition, not enough understanding (but I'm reading on).  
Does this change make sense to you?

Thanks for staying with this - Randy

---

### Post by Randy Schilling on 2012-10-22
OK.  Progress! Yes,  You're right, under name-based virtual hosting,
you have to setup a default <VirtualHost>  section.  

I finally feel like I know enough where I can experiment without 
"blowing up the ship."  Thanks!


Point of confusion:  My main configuration file came with the following
(commented) statements.
# 'Main' server configuration
#
# The directives in this section set up the values used by the 'main'
# server, which responds to any requests that aren't handled by a
# <VirtualHost> definition.  These values also provide defaults for
# any <VirtualHost> containers you may define later in the file.
#
# All of these directives may appear inside <VirtualHost> containers,
# in which case these default settings will be overridden for the
# virtual host being defined.

Here "directives in this section" refers to directive you would find
in a <VirtualHost>  section, but, in my main configuration file,
they're NOT bounded by <VirtualHost>...</VirtualHost>.
I first went by these statements and setup just one <VirtualHost> section, 
and things didn't work the way I expected them to work. 
Then I (finally) read the reference 
[http://httpd.apache.org/docs/2.4/vhosts/name-based.html](http://httpd.apache.org/docs/2.4/vhosts/name-based.html)
on name based virtual hosting which tells you that the first  <VirtualHost> section
acts as a default.

I would guess then that the previous commented stuff applies 
only to ip-based virtual hosting.

Here are my <VirtualHost> sections, each in its own .conf file which are
"Included" in my main configuration file in the appropriate order.

<VirtualHost *:80>
    ServerName localhost:80
    ServerAlias default:80     
    ServerAdmin [email]rjschilling@comcast.net[/email]
    DocumentRoot /usr/local/apache2/htdocs/default/
    DirectoryIndex index.html
    ErrorLog logs/default/error_log
    TransferLog logs/default/access_log
</VirtualHost>

<VirtualHost *:80>
    ServerName  rjs357.com:80
    #ServerAlias [www.rjs357.com:80](www.rjs357.com:80)
    ServerAdmin [email]rjschilling@comcast.net[/email]
    DocumentRoot /usr/local/apache2/htdocs/rjs357/
     DirectoryIndex index.html
     ErrorLog logs/rjs357/error_log
     TransferLog logs/rjs357/access_log
</VirtualHost>

These work but I wonder if you see anything wrong with them?

I remain I'm confused by the ServerAlias directive.
The directive ServerAlias [www.rjs357.com:80](www.rjs357.com:80) proved to be unnecessary
because both urls, [http://rjs357.com](http://rjs357.com) and [http://www.rjs357.com](http://www.rjs357.com) take
you to the correct page.

The url [http://localhost](http://localhost) takes me to my default page and I expected,
with the directive  ServerAlias default:80, that [http://default](http://default) would take me
to the same page.  That fails and I don't know why.

Thanks very much for all your support, Randy.

---

### Post by Lars Noodén on 2012-10-23
With a cursory glance they seem fine.  You might use [<VirtualHost _default_:*>](http://httpd.apache.org/docs/2.2/vhosts/examples.html#default) for your default vhost just to catch everything.  

About the logs, you can use [logrotate](http://manpages.ubuntu.com/manpages/precise/en/man8/logrotate.8.html) to keep them from getting out of hand.  /etc/logrotate.d/ is where you would put the configuration file for Apache.  There's one there already for Apache2 you can either modify that or add one for your vhosts.

---

### Post by Lars Noodén on 2012-10-23
Also since you are maintaining Apache manually, you might consider subscribing to the [Apache Server Announcements mailing list](http://httpd.apache.org/lists.html#http-announce).  That way you'll know when there is a patch available that you should get.

---

### Post by Randy Schilling on 2012-10-26
Mr Nooden, would you please check out my latest post 
"Problems with LAMP Virtual Hosts,"
which is not getting any attention from the forum.
I've replaced my src-based LAMP with the distribution-based,
as you suggested.

Thanks, Randy

---

### Post by Lars Noodén on 2012-10-26
I've taken a look.  It was probably educational to build from source, but in the long run using the repository saves time and effort.

---

### Post by Randy Schilling on 2012-11-06
Mr. Nooden,

Would you please look at my post "LAMP perl cgi problem" under the
Generl Help Forum?

---

