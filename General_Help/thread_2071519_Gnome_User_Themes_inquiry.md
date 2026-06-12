---
title: "Gnome User Themes inquiry"
date: 2012-10-15
forum: General Help
---

### Post by Deucalion29710 on 2012-10-15
I had posted previously a question about how to make my shell user themes work in gnome.  One of the answers directed me to here:

[https://extensions.gnome.org/extension/19/user-themes/](https://extensions.gnome.org/extension/19/user-themes/)

My goal is to make the orange triangle go away so that I can theme my shell.  I have Gnome up and running and I am logged into it now.  I understand that it must be of the same version of gnome that is acquired in update manager.


How do I use this to install shell user themes?

Thanks in advance.

](*,)

---

### Post by Cheesemill on 2012-10-15
Have you installed the extension yet?

Once you have then you can browse for a theme you've downloaded using the Advanced Settings application (gnome-tweak-tool).

---

### Post by Deucalion29710 on 2012-10-15
I have not installed the extension yet.  How do I install it?  I would rather install from deb file as opposed to terminal if at all possible.

---

### Post by Cheesemill on 2012-10-15
You install extensions from the Gnome Extensions website, just click on the slider in the top left of the page.

---

### Post by Deucalion29710 on 2012-10-15
I did the slider and it asked if I wanted to install the extension and nothing happened.  In fact I cannot open the tweak tool.  It crashes every time.  I have removed it and installed it again.  Same result.  This is a fresh install of xubuntu with all updates completed..

---

### Post by Cheesemill on 2012-10-15
Try this fix from the extension web page:
```
sudo cp ~/.local/share/gnome-shell/extensions/user-theme@gnome-shell-extensions.gcampax.github.com/schemas/org.gnome.shell.extensions.user-theme.gschema.xml /usr/share/glib-2.0/schemas/
sudo glib-compile-schemas /usr/share/glib-2.0/schemas/
```

---

### Post by BlinkinCat on 2012-10-15
Hi,

I am a bit dull and may be misreading the situation here, but I thought that the gnome extensions applied only for gnome shell installations. Correct me if I am wrong.

Cheers - :p

---

### Post by Cheesemill on 2012-10-15
> **BlinkinCat said:**
> Hi,

I am a bit dull and may be misreading the situation here, but I thought that the gnome extensions applied only for gnome shell installations. Correct me if I am wrong.

Cheers - :p
You are correct.

From the OP:
> I have Gnome up and running and I am logged into it now.

---

### Post by BlinkinCat on 2012-10-15
> **Cheesemill said:**
> You are correct.

From the OP:


I am sorry if I was/am in error - I read #5 where up to date Xubuntu was mentioned.

Kindly accept my apology - :)

---

### Post by Deucalion29710 on 2012-10-15
> **Cheesemill said:**
> Try this fix from the extension web page:
```
sudo cp ~/.local/share/gnome-shell/extensions/user-theme@gnome-shell-extensions.gcampax.github.com/schemas/org.gnome.shell.extensions.user-theme.gschema.xml /usr/share/glib-2.0/schemas/
sudo glib-compile-schemas /usr/share/glib-2.0/schemas/
```


You're amazing, man.  Worked like a charm.  Fully functional now.  We can mark this as solved.

---

### Post by Cheesemill on 2012-10-16
> **Deucalion29710 said:**
>  We can mark this as solved.
Go on then :)

---

