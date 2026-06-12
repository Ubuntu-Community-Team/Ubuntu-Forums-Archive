---
title: "Enabling use of htaccess files in Feisty"
date: 2007-06-13
forum: General Help
---

### Post by Peter Mount on 2007-06-13
Hi

I was looking at [this page]("https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles?highlight=%28.htaccess%29")

I read this problem:

"See [WWW] [http://httpd.apache.org/docs/2.0/mod/core.html#allowoverride](http://httpd.apache.org/docs/2.0/mod/core.html#allowoverride) for more info on AllowOverride.

(XXX: I'm having trouble getting this to work on Feisty/7.04. Anyone else? -- [WWW] ChrisWagner) "

Does anybody know of a fix to this? I'm trying to get mod_rewrite to work on localhost so I can test a web blog before uploading it to my web hosting account

Thanks

---

### Post by dominator22 on 2007-06-13
This is an Apache issue.  To resolve it edit /etc/apache2/apache2.conf to include this: 

```
<Directory "/home/peter/public_html">
AllowOverride <directives you want to be able to override using .htaccess>
</Directory>
```

EDIT: The above assumes you username is peter and your site is in ~/public_html

---

