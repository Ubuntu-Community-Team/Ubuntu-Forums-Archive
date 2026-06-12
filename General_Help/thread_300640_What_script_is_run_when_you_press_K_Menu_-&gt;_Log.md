---
title: "What script is run when you press K Menu -&gt; Logout -&gt; Turn off?"
date: 2006-11-16
forum: General Help
---

### Post by solarwind on 2006-11-16
Hi, I have a Dell inspiron 6000 laptop and Kubuntu 6.10. When i pres The K Menu -> Logout -> Turn off computer, sometimes it works well, someimes it just blanks the screen. What script is run when I press the turn off computer button? I'll have to edit it.

---

### Post by kerry_s on 2006-11-16
/sbin/shutdown & /sbin/reboot

---

### Post by solarwind on 2006-11-16
> **kerry_s said:**
> /sbin/shutdown & /sbin/reboot

It calls those directly or it uses another script that includes those? I noticed that those binary files and not scripts. using halt never failed me but when I shut down using the shutdown button, it fails most of the time. Same problem kubuntu 5.10, 6.06, 6.10. I bet it's some damn script.

---

### Post by kerry_s on 2006-11-16
It calls it directly, think it's a problem with acpi. My friend had the same problem, we just created a launcher on the desktop for reboot & shutdown and added shutdown to the sudoers list so he didn't need to enter a password. The launchers just have "sudo shutdown now -h" & "sudo shutdown now -f -r" for the commands.

---

