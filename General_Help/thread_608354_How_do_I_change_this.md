---
title: "How do I change this?"
date: 2007-11-09
forum: General Help
---

### Post by ardchoille42 on 2007-11-09
I am running Kubuntu 7.10 (Gutsy Gibbon) and would like to change the picture associated with my account.

In System Settings it is:
System Settings > About Me > Password & User Account > picture

In KDE Control Center it is:
kcontrol > Security & Privacy > Password & User Account > picture

I click on the box to change the picture (first screenshot) and a message box (second screenshot) pops up stating:

"Your administrator has disallowed changing your image."

I installed Kubuntu on this box and I am the only user on the system. How do I change this picture?

See the screenshots below if this isn't explanatory enough.

---

### Post by omrsafetyo on 2007-11-09
you are undoubtedly the administrator... 

you do also have a root user, you just don't have access to it.

However, I would open this GUI application up with the sudo command from the terminal.  I'm not sure what the application is, personally... or I would give you the specific command to run... I don't use KDE... but you should be able to open that with sudo, and then you will be able to change it.

perhaps ```
sudo kuser
``` and then enter your password at the prompt.  I'm not sure where the settings to re-enable that are either.

---

### Post by ardchoille42 on 2007-11-09
Thank you for the tip, I didn't think about using kdesudo.

I tried opening kcontrol with sudo:

```
kdesudo kcontrol
```

and guess what.. I get the same message box telling me the administrator has disallowed changing my picture. Can you believe that?

Is this something the Kubuntu devs have disabled?

---

### Post by omrsafetyo on 2007-11-09
I wouldn't think so... KDE is generally known as being very customizable..   I am not familiar with it though..  hopefully someone else knows where the configuration for that option is.  Sorry!

---

### Post by cookies on 2007-11-10
> **ardchoille42 said:**
> Thank you for the tip, I didn't think about using kdesudo.

I tried opening kcontrol with sudo:

```
kdesudo kcontrol
```

and guess what.. I get the same message box telling me the administrator has disallowed changing my picture. Can you believe that?

Is this something the Kubuntu devs have disabled?

It's a weird permissions thing. KControl > System Administration > Login Manager > Users (Hit "Administrator Mode")> User Image Source. You can set various options. User then Admin seems best. Restart KDE and then set the image.

---

### Post by ardchoille42 on 2007-11-10
cookies, that worked perfectly, thank you very much. And, you're right, that is weird.

---

