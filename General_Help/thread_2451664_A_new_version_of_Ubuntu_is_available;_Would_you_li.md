---
title: "A new version of Ubuntu is available; Would you like to upgrade?"
date: 2020-10-08
forum: General Help
---

### Post by Skaperen on 2020-10-08
A new version of Ubuntu is available; Would you like to upgrade?

i keep getting this message in a popup.  i'm sure it's telling me about 20.10 while i'm still on 18.04.  but this pops up on every user even if that user cannot sudo to root. *that's stupid.*  **how can i disable this?**  i am still planning my upgrade to Xubuntu 20.04 LTS, but this planning also involves resizing partitions and/or re-usage of hard drives (such as having sdc be my encrypted drive and/or sdb be my system drive).

---

### Post by deadflowr on 2020-10-08
>  i'm sure it's telling me about 20.10 
No, it's for 20.04.
The upgrade option was finally made available recently.

There are no upgrades to 20.10 yet, except for development releases.
And those have to be actively sought by the user as they require an additional flag.

---

### Post by grahammechanical on 2020-10-08
How do you turn it off?

Open Software & Updates>Updates tab and at the panel with the label Notify me of a new Ubuntu version change it from For long-term support versions to Never. 

Regards.

---

### Post by Skaperen on 2020-10-08
> **grahammechanical said:**
> How do you turn it off?

Open Software & Updates>Updates tab and at the panel with the label Notify me of a new Ubuntu version change it from For long-term support versions to Never. 

Regards.
where do i find that?

---

### Post by CelticWarrior on 2020-10-08
Search for "Software & Updates" or navigate the Xubuntu menu.

---

### Post by Yellow Pasque on 2020-10-08
or:
```
software-properties-gtk --open-tab=2
```

---

### Post by Skaperen on 2020-10-10
> **Yellow Pasque said:**
> or:
```
software-properties-gtk --open-tab=2
```
that's my way of direct answers.  of course a command that makes the change and breaks in over the authentication would be faster and more direct :)

---

### Post by Yellow Pasque on 2020-10-10
> **Skaperen said:**
> that's my way of direct answers.  of course a command that makes the change and breaks in over the authentication would be faster and more direct :)

?? So you changed the setting and it worked? Please mark thread solved if so.

---

### Post by Skaperen on 2020-10-11
i'm waiting to the end of the weekend to see if it works.  but this did get me to where i can change the setting and i did change it to "never".  this also give me a feeling of  failure with regard to GUI for not leading me there.  what is the equivalent of a man page for GUI?

---

