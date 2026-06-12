---
title: "Login is freezing after Enter"
date: 2012-10-24
forum: General Help
---

### Post by compauer on 2012-10-24
Hello,

I am using Ubuntu for few days and now I got a Login problem.
Like you can see my problem in the title. My System is freezing, if I try to login. I can use the terminal und I can even use programs with the terminal, but I can´t login to the ubuntu desktop.

It would be nice to get some help.

(My english is not so good)

---

### Post by danielbauwens on 2012-10-24
Try this:
```
CTRL-ALT-F2
```

Then type:
```
sudo stop lightdm
```
you will get a notification: lightdm stop/wait then enter the following:

```
sudo start lightdm
```
This will restart your Xserver and you should go back to the login screen.

***Thanks to TrailRider for this information.***

Daniel

---

### Post by compauer on 2012-10-24
Hi ty for your answer.
After typing sudo stop lightdm, i got this error:
stop: Unknown job lightdm

---

### Post by danielbauwens on 2012-10-24
Okay try instead of "sudo stop and start lightdm"

Type this:
```
sudo restart lightdm
```

---

### Post by compauer on 2012-10-24
Same result :(

---

### Post by danielbauwens on 2012-10-24
Hmp...
Try:
```
sudo service lightdm restart
```

If that doesn't work try:

```
sudo restart gdm
```

or:

```
ALT-Prtsc-k
```

Hope it helps
Daniel

---

### Post by compauer on 2012-10-24
I get an errer after the first code:
The system is running in low-graphics mode

Your screen, graphic, and input settings could not br detected correctly. You will need to configure these yourself.



I guess i can't do it by myself :/

---

