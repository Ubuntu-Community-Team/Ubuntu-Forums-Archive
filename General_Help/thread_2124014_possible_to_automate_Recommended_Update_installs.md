---
title: "possible to automate Recommended Update installs?"
date: 2013-03-09
forum: General Help
---

### Post by glln0v on 2013-03-09
My dad needs a new computer. He's not very good with computers and understands very little. 

I want to have him use Ubuntu. To simplify it as much as possible, I'd like to automate all updates (including recommended). 

Is this possible?
Is this a bad idea to automate recommonded updates?

I found this [http://askubuntu.com/questions/9/how-do-i-enable-automatic-updates](http://askubuntu.com/questions/9/how-do-i-enable-automatic-updates)
but I can't tell whether ```

sudo apt-get install unattended-upgrades
```
```
sudo dpkg-reconfigure unattended-upgrades
```
is to make Recommonded Updates automate or just the Security Updates.

---

### Post by schragge on 2013-03-09
See this answer: [http://askubuntu.com/questions/87849/how-to-enable-silent-automatic-updates-for-any-repository](http://askubuntu.com/questions/87849/how-to-enable-silent-automatic-updates-for-any-repository)

Recommended upgrades are ```
"${distro_id} ${distro_codename}-updates"
```

Also, although I'm not sure, I think if your run *dpkg-reconfigure* with low priority questions enabled, it'll give you more options:
```
sudo dpkg-reconfigure -plow unattended-upgrades
```

---

