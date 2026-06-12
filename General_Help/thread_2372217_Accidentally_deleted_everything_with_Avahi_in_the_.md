---
title: "Accidentally deleted everything with Avahi in the name"
date: 2017-09-22
forum: General Help
---

### Post by novex2 on 2017-09-22
I didn’t think I would need it and it kept maxing my CPU, so I went ahead and ran something like find | grep avahi | rm -rf

I don’t think I’ll be recovering those. My computer is now unable to open any software and unable to use the apt-get function. How can I get back the avahi files that I so stupidly deleted? Thanks

Edit: apt-get install avahi-daemon does not fix it because avahi-daemon and libnss-mdns:amd64 encounter errors when doing any apt-get function.

---

### Post by Bucky Ball on 2017-09-22
Welcome. Are you using Ubuntu? Which release? Have you tried

```
sudo apt install ubuntu-desktop
```

? 

That will re-install all of Ubuntu's default components, hopefully including what you're missing.

Not sure what that code you input does, but I would *_strongly advise you avoid inputting code which includes 'rm -rf' unless you absolutely know what you are doing_*. ;)

Might be better to seek help troubleshooting why avahi is 'maxing your CPU'.

---

