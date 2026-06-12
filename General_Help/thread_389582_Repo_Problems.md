---
title: "Repo Problems"
date: 2007-03-20
forum: General Help
---

### Post by skoalman88 on 2007-03-20
I am trying to install some programs from the synaptic and apps>add/remove, but the downloads won't start. When I run sudo apt-get update, the update freezes on "us.archive.ubuntu.com (91.189.89.8)" at 99%. Any ideas what is wrong?

---

### Post by larrybrazos on 2007-03-20
same here /bump

0% [Connecting to archive.ubuntu.com (91.189.89.8)]
timin' out . . .

---

### Post by BKonkle on 2007-03-20
I'm having the same experience.  I tried both the US archive, and the general archive.ubuntu.com.  Anyone know any mirrors?

---

### Post by raffytaffy on 2007-03-20
trying to update to feisty from edgy on test install...same issue.

  Could not connect to us.archive.ubuntu.com:80 (91.189.89.6), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg                               
  Could not connect to archive.ubuntu.com:80 (91.189.89.8), connection timed out
99% [Connecting to us.archive.ubuntu.com (91.189.89.8)]

---

### Post by X-626 on 2007-03-20
Are any of you using Firestarter?  This seems to be happening quite often because of it.  Take a look at these topics:
[http://www.ubuntuforums.org/showthread.php?p=2309611](http://www.ubuntuforums.org/showthread.php?p=2309611)
[http://www.ubuntuforums.org/showthread.php?p=2282657](http://www.ubuntuforums.org/showthread.php?p=2282657)

That should explain it.

---

### Post by raffytaffy on 2007-03-20
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
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) feisty main restricted 
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) feisty universe multiverse 
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse

# Ubuntu backports project
# GPG key: 437D05B5
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse 



im using british mirrors for now with adequate speed.

---

### Post by BKonkle on 2007-03-20
No, I have no firewall of any kind installed on my system.  Thanks for the links, though - had I been using Firestarter that would have explained it!

---

### Post by kenwebb1 on 2007-03-20
No firestarter here just did a fresh edgy install an i have the same issue.

---

### Post by skoalman88 on 2007-03-20
No Firestarter here.

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg                              
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.6), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.6), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.6), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.6), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.6), connection timed out

---

### Post by BKonkle on 2007-03-20
> **raffytaffy said:**
> im using british mirrors for now with adequate speed.

Good idea!  I just tried it, and I am now successfully connecting.  This should work for a little while at least, until the US servers come back online.

Thanks!

---

### Post by skoalman88 on 2007-03-20
How do I make the switch to British repos?

---

### Post by BKonkle on 2007-03-20
> **skoalman88 said:**
> How do I make the switch to British repos?

Edit your /etc/apt/sources.list file, and use the Replace tool to change all of the us.archive.ubuntu.com references to gb.archive.ubuntu.com.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by X-626 on 2007-03-20
I am currently able to access **both** archive.ubuntu.com and us.archive.ubuntu.com.  Something on your computers must be interfering with your ability to connect to those mirrors.  I have Firestarter running, and I'm able to connect right now.  Those repositories (us.archive.ubuntu.com and archive.ubuntu.com) attempt to make a connection back to you.  If the connection to you is dropped, then your connection will time out.  Something else may be blocking the packets (like maybe a router if you have one).

---

### Post by larrybrazos on 2007-03-20
poor gb servers :( workin overtime tonight!

---

### Post by qpwoeiruty on 2007-03-20
Should there be all us. something? All I have is [http://archive.ubuntu.com](http://archive.ubuntu.com) and the like (no prefixes there)

---

### Post by skoalman88 on 2007-03-20
I changed the source list to gb, but I am still getting hung up at 91.189.6

---

### Post by X-626 on 2007-03-20
You can use either us.archive.ubuntu.com or archive.ubuntu.com.  It doesn't matter if it has a prefix.
Edit: When you edited it, did you use the command "sudo apt-get update"?  Anytime you edit your sources.list, you need to use that command.

---

### Post by skoalman88 on 2007-03-20
About 5 minutes before this issue, I downloaded KDevelop stuff and that went smoothly. I am connecting to a router, but there has never been an issue.


UPDATED!

Working now. Thanks for all the help.

---

### Post by incubus on 2007-03-20
us.archive and archive are pointing to the same IP address, from what I'm seeing.

I switched to Canada.  Of course you can probably use any country, but I suppose Canada is closer to here.

```

$ sudo cp /etc/apt/sources.list{, .bak}  #backup
$ sudo vi /etc/apt/sources.list

 :%s/archive/ca.archive

or

 :%s/us\.archive/ca.archive

```

...should do the trick.  I'm sure somebody will come up with a one-liner awk/sed hehe.

incubus

---

### Post by mario8723 on 2007-03-20
Definitely not a router or firewall issue. I too, had been unable to connect to us.archive.ubuntu.com but when I changed the repos to the British ones mentioned here, I was able to update/upgrade without incident.

---

### Post by incubus on 2007-03-20
At least for me, the US servers are back.  The British boxes must be glad.  : )

incubus

---

### Post by Ek0nomik on 2007-03-20
It's back online folks.

---

