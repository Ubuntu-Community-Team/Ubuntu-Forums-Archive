---
title: "Is it possible to set noatime as default for all mounts?"
date: 2022-09-07
forum: General Help
---

### Post by Paddy Landau on 2022-09-07
The default mount option for Ubuntu is [FONT=courier new]relatime[/FONT]. However, for most purposes these days, [FONT=courier new]noatime[/FONT] is preferred, especially for SSDs or where disk speed is critical.

Is it possible to change the default mount to [FONT=courier new]noatime[/FONT], which of course could be overridden where necessary? At present, I have to manually specify it for items not in [FONT=courier new]/etc/fstab[/FONT], e.g. external USB drives, which means that I don't use automatic mounting methods such as Disks ([FONT=courier new]gnome-disks[/FONT]).

 I'll probably never need or want to use [FONT=courier new]relatime[/FONT].

I've been searching on the 'net, and so far the only solution that I've found is to change the code in the kernel and recompile it! That is unsuitable for someone like me, not only because I wouldn't know where to start, but also because I'd have to do it every time the kernel is updated.

---

### Post by TheFu on 2022-09-07
I'd use a devops tool that is omnipotent and have it force any options I wanted into the fstab, autofs files and any systemd-mount-unit files.  The "defaults" for mounts is set by the build options for mount, I'd think.  Of course, if you change the defaults in the source code, then you'll have to maintain those going forward.  I'd use ansible, if this was really bothersome. Since I generally touch the fstab just a few times over the life of most systems, I don't find setting mount options too cumbersome. They are part of my system-setup checklist.

---

### Post by Paddy Landau on 2022-09-07
> **TheFu said:**
> I'd use a devops tool that is omnipotent and have it force any options I wanted into the fstab, autofs files and any systemd-mount-unit files.
That's an interesting concept, but how specifically would one do this? Can it be done reasonably simply, or would it be a complex procedure?
> **TheFu said:**
> The "defaults" for mounts is set by the build options for mount, I'd think.  Of course, if you change the defaults in the source code, then you'll have to maintain those going forward.
That's what I expected, but I was hoping wouldn't be the case!
> **TheFu said:**
> I'd use ansible, if this was really bothersome.
I'm unfamiliar with Ansible. It looks like an organisation-wide automation tool rather than something that I'd use on a desktop. Am I right?
> **TheFu said:**
> Since I generally touch the fstab just a few times over the life of most systems, I don't find setting mount options too cumbersome. They are part of my system-setup checklist.
I've actually written a script to mount my most popular devices automatically with noatime.

… And, as I write this, I have just realised that I can place them in /etc/fstab using the UUID to identify the partitions. Damn, in hindsight, that is the obvious way for my frequent devices!

---

### Post by TheFu on 2022-09-07
> **Paddy Landau said:**
> That's an interesting concept, but how specifically would one do this? Can it be done reasonably simply, or would it be a complex procedure?
Learning to use ansible is about 15 minutes for simple things like modifying lines in 1 system file.

> **Paddy Landau said:**
> I'm unfamiliar with Ansible. It looks like an organisation-wide automation tool rather than something that I'd use on a desktop. Am I right? For 1 systems, devops tools are overkill, but for 5 systems, they start making sense.  For 50,000 systems, there's no other choice.  I do use Ansible to manage single systems, but I started out having it manage the /etc/hosts files on all my systems as my first goal.  That uses a template, since the /etc/hosts file for each system is slightly different. There is a templating replacement language - Jinga2 - I think that's the name. {{parameter}} and as long as the parameter is specified in the ansible playbook for the system, it will be replaced with the value.

> **Paddy Landau said:**
> I've actually written a script to mount my most popular devices automatically with noatime.
Why?  That seems like the hard way.

> **Paddy Landau said:**
> … And, as I write this, I have just realised that I can place them in /etc/fstab using the UUID to identify the partitions. Damn, in hindsight, that is the obvious way for my frequent devices!
UUIDs are fine for computers.  Humans are better served using LABELs (partition or file system) or if you use LVM, the /dev/{vgname}/{lvname} provides clear information about a mount device/file system, unlike a label or UUID.

Just ensure that the LABEL is unique.

---

### Post by Paddy Landau on 2022-09-07
Thanks for all the information!
> **TheFu said:**
> Humans are better served using LABELs
… And that's my second facepalm moment today, ha ha! Yes, you are absolutely correct! Thank you.

---

