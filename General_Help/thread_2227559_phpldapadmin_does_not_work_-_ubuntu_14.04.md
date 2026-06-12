---
title: "phpldapadmin does not work - ubuntu 14.04"
date: 2014-06-02
forum: General Help
---

### Post by project722 on 2014-06-02
I pulled down phpldapadmin which gets v1.2.2.5. I got errors upon installation end saying:

Errors were encountered while processing:
  phpldapadmin
 E: Sub-process /usr/bin/dpkg returned an error code (1)

I proceeded to make all the changes as per the instructions here:

[https://www.digitalocean.com/community/articles/how-to-install-and-configure-a-basic-ldap-server-on-an-ubuntu-12-04-vps](https://www.digitalocean.com/community/articles/how-to-install-and-configure-a-basic-ldap-server-on-an-ubuntu-12-04-vps)

However when I put in ldap.example.com/phpldapadmin in firefox I get 404 not found. So I though it was probably related to the install errors. I traced the errors back and according to Launchpad its a bug. So I then proceed to remove that version of phpldapadmin in favor of v1.2.3. I followed the install instructions to the T and I still get a 404 not found when I put the url/phpldapadmin in firefox. 

My apache2 service is running. Any ideas?

---

