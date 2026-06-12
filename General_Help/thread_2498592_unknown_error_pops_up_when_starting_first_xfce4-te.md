---
title: "unknown error pops up when starting first xfce4-terminal"
date: 2024-06-20
forum: General Help
---

### Post by Skaperen on 2024-06-20
i run a big long script after boot up to se up everything i use.  it starts 12 users and 48 instances of xfce4-terminal.  under on specific user ("pdh") it switches workspace to where a full screen terminal goes, but a popup comes up first and the xfce4-terminal window comes up and covers over the popup.  it has this error message:
```

g-dbus-error-quark: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name :1.169 was not provided by any .service files (2)

```
and a big wide close button.

i don't understand what this message means.  i am not having any error situation.  it does not happen for any other user.  user "pdh" is not the first user started up.  the message only comes up once even though this user start up 6 instances of xfce4-terminal, each in a different workspace.

a ddg search gets similar messages but they talk about the different details.

ddg = duckduckgo.com, the search engine i use.

---

### Post by currentshaft on 2024-06-20
Without seeing the script, it's hard to tell. You could use dbus-monitor to figure out which process is making that message, something like:

dbus-monitor --system "type='signal',sender=':1.169'"

---

### Post by Skaperen on 2024-06-21
what i consider odd is that it affects just one user and only happens in one context.  for 6 workspaces (1..6 out of 0..19) it does the same thing.  and the same steps happen for user "phil" which does not get the popup.  but it happens after the first workspace is switched and before the first xfce4-terminal is started (or at least seen).  perhaps i should focus on it that way.  i wish i understood that message.  i wonder what it means by "Quark".  or could this be a quantum mechanics thing?

---

