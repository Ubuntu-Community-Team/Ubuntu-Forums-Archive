---
title: "Firefox Secure Pages"
date: 2008-03-18
forum: General Help
---

### Post by gamblitis on 2008-03-18
When i start firefox the only pages i can access are secure ones.So unless i make them all https ithe server just times out and nothing happens!Any suggestions as to how i could fix this?
Thanks

---

### Post by Ub1476 on 2008-03-18
Does this only occur with Firefox or other browsers as well?

You can try Epiphany (Gnomes web-browser) and see how it works:

```
sudo apt-get install epiphany-browser
```

If everything is alright with Epiphany, there's probably some odd settings in Firefox set. Maybe reinstalling Firefox and delete the config folder in /home will help, if you don't know elsewhere to look. 

If Epiphany doesn't work either, I believe there some settings you need to change in your router.

---

### Post by markharding557 on 2008-03-18
do you have a firewall blocking http?

---

