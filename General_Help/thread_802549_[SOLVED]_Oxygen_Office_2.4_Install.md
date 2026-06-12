---
title: "[SOLVED] Oxygen Office 2.4 Install"
date: 2008-05-21
forum: General Help
---

### Post by ktechman on 2008-05-21
Can anyone help me install Oxygen Office 2.4 on an x86 amd64 system I need the dual monitor support it provides unless someone is using the beta of Ooo 3.0 and has had success with Impress and Twinview.

                             Regards

---

### Post by forestpixie on 2008-05-21
When you've downloaded and I assume extracted it what do you have in the folder, is there a folder with .debs in it?

---

### Post by ktechman on 2008-05-21
Yes 60 in all. Also do I need to uninstall open office?

---

### Post by forestpixie on 2008-05-21
Afraid I don't know that and I'm not downloading it to find out :) - maybe there is a readme in the folder, try searching google - you can > searchterm site:ubuntuforums

I would think that installing it is just a matter of running the debs in that folder - do that from the terminal.

You'll need to navigate to the folder - ```
cd Desktop
``` first - if it's on the desktop.

Change directory to the extracted folder - you can use tab to fill in the name

cd <tab> until you've got to the folder and open it, once there change into the debs directory - bear in mind that linux is case sensitive, when in the debs directory run

```
sudo dpkg -i *
```

I believe that if there are any dependency problems it will tell you and abort.

---

### Post by ktechman on 2008-05-21
Ok thank you. I started gdebi and it told me that I did need to uninstall before I even get started with it is there anything in Ubuntu that depends on Open Office or possibly break X if I do the uninstall? Also are most install folders set up in order they should be installed?

---

### Post by forestpixie on 2008-05-21
No it should be fine - in feisty and gutsy I removed the ubuntu version and installed the openoffice versions without any trouble. It will tell you it's removing ubuntu-desktop, that is  ameta package nothing to worry about.

Use synaptic to search for all openoffice and mark for complete removal.

If you're using gdebi does that not need to be done for each deb? Don't know whether that's the case but it might be easier to do it from terminal with the above command.

---

### Post by ktechman on 2008-05-21
Thank you again. 

       Cheers

---

### Post by forestpixie on 2008-05-21
Assume you've done it then and you're welcome :)

Could you mark thread solved please.

---

