---
title: "Vista in Ubuntu -- dream or reality?"
date: 2007-02-03
forum: General Help
---

### Post by dmee on 2007-02-03
Colleagues, is it **POSSIBLE** to run **Windows Vista** on a Beryl/Compiz cube's side in Ubuntu?

[LIST=1][*]Why **Xen 3.0.3** sucks?
[LIST][*]it DOES NOT support Vista as DomU (it is freezing at the beginning of an install)[*]beryl DOES NOT run on a xenified kernel[*] 'guests currently cannot be saved and restored, nor migrated'[*]'there's currently no support for APM or ACPI, hence you'll experience reduced battery life and no suspend/resume'
[/LIST]
[*]Why **kvm 1.2 + modified qemu** sucks?
[LIST][*]it DOES NOT support Vista (it is freezing at the beginning of an install)[*]it is really slow! yeah, i DO HAVE hvm support.[*]it DOES NOT allow to maximize a guest window (--fullscreen is not a solution of the problem at all)
[/LIST]
[*]Why **vmware** sucks?
[LIST][*]it is VERY SLOW
[/LIST]
[/LIST]

**[COLOR="Blue"]Any suggestions?[/COLOR]**

---

### Post by glabouni on 2007-02-03
xen doesn't support 3D acceleration hence beryl not working and I guess vista not installing. you can check if sabayon would run as a guest to try this.

btw does your cpu include virtualization technology ? 
have you checked that the vista version you're using is allowed to run into an emulated machine ? I've heard some vista version are locked out of virtualization, dont know if it's license only or if they're s actually code that prevent you from doing it in vista.

it seems to me that vista is the sucking part of your trouble, not the other way around.
could be that vista is designed not to run in xen, qemu or vmware, [microsoft has long history of playing the incompatibility card]("http://www.theregister.co.uk/1999/11/05/how_ms_played_the_incompatibility/"), or could be that software vendor have to upgrade their software for vista compatibility.

---

### Post by dexter on 2007-02-03
Remember that you need to get Vista Ultimate to run in a virtual machine, the other versions won't install on virtual machines.

---

### Post by dmee on 2007-02-03
> **glabouni said:**
> btw does your cpu include virtualization technology ?
Sure, I have doublechecked.

> **dexter said:**
> Remember that you need to get Vista Ultimate to run in a virtual machine, the other versions won't install on virtual machines.
You sure? Very interesting because I do have Vista Business.

---

### Post by meng on 2007-02-03
I remember hearing that running Vista in a VM was contrary to the EULA. I didn't know there was an exception for Ultimate.

---

### Post by jocko on 2007-02-03
[http://www.dailytech.com/article.aspx?newsid=5951](http://www.dailytech.com/article.aspx?newsid=5951)

---

### Post by dmee on 2007-02-03
1) Business edition supports virtualization
2) Vista installer DOES NOT know my product key before I have provided one. So it DOES NOT know my Vista edition before that moment. But anyway it is freezing before that moment

So the problem is hiding somewhere else. **[COLOR="Blue"]WHERE?[/COLOR]**

---

### Post by clicks on 2007-02-06
I have installed a Vista Business Edition under Paralles Workstation 2.2 and VMware Workstation 6 Beta, both work without problems - of course the Aero interface doesn't work. Actually VMware seems to be a bit faster and perhaps they will be able to improve the DirectX emulation in next versions.

---

### Post by Rich78 on 2007-02-06
Use VirtualBox instead, it's quicker than VMWare too.

As you'll see on this thread running Vista with Beryl/Compiz enabled.

[http://www.ubuntuforums.org/showthread.php?t=351212&highlight=virtualbox]("http://www.ubuntuforums.org/showthread.php?t=351212&highlight=virtualbox")

---

### Post by dmee on 2007-02-06
Thank you.

It is Windows XP but anyway :D

---

### Post by Rich78 on 2007-02-06
](*,) So it is, just took one look at the theme and thought it was Vista.

Never mind it all looks the same \\:D/

---

### Post by stbcomp on 2007-03-02
I have managed to get Vista Ultimate working under vmware server. But I can't seem to get the ethernet card to work even though I have the correct driver from realtek. It installs the software correctly, but still doesn't pick up the driver. It's an RTL8139c, and works fine under Ubuntu.
Any ideas?

---

