---
title: "Customizing Wubi"
date: 2008-07-04
forum: General Help
---

### Post by doktoreas on 2008-07-04
Hello everybody.

I have customized the ubuntu livecd to suite my need; now I'd like to add more applications in the menu shown when the livecd starts in Windows.

Is it possible?

Thanks

---

### Post by ago on 2008-07-04
Yes, see the umenu project in launchpad. You will need to change the source and recompile. It is written in nsis.

---

### Post by doktoreas on 2008-07-04
Thanks for your answer..
Inside the project page in launchpad, I haven't find the source package.

Got any other link?

Bye
Luca

---

### Post by ago on 2008-07-04
[https://code.launchpad.net/~ubuntu-installer/umenu/devel](https://code.launchpad.net/~ubuntu-installer/umenu/devel)

You need to use bzr

bzr branch lp:umenu

---

### Post by doktoreas on 2008-07-04
Ago, thank you very much for all the info you submitted.
I have read the INSTRUCTION file and some tutorial on NSIS, but haven't understand the part where it put the setup for the windows application (like firefox)..any idea?

Thanks
Luca

---

### Post by ago on 2008-07-04
> **doktoreas said:**
> Ago, thank you very much for all the info you submitted.
I have read the INSTRUCTION file and some tutorial on NSIS, but haven't understand the part where it put the setup for the windows application (like firefox)..any idea?

Thanks
Luca


In the umenu case nsis is used only as a frontend to run some commands. To compile from within Ubuntu run

make prerequisites && make

that will generate an exe in the dist folder

You may want to change src/umenu.nsi show_welcome
In ther the AddControlBlock macro adds button and label
The actual commands are executed within .onGUIEnd

---

