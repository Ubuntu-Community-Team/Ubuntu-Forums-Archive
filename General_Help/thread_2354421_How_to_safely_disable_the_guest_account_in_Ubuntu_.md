---
title: "How to *safely* disable the guest account in Ubuntu 16.04 LTS"
date: 2017-03-02
forum: General Help
---

### Post by John_Patrick_Mason on 2017-03-02
Yesterday I was looking to try to disable the guest account on one of my laptops when I practically ended up bricking the system, forcing me to reinstall Ubuntu from scratch. Luckily, I always back up my all my files on a USB thumb drive. So, what do I need to do to disable the guest account? I'm looking for some configuration file I can quickly edit, where I can add a command that I can later disable/re-enable by commenting it out.

---

### Post by deadflowr on 2017-03-02
I usually create a file:
```
/etc/lightdm/lightdm.conf.d/10_my-config.conf
```
and add whatever I need for what ever setting I want for the login.
In this case adding the guest disable entry.

***You must create and save the file as root, so use either gksu gedit, or sudo nano (or sudo vi; all depending on which text editor you prefer. 
(( gksu needs to be installed, easy enough, just run *sudo apt install gksu*))

It should look like this:
```
[SeatDefaults]
allow-guest=false
```
then save 
and restart lightdm
```
sudo systemctl restart lightdm
```
(If you are running a session (meaning you are logged in), this command will reset that back to the login screen, so save anything before applying)
rebooting also work, if that's your thing.

More on lightdm here:
[https://wiki.ubuntu.com/LightDM]("https://wiki.ubuntu.com/LightDM")

---

### Post by John_Patrick_Mason on 2017-03-02
> **deadflowr said:**
> 

***You must create and save the file as root, so use either gksu gedit, or sudo nano (or sudo vi; all depending on which text editor you prefer. 
(( gksu needs to be installed, easy enough, just run *sudo apt install gksu*))



Question: How did you create the file as root?

I tried typing:
```
sudo > 10_my-config.conf
```

but it wouldn't let me.

---

### Post by deadflowr on 2017-03-02
Use a text editor, like nano
```
sudo nano /etc/lightdm/lightdm.conf.d/10_my-config.conf
```
Write the entries for the file, then
To save press ctrl + X.
then press enter to accept that you are modifying the file.
Then press enter to save the file, you can double check that the file name and the location it says are correct; if the file name is not right you can change it here, before you press enter.
Then that is it.

Hope that makes sense

---

### Post by John_Patrick_Mason on 2017-03-02
I get it now. I didn't know you could create files using nano, I thought nano was just for *editing* text files. Could you do the same using vi? I much prefer it over nano.

```

sudo vi /etc/lightdm/lightdm.conf.d/10_my-config.conf

```

---

### Post by ajgreeny on 2017-03-02
Yes; use whatever text editor you want, either GUI such as gedit, or cli such as nano or vi, it makes no difference as you are just creating a text file.

---

### Post by John_Patrick_Mason on 2017-03-02
It works! Thanks guys for helping me out.

---

