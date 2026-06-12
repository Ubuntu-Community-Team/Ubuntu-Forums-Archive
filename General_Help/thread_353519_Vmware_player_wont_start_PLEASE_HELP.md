---
title: "Vmware player wont start PLEASE HELP"
date: 2007-02-04
forum: General Help
---

### Post by battleroyalex on 2007-02-04
I installed vmware player with automatrix 2. In hopes of booting up windows 2000. I click the icon it gave me.. and it just says vmware palyer is starting. Then it goes away and nothing happens

---

### Post by battleroyalex on 2007-02-04
please help I've been at this for hours :(

---

### Post by kellsens on 2007-02-04
Hi battleroyalex,

   There must be some error that is not shown in X. Try start vmplayer from a console and post the message.

Kellsens

P.S.: Sorry my english

---

### Post by Drillbit on 2007-02-11
Can someone help with this as it's happening to me too. Thank you.

---

### Post by likwid on 2007-02-11
Do as kellsens says and all will become clear. Ubuntu updated this morning and you'll subsequently need to reconfigure vmware.

---

### Post by Drillbit on 2007-02-11
I'm a newbie and don't understand what "starting from a console" means.

---

### Post by likwid on 2007-02-11
Don't worry, it's really easy to fix this one.

Applications>Accessories>Terminal 

su vmware

(if this doesn't work you'll need to find the command that runs vmware. Right click on Applications and select edit menu, locate the vmware shortcut, right click on it and select properties. Now you can copy the command gnome uses to run vmware. There's possible an easier way to do this but i'm pretty new to all this too.)

The terminal will inform you that vmware need to be reconfigured. Run the command it prompts leaving all settings as the script suggests, and all will be fixed in no time.

---

### Post by Drillbit on 2007-02-11
> **likwid said:**
> Don't worry, it's really easy to fix this one.

Applications>Accessories>Terminal 

su vmware

(if this doesn't work you'll need to find the command that runs vmware. Right click on Applications and select edit menu, locate the vmware shortcut, right click on it and select properties. Now you can copy the command gnome uses to run vmware. There's possible an easier way to do this but i'm pretty new to all this too.)

The terminal will inform you that vmware need to be reconfigured. Run the command it prompts leaving all settings as the script suggests, and all will be fixed in no time.

I love you.

---

