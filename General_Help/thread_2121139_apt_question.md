---
title: "apt question"
date: 2013-03-01
forum: General Help
---

### Post by fisch246 on 2013-03-01
OK so this isn't exactly support, and I'm fully aware of how problematic this might be... However I have a mother who uses Ubuntu and I'd like to find a way to tell her machine to simply update daily. I was going to put it in rc.local. My question though is that if i put these two commands in rc.local:

```
apt-get update
apt-get -y upgrade
```

would they work? Yes again I'm fully aware that things can break and all that. However I'm essentially doing this all the time with update manager. Have yet to have an issue. I figure as long as I don't get some weird PPA on her machine everything should be fine.

---

### Post by UltimateCat on 2013-03-01
;)Hi:

Yes that will work but I don't think (-y) will:
RUN both commands as a 'Root' user
```
apt-get update

```
And than run:
```
apt-get upgrade

```

Not sure if putting them in rc.local is correct-
I update both of my systems once each week unless the Ubuntu Security or the Debian Security team e-mails me with an advisory to update that day.
You could write a script and just have that scheduled to run -

[http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)
[http://www.wikihow.com/Write-a-Shell-Script-Using-Bash-Shell-in-Ubuntu](http://www.wikihow.com/Write-a-Shell-Script-Using-Bash-Shell-in-Ubuntu)
[http://ubuntuforums.org/showthread.php?t=1049837](http://ubuntuforums.org/showthread.php?t=1049837)

Hope this helps

---

### Post by fisch246 on 2013-03-01
My concern for not having the -y is that it will ask if I want them upgraded and hang there cause there's no other input. So if I do -y it will say yes to all questions.

---

### Post by fisch246 on 2013-03-01
Oh and I'm aware of how to upgrade. I just want it to auto upgrade. Without having my mother to do it. Cause I noticed that for her, simply pressing install updates has become too much work, as she had about 130 updates. Also she managed to screw up the process and is now less likely to do it. This is 12.04, so it's before the update manager was nice, and problem free. I figure setting up her machine to just update on it's own without even asking for a password would be nice, as this is a feature in windows. Unfortunately the drivers needed for her machine to run on windows are no longer supported.

---

