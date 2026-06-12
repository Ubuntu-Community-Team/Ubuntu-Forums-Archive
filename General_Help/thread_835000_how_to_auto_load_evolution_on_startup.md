---
title: "how to auto load evolution on startup"
date: 2008-06-20
forum: General Help
---

### Post by afeasfaerw23231233 on 2008-06-20
how to auto load evolution on startup?

---

### Post by iaculallad on 2008-06-20
System->Preferences->Sessions->Startup Programs
Click New, and then in the Command box type in the Applications launch command.
Application launch name: evolution

---

### Post by afeasfaerw23231233 on 2008-06-20
thanks

---

### Post by afeasfaerw23231233 on 2008-06-20
i what i need is to get the evolution email notifier auto-loaded. i followed your step and figured out i don't need evolution loaded on the startup. i just want the icon pop out to tell me "you've got 1 new mail". i want it to work in the background. 
i find out the evolution alarm notifier is checked but still i've got no notification when i received mail. i only know i have new mail when i start the evolution program.
see my screenshot:

---

### Post by iaculallad on 2008-06-20
Then you need to download mail-notification-evolution application for Evolution:

```
sudo apt-get install mail-notification-evolution
```

After it has been successfully setup'ed, Navigate to Applications->Internet, and select "Mail Notification". You can configure it from there if you want to auto start the application upon session opening. You also have to add your mailbox settings.

*Try to remove your Evolution autostart on System->Preferences->Sessions

---

### Post by afeasfaerw23231233 on 2008-06-20
i've just run your apt-get command.
i load it and 
it says this: 
```
Mail Notification can not contact Evolution. Make sure that Evolution is running and that the Evolution Jean-Yves Lefort's Mail Notification plugin is loaded.
```
i have a look at my evolution plugins and this  Evolution Jean-Yves Lefort's Mail Notification plugin is checked. but when i click the configure button nothing show up

---

### Post by afeasfaerw23231233 on 2008-06-22
BumP

---

### Post by neosofti on 2008-07-10
Hi this help me

```

sudo dpkg-reconfigure  mail-notification-evolution

```

---

