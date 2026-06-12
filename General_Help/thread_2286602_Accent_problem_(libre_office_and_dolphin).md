---
title: "Accent problem (libre office and dolphin)"
date: 2015-07-13
forum: General Help
---

### Post by Constantinopolitan on 2015-07-13
Dear all,

I am using Kubuntu and Libre office, and I have a problem with the accent signs. My keyboard settings are German and Turkish, but sometimes I need to write in French. I installed the AZERTY keyboard but find it difficult to write with that one; I'd prefer to use the German keyboard and just type "`", "´" or "^" + the letter in order to get é, à or ô. Unfortunately Libre Office denies me that option. Before installing Kubuntu, I had Linux Mint on my old computer, and the accents worked without any problem. 

In some German forum I read something about "dead keys" that should be (de-?)activated, but I could not find that option on my keyboard settings.

Another problem is that I can neither save any file with a name containing accents or special characters (e.g. Turkish words like "kat&#305; at&#305;k yönetimi" or German words with ä, ö, ü, ß...) nor open it. 

I saw a similar thread in this forum but could not understand exactly how the problem was solved.

Thanks a lot for giving me some ideas!

Eva

---

### Post by sudodus on 2015-07-13
Try the following

[Install and] run ***onboard***, a virtual keyboard, that will show what you get on each key.

Change the keyboard with

```

setxkbmap fr
setxkbmap de
setxkbmap tr   # my guess for Turkish

```

---

### Post by Constantinopolitan on 2015-07-15
Dear Sudodus,

thanks a lot for the answer, but unfortunately it does not help me. I do have access to a layout showing me where I can find the accents, but the accents don't work. 
I also found a Turkish keyboard layout indicating me that I have to use AltGr in order to get characters like &#287; or &#351;, which is different from the standard Turkish keyboard but still feasible for report writing etc. 
However, I cannot get the accent keys to work in libre office, and it is impossible to save/ open a document called, for example, "enseignement général" or something like that. In Firefox, accents work without problem. 

I think maybe the "activation of dead keys" is the solution, but I don't find a place where I can try that option.

If you or anyone else has already experienced and solved the same problem, any hints are very much appreciated!

Best regards,

Eva

---

### Post by sudodus on 2015-07-15
Maybe you can try with another Ubuntu flavour: standard Ubuntu, Xubuntu, Ubuntu Mate, Ubuntu Gnome, Lubuntu. Try these live (booted from a DVD or USB drive) and install only if the problem is solved.

Are you running the long time support version 14.04 LTS?

Have you installed the **restricted extras**?

```
sudo apt-get install  kubuntu-restricted-extras
```

Have you tried **another font**, that might contain Turkish letters and accent signs.

You can also try another word processor, for example Abiword or Open Office, that might work where Libre Office fails.

---

### Post by Vladlenin5000 on 2015-07-15
> **Constantinopolitan said:**
> I think maybe the "activation of dead keys" is the solution, but I don't find a place where I can try that option.

Perhaps. I use it with US layout.
"Dead keys" is a layout variant, not an option. You need to add the correct keyboard layout in the variant "with dead keys".

---

