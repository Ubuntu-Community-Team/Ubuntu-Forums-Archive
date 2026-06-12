---
title: "Ubuntu - Update, Synaptic, and Install/Remove only work through terminal"
date: 2007-09-19
forum: General Help
---

### Post by Lemons on 2007-09-19
Recently I have wanted new software and theres been some updates, and I must go through the terminal ("synaptic w/ root or update-manager") to have them install the application. Is this something I have setup or is it a problem? Thanks

---

### Post by tszanon on 2007-09-19
> **Lemons said:**
> Recently I have wanted new software and theres been some updates, and I must go through the terminal ("synaptic w/ root or update-manager") to have them install the application. Is this something I have setup or is it a problem? Thanks
What happens when you:
1. click the icon warning about new updates?
2. Run Synaptic through the menu?

---

### Post by Lemons on 2007-09-22
Sorry for the late response, was busy.

1. Click the icon warning about new updates?
There isnt a warning, just nothing happens. I click "update all" and then it just reloads the list instead of downloading updates.

2. Run Synaptic through the menu?
Dosnt open, says for a brief moment "Starting Synaptic" then shuts down immediatly (No window, in the window list)

---

### Post by tszanon on 2007-09-22
> **Lemons said:**
> 2. Run Synaptic through the menu?
Dosnt open, says for a brief moment "Starting Synaptic" then shuts down immediatly (No window, in the window list)
Ok, so let's see what error messages synaptic gives us when we run it through the terminal. Please type this in the Terminal:
```
gksudo synaptic
```
Paste the output here. I hope the error messages are helpful.

Edit: I just re-read your first post. So there's no error messages when you run synaptic in the terminal? It just runs as expected?

---

### Post by Lemons on 2007-09-24
Well, everything works, but heres the errors for both:

Synaptic:
```
(synaptic:11994): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

```
That only pops up after starting an installation, the problem with this is it wont even open :S

Update Manager:
```
warning: could not initiate dbus
current dist not found in meta-release file
could not send the dbus Inhibit signal: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

---

### Post by tszanon on 2007-09-25
> **Lemons said:**
> Update Manager:
```
warning: could not initiate dbus
**current dist not found in meta-release file**
could not send the dbus Inhibit signal: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```
Sorry, I don't have any more ideas. But that message above is really strange to me. What could have happened that made your distro unrecognizable?

If I were you, I would:
- wait some more to see if the pros here have a solution (sometimes, it takes time for them to show up :));
- if there's no solution, upgrade to Gutsy when it's released (in a month);
- if the problem persists (or the upgrade fails), do a clean install.

---

### Post by Seisen on 2007-09-25
This link should help you fix your problem.

[http://www.go2linux.org/upgrading-to-gutsy]("http://www.go2linux.org/upgrading-to-gutsy")

---

### Post by Lemons on 2007-09-25
Worked perfectly :D, but I have another question. I just started using F-Spot photo, and for the slideshow, it goes to fast to show off my images, any way to slow it down?

Thanks

---

