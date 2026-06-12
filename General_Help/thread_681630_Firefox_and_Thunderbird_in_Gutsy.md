---
title: "Firefox and Thunderbird in Gutsy"
date: 2008-01-29
forum: General Help
---

### Post by labtek on 2008-01-29
Hello to the group and good day.

Yesterday I loaded Gutsy Gibbon 7.10 on my system and went into Adept Manager to install Firefox and Thunderbird since I typically have used them.

They are showing in the list of apps but are greyed out and are un-clickable. Konqueror is the only web browser that is loaded and I suppose I could continue to use it but I prefer Firefox. I could use KMail but I prefer Thunderbird.

Do I have to go on line and get Firefox and Thunderbird from the web site?

Thanks for any comments/suggestions.

---

### Post by jeffus_il on 2008-01-29
You should be able to install firefox and thunderbird using KDE, I have them installed. Try the install from a terminal and post the output.
```
sudo apt-get install firefox
```It is safer, better and easier to work with the repository.

---

### Post by fyo on 2008-01-29
Or, if you prefer using not using a terminal, you could use Synaptic to install firefox and any other package in the repositories.

---

### Post by Seisen on 2008-01-29
Post the results of ```
cat /etc/apt/sources.list
```

---

### Post by jeffus_il on 2008-01-29
> **fyo said:**
> Or, if you prefer using not using a terminal, you could use Synaptic to install firefox and any other package in the repositories.
He is using Adept which is the same as Synaptic, but KDE, It won't work because for some reason it is greyed out, I suggested the CLI to see if I can help him once I (or you) have read the error output. Don't confuse him, and read the posts!

---

### Post by labtek on 2008-01-29
Thanks for the posts

I tried using

sudo apt-get install Firefox  

and I got the reply

couldn't find package Firefox

Konqueror can't seem to connect to the Internet as well, so I suspect I will have to address that issue first.  Consequently, I cannot post any information from the unit.

I am trying Gutsy on my test computer- my main computer is running Feisty 7.04 quite happily. I try to test new distros before committing to them.

Thanks again to the group.

---

### Post by jeffus_il on 2008-01-29
Firefox must be with a small"F" -- firefox

---

### Post by labtek on 2008-01-30
OK, with the small 'f'...

Building dependency tree
Reading state information-done
Package firefox is not available but is referred to by another package
This may mean that the package is missing, obsoleted or is available from another source
Package firefox has no installation candidate

On a hunch, I ran the live CD again and both Firefox and Thunderbird appear as installation options.

Why are they on the live CD but not in the installed version?

---

### Post by erginemr on 2008-01-30
> **Seisen said:**
> Post the results of ```
cat /etc/apt/sources.list
```

+1 to that.

---

