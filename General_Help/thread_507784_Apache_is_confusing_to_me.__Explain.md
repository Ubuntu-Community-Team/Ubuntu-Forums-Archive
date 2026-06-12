---
title: "Apache is confusing to me.  Explain?"
date: 2007-07-23
forum: General Help
---

### Post by whoopn on 2007-07-23
Ok so I am trying to set up a web-based mapping application (any help on that would be sweet but thats not my questions; first things first) in Ubuntu and I am using (or trying to at least) Apache.

Here is what I don't get:

How does one install apache (I did the sudo apt-get apache thing) so that [http://localhost:80/somefile.*](http://localhost:80/somefile.*) (say php) will show in the browser?

How does Apache tell Ubuntu where to send HTTP requests?  How can I change that?

If there is a great tutorial (similar to Dive into Python except for Apache) then I would be stoked!  

Thanks!

---

### Post by kknd on 2007-07-23
sudo aptitude install apache2 libapache2-mod-php5 php5

Your pages will be in /var/www

---

### Post by LaRoza on 2007-07-23
Or
```

sudo tasksel

```
Choose LAMPP.

---

### Post by p_quarles on 2007-07-23
I don't think that installing via apt-get will actually start up the server daemon on its own. You need to run this:
```
sudo /etc/init.d/apache2 start
```
And, as others have pointed out, you will need to have the php parser installed in order to work with any application scripted in that language.

---

### Post by whoopn on 2007-07-23
I did this:
sudo aptitude install apache2 libapache2-mod-php5 php5
and it installed and initiated the server.  The test page works!

I appreciate your help all!

---

