---
title: "[SOLVED] sudoers complications"
date: 2008-02-09
forum: General Help
---

### Post by &amp;)ky#)^ on 2008-02-09
I'm having trouble customizing my sudoers file. Here's what I want to do.  I want to give a user access to Synaptic, GDebi-GTK, time-admin, software-properties-gtk, shares-admin, services-admin, displayconfig-gtk, restricted-manager, gdmsetup, and gnome-language-selector.  However, I don't want to give the user blanket permissions by adding him to the admin group.  I've read through the man page for sudoers twice now and I'm just not getting it.  I either brick my sudoers file and have to boot into recovery mode which is a pain in the ***, or the sudoers file works but the user is still not able to access those programs due to a GTK/display error.  Any tips?

---

### Post by zvacet on 2008-02-10
>  I don't want to give the user blanket permissions by adding him to the admin group

But that is what you want to achieve.You want synaptic to work (installing,removeing...) and for that you need admin privileges,and you want your second user to be able to do that.Only way to do it is give that user admin privileges.That way you will have two users with that kind of privileges wich is redundant.

---

### Post by PeterJS on 2008-02-10
Have you tried:
```

user2	ALL = /usr/sbin/synaptic, /usr/bin/gdebi-gtk, and_so_on

```

using the full name for each program strung together with commas?

@zvacet
You don't need to be in the admin group to run synaptic, the bare minimum requirement is being able to run /usr/sbin/synaptic with root privilages. Being in the admin group is the easiest way to accomplish this. Although it would be a monumentally bad idea, you could also setuid synaptic to allow allow all users to run synaptic. Or you could set up limited sudoers permissions as the OP is trying to do.

---

### Post by &amp;)ky#)^ on 2008-02-10
@zvacet
Okay, I've re-evaluated the whole synaptic thing.  Perhaps I don't want the user to have install/uninstall ability.  However, I do want them to have control over the other applications.  The whole point here is that I want the user to be able to partially administer the system, but I don't want them to have access to most of the system config files, nor the files of other users.

@PeterJS
Yes, I have tried that approach for synaptic and it gives the user gtk/display errors.  I haven't had time to try the others yet.

---

### Post by PeterJS on 2008-02-10
> **bluej774 said:**
> Yes, I have tried that approach for synaptic and it gives the user gtk/display errors.  I haven't had time to try the others yet.

Well if they give you gtk errors as well could you post those, might be something I recognize, if nothing else it'll make good google fodder.

---

### Post by zvacet on 2008-02-10
@ **PeterJS**


> Although it would be a monumentally bad idea, you could also setuid synaptic to allow allow all users to run synaptic

I never said it is not possible,just redundant and unsecure.That is why administrator only may do that kind of things by default.You can change that,but how smart that will be?

---

### Post by &amp;)ky#)^ on 2008-02-11
Never mind.  I've found an alternative to the dilemma that started all this insanity.  But thanks for the suggestions.

---

