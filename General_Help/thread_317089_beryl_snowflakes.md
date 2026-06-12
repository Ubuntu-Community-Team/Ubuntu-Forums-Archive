---
title: "beryl snowflakes"
date: 2006-12-11
forum: General Help
---

### Post by g3k0 on 2006-12-11
I read something about snowflakes in beryl... how do I do this

---

### Post by orb9220 on 2006-12-11
Go here and read the forums. Snowflake is new so isn't in the latest repo's.
[http://www.beryl-project.org/](http://www.beryl-project.org/)

---

### Post by hikaricore on 2006-12-11
It's availible ins Trevino's SVN builds of beryl here:

[http://www.ubuntuforums.org/showthread.php?t=279456](http://www.ubuntuforums.org/showthread.php?t=279456)
[http://download.tuxfamily.org/3v1deb/index.html](http://download.tuxfamily.org/3v1deb/index.html)

--

or just add his repo to your sources.list:

> 
# Treviño's Ubuntu edgy Beryl-SVN Repository (GPG key: 81836EBF - DD800CD9) Daily Updated Beryl (and related projects) Packages...
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn


---

### Post by g3k0 on 2006-12-12
hmm.. is it possible to just upgrade to svn or do i have to completly remove the beryl I have now

---

### Post by Naegling23 on 2006-12-12
I like the snow too, but I'm not going to go messing around with beta beryl software....beta beta software...hmmmm.  Anyway, I'll wait for it to come out in the new build, is there a time frame for this, as 0.1.3 was just released.

---

### Post by g3k0 on 2006-12-12
Well i got it to kinda work... I downloaded the svn plugins and beryl had snow.  But the only time it moves is when I open something or movesomething... or use large amount of processor..

---

### Post by hikaricore on 2006-12-12
> **g3k0 said:**
> hmm.. is it possible to just upgrade to svn or do i have to completly remove the beryl I have now

You should be able to safely upgrade to svn without any trouble.  That's exactly the way I installed it.  :)  If all else fails, just remove it then install from svn.  All your settings will be safe in your .beryl folder (tho some options have changed since the original release) so you can't really hurt anything either way.

---

### Post by g3k0 on 2006-12-12
so wait... i add those repos to my sources.list... then what

---

### Post by hikaricore on 2006-12-12
> **g3k0 said:**
> so wait... i add those repos to my sources.list... then what

```

sudo apt-get update
sudo apt-get upgrade
```

---

### Post by g3k0 on 2006-12-12
eh I'm kinda incompetent sorry...  I'm getting this error

W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems

---

### Post by g3k0 on 2006-12-12
i tried something on the site but that didnt work either.

zaccheus@geckoLaptop:~$ KEY=81836EBF; gpg --keyserver subkeys.pgp.net --recv $KEY && gpg --export --armor $KEY | sudo apt-key add -
gpg: requesting key 81836EBF from hkp server subkeys.pgp.net
gpgkeys: key 81836EBF not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
zaccheus@geckoLaptop:~$

---

### Post by marc_th on 2006-12-12
This thread should merge with this [one]("http://ubuntuforums.org/showthread.php?t=316247").

I've been trying to get the xglsnow to work but without much success.  Installing the subversion package isn't a big deal; in [thread 316247]("http://ubuntuforums.org/showthread.php?t=316247") I outlined how I did it.  Beryl is working fine plus it has a few more features (plugins) that are nice, however still can't get the snow to work right.

---

### Post by hikaricore on 2006-12-13
> **g3k0 said:**
> eh I'm kinda incompetent sorry...  I'm getting this error

W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems

woops here's the apt-get key (run this whole line in terminal to add it):

```
wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
```

---

