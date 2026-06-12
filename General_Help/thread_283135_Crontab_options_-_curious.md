---
title: "Crontab options - curious"
date: 2006-10-23
forum: General Help
---

### Post by Coelocanth on 2006-10-23
Just a quick question. I was checking out the Ubuntuguide.org Wiki for Dapper and was looking at the crontab entry under the 'How To Automatically Update Ubuntu' section and it says to insert the following line into your crontab file:

```
0 0 * * * apt-get -y update && apt-get y upgrade && apt-get -y dist-upgrade && apt-get -y clean
```

So the question I have is twofold:

1) What is the -y option? I've not been able to discover this. Best I can surmise is it means to use the present calendar? Yes, no? (I know what the other entries in this string mean, but I can't figure out the 'y')

2) Why are all the options -y except the 'apt-get y upgrade' entry?

Thanks for any enlightenment on this.

---

### Post by CatKiller on 2006-10-23
Those are options for apt-get, rather than options for cron. From **man apt-get**: >        -y, --yes, --assume-yes
              Automatic  yes to prompts; assume "yes" as answer to all prompts
              and run non-interactively. If an undesirable situation, such  as
              changing  a  held  package,  trying to install a unauthenticated
              package or removing an essential  package  occurs  then  apt-get
              will abort. Configuration Item: APT::Get::Assume-Yes.
 And I suspect the "apt-get y upgrade" is a typo.

---

### Post by Coelocanth on 2006-10-23
Thank you Cat. *slaps forehead* Never occurred to me to relate it to apt-get. D'oh!

---

