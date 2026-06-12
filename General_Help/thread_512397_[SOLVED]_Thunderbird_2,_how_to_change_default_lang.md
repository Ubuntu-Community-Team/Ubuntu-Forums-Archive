---
title: "[SOLVED] Thunderbird 2, how to change default language?"
date: 2007-07-29
forum: General Help
---

### Post by orbital on 2007-07-29
How do I change my Thunderbird 2 language. I installed it in Finnish but I want it to be English-only.

---

### Post by Koybe on 2007-07-29
I think you can remove the finish locale.
```
sudo apt-get remove mozilla-thunderbird-locale-fi
```

I'm not sure about the finish code, I put fi but adapt to your real code.

---

### Post by orbital on 2007-07-30
> **Koybe said:**
> I think you can remove the finish locale.
```
sudo apt-get remove mozilla-thunderbird-locale-fi
```

I'm not sure about the finish code, I put fi but adapt to your real code.

Package not found. There is a package thunderbird-locale-fi, but it's not installed. Help please...

---

### Post by yorkie on 2007-07-30
Open synaptic package manager
search for thunderbird 
look for thunderbird -locale-en
select for installation 
look for thunderbird -locale-fi select for removal then click on apply
 or you could remove thunderbird then reinstall with the language you want

---

### Post by yorkie on 2007-07-30
You can download TB2 from here

[http://en.www.mozilla.com/en/thunderbird/all.html](http://en.www.mozilla.com/en/thunderbird/all.html)

download page with all languages for you to select.

---

### Post by orbital on 2007-07-30
> **yorkie said:**
> Open synaptic package manager
search for thunderbird 
look for thunderbird -locale-en
select for installation 
look for thunderbird -locale-fi select for removal then click on apply


Only packages i got installed are mozilla-thunderbird and thunderbird-locale-en-gb. And still only finnish language.

---

### Post by orbital on 2007-07-31
Removing Thunderbird and installing it again didn't help. I'm not getting the installation menu where I could select language to use.

---

### Post by orbital on 2007-07-31
I followed the instructions given here and got the localisation changed.

[http://wiki.foresightlinux.com/confluence/display/docs/FAQ#FAQ-HowdoIchangethelocalisationofThunderbird2%3F](http://wiki.foresightlinux.com/confluence/display/docs/FAQ#FAQ-HowdoIchangethelocalisationofThunderbird2%3F)

---

