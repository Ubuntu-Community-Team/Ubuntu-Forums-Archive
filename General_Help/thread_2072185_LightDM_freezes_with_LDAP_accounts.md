---
title: "LightDM freezes with LDAP accounts"
date: 2012-10-17
forum: General Help
---

### Post by uylug on 2012-10-17
I've just set up a new box with Ubuntu Desktop 12.04 64 bit and installed the LDAP client by following [this guide]("http://sanjaybdalal.wordpress.com/2009/06/23/setup-openldap-serversambaauto-mount-in-ubuntu-9-04/").

My current setup is: an OpenLDAP server running o Ubuntu Maverick ( i know I have to update it ) with four working clients. All of them were setup by following the previously mentioned website.

The problem is that the new box logins just fine with local accounts, running

```
#getent passwd
```... shows all of the LDAP users, users can login through a terminal or SSH and everything appears to work.

However, LightDM just freezes. By freezing I mean it does accept the password but never gets to the desktop so it gets completely unusable. I can restart LightDM by using ALT+F1 but that doesn't fix the problem. I have installed Ubuntu twice because I thought something could have gone wrong but got the same results.

I should also add that I've set pam to automatically create home dirs. When a LDAP user logins for the first time, the home folder and its subfolders **are** created correctly.

I'm pretty much stuck with this issue so any comments or suggestions would be greatly appreciated.

Thanks.

---

