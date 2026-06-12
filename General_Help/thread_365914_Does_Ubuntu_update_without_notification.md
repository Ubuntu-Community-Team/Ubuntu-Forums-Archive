---
title: "Does Ubuntu update without notification?"
date: 2007-02-20
forum: General Help
---

### Post by OrangeCrate on 2007-02-20
A curiosity question, that a search of the forum doesn't answer for me...

Once in a while I'll hear the box chugging, and previous experience tells me that an update is coming. But, there is no notification. Does Ubuntu ever update internals without notification?

---

### Post by louis_nichols on 2007-02-20
By default it doesn't, but it can be set to. If I remember well, the setting can be found under System>Administration>Application sources. I can check this when I get home, at my machine.

---

### Post by OrangeCrate on 2007-02-20
^, Thanks, I checked my settings. I do not have the silent install option checked. In Windows of course, something is always updating, but hearing the hard drive cycle since I installed Dapper, is so uncommon, that it makes me wonder what's happening. As I said, usually it's an update, but if it is, the box hasn't been telling me what it's been doing.

----

Due to a mistake on my part trying to use a tutorial, I had to reload the source list in Synaptic, and I used the auto-generated code:

# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

(You can read the whole story if your interested, in this thread: [http://www.ubuntuforums.org/showthread.php?t=362838](http://www.ubuntuforums.org/showthread.php?t=362838))

Everything seems to be working fine with that install, but I wonder if I maybe missed something, and Ubuntu is trying to update something that it can't? (I don't know, it's just a guess since I'm pretty new to Linux, and still learning the OS detail.)

Could anyone comment?

---

