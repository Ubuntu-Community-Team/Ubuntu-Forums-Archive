---
title: "Charity class room deployment situation - seeking help"
date: 2016-11-19
forum: General Help
---

### Post by bruce+chastain on 2016-11-19
Hello,

I'm part of a charity and we support a small computer lab in west Africa, the country of Benin specifically. And I've managed to convince the rest of the team that it would be good for us to change from Win7/xp to Ubuntu. So what we're looking to do is come up with a way which we can install ubuntu on all the computers in the lab, about 20 of them. We would like the computers to have some specific software installed and it would be great if that could be somehow included in the installation. In addition we would like to disallow any writing to the home folders. I've seen some ideas by searching around but nothing that seems to really fit the bill. Could anyone point me in the right direction please?

Thank you,
Bruce

---

### Post by wildmanne39 on 2016-11-19
To know if the software can be installed we need to know what software it is, if it is windows software then it can not.

---

### Post by bruce+chastain on 2016-11-19
Hi Wild Man! no certainly not Windows software! :) Actually we haven't really talked about what software yet. I'm thinking just some common stuff like for example kolourpain, chromium, kdenlive.

---

### Post by sudodus on 2016-11-19
Welcome to the Ubuntu Forums :-)

I suggest that you configure a master system as an [OEM installation](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview), which makes it easy to install the same system to the other computers.

You can use the [guest session](https://help.ubuntu.com/community/CustomizeGuestSession) in order to protect the system. What was created during a guest session will be wiped after logout.

---

### Post by wildmanne39 on 2016-11-19
kolourpain is for kubuntu it is still in the repositories, but if you use ubuntu then it will most likely pull in a lot of kubuntu packages as well, so you may want to use kubuntu.

Ubuntu has gimp instead it is a very good program but it has a learning curve. The buntu family of Os's come with hundreds and hundreds of software that can be easily installed, and if it is not in the repositories can probably be installed from a third party source but they is usually discouraged unless you trust the third party source.

Chromium and kdenlive can be installed but I am not sure if they can be during install though.

---

### Post by bruce+chastain on 2016-11-19
actually getting the software isn't an issue really for me. For the protection of the systems I think the guest session seems like a good solution. However I think I didn't do a good job of explaining the goal for the deployments. What I'm looking to do is find a way to have an installation image with some software already installed. This way we can easily install the same system with the same software on all the PCs. Also if somehow one of them gets trashed, we can easily get that one PC going again with this image. I was searching and I found this software called clonezilla and it looks like that might do the trick, but I need to look more into it.And Sudodus thanks for the welcome :)

---

### Post by sudodus on 2016-11-19
Yes, Clonezilla fits into this picture. The idea with the OEM installation method is to use Clonezilla (or some other method) to make an image of the master system, and copy/clone from the image to the other computers.

You can do it without OEM method too, but then the systems will get the same IDs etc, which will cause confusion, if you connect them in a local area network. The OEM method will make each system unique - the computer ID, and a user will be selected individually and with an individual password, if that is what you want.

---

### Post by bruce+chastain on 2016-11-20
Okay, I think I have enough to go on now. Thanks so much for the help!

---

### Post by sudodus on 2016-11-20
You are welcome :-)

Finally, when you feel that the problem described in post #1 is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED.

If you need help later, it is better to start a new thread with a good title that describes the new problem.

---

