---
title: "SVN Server"
date: 2008-01-19
forum: General Help
---

### Post by yngndrw on 2008-01-19
Hi,

Firstly I've searched and havn't really found anything useful to me. (Well nothing that made sense to me anyway.) I've even looked through [this]("http://svnbook.red-bean.com/en/1.1/svn-book.html") and it didn't make sense.

Anyway, I've setup an SVN server based upon a Ubuntu x64 7.10 Server with LAMP. I pretty much just followed [this guide]("http://www.debuntu.org/2006/05/20/54-how-to-subversion-svn-with-apache2-and-dav") and it's working great.
However there's a few more things that I want from it.

Currently I have: [http://ip/svn/project](http://ip/svn/project) where /svn is the root of the SVN.
I can access the project fine but if I try to access /svn it gives me a "Forbidden" error. I'd like this to be a directory of all the projects that I have access to - Any ideas how I could get this ?

Also I'm currently just using basic authentication, but I'd like to be able to setup users to have access to some projects only. I'd also like to only have to enter a suer / password combination once. This means that if I change the password for one user, it will change it on all projects. Any ideas on this ? A step-by-step guide would be awesome because I come from Windows so I'm not used to Linux commands and users/groups.

As well as this, I'd like to be able to sym-link a dirctory into my user's home directory (eg: /home/yngndrw/SVNTools) which would contain nice scripts allowing me to create / remove svn projects along with users. Also being able to link / unlink users to / from projects would be nice.

Finally I'd like to setup a private and secure ftp server, which would allow access to the WHOLE filesystem, whilst still being secure. (eg: Only allowing local IP's to connect and only allowing my username to connect.) Guides and tutorials on doing this would be awesome.

Thank you very much for any help,
-Andrew.

---

### Post by Sam on 2008-01-19
> **yngndrw said:**
> Currently I have: [http://ip/svn/project](http://ip/svn/project) where /svn is the root of the SVN.
I can access the project fine but if I try to access /svn it gives me a "Forbidden" error. I'd like this to be a directory of all the projects that I have access to - Any ideas how I could get this ?
I've always had the same behaviour. I think it's not possible to get the repo listing.

> **yngndrw said:**
> Also I'm currently just using basic authentication, but I'd like to be able to setup users to have access to some projects only. I'd also like to only have to enter a suer / password combination once. This means that if I change the password for one user, it will change it on all projects. Any ideas on this ? A step-by-step guide would be awesome because I come from Windows so I'm not used to Linux commands and users/groups.

Yes it's possible. Use the instructions [here](http://svn.spears.at/#3.2) (ok this is a windows version but it's the same).

---

### Post by yngndrw on 2008-01-19
Thanks your reply and the link - It seems to detail exactly what I need for that part. I'll go through it properly when I get home.

I also didnt know that SVN supported "teams", which will help me out somewhat.

It does raise another question however, can a team contain other teams ?

Eg:
```
[groups]
team1 = ross, rachel
team2 = team1, andy
```

Thanks again.

Edit: It's working great now. I also tried setting groups of groups and it does work as long as the group is specified as @group_name, eg:
```
[groups]
team1 = ross, rachel
team2 = @team1, andy
```

Thanks again. :)

---

