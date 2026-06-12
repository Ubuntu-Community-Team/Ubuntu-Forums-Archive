---
title: "Installing &amp; running Mediawiki under 7.10"
date: 2007-10-21
forum: General Help
---

### Post by Jiawen on 2007-10-21
I'm trying to get Mediawiki running under 7.10 but encountering lots of problems.

I have installed Apache, MySQL, PHP and Mediawiki through Synaptic. The directory /usr/share/mediawiki1.10/ now exists. If I go to [http://localhost/](http://localhost/), I get the directory page showing /apache2-default/ as a subdirectory. If I go into that directory, I get the "It works!" message.

Going to [http://localhost/mediawiki/](http://localhost/mediawiki/) just gives me a 404 (as expected, since the only thing in [http://localhost/](http://localhost/) is the apache2-default directory). 

It appears that there may be [problems with Apache's configuration]("http://ubuntuforums.org/showpost.php?p=2413258&postcount=5"), but I have no idea how to fix that.

If I go into PHPMyAdmin, there is no Wiki database set up. 

I've tried [http://www.mediawiki.org/wiki/Manual:Running_MediaWiki_on_Ubuntu](http://www.mediawiki.org/wiki/Manual:Running_MediaWiki_on_Ubuntu), but it assumes a completely manual installation (i.e., no Synaptic). For that reason, I have no idea what the appropriate equivalent of "rename the extracted directory name to wiki" is.

I've tried [http://www.mediawiki.org/wiki/Manual:Running_MediaWiki_on_Ubuntu_GNU/Linux](http://www.mediawiki.org/wiki/Manual:Running_MediaWiki_on_Ubuntu_GNU/Linux), but it's very unclear right around the spot where I need help.

Please help me get my MediaWiki up and running!

---

### Post by ViRMiN on 2007-12-10
I'm just doing the same thing!

Edit /etc/mediawiki1.10/apache.conf and remove the '#' on the third line so that it reads:

> Alias /mediawiki /var/lib/mediawiki1.10


You should be able to open [http://localhost/mediawiki/](http://localhost/mediawiki/) now :)

---

