---
title: "apache2 ubuntu"
date: 2013-09-28
forum: General Help
---

### Post by remo2 on 2013-09-28
Mikä määrittely aiheuttaa sen, että tuo sivu tulee vastauksena ko. osoitteella (määrittelytiedoston nimi ja määrittely)
Mikä tuo latautunut sivu on (sivun nimi ja hakemistopolku)?

[ATTACH=CONFIG]246567[/ATTACH]

---

### Post by oldos2er on 2013-09-28
Please post in English.

---

### Post by Iowan on 2013-09-28
Alternately, you can try [http://www.ubuntu-fi.org/]("http://www.ubuntu-fi.org/")

---

### Post by Lars Noodén on 2013-09-28
What you are seeing there is the effect of the option *Indexes* in the directive [Options](http://httpd.apache.org/docs/2.4/mod/core.html#options).  As you can see, if there is no *index.html* file in a directory, Apache2 will show you the contents of that directory.  If you don't want the directory contents to be shown, add a file called *index.html* there with the contents that you do want shown.  

Another, more complicated method, is to have the server return an error message when *index.html* is missing.  You could choose specific options for that virtual host to deny browsing of directory contents.  Specifically you could add something like the following to your vhost's configuration.

```

        <Location />
                Options FollowSymLinks
        </Location>

```

So that would go between the <VirtualHost></VirtualHost> tags.  

Note that [Location](http://httpd.apache.org/docs/2.4/mod/core.html#location) specifies a path relative to the one you see in the browser.

---

### Post by lisati on 2013-09-28
Please do not start multiple threads for the same problem.

Thread closed.

> Älä aloita useita lankoja sama ongelma.

Thread suljettu.

---

