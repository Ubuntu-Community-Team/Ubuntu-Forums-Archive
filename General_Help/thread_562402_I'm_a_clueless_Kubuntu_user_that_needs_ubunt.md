---
title: "I'm a clueless Kubuntu user that needs ubunt"
date: 2007-09-28
forum: General Help
---

### Post by 02walshe on 2007-09-28
hi,
I'm a good windows guy, and i've been tinkering around with Kubuntu, but now i need to set up a server thin client setup on my five machines, with the server holding all the documents, settings, boot, etc... is there any documentation on this? Is there anything special about doing it with linux? Is it similar to windows in that you install and then set up or do you install a different version?
Thanks,
02walshe

---

### Post by GSF1200S on 2007-09-28
> **02walshe said:**
> hi,
I'm a good windows guy, and i've been tinkering around with Kubuntu, but now i need to set up a server thin client setup on my five machines, with the server holding all the documents, settings, boot, etc... is there any documentation on this? Is there anything special about doing it with linux? Is it similar to windows in that you install and then set up or do you install a different version?
Thanks,
02walshe

Ughhh.. this is a tough one. Its prolly easy to do, but people here will be hesitant to give you advice because theyre familar with Gnome and dont want to give you bad advice. Kubuntu is of course KDE, so some gui's etc can be different. You can of course try the Kubuntu forums, but I know they arent as active. 

I really want to help you but I dont have any other computers to gain experience with the setup youre referring to. Im in the same boat with you on the KDE side... so if you find any tutorials on gui based ways to do what your aiming for with gnome, post back and well figure out the KDE way. Im pretty sure most of it will be the same though...

---

### Post by Beernut on 2007-09-28
You might want to check out the Linux Terminal Server Project here a link.

[http://www.ltsp.org/](http://www.ltsp.org/)

I haven't had an opportunity to mess with it but I believe this what you are looking for.

---

### Post by adriantry on 2007-09-28
> **02walshe said:**
> hi,
I'm a good windows guy, and i've been tinkering around with Kubuntu, but now i need to set up a server thin client setup on my five machines, with the server holding all the documents, settings, boot, etc... is there any documentation on this? Is there anything special about doing it with linux? Is it similar to windows in that you install and then set up or do you install a different version?
Thanks,
02walshe

Edubuntu ([www.edubuntu.org](www.edubuntu.org)) is set up to use thin client almost automatically from what I understand. (I haven't tried it yet though).

There is a good article about it at
[http://www.freesoftwaremagazine.com/articles/linux_terminal_server](http://www.freesoftwaremagazine.com/articles/linux_terminal_server)

The screenshots on [http://www.edubuntu.org/GettingStarted](http://www.edubuntu.org/GettingStarted) show that there are options to install a terminal server or workstation from the boot menu.

There is further information about the thin client setup here
[http://www.edubuntu.org/ThinClientConfig](http://www.edubuntu.org/ThinClientConfig)

Edubuntu seems to use Gnome. If you prefer KDE, you could either install the kubuntu-desktop package after installation, or remaster your own version. There may be information about this on the Edubuntu site, but I didn't notice it in my quick look around.

Hope this helps.

Adrian
[www.tryanotherangle.org](www.tryanotherangle.org)

---

### Post by adriantry on 2007-09-29
A guy on the PCLinuxOS forums has just tried out a bunch of thin client Linux distros, and gives some helpful feedback.

[http://www.pclinuxos.com/index.php?option=com_smf&Itemid=26&topic=32487.0;topicseen](http://www.pclinuxos.com/index.php?option=com_smf&Itemid=26&topic=32487.0;topicseen)

---

### Post by 02walshe on 2007-10-27
Hi,
Yeah, I've looked at those links. I have a laptop that has no hard drive, but just meets the minimum standard for a network boot. It's that computer I need to boot from a server, otherwise, the other 3 need to boot themselves, not from the server, but have the documents located off of the harddrive, or a sync/backup copy on the server. In Windows you could change the local paths and data locations for users through the management consoles, but is there any way to do this in edubuntu?
Even if it's an automatic backup of data at the end of the session thats ok.

cheers,
02walshe

---

