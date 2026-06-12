---
title: "Ubuntun Server SVN repository, Client Windows XP"
date: 2008-07-06
forum: General Help
---

### Post by lindylex on 2008-07-06
I want to create an SVN repository using my Ubuntu install.
The clients connecting will use Tortoissvn on a Windows XP P.C.  I have installed some packages for svn.  I created the repository but I am not linking the bridge how do I get the client to checkout the repository?

The repository is located on 10.0.0.81 computer.  And the files on that computer are located at /var/www/documents/testrepository

So with the client I type in something like [http://10.0.0.81/var/www/documents/testrepository](http://10.0.0.81/var/www/documents/testrepository) but this does not download the files within the repository.  This is on a local area network.

I get an error.  I don’t remember and this might be a little vague but.  If you know something that might help me understand this connecting better that would be great.

Thanks, Lex

---

### Post by txcrackers on 2008-07-06
Did you install Apache and the set it up to serve up Subversion? Or are you just running the svn server daemon? If the latter, try using the "svn" protocol:
```
svn://10.0.0.81/
```

I'd run through the setup and usage documents a bit more - and be prepared to start over a couple of times. If you've never set up a code-versioning system, you will muck it up the first couple of times. I always practice a bit when using a new one, even though I've set quite a few up... :wink:

---

