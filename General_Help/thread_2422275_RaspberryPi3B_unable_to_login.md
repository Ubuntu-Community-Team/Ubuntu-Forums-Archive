---
title: "RaspberryPi3B unable to login"
date: 2019-07-04
forum: General Help
---

### Post by ccor58 on 2019-07-04
I have created new key pairs using keygen defaults and ubuntu1 does not accept them so I can't log into RaspPi ubuntu Core. It keeps asking for a password that does not exist; hitting return with a blank password only results in an error. The device is sitting on the table in front of me why do I need to use ssh key through ubuntu 1 login to initially set the damn thing up. 

I have separate ubuntu 1 logins for different purposes and devices but they are all accessed from a single username/home directory on the linux ubuntustudio box. Only this one that needs a key transferred is a problem and there is no way to just use a password. Is there a workaround to this madness so I can just log into the ubuntu Core Pi OS and switch to root and set it up the way I want it?

---

### Post by CharlesA on 2019-07-04
Hi,

I'm guessing you were following this guide, right? [https://ubuntu.com/download/iot/raspberry-pi-2-3-core](https://ubuntu.com/download/iot/raspberry-pi-2-3-core)

Do you see your SSH key on your Ubuntu One account?

---

### Post by ccor58 on 2019-07-04
No I don't. When I created the initial one for another email address that one was imported and showed properly. However, when I created the key pair for the second email login address I use with the ubuntu 1 for a different device/purpose I do not see it in the login screen. I am able to create separate folders in the .ssh folder to hold the key pairs and just have the active one I want at any time showing in the .ssh folder as a available, however when I go to import it it does not get imported into the second login; which has a different email and username distinct from the initial one.

The only other google search result almost intimated I had to create separate linux users with separate home directories for each key pair which seemed strange to me.

---

### Post by CharlesA on 2019-07-04
> **ccor58 said:**
> No I don't. When I created the initial one for another email address that one was imported and showed properly. However, when I created the key pair for the second email login address I use with the ubuntu 1 for a different device/purpose I do not see it in the login screen. I am able to create separate folders in the .ssh folder to hold the key pairs and just have the active one I want at any time showing in the .ssh folder as a available, however when I go to import it it does not get imported into the second login; which has a different email and username distinct from the initial one.

The only other google search result almost intimated I had to create separate linux users with separate home directories for each key pair which seemed strange to me.

That doesn't sound right. What error did you get when you tried to upload the public key? There was a link to do so here: [https://login.ubuntu.com/ssh-keys](https://login.ubuntu.com/ssh-keys)

---

### Post by ccor58 on 2019-07-05
error is   Invalid SSH key data: '~/.ssh/id_rsa.pub'

---

### Post by HermanAB on 2019-07-05
Try my guide here:
[https://www.aeronetworks.ca/2017/12/raspberrypi-3-headless-with-ssh.html](https://www.aeronetworks.ca/2017/12/raspberrypi-3-headless-with-ssh.html)

---

### Post by CharlesA on 2019-07-06
> **ccor58 said:**
> error is   Invalid SSH key data: '~/.ssh/id_rsa.pub'

Just in case, I'm missing something, did you open the file and paste the contents of it, or just paste the path?

Also check out Herman's link. That's a good write up, too.

---

