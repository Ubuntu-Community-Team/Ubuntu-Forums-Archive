---
title: "How make Synaptic ignore one process and your dependencies ?"
date: 2018-06-20
forum: General Help
---

### Post by henrique-rj on 2018-06-20
How ?

---

### Post by QIII on 2018-06-20
Hello!

Could you please add enough detail to your question to allow the community to understand exactly what it is you would like assistance with?

---

### Post by henrique-rj on 2018-06-20
Well, I instaled one bank app in my Kubuntu 14.04 and it cause slowlly execution of the Synaptic when I open it.

---

### Post by monkeybrain20122 on 2018-06-20
> **henrique-rj said:**
> Well, I instaled one bank app in my Kubuntu 14.04 and it cause slowlly execution of the Synaptic when I open it.

Man of very few words indeed. I have no clue what you are talking about and I doubt that any has.

---

### Post by dragonfly41 on 2018-06-20
Try installing GDebi Package Installer and use that instead of Synaptic to install your "bank app" (assuming it is a *.deb file).

---

### Post by henrique-rj on 2018-06-20
> **dragonfly41 said:**
> Try installing GDebi Package Installer and use that instead of Synaptic to install your "bank app" (assuming it is a *.deb file).

But I used exactely GDeb in the instalation.

The process it causes the slow Synaptic it's " /local/bin/warsaw/wsatspi ( processing go to 100% for ~10 minutes ).

I have the necessity Synaptic ignore this " wsatspi " ( it's a security plugin bank component ) in your search at the begining.

Any sugestion ?

---

### Post by dragonfly41 on 2018-06-20
I do not know your "warsaw" package ..

but I note that the path "[COLOR=#545454][FONT=arial]/[/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**usr**[/FONT][/COLOR][COLOR=#545454][FONT=arial]/[/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**local**[/FONT][/COLOR][COLOR=#545454][FONT=arial]/[/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**bin**[/FONT][/COLOR][COLOR=#545454][FONT=arial]/[/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**warsaw**[/FONT][/COLOR][COLOR=#545454][FONT=arial]/" is not shown above.

Instead you have "[/FONT][/COLOR][COLOR=#545454][FONT=arial]/[/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**local**[/FONT][/COLOR][COLOR=#545454][FONT=arial]/[/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**bin**[/FONT][/COLOR][COLOR=#545454][FONT=arial]/[/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**warsaw**[/FONT][/COLOR][COLOR=#545454][FONT=arial]/"
which will create a "path not found" error

I would check your paths

Run command ...
```
sudo update
``` .. and wait some time to complete index of all your files

then run ..
```
sudo locate warsaw
```

You should see /usr/local/bin/warsaw

[/FONT][/COLOR]

---

### Post by henrique-rj on 2018-06-22
Solved  !!!

I kill the process /local/bin/warsaw/watsatspi and /local/bin/warsaw/core with process manager Ksysguard.

Now Synaptic run quickly.

For reactivate the refer process it's necessary reboot the system.

Thanks guys !!!

---

