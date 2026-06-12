---
title: "How do I activate ANTHY-input via SCIM in Gnome?"
date: 2006-11-28
forum: General Help
---

### Post by kaminix on 2006-11-28
I don't get it, there's loads of turn on/turn off things for the various engines, and I think I've tried all of them, yet my anthy input method won't show up?

How do I enable ANTHY-input via SCIM while in Gnome? I've installed scim-anthy and the japanese tables for scim.

---

### Post by rbalfour on 2006-11-28
> **kaminix said:**
> I don't get it, there's loads of turn on/turn off things for the various engines, and I think I've tried all of them, yet my anthy input method won't show up?

How do I enable ANTHY-input via SCIM while in Gnome? I've installed scim-anthy and the japanese tables for scim.

In english mode, you need to add the following lines to your export file.


```
declare -x XIM_PROGRAM="scim -d"
declare -x XMODIFIERS="@im=SCIM"

```

---

### Post by kaminix on 2006-11-28
> **rbalfour said:**
> In english mode, you need to add the following lines to your export file.


```
declare -x XIM_PROGRAM="scim -d"
declare -x XMODIFIERS="@im=SCIM"

```
What's enlgish mode and what's export file?
What does that piece of code do?

---

### Post by rbalfour on 2006-11-29
> **kaminix said:**
> What's enlgish mode and what's export file?
What does that piece of code do?

When you login, do you login with a Japanese interface or English Interface?
Judging from your problem, you are logging in with a English interface, hence the reason, WHY you can't see the language bar. Did you try logging in with a Japanese Interface to ensure the SCIM is install properly?

anywhoo. 

```

sudo touch /etc/X11/Xsession.d/74custom-scim_startup
sudo chmod 646 /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XMODIFIERS="@im=SCIM"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export GTK_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XIM_PROGRAM="scim -d"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export QT_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
sudo chmod 644 /etc/X11/Xsession.d/74custom-scim_startup 

```

Reboot. Ctrl-Space should bring up the lang-bar in engrish mode.

---

