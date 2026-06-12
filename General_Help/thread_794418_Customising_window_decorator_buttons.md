---
title: "Customising window decorator buttons"
date: 2008-05-14
forum: General Help
---

### Post by chunlong on 2008-05-14
Hi everyone.

I'm just wondering if it's possible to move the window decorator buttons around? You can do this in kubuntu and xubuntu, but I can't seem to do this in the default ubuntu. The default is to have them on the right, but i prefer to have them on the left. Is there a plugin or something for this?

---

### Post by Exsecrabilus on 2008-05-14
For **GTK Window Decorator**, do this:

Click Alt+F2, type in *gconf-editor* and click **Run**.

On the left side, click **app**, then **metacity**, then **general**.

Now take a look at the right side. Find the one with the name **button layout**.

Double-click on it and a new window will pop up. Change it accordingly.

(You can use common sense to find out which word (menu,minimize,maximize,close) represents which button.
Also, use common sense to find out what the colon ( : ) and the comma ( , ) represent--since it's kinda hard to explain.)

---

### Post by chunlong on 2008-05-14
wow, sweet, thanks that worked!
sorry to be a pain, but is there something like this for emerald as well?

---

### Post by Exsecrabilus on 2008-05-15
Emerald themes come already with the window decorator buttons in position for its theme.

I do not know how to change it though, sorry.

---

### Post by chunlong on 2008-05-16
oh ok, I didn't realise emerald themes predetermine button position. Thanks again for that :)

---

