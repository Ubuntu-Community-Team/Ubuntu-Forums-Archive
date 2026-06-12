---
title: "Some software similar to Ofris"
date: 2022-08-21
forum: General Help
---

### Post by lobras on 2022-08-21
Hi ¡¡¡ Could someone help me to find a way to freeze one user? I am teacher and a lot of pupils use the same computers. I would like to have the computer equal forever, like a liveusb.

I have tried to use Ofris, but now it does not work.

any ideas?

Thanks

---

### Post by coffeecat on 2022-08-21
*Thread moved to **General Help**.*

---

### Post by Impavidus on 2022-08-21
I've never done this myself, so I shan't give detailed instructions, but I've got a few considerations.

For school systems, there are basically two ways to arrange things:

1: Create one user to be used by all pupils. They can login and do whatever they want on the pupil account, but cannot change anything outside the /home/pupil directory. After logout, this directory is reset to defaults, password is reset too. You don't really need a password. I think there's something called guest account, but I'm not sure it's still available. It basically does as described above. The pupils cannot keep their files from one session to another, but have to store them on usb or in the cloud instead. I've seen the suggestion to delete the account after use and create a new one.

2: Give each pupil a separate login, with home directories on network storage, so that the same home directory is available on every computer. Login credentials can be centrally stored too. The pupils can keep their files from one session to the next, cannot mess with each other's account (except through social engineering), but may share files if they want. The admin user (you) needs a script to reset the pupils' settings whenever they mess things up (which will undoubtedly happen). It's possible to give each pupil a quotum for the disk space they are allowed to use.

Option 1 may be easier to set up, but will frequently lead to lost files, lack of backups and it's just not very convenient.

---

