---
title: "Trouble rebinding close window key to &lt;CTRL&gt; + q"
date: 2013-04-30
forum: General Help
---

### Post by tabruhn on 2013-04-30
I'm trying to bind <CTRL> + q to close active windows the way <Alt> + F4 is set up to by default. I'm using the unity interface and use Compiz Config Setting Manager (CCSM) to change some other bindings. 

I've tryed to use Compiz Config Setting Manager (CCSM) General Options>Keybindings to change the close window binding to <CTRL> + q but I've had no luck. It will allow me to input the new binding but when I close the manager the new binding doesn't work. I return the CCSM to find the binding has changed back.

I've also tried setting in the keyboard>application shortcuts a number of different commands which haven't worked yet.

Is there anything I can do or try to make the <CTRL> + q to function the way <ALT> + F4 does by default installation?

I'm running 12.04 LTS

---

### Post by dino99 on 2013-04-30
install dconf-tools (if not yet done) and try to set your pref that way.

---

### Post by tabruhn on 2013-04-30
> **dino99 said:**
> install dconf-tools (if not yet done) and try to set your pref that way.

I tried dconf-tools as well. Problem is, I am not using gnome. I am using Unity. But it seems there is only an option to change the key configurations for gnome in dconf. I might be wrong about this. If so, can you please point me to the right directory in dconf?

---

### Post by tabruhn on 2013-05-01
Are there other places I can change the close window key? Any ad-hoc approaches that might work?

---

