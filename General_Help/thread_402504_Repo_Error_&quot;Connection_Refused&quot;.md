---
title: "Repo Error &quot;Connection Refused&quot;"
date: 2007-04-05
forum: General Help
---

### Post by atselby on 2007-04-05
For a few days now I've had a buggy sources.list and I just now got around to fixing it up, basing on DebianAdmin.com's and fixing it so it actually worked, and now I get this error for all repos in Synaptic and in the terminal. Any clues as to this? Should I revert to the default sources.list, although I can't recall where I found it before, and go from there? 

```
{url to repo}: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
```

Thanks for the help guys,

---

### Post by atselby on 2007-04-05
Anyone with any ideas?

---

### Post by atselby on 2007-04-05
Erm... Thanks.

I'd expect better from this forum.

---

### Post by atselby on 2007-04-06
...At least any just restore the sources.list? Something, I mean come on.

---

### Post by Maestro23 on 2007-04-06
Try your last suggestion:  [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Can you post your current /etc/apt/sources.list


*Don't knock the forums.  Best I have seen for any distro.  Works both ways though.

Good luck.

---

### Post by atselby on 2007-04-06
I wasn't necessarily knocking the forum, more the thing that this time I didn't even get any comments for it at all. I got my sources.list from debianadmin.com, [http://www.debianadmin.com/ubuntu-edgy-eft-complete-sourceslist-repository-list-file.html](http://www.debianadmin.com/ubuntu-edgy-eft-complete-sourceslist-repository-list-file.html), and of course it had its own share of problems with some uncommented lines etc. so after I had fixed this my sources didn't work and I had never seen the erorr message for refused connection for all repos. I'll restore the original from that link and then go from there. Thanks.

Edit: I am still getting the same error. I tried the troubleshooting suggestion at the website and it did not fix it. Any clue as to where else to look? 

Current output for source one:
```
Err http://security.ubuntu.com edgy-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

```
Thanks again,

---

### Post by atselby on 2007-04-06
Anyone?

---

### Post by pradeepadapa on 2007-04-08
why dont u post ur  /etc/sources.list file man

---

### Post by r00tintheb0x on 2007-04-08
It looks like you're trying to connect to your own machine as a repository. What was your /etc/hosts look like also?

---

### Post by atselby on 2007-04-08
I resolved this over the IRC channel earlier. My /etc/hosts had added values it apparently did not need and anon-proxy was installed. Fixing /hosts and removing anon-proxy have fixed this.

--Posted for documentation for future help--

---

