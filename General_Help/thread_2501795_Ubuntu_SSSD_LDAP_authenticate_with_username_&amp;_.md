---
title: "Ubuntu SSSD LDAP authenticate with username &amp; email address"
date: 2024-10-21
forum: General Help
---

### Post by massoo-gmail on 2024-10-21
Hello


As of now I am able to authenticate with Onelogin VLDAP service using the username. I would also like to authenticate with email address in addition to the username.


Some of users are created with their email address as their username and I am unable to authenticate against LDAP with these email addresses as their usernames.


The /etc/sssd/sssd.conf is : [https://pastebin.com/raw/jMzmRFC4](https://pastebin.com/raw/jMzmRFC4)


The /etc/nsswitch.conf is : [https://pastebin.com/raw/s8Eap6HP](https://pastebin.com/raw/s8Eap6HP)


The /var/log/sssd/sssd_domain.com.log is :


part#1/3 : [https://pastebin.com/raw/mwpcCDx3](https://pastebin.com/raw/mwpcCDx3)


part#2/3 : [https://pastebin.com/raw/UxfzxkNJ](https://pastebin.com/raw/UxfzxkNJ)


part#3/3 : [https://pastebin.com/raw/VLNTyCzf](https://pastebin.com/raw/VLNTyCzf)


BTW: the usernames are:


Working Case: username = abc123


Not Working Case: usernames = [EMAIL="ldauser01@mydomain.com"]ldauser01@mydomain.com[/EMAIL], [EMAIL="ldauser02@mydomain.com"]ldauser02@mydomain.com[/EMAIL] , [EMAIL="ldapuser01@mydomain.com"]ldapuser01@mydomain.com[/EMAIL] (emailaddress of ldapuser01) [EMAIL="ldapuser02@mydomain.com"]ldapuser02@mydomain.com[/EMAIL] (emailaddress of ldapuser02)


The user [EMAIL="ldapuser02@mydomain.com"]ldapuser02@mydomain.com[/EMAIL] has never authenticated in the system and hence nothing is cached


Please help to resolve this.


I also observed that even after keying the password twice, we cannot login into the Ubuntu GUI, it just returns back to the screen to key in the password


Sometimes succeeds after 2 attempts, and sometimes 3 attempts
The OneLogin VLDAP services are configured as : Virtual distinguished name Virtual DN: cn=email,ou=users,dc=mysubdomain,dc=onelogin,dc=com User Identifier (cn)


Note: When


a. "ldap_user_name = username" in [domain/mydomain.com], we can authenticate with username


b. "ldap_user_name =" in [domain/mydomain.com] blank or the whole line is commented, we cannot authenticate with any user account (username or mail address)


c. "ldap_user_name = mail" in [domain/mydomain.com], we can authenticate with username


How to resolve this ?

---

