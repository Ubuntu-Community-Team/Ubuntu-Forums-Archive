---
title: "Paste as Plain Text as default in Pidgin?"
date: 2008-06-25
forum: General Help
---

### Post by KenBW2 on 2008-06-25
I hate how Paste destroys your formatting in Pidgin, and there appears to be no setting to change it to Paste as Plain Text by default. This is the biggest (80%) reason I never got used to middle-click pasting.
Is there a config file or something I could edit?

---

### Post by Egotist on 2010-05-25
With the (current) latest Pidgin, version 2.7.0 this is now a possibility

Just append the following to your gtkrc file

```
bind "<ctrl>v" { "paste" ("text") }
```




-- Sorry for resurrecting such an old thread, but this is still a relevant topic when you search "Pidgin paste as plain text" in Google, and a lot of people who read the change log are wondering how to do it.

---

### Post by ligaa9mm on 2010-09-14
Thought I would update this (or add to it, as I'm sure my setup is a little different). I'm on Ubuntu Netbook Remix 9.10 with Pidgin 2.7.3 installed.

1. Go to ***/usr/share/themes/Default/gtk-2.0-key/*** (replace Default with whatever theme it is that you use).
2. Open the **gtkrc** file in Gedit or whatever text editor you prefer (you may need to chmod or something to get permission to do so).
3. Add this code below the comments:

```
binding "my-bindings"
{
    bind "<ctrl>v" { "paste" ("text") }
}
widget "*pidgin_conv_entry" binding "my-bindings"
```

4. ???
5. Profit!

Took me forever and a day to figure out. Hope this helps others.

---

