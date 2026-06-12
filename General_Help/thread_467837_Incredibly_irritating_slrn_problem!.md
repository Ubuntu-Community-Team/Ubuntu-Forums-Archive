---
title: "Incredibly irritating slrn problem!"
date: 2007-06-08
forum: General Help
---

### Post by andrew.46 on 2007-06-08
Hi,

 I have an incredibly irritating slrn problem: when I compile my own fron source I cannot see the message 'tree properly:

[http://people.aapt.net.au/~adjlstrong/lost_tree.png](http://people.aapt.net.au/~adjlstrong/lost_tree.png)

 but when I use the version from the ubuntu repos the tree is fine:

[http://people.aapt.net.au/~adjlstrong/tree_better.png](http://people.aapt.net.au/~adjlstrong/tree_better.png)

 I must be doing something wrong with compiling. I use the following commands in sequence:

```
./configure --with-mta=/bin/true
make
sudo checkinstall -D
```

I have tried with various flavours of the s-Lang dev files but no success. I have also posted on news.software.newsreaders with no real resolution.

      Any thoughts?

           Andrew

---

### Post by andrew.46 on 2007-06-11
Hi!

 Well I have solved my own problem :-) The Dapper version is actually the last official 'developer' version rather than the official 'stable' version. When I compiled the developer version all was well.

                  Andrew

---

