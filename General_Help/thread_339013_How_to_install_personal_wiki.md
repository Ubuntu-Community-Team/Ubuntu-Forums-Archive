---
title: "How to install personal wiki"
date: 2007-01-15
forum: General Help
---

### Post by ravisghosh on 2007-01-15
Hi friends, 
I was looking for a wiki software for my personal needs which are as follows: 
1. to work as a Personal Information Manager, keep to do, address, etc. 
2. Jot down information and thoughts. 
3. publish the whole thing on web but keep few personal pages locked with password so that only I can view them. 
4. desirable features are free, easy installation, WYSIWYG editing (i dont know html tagging), files saved in text, page permission, search, can put image, probable easy migration in future to other wiki, easy editing, readymade themes and skins, file attachment, easy publish on web.

On searching in wikimatrix.org, it gave a list [ http://www.wikimatrix.org/compare/JSPWiki+KeheiWiki+MoinMoin+MoniWiki+PhpWiki+PmWiki+PukiWiki+SnipSnap+TWiki ]( http://www.wikimatrix.org/compare/JSPWiki+KeheiWiki+MoinMoin+MoniWiki+PhpWiki+PmWiki+PukiWiki+SnipSnap+TWiki ) of JSPWiki, KeheiWiki, MoinMoin, MoniWiki, PhpWiki, PmWiki, PukiWiki, SnipSnap, TWiki.

On searching further on web, there were recommendation for moinmoin and pmwiki. These 2 had a desktop version too which supposedly was easy to install and did not require addltional webserver. 

Tiddly was very very easy but i excluded it because of no page permission, single file which takes hell lot of time to download and display if its large (even  5 mb) and hence not good to publish large stuff.

PmWiki's standalone version does not have "how to" for linux [http://www.pmwiki.org/wiki/Cookbook/Standalone]("http://www.pmwiki.org/wiki/Cookbook/Standalone"). Its normal installation [http://www.pmwiki.org/wiki/PmWiki/Installation]("http://www.pmwiki.org/wiki/PmWiki/Installation") does not give details of how to install server and other stuff (sorry, I'm a noob). Also i did not understand what this line means [COLOR="Red"]Open a web browser to the pmwiki.php script on the server (i.e., not the one on your local computer or accessed using a file://... URL).[/COLOR]"

If anybody has installed the standalone version or the full version, then please put the steps here including the server thing. Also, as far as I know, apache is very heavy and hence, please suggest something lightweight and secure for a noob. 

For MoinMoin, I tried the desktop version [http://moinmoin.wikiwikiweb.de/DesktopEdition?highlight=%28desktop%29]("http://moinmoin.wikiwikiweb.de/DesktopEdition?highlight=%28desktop%29"). I installed using python, download moinmoin and unpacked it using "tar -xjvf moin-desktop-1.5.5a-1.tbz". Then following instructions, I typed "python moin.py" and got the following error: Code:

[shantanu@bluehead moin-desktop]$ python moin.py 
Loading ... 
MoinMoin - 1.5.5a [97bf3d768af3 tip; DesktopEdition Release 1.5.5a-1] 

Traceback (most recent call last): 
  File "moin.py", line 54, in ? 
    run(Config) 
  File "/home/shantanu/personal/wiki/moin-desktop/MoinMoin/server/standalone.py"                                                               , line 510, in run 
    httpd = makeServer(config)    
  File "/home/shantanu/personal/wiki/moin-desktop/MoinMoin/server/standalone.py"                                                               , line 450, in makeServer 
    return serverClass(config) 
  File "/home/shantanu/personal/wiki/moin-desktop/MoinMoin/server/standalone.py"                                                               , line 176, in __init__ 
    SimpleServer.__init__(self, config) 
  File "/home/shantanu/personal/wiki/moin-desktop/MoinMoin/server/standalone.py"                                                               , line 63, in __init__ 
    BaseHTTPServer.HTTPServer.__init__(self, address, MoinRequestHandler) 
  File "/usr/lib/python2.4/SocketServer.py", line 330, in __init__ 
    self.server_bind() 
  File "/usr/lib/python2.4/BaseHTTPServer.py", line 101, in server_bind 
    SocketServer.TCPServer.server_bind(self) 
  File "/usr/lib/python2.4/SocketServer.py", line 341, in server_bind 
    self.socket.bind(self.server_address) 
  File "<string>", line 1, in bind 
socket.gaierror: (-2, 'Name or service not known') 

And hence, could not get moinmoin working either. There is a discussion about this bug in moinmoin page but no possible solution.

Please help me out installing standalone pmwiki or desktop moinmoin if you have already done that.

Thanks

Ravi S Ghosh

---

### Post by WiseElben on 2007-01-15
You need a server setup in order to install a wiki. I use PmWiki for my projects because it is very simple and get's the job done. For that PmWiki line, that means that you need to upload PmWiki to your server (using FTP or whatever). You can't just run it from your own computer.

The error with MoinMoin is the same thing. You're trying to run something that needs to be on a server locally.

---

### Post by smartbei on 2007-01-15
I am assuming that you want something you can access from everywhere (not only your own computeR), otherwise you would use Tomboy. 

If you are looking for a wiki that only you will use it isn't really a wiki at all. There might be solutions at cmsmatrix as well.

---

### Post by 23meg on 2007-01-15
You can try Instiki 0.10.x, whose sole dependency is Ruby. In its most recent version it requires an SQL backend as well.

[http://instiki.org](http://instiki.org)

---

### Post by NoWhereMan on 2007-01-15
search for wiki in synaptic or gnome-app-install ; IIRC there was a stand-alone wiki-like app, there

bye

---

### Post by ardchoille42 on 2007-01-15
> **WiseElben said:**
> You need a server setup in order to install a wiki. I use PmWiki for my projects because it is very simple and get's the job done. For that PmWiki line, that means that you need to upload PmWiki to your server (using FTP or whatever). You can't just run it from your own computer.

The error with MoinMoin is the same thing. You're trying to run something that needs to be on a server locally.

You can indeed run PmWiki from your computer. You just need to install and config apache and PHP, then you can run PmWiki from your personal computer. For this you need to install PmWiki server version because the stand-alone version comes with a small server but you don't need the server if you're running apache.

---

### Post by 23meg on 2007-01-15
> You just need to install and config apache and PHP, then you can run PmWiki from your personal computer. The point is, running Apache and PHP just for a personal wiki will be overkill in most cases, and once you run those, your personal computer is a server anyway.

---

### Post by m83 on 2007-01-15
As a personal wiki I use [Zim Desktop Wiki]("http://www.pardus.nl/projects/"). It's a desktop application written in Perl and I really love it. I always keep it opened in a workspace for when I have to make notes of something.

You can also try [DidiWiki]("http://didiwiki.org/"). it's prety nice.

---

### Post by NoWhereMan on 2007-01-15
> **m83 said:**
> As a personal wiki I use [Zim Desktop Wiki]("http://www.pardus.nl/projects/"). It's a desktop application written in Perl and I really love it. 

exactly the one I was referring to

---

### Post by 23meg on 2007-01-15
[QUOTE=ravisghosh]3. publish the whole thing on web but keep few personal pages locked with password so that only I can view them. [/QUOTE]Zim isn't adequate for this feature the OP requested.

---

### Post by NoWhereMan on 2007-01-15
oh, i see, sorry. there are many web2.0-style ajax-powered tools of this kind, he could look for one (maybe not really wiki-style, but I know of many PIMs)

HTH, bye :)

---

### Post by ravisghosh on 2007-01-16
Zim is really nice and i use it for putting thoughts, but its severely feature deficient. Moinmoin's instruction says that one does not need any server like apche or lighttpd, etc, since there is a built-in server in desktop version, but again the same error. I have sent a message to the developer of pmwiki about the instruction for standalone version (though after many default replies, i was able to get the correct email, donno yet whether that wll reach him/her or not)

---

### Post by accensi on 2007-01-16
Moinmoin is available in Ubuntu repositories (version 1.5.3), packages moinmoin-common and python-moinmoin.

It is very easy to install with Synaptic, aptitude or apt-get.

Activation of the embedded stand-alone web server is documented in packages. This configuration is 99.99% identical to the Personal Desktop Edition

---

### Post by ravisghosh on 2007-01-16
how about pmwiki????

---

