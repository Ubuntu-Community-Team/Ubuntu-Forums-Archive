---
title: "I would like to serve up a few html pages, is Apache overkill?"
date: 2007-01-08
forum: General Help
---

### Post by Biggus on 2007-01-08
Hi there.

I would like to set up a little service running on my Ubuntu 6.10 (desktop) install, which will basically serve up a few web pages, strictly html + css + assorted GIFs, no php or anything.

I understand that most people would use apache for the purpose of setting up a web server, but might apache be rather more than I need in this instance?

I have no plans to use MySQL or PHP, so is there perhaps a more straightforward solution available, as my main concern is that I do not currently have a great deal of knowledge with regards to file permissions and user groups, and I wouldn't like to leave any unnecessary security holes in my configuration files.

---

### Post by kj1h234lkj1234 on 2007-01-08
Apache is relatively simple to configure if you're just serving up static pages.

To install the bare minimum apache2:
```
apt-get install apache2-mpm-prefork
``` (or do it through synaptic)

Your enabled sites are in /etc/apache2/sites-enabled and you'll only have 1 by default.

The default site's document root is /var/www, so that is where you would dump your html files.

You may want to edit /etc/apache2/sites-enabled/000-default and change the following line:
```
Options Indexes FollowSymLinks MultiViews
```to```
Options -Indexes FollowSymLinks MultiViews
```
to prevent people from getting directory listings if a folder does not have an index.html page present. After making that change, you'll need to ```
sudo /etc/init.d/apache2 reload
``` to put the changes into effect.

Apache runs as the www-data user, and by default root owns /var/www, so security shouldn't be an issue at all (unless there is an actual exploit in Apache itself)

Good luck

---

### Post by az on 2007-01-08
Apache is quite modular.  Unless you install the different modules, apache is quite lean.  Just the barebones apache2 package will install a webserver that does just what you describe you need and nothing more.

---

### Post by Biggus on 2007-01-08
Chaps, you are absolute genii.

I had no idea that this app was so lightweight, and relatively straightforward from what I've seen.

I had this crazy idea that I would have to spend a couple of days at the terminal, but to be honest, it surpassed all of my expectations.

One of me good mates (who just passed the first part of the first level of his LPI certification Level 1 today - well done old bean, I know ya frequent the ubuntu forums here) very kindly came over and helped me out with a few of the terminal commands to move a couple of test html pages into the right places.

Hurrah!

---

### Post by ~LoKe on 2007-01-08
Only way to get the pages on the 'net, unless you host them somewhere.

---

### Post by Biggus on 2007-01-08
Chaps,

I've had a look a couple of the logfiles in the apache folder in var/log/apache2, and I've noticed a couple of strange little things.

In the error log file, I have a few entries like
> 
[Mon Jan 08 23:15:05 2007] [error] [client 212.11.17.x] Invalid method in request \x84\x8bl\x10\x1d\xc3\x03\xe8OD\x01
[Mon Jan 08 23:16:08 2007] [error] [client 212.11.17.x] Invalid method in request 5\xa0\xae\x83\x81[\x13\xfa\xd9\x0e\xe8\x80@b(
[Mon Jan 08 23:18:13 2007] [error] [client 212.11.17.x] Invalid method in request 1A\x15\x8d\x14\x95A\xb1@\xf1
[Tue Jan 09 00:18:07 2007] [error] [client 60.48.117.x] Invalid method in request 1v\xfd@\x97\x9b\xb5a\xf9\xde\xb6

Maybe it's just me, but doesn't that look a little bit like shellcode?

Should I be trembling and quaking at the prospect of imminently being 'haxored'?

---

### Post by llamakc on 2007-01-08
> **~LoKe said:**
> Only way to get the pages on the 'net, unless you host them somewhere.

No, this is wrong. There are several web servers other than Apache, which is why the OP wanted to know if there was an option other than a full-blown Apache install. We all learned that one may install a bare-bones Apache and serve the same purpose.

For example:

thttpd - tiny/turbo/throttling HTTP server
lighttpd - A fast webserver with minimal memory footprint
dhttpd - minimal secure webserver without cgi-bin support
boa - Lightweight and High Performance WebServer

All of those are available in the repositories.

I'm glad they went with Apache though.

---

### Post by kj1h234lkj1234 on 2007-01-08
> **Biggus said:**
> In the error log file, I have a few entries like


Maybe it's just me, but doesn't that look a little bit like shellcode?

Should I be trembling and quaking at the prospect of imminently being 'haxored'?

Those exploits were trying to come in from France and Malaysia.

They're most likely infected Windows machines trying ancient Apache/IIS exploits. They just scan random IP ranges and find open ports, then try to get control of those machines by using known exploits.

You'll sometimes see requests that are actually exploits for popular CMSes like Drupal as well.

Nothing really to worry about, as issues like that in Apache are quite rare.

---

### Post by goneskiing on 2007-01-08
you really should use a web hosting service - available for as little as $5/mo - makes your life much easier.   Then all you have to use is gftp to upload and manage your content files.   If you are just working on your own desktop then use Mongrel (used by a lot of Ruby folks).

---

### Post by az on 2007-01-09
> **kj1h234lkj1234 said:**
> 

Nothing really to worry about, as issues like that in Apache are quite rare.

Keep your system up-to-date with all of the updates from the repositories,

---

### Post by Biggus on 2007-01-09
> They're most likely infected Windows machines trying ancient Apache/IIS exploits. They just scan random IP ranges and find open ports, then try to get control of those machines by using known exploits.

Spot on old bean! I'm not sure how you knew it, but the machines which were targetting me were infected with a trojan called 'sub7'.

> you really should use a web hosting service - available for as little as $5/mo - makes your life much easier. Then all you have to use is gftp to upload and manage your content files.

I do have a 'paid for' hosting account already, with GoDaddy, but I wanna learn about how these things work, not pay someone else to know on my behalf. Thanks for the thought anyway.

> Keep your system up-to-date with all of the updates from the repositories
Will do!

---

### Post by revertex on 2007-04-12
apache eat tons of resources, try thttpd, there is no better server for static pages.

---

### Post by Biggus on 2007-04-25
Just thought I would add to this thread again.

I got my Apache server set up, and it was a good deal easier than I thought (and I did learn the chmod command in doing so :)  )

I can't say I've ever had any trouble with it, I just put the static html in the /var/ww/ folder, and that was it!

I also can't say that I notice any sort of major resource hog, although never having used any other server, I can't really compare.

I had no idea the whole Apache package was so small, I just assumed it was gonna be measured in GB.

If it ever falls over, or if I ever feel the need to do a fresh install, then I'll certainly give one of the others a go.

---

### Post by revertex on 2007-04-25
I guess it's not about the easyness to install but about resources used.

thttpd binary is just a few kb ,(84), apache binary is several mb.

thttpd memory usage is also a few kb, apache a is some mb.

if you are plenty of resources maybe you don't care about, but if you are really interested in some performance gain in a low resource system where every mb of used ram count you should reconsider.

another point is that apache is a full feature web server full of resources, it even open room for misconfigurations or security flaws that can lead some security risks.

in the other hand thttpd wasn't any security flaw in years, configuration is dead simple, and run in chroot by default.

thttpd was a  feature that id very useful in your scenario, throttle.

you can limit the outgoing bandwith connection, this will ensure that nobody will steal all your upload bandwith visiting or downloading something from your page.

---

