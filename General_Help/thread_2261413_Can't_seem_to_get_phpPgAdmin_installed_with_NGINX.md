---
title: "Can't seem to get phpPgAdmin installed with NGINX"
date: 2015-01-18
forum: General Help
---

### Post by stevenm-wills on 2015-01-18
[COLOR=#000000][FONT=verdana]I had it working once upon a time, and I just don't remember what I did to get it working.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]From start to finish what do i do to get phpPgAdmin installed and working?[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]I install NGINX and it works, I install postgresql and it works.
[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]I installed phppgadmincreate a symlink doing this[/FONT][/COLOR]
```
ln -s /usr/share/phppgadmin /usr/share/nginx/html
```
[COLOR=#000000][FONT=verdana]After that I often get the 403 error which is common, but I can't get past it.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]So what are the correct steps to get it working? I am getting aggravated at how long this is taking me to figure out.. This should have been a 5 minute ordeal..[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Thanks.

I'm assuming it's as simple as installing phppgadmin, creating the symlink, and creating a config at /etc/nginx/conf.d. What does a basic working config even look like?

What should I do start to finish?[/FONT][/COLOR]

---

