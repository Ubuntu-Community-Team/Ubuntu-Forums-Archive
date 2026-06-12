---
title: "Firefox is really slow"
date: 2005-06-13
forum: General Help
---

### Post by thor on 2005-06-13
Hi!

I use Firefox with Ubuntu (at work) and Windows (at home).  It's _really_ fast in Windows, but most of the time is really slow/cpu intensive in Linux.

The problem is not connected with animated graphics and/or flash. Neither it is a network connection.  I repeatedly observe high cpu usage (firefox becomes unresponsive for several seconds) in following scenarios:

1. Loading plain-text document (rfc, for example) about 0.5 meg in size from disk.
2. Loading saved documentation about cisco routers from disk. (docs are about 1 meg in size, with 20-30 static images).
3. Web-server gives me video clip (6 megs) as content-type: text/plain. (I had to stop download with iptables to revive firefox).

There are several other similar sites which cause high cpu usage of firefox.

It upsets me to see that the same application (open source! frequently used!) performs that differently in windows and linux.

Any hints will be greatly appreciated.

P.S. my pc is 2 Ghz Celeron, 256 MB RAM, intergated ProSavage8 video card.

---

### Post by ubuntu_demon on 2005-06-13
I use firefox from backports. It's fast for me. Maybe you should try.

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by thor on 2005-06-13
I tried Firefox 1.0.4 downloaded directly from mozilla.org with no difference.

---

### Post by ubuntu_demon on 2005-06-13
[QUOTE=thor]I tried Firefox 1.0.4 downloaded directly from mozilla.org with no difference.[/QUOTE]
 that's not the proper way :)

It's better to install packages using synaptic / apt-get because :

- they are packaged especially for ubuntu and less likely to cause problems
- easier to maintain (otherwise you would have to check for security updates yourself
- easier to remove

So just try the backport and ask there if there are still problems :)

---

### Post by thor on 2005-06-14
I tried Firefox 1.0.4 from backports. It suffers from the same problem.. :(

---

### Post by ubuntu_demon on 2005-06-14
[QUOTE=thor]I tried Firefox 1.0.4 from backports. It suffers from the same problem.. :([/QUOTE]
 In breezy the package isn't called mozilla-firefox anymore. They backported the package firefox.
did you try to install the package firefox ?

$sudo apt-get install firefox

If there are still problems after this. Please go to the backports forum and ask there. If it's a bug that way there will be a bugfix in breezy faster and you are helping everyone :)

---

### Post by FLeiXiuS on 2005-06-20
yes I've run into the same exact problem.  Firefox for me sucks in linux.  No reasons why...hmmm

---

### Post by FLeiXiuS on 2005-06-20
yes I've run into the same exact problem.  Firefox for me sucks in linux.  No reasons why...hmmm

---

### Post by dissident on 2005-06-20
If you're feeling adventurous, try downloading the latest nightlies. They're a lot faster in my experience. Just don't tell anyone you did.  :-#

PS: Don't forget to enable [fast back](http://weblogs.mozillazine.org/chase/archives/008085.html). :-\"

---

