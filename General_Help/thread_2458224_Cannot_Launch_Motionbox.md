---
title: "Cannot Launch Motionbox"
date: 2021-02-19
forum: General Help
---

### Post by sierraalpha288 on 2021-02-19
I installed motionbox and all of it's dependencies. There wasn't any errors on the build. I restarted my pc and searched for the app and there isn't anything. I tried to launch from terminal in every way I could come up with. Still nothing. Anyone have an idea what I'm doing wrong?

---

### Post by howefield on 2021-02-19
MIght help to show others what is happening and the version of Ubuntu that you are using.

```
cat /etc/os-release
```

Copy/paste the terminal input/output when you try to start Motionbox,

---

### Post by sierraalpha288 on 2021-02-19
I'm currently at work, but when launching from terminal using command "motionbox" it says no such file or directory when I can see the files are installed. Searching for the program in the menus shows nothing. I'm running 20.10.

---

### Post by howefield on 2021-02-19
Does..

```
./start.sh
```

run from the extracted Motionbox folder start the application ?

---

