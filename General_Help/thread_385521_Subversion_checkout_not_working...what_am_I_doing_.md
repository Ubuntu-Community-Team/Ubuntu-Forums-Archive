---
title: "Subversion checkout not working...what am I doing wrong?"
date: 2007-03-15
forum: General Help
---

### Post by smitjel on 2007-03-15
I'm having some trouble with subversion.  When I issue the checkout command, I'm getting connection refused errors.

I have a project hosted on a box running Edgy Server, with subversion 1.3.2 (installed via apt-get).  I have another box running Fedora Core 5 with subversion 1.3.2 and I can checkout the project just fine.

I want to check out the project on a Dapper Server box, running subversion 1.3.1 (installed via apt-get).  When I issue the checkout command, I get connection refused.

Do I have a versioning problem?  Do I _have_ to have the exact same version of subversion on the client machine as the server to be able to checkout from the repository?  Thanks for ANY help!  ](*,)

```
svn checkout svn://xx.xxx.xx.x/myrepo/MyProjectName MyProjectName
svn: Can't connect to host 'xx.xxx.xx.xx': Connection refused
```

---

### Post by jazzgossen on 2007-03-16
No, you shouldn't need to have the same SVN version. "Connection refused" seems more like a firewall problem, or something similar. Can you connect to the Edgy box from the Dapper box at all, with SSH for example?

---

