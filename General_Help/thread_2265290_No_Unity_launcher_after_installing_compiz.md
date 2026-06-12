---
title: "No Unity launcher after installing compiz"
date: 2015-02-14
forum: General Help
---

### Post by Sagar_Patil on 2015-02-14
Hi, somehow I don't have the unity launcher after installing compiz. I enabled one of the tweak done know which one. I have tired opening the terminal but it does not open.
I have tried this [http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears](http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears) but there is no unity plugin to enable. 

My last option is to factory reset or there is a way?

---

### Post by deadflowr on 2015-02-14
I'm guessing you mean you installed ccsm, since compiz would already be installed if you are using unity.
So in the section Desktop there is nothing called Ubuntu Unity Plugin?
Perhaps reinstall unity.
```
sudo apt-get install unity
```
but I would double/triple check that the unity plugin is actually not there before trying a reinstall.

---

### Post by Sagar_Patil on 2015-02-14
> **deadflowr said:**
> I'm guessing you mean you installed ccsm, since compiz would already be installed if you are using unity.
So in the section Desktop there is nothing called Ubuntu Unity Plugin?
Perhaps reinstall unity.
```
sudo apt-get install unity
```
but I would double/triple check that the unity plugin is actually not there before trying a reinstall.

I installed Unity using the code and it appeared in the compiz manger. I enabled it and restarted my computer, but it didn't work.

There is no unity.

---

### Post by deadflowr on 2015-02-14
Do you have another desktop session installed?
Like, did you install the gnome flashback session?

(I ask, because that ccsm looks like what it looks like when gnome flashback(with compiz) is in session.
in normal unity session the unity plugin does not have an enable check box next to it. To enable or disable unity you need to enter the plugin's page.)

---

### Post by Sagar_Patil on 2015-02-14
I have no idea what you mean by gnome flashback session.

I dual booted windows 7 and ubuntu.

---

### Post by deadflowr on 2015-02-14
When you log into Ubuntu how do you open ccsm?

---

### Post by Sagar_Patil on 2015-02-14
I press Ctrl+Alt+F1 to open tty1
I login with the user name and password
type ```
export DISPLAY=:0
```
then ```
ccsm
```
then press Ctrl+Alt+F7/F8 (dont remember)
then ccsm opens.

---

### Post by monkeybrain20122 on 2015-02-14
Doesn't make a lot of sense since Ubuntu comes with compiz and unity already installed. Are you sure you are using Ubuntu and not variations like xubuntu or kubuntu?

---

### Post by Sagar_Patil on 2015-02-14
Yes, its ubuntu.

---

### Post by deadflowr on 2015-02-14
I wonder if by doing the method you are trying you are simply loading the wrong profile when you login.
Ubuntu comes with two compiz profiles Unity and default.
My thinking is that when you use the export display method, it sets it for one, but when you login it loads it for the other.
Perhaps when you do the export method go into the Preferences section in the side pane and toggle the profile.
Thentry setting up the unity plugin for both.
Then restart and try it.

You might also try the dconf method, using the same export method you use, do
```
sudo apt-get install dconf-tools
```
then
```
dconf reset -f /org/compiz/
```
then
```
setsid unity
```
then, again, try to restart it.

---

### Post by Sagar_Patil on 2015-02-14
> **deadflowr said:**
> I wonder if by doing the method you are trying you are simply loading the wrong profile when you login.
Ubuntu comes with two compiz profiles Unity and default.
My thinking is that when you use the export display method, it sets it for one, but when you login it loads it for the other.
Perhaps when you do the export method go into the Preferences section in the side pane and toggle the profile.
Thentry setting up the unity plugin for both.
Then restart and try it.

You might also try the dconf method, using the same export method you use, do
```
sudo apt-get install dconf-tools
```
then
```
dconf reset -f /org/compiz/
```
then
```
setsid unity
```
then, again, try to restart it.

I love you. 

Thanks for helping!

---

