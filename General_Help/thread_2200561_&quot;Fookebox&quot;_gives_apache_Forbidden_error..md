---
title: "&quot;Fookebox&quot; gives apache Forbidden error..."
date: 2014-01-20
forum: General Help
---

### Post by mike-musicplace on 2014-01-20
It looks like Fookebox doesn't have much of a userbase, because I've found next to nothing about it, but here goes :-)

A new install, from ubuntu repos, of fookebox gives an apache Forbidden ("You don't have permission to access /fookebox on this server.") error. I have checked the following:

[LIST]
[*]File/directory permissions on the apache.conf file, the fookebox.wsgi file itself, and the /usr/share/fookebox directory tree 
[*]That the wsgi module is installed and loaded by apache 
[*]that the /etc/fookebox/apache.conf file is being included from my conf-enabled directory 
[/LIST]

But in the apache error log I continue to get:

```
AH01630: client denied by server configuration: /etc/fookebox/fookebox.wsgi
```

What else should I be checking???

Thanks in advance!

---

