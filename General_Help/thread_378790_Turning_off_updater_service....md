---
title: "Turning off updater service..."
date: 2007-03-07
forum: General Help
---

### Post by ardvark71 on 2007-03-07
Hi...

Is there a way to turn off the updater service in Gnome (Breezy 5.10?) Every session it looks for updates when I connect to the 'net and occasionally it has to download everything in my sources.list file. It hogs my connection for quite a few minutes and competes with other programs with respect to resources, making it a royal pain. 

I've tried one configuration adjustment that didn't help and that was telling it not to automatically check for software updates.

Thanks!

---

### Post by rsambuca on 2007-03-07
I don't know about Breezy, but on Edgy you just right-click the icon and select "Remove from panel".

---

### Post by Kateikyoushi on 2007-03-07
Do you have system > administration > services in 5.1 ? It can be turned off there.

---

### Post by ardvark71 on 2007-03-07
> **Kateikyoushi said:**
> Do you have system > administration > services in 5.1 ? It can be turned off there.

There is no mention of it. Is it bundled in with one of the listed services?

Thanks!

---

### Post by Kateikyoushi on 2007-03-07
In later versions / I turned it off in edgy / it had it's own entry.

---

### Post by igknighted on 2007-03-07
system->preferences->sessions, then go to the "startup programs" tab and disable "update-notifier"

---

### Post by ardvark71 on 2007-03-07
> **igknighted said:**
> system->preferences->sessions, then go to the "startup programs" tab and disable "update-notifier"

Hi...

The "startup programs" tab produces an empty box where I can add programs to the list. However, the updater is listed the "current session" tab. Is that where it can be deleted?

Thanks!

---

### Post by ardvark71 on 2007-03-08
Still need help with this.....

---

### Post by ardvark71 on 2007-03-08
No one has an answer for this??? What about those who DESIGNED and coded Ubuntu? Where are they?

Thanks...

---

### Post by rsambuca on 2007-03-08
You can't just right-click the applet and remove it?

---

### Post by ardvark71 on 2007-03-08
> **rsambuca said:**
> You can't just right-click the applet and remove it?

Not that I've seen. The only thing that comes close is preferences and even that doesn't give me the option to disable it.

---

### Post by rsambuca on 2007-03-08
Time to upgrade!

---

### Post by Sepero on 2007-09-11
To disable automatic download of updates:
System -> Administration -> Software Sources
Updates (tab)
heck for Updates [uncheck]
Close

To disable just the update notifier for one user and not others:
System -> Preferences -> Sessions
Startup Programs (tab)
Update Notifier [uncheck]
Close

---

