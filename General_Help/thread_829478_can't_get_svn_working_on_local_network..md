---
title: "can't get svn working on local network."
date: 2008-06-14
forum: General Help
---

### Post by Mateo on 2008-06-14
ok, so i have an svnserve running on a computer in my house.   from THAT COMPUTER I can run 

```
svn co file:///localhost/opt/directory
```

and it works.  However, from another computer i run:

```
svn co file:///hostname/opt/directory
```

and that doesn't work. says this:

```
svn: Unable to open an ra_local session to URL
svn: Unable to open repository 'file:///hostname/opt/directory'
```

so now i'm thinking that maybe i need to use http.  So I try:

```
http://hostname:3690/opt/directory
```

but that gives me this error:

```

svn: PROPFIND request failed on '/opt/directory'
svn: PROPFIND of '/opt/directory': Could not read status line: connection was closed by server (http://hostname:3690)

```

what am I to do!

---

