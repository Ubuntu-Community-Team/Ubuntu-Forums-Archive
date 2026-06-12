---
title: "Can't get apache or mail servers working under 13.10"
date: 2013-11-21
forum: General Help
---

### Post by grizdog on 2013-11-21
Hi,

I hope this is the right forum.  For the most part networking works fine - I'm posting this from the computer in question.  The problem comes up when I try to use the computer as a mail or web server.

The IP address that my router has, and the one that one my registrar has assigned to my domain name are the same, so that is not the problem, and anyway experiments with the ip  address or "localhost" fail as well.  I don't think that is the problem.

Let's just make this post about apache2, since it's just one thing.  I can go into the mail components in another post.

As an aside, I am concerned about an ssl problem, even though I am not using https on my site.  All of this is with iptables wide open.

When I installed apache2, with minimal configuration, it worked, and found the page at /var/www when I used localhost, although it would not work on the net.

Then I changed /var/www to /var/www/html in apache2.conf and default-ssl.conf and now it wouldn't work.  The directory /var/www is owned by root, the directory /var/www/html is owned by me, as is the whole hierarchy below it.  Permissions for the directories are rwxr-xr-x and for the files rw-r--r--

Here is a sample line from /var/log/apache2/error.log

```
[Thu Nov 21 06:22:03.105808 2013] [authz_core:error] [pid 8790:tid 140187582301952] [client 127.0.0.1:43267] AH01630: client denied by server configuration: /var/www/
```

I have greped the /etc/apache2 hierarchy.  There is no place there where /var/www appears by itself without html tacked on.  I restarted apache2 before gathering all this information and posting this.

Thanks for any help

---

### Post by SeijiSensei on 2013-11-22
The default configuration for apache on Ubuntu is contained in the file /etc/apache2/sites-available/000-default.conf, where the /var/www DocumentRoot is defined.  "Enabled" sites have symbolic links in the directory /etc/apache2/sites-enabled/ that point back to files in /sites-available/.  On my vanilla apache2 installation, only 000-default.conf is enabled; default-ssl.conf is not.
If I run "grep '/var/www' /etc/apache2/*/*" it returns

```

$ grep '/var/www' /etc/apache2/*/*
/etc/apache2/sites-available/000-default.conf:	DocumentRoot /var/www
/etc/apache2/sites-available/default-ssl.conf:	DocumentRoot /var/www
/etc/apache2/sites-enabled/000-default.conf:	DocumentRoot /var/www

```

The 000-default.conf configuration does not contain a ServerName directive, so it matches all residual requests on port 80 that have not been handled by a name-based virtual host.  You add name-based hosts by putting additional configuration files in /sites-available/ and use a2ensite to enable them.  These files all need to have a ServerName directive matching the site's canonical name, and an optional ServerAlias directive for any other names it should handle.

If you want to enable SSL, use the command "sudo a2ensite default-ssl".   A symbolic link will be created in /sites-enabled/ just as there is for 000-default.conf.  You'll also need to activate the SSL module with the command "sudo a2enmod ssl" followed by "sudo service apache2 restart" to put the SSL site into operation.  After that, a request for [https://locahost](https://locahost) should bring up the browser's warning page for an untrusted site.

Some things changed about apache in 13.10.  I suggest reading 000-default.conf.  The Ubuntu Server Guide for 13.10 still has out-of-date information about the prior apache version.

---

### Post by grizdog on 2013-11-23
Thanks, that's helpful.  My router seems to have magically acquired an invisible firewall.  I have port forwarding on, and everything else, but apache and ssh requests stop there.  On my LAN at home, everything works, but no one can get in.  I changed nothing on the router when this began - since then I have downloaded new firmware, no change.  The router logs connection events, but nothing ever makes it to my computer's logs.  The router, a Netgear  WNR3500 does not appear to have any real firewall capability, even if I wanted to turn it on.  Just some parental control stuff which is all off.  Very odd.

But thank you, everything works on the LAN now, at least.

---

