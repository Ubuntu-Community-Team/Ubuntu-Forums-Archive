---
title: "Problems while installing .bin packages or from source"
date: 2008-07-07
forum: General Help
---

### Post by rodrigodiaz on 2008-07-07
Hi guys 
This will be my first post here. I m on ubuntu 8.04. 
Whenevr i try to install a software from source or binary files, i get permission errors. Elevating as root from terminal also gives same errors.

Do i need to log in as root to do such installs ?

Plz help .

---

### Post by iaculallad on 2008-07-07
> **rodrigodiaz said:**
> Hi guys 
This will be my first post here. I m on ubuntu 8.04. 
Whenevr i try to install a software from source or binary files, i get permission errors. Elevating as root from terminal also gives same errors.

Do i need to log in as root to do such installs ?

Plz help .

Maybe, you just missed inserting sudo in your commands.

Try relating to this [page]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by rodrigodiaz on 2008-07-07
sudo was there but i figured the problem from the page you linked . It was a permissions issue. I added the execute permission and it went fine. Thank you for the help. :)

The binary was installed . I ll try installing from source and post back the result.

One more thing i would like to ask - Regarding installing softwares. I know its always better to install using the synaptic package manager , but if something isnt there , then other packages are there. But do we need to create launchers for every such install and how to make them come in add/remove ????
I installed a binary and now have no idea where it has gone , where to use it and where to remove. :(

---

### Post by lamego on 2008-07-07
What software are you trying to install ? Some software installed from executables does create the desktop entry for you. You can also search for the software on getdeb.

---

### Post by rodrigodiaz on 2008-07-07
i installed sun java . Got the .bin from their website.
Would it be better to just stick to synaptic and .deb packages for now ?

---

