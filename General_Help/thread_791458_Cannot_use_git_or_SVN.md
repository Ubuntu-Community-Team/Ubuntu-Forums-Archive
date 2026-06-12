---
title: "Cannot use git or SVN"
date: 2008-05-12
forum: General Help
---

### Post by castironpants on 2008-05-12
I don't seem to be able to use SVN or git. Whenever I try, they try to copy the branch but just keep going without doing anything. SVN used to work in gutsy, but now in hardy it doesn't. What's going on?

---

### Post by ShodanjoDM on 2008-05-12
svn, git and bazaar are working fine here. Infact I've just compiled pcmanfm 0.4.1.1. from svn.

something related to your network connection, perhaps?

---

### Post by castironpants on 2008-05-12
Yeah, I'm behind a proxy. I have the proxy set under Network settings, but is there some way to make git proxy?

---

### Post by moore.bryan on 2008-06-06
> **castironpants said:**
> Yeah, I'm behind a proxy. I have the proxy set under Network settings, but is there some way to make git proxy?
supposedly, there's a way through either/both the ~/.curlrc and ~/.gitconfig files, but neither works for me. i know this thread's been "dead" for a little while, but i hope someone out there can lend a little lovin'...

---

### Post by ShodanjoDM on 2008-06-06
Ouch, sorry I lost track of this thread.

Googled for "git through proxy" for you guys. Here's a couple of many search results:

[http://linux.derkeiler.com/Mailing-Lists/Kernel/2006-02/msg08267.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2006-02/msg08267.html)

[http://kerneltrap.org/mailarchive/git/2006/5/16/204982](http://kerneltrap.org/mailarchive/git/2006/5/16/204982)

Hope that helps.

---

### Post by moore.bryan on 2008-06-06
> **ShodanjoDM said:**
> Ouch, sorry I lost track of this thread.
no worries...
> 
Googled for "git through proxy" for you guys. Here's a couple of many search results:
[http://linux.derkeiler.com/Mailing-Lists/Kernel/2006-02/msg08267.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2006-02/msg08267.html)
[http://kerneltrap.org/mailarchive/git/2006/5/16/204982](http://kerneltrap.org/mailarchive/git/2006/5/16/204982)
Hope that helps.
unfortunately, i already took that same step. transconnect is a really neat idea, but it didn't do ***** for me; thanks for the input, though.
any other suggestions?

---

