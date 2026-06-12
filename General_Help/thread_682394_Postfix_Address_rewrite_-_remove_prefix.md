---
title: "Postfix Address rewrite - remove prefix"
date: 2008-01-30
forum: General Help
---

### Post by JinxAu on 2008-01-30
Gday,

Just wondering if anyone has any ideas on rewriting sender addresses for Postfix to remove a prefix in the email. 

Basically due to a Winbind configuration, there is a winbind seperator of "+" that seperates Winbind users from the local users. So the Winbind users look like: DOMAIN+firstname.lastname.

As we're running quotas it would be good to be able to use warnquota to send an email to the user when they have exceeded their soft limit. Warnquota will send the email, but it is sent to DOMAIN+firstname.lastname@domain.com, where the valid address is [email]firstname.username@domain.com[/email]. I am under the assumption that the best way around this is to use Postfix address rewrite rules to remove the "DOMAIN+" component?

Going to play around with the LDAP configuration in /etc/warnquota.conf to see if the mail info can be pulled from ADS... but expecting the same issue with looking up usernames, as the domain prefix will make the user invalid. :|

Cya round
Jinx

---

### Post by PaulFr on 2008-01-30
I would suggest you test the virtual alias map with pcre (or regexp if you do not have pcre support in your Postfix) with something like the following:

1. In /etc/postfix/virtual_pcre, map **/^DOMAIN\+(.*)@domain\.com$/** --to-- **$1@domain.com**
2. in main.cf, add **pcre:/etc/postfix/virtual_pcre** to **virtual_alias_maps** definition.

See **[http://www.postfix.org/ADDRESS_REWRITING_README.html#virtual](http://www.postfix.org/ADDRESS_REWRITING_README.html#virtual)** for details. YMMV.

---

### Post by JinxAu on 2008-01-31
Gday Paul,

Thanks for the reply. It didn't work straight up, but I will have a play and see if I can get it to work.

On the right track at least. :)

Cya round
Jinx

---

### Post by jamessnell on 2008-07-24
Did you manage to get this working?

---

