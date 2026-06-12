---
title: "FireFox Local Virtual Host issue"
date: 2020-11-10
forum: General Help
---

### Post by sdsurfer on 2020-11-10
Ubuntu 18.04
Apache2 2.4.29
FF 82.0.2 (64-bit)

This is strictly a FireFox issue, over multiple computers running Ubuntu 18.04. The problem doesn't exist in Chrome or Chromium, only FF. I have some local development virtual domains, for example test.com, and they are configured in my hosts file as well as the local apache2 server. **I can access these fine in Chrome or Chromium**, but FF will absolutely not respect the local domains, and it used to.

I've tried clearing DNS cache, fiddled about with FF configs, multiple searches and suggestions, none of which have worked. On one computer I can get to the virtual domains by setting **network.dns.native-is-localhost** to true, but of course that nukes any external request functionality and only works on that one computer. 

At some point something has changed in FF, has anyone got any pointers on what to do?

---

### Post by SeijiSensei on 2020-11-10
Let's see a couple of representative .conf files with VirtualHost definitions.

---

### Post by TheFu on 2020-11-10
A few months ago, FF changed a default to ignore local DNS and use their own DNS-over-HTTPS solution.  Have you disabled that? [https://support.mozilla.org/en-US/kb/firefox-dns-over-https](https://support.mozilla.org/en-US/kb/firefox-dns-over-https)

---

### Post by HermanAB on 2020-11-10
Firefox Preferences, Network Settings, Right at the bottom is Enable DOH over Cloudflare - clear the box if it is selected.

---

### Post by sdsurfer on 2020-11-11
TheFu and HermanAb, thank you! That alone didn't do it, I also had to set it to no proxy (not sure how that got enabled.) SeijiSensei thank you, but as mentioned I eliminated virtual server setup as a possibility as it works in Chrome. It's like so:

```

127.0.0.1 localhost
127.0.0.1 php-myadmin
127.0.0.1 test.com

```

and in sites-available/test.com.conf, pretty much out of the box standard. Comments removed, typed out as it's not this computer.
```

<VirtualHost *.80>
  ServerAdmin admin@test #(not used)
  ServerName test.com
  ServerAlias www.test.com
  DocumentRoot /var/www/test.com/public_html
  DirectoryIndex index.html index.php
  ErrorLog ${APACHE_LOG_DIR}/error.log
  CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

```

---

### Post by TheFu on 2020-11-11
Be careful about putting comments on the same lines as configuration settings.  Many Unix config files and scripts will break if you do that - put comments on the same line with code.  It is one of those bad habits to avoid.  

Also, ensure that any script or text file has at least 1 empty line at the end of the file.  In theory, it shouldn't matter, but it does, sometimes.

There's a point were being correct, but stuck troubleshooting dumb issues is just a waste of our time. That's where experience comes into play.  Many problems can be avoided by doing a few specific things. Sure, those things shouldn't matter, until they do. Then it really sucks.

---

