---
title: "Sudo question"
date: 2007-11-08
forum: General Help
---

### Post by LizardKing73 on 2007-11-08
Hey all.

Got a question about sudo.

I've been using Fedora over the last year and now coming across to Ubuntu/Debian Linux, having worked with YUM for awhile I have a basic understanding of sudo but there is one thing I want to know.
In YUM typing the command "yum list update all" would cause YUM to list all the updates available, mandatory and optional as well as uploaded repository updates.
Does sudo have a command that gets it to do the same thing or close to?
A little help please.
Thanks.

---

### Post by civic_si on 2007-11-08
Do you mean Aptitude or apt-get? sudo is for root access not for updates.

---

### Post by trvllr on 2007-11-08
If you're using Gnome you can just run the update manage, or synaptics package manager.  If you're not using a GUI, then the running the command "aptitude" at the CLI will drop you into a text driven menu of the updates.  One thing you should consider is adding the other available repositories.  There are several posts on how to do that.

Enjoy!

---

### Post by LizardKing73 on 2007-11-08
> **civic_si said:**
> Do you mean Aptitude or apt-get? sudo is for root access not for updates.
Ok apt-get then, I guess for me it was the whole first thing typed thing YUM/sudo LOL.
Thanks for correcting me and yes thats what I mean.

---

### Post by LizardKing73 on 2007-11-08
> **trvllr said:**
> If you're using Gnome you can just run the update manage, or synaptics package manager.  If you're not using a GUI, then the running the command "aptitude" at the CLI will drop you into a text driven menu of the updates.  One thing you should consider is adding the other available repositories.  There are several posts on how to do that.

Enjoy!

Thanks for the info and YES I plan on adding any and all repositories, I was just wanting to get to a text list so I could see what all is there.

---

### Post by az on 2007-11-08
[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

---

### Post by LizardKing73 on 2007-11-08
> **az said:**
> [https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

A well of information including a yum / apt-get equivalent.
Thank u, thank u, thank u, and again thank u.

---

### Post by Maestro23 on 2007-11-08
> **LizardKing73 said:**
> A well of information including a yum / apt-get equivalent.
Thank u, thank u, thank u, and again thank u.

Just some more logs on the fire for ya. :)

Aptitude:[https://help.ubuntu.com/community/AptitudeSurvivalGuide?highlight=%28Aptitude%29](https://help.ubuntu.com/community/AptitudeSurvivalGuide?highlight=%28Aptitude%29)

Apt-Get: [https://help.ubuntu.com/community/AptGetHowto?highlight=%28get%29%7C%28apt%29](https://help.ubuntu.com/community/AptGetHowto?highlight=%28get%29%7C%28apt%29)

Synaptic: [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by LizardKing73 on 2007-11-09
> **Maestro23 said:**
> Just some more logs on the fire for ya. :)

Aptitude:[https://help.ubuntu.com/community/AptitudeSurvivalGuide?highlight=%28Aptitude%29](https://help.ubuntu.com/community/AptitudeSurvivalGuide?highlight=%28Aptitude%29)

Apt-Get: [https://help.ubuntu.com/community/AptGetHowto?highlight=%28get%29%7C%28apt%29](https://help.ubuntu.com/community/AptGetHowto?highlight=%28get%29%7C%28apt%29)

Synaptic: [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

Thanks yet again. When u want/need to know something ya just cant go wrong with a crowd like this. Y'all ROCK :guitar:

---

