---
title: "Trouble with network printer (Ubuntu - Ubuntu)"
date: 2005-05-05
forum: General Help
---

### Post by DutchLau on 2005-05-05
Hello Ubuntu community, I have a new question for all of you (It's similar to the XP and printing one).

How can I install my HP printer on my network. I read the post about the XP printing problem, but I don't know how to get the IP adress of my PCs in Ubuntu. How can I do this? I think I'm good after that,

Thanks,

DutchLau

---

### Post by Xerampelinae on 2005-05-05
```

ifconfig

```

Look for inet addr of your network device (probably eth0)

Also, I guess Ubuntu includes a script to enable network printer browsing.
```

/usr/share/cups/enable_browsing

```

You'll also have to go to the printer config in system -> administration -> printing and from a menu say enable network printers or something like that, on any client machine you want to be able to use the printer.

---

