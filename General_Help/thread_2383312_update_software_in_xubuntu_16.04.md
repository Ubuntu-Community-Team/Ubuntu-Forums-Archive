---
title: "update software in xubuntu 16.04"
date: 2018-01-23
forum: General Help
---

### Post by ulissipus on 2018-01-23
Having a bit of a problem with Software Updater in Xubuntu 16.04. Usually get an error message stating software updater failed / check your internet connection / please try later etc. Then as I prepare to turn off, I get another message saying that some updates were downloaded but not all.

My question: with 'sudo get update' & 'sudo get upgrade' do i get the same thing as in Software Updater?

Thanks for replies.

---

### Post by vasa1 on 2018-01-23
> **ulissipus said:**
> Having a bit of a problem with Software Updater in Xubuntu 16.04. Usually get an error message stating software updater failed / check your internet connection / please try later etc. Then as I prepare to turn off, I get another message saying that some updates were downloaded but not all.

My question: with 'sudo get update' & 'sudo get upgrade' do i get the same thing as in Software Updater?

Thanks for replies.
The correct commands are```
sudo apt-get update
```and```
sudo apt-get upgrade
```You could post the entire outputs of each command here if there's something you don't understand.

---

### Post by Impavidus on 2018-01-23
And to make it complete, there's```
sudo apt-get dist-upgrade
```which may install new packages like kernel updates. Those three commands together do the same as the update manager, but add useful error messages.

---

### Post by ulissipus on 2018-01-25
thank you very much. You in a way confirmed what I thought. But I must say I knew nothing of   ... dist-upgrade.

Thanks again!

---

