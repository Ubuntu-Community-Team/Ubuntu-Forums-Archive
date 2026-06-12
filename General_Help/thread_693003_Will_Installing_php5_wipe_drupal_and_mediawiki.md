---
title: "Will Installing php5 wipe drupal and mediawiki?"
date: 2008-02-10
forum: General Help
---

### Post by jonjonz on 2008-02-10
I would like to upgrade to php5 from php4 so I can upgrade drupal from 4.5 to 5.7, however when I go to install libapache2-mod-php5 I get the following warning in Synaptic Package Manager.

===============
message mark additional required changes?
The chosen action also affects other packages. The following changes are required
in order to proceed.

To be removed
drupal
libapache2-mod-php4
mediawiki
mediawiki-math
php4
phpmyadmin

to be upgraded
php5-common

=====================

Does this mean that if I choose to install libapache2-mod-php5, that drupal and mediawiki will be removed? Or what?

It makes no sense to me, why does drupal and mediawiki have to be removed? Does this mean this process is going to to the removing or just telling me to do it?

This has me very confused, and I can't afford to just try it to see what it does, since I really don't want to have to rebuild everything in drupal and mediawiki from scratch, or a backup.

Please explain.

---

### Post by k9disc on 2008-03-18
I recently upgraded to php5 via .htaccess. I might have some problems like you are mentioning here. 

In my reading about how to get php5+ to work, I found that there are some simple codes you can put into the .htacess files, and IIRC, you can place these .htacess files on particular directories. 

So you may be able to use php5 for what you need it for by creating an .htacess file inside of the directories you need it in, and leave your MW and Drupal installs working off of 4.x . 

I hope that makes sense. 

I'm not an ubuntu user, and was just looking up something else, but noticed that your question was languishing on the vine and thought I'd share some of my limited knowledge with you. 

Cheers, 
Ron

[http://k9disc.com](http://k9disc.com)
[http://pawsitivevybe.com/discdogopedia](http://pawsitivevybe.com/discdogopedia)
[http://pawsitivevybe.com/show2](http://pawsitivevybe.com/show2)

---

