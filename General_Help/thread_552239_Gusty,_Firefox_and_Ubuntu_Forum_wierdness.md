---
title: "Gusty, Firefox and Ubuntu Forum wierdness"
date: 2007-09-16
forum: General Help
---

### Post by exile on 2007-09-16
OK this is a stumper. I haven't posted the problem for several days trying to work it out myself but I give up. I've never had a problem logging into these Forums but since upgrading one of my machines to Gutsy It says when I log into the forums that it was successful and then dumps me back at the start page without actually logging me in. Meanwhile all other machines login fine under the account. On two different Feisty machines (a desktop and a notebook), windowsXP and even Vista. Firefox and/or Ie6 and ie7 no problems. Gusty, Firefox and these forums is no go for me. I can't work out why. It's a default install that I put on 3 weeks ago. Every other forums (slashdot, some phpbb boards) all authenticate fine on gusty.

When I login all appears to go well. After clicking the button it goes to the next page where it says that my login was successful and then it takes me back to the forum I was browsing but with the login box still in the top right. When I log in on the other machine it doesn't recognize that I have been logged in recently.

Any help would be appreciated. Gnome desktop, very, very vanilla install, nothing fancy on an oldish Dell Optiplex 2ghz Intel based machine.

Thanks in advance.

---

### Post by nowshining on 2007-09-16
do you have allow sites to set cookies unchecked and are you only allowing certain sites if so allow ubuntuforums.org into your exceptions listas either Allow or Allow for Session.

---

### Post by exile on 2007-09-16
Yeah accept cookies are on for all sites. I can inspect my cookie that has been set by ubuntuforums. I get "$ is not defined" message in firebug - but I get that on all the different machines when looking at this site - ie I don't think that that is the problem because I get it even when it works.

---

### Post by nowshining on 2007-09-16
firebug ???

---

### Post by exile on 2007-09-16
firebug is a cool firefox extension for webcode debugging.

[http://www.getfirebug.com/]("http://www.getfirebug.com/")

---

### Post by nowshining on 2007-09-16
well try disabling it - restart firefox and see if that helps??

---

### Post by exile on 2007-09-16
I'm 99.8% sure it isn't firebug at least two of my other successful machines have it installed. I will try though just to cover that base. 

No luck :(

---

### Post by nowshining on 2007-09-16
try clearing out both your cache and cookies and then re-try??

---

### Post by exile on 2007-09-17
still no good. I have no idea why this is happening.

UPDATE: Icewesel 2.0 works fine. I am posting here on the "troubled" machine. Firefox still doesn't work though :(

---

### Post by por100pre1 on 2007-09-17
Try renaming your Firefox profile:

Close firefox and then:

```
cd .mozilla
```

```
mv firefox firefox_backup
```

and restart Firefox.
[I]
If that doesn't work put it all back together:

Close firefox and then:[/I]

```
*cd .mozilla*
```

```
*mv firefox_backup firefox*
```

---

### Post by exile on 2007-09-17
Thanks for the help guys, I appreciate it.

I actually already rm -rf .mozila to get rid of my profile before I even posted the first time. As I have said, I have never seen this in my 6ish years of linux - this is a total mystery for me.

---

### Post by exile on 2007-09-18
just apt-get updated and now firefox logs into the forums just fine. I still have no idea why - I didn't notice any firefox related updates.

Anyway...

---

### Post by nowshining on 2007-09-18
ahhh just noticed "Gutsy Gibbon Testing User" it's not official :) Ubuntu uses its own version of Firefox - well a crippled one in the end so If u want links to open up in tabs instead of new windows - you  best get the regular Mozilla build. edit: unless this was fixed in the Gutsy version - also after 18 months - Ubuntu will provide no security updates whatsoever even for firefox - after the official release of Gutsy - well firefox will not be updated to a newer version unless a's for a security update.

ubuntuzilla is a script that downloads - backups and then installs it from the regular mozilla website.

---

### Post by maybeway36 on 2007-09-18
Or you could enable fesity-backports after gutsy release, for new versions.

---

