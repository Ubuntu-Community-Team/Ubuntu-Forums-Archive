---
title: "Installing NIS, no /etc/default/portmap file to edit"
date: 2014-03-05
forum: General Help
---

### Post by maevik on 2014-03-05
I am presently working on installing an NIS server for a small computer lab with ~6 users. I am working off of the Ubuntu instructions on setting up NIS here: [https://help.ubuntu.com/community/SettingUpNISHowTo](https://help.ubuntu.com/community/SettingUpNISHowTo)

Step 4 instructs me to edit a line found in /etc/default/portmap which is non existant on my system. I'm not sure if it is related, but this is my second time through the installation after a clean reinstall. If I were to ignore this stem and continue, I would get stuck at 

step 9: 
sudo /etc/init.d/portmap restart
[FONT=arial]
[/FONT][FONT=arial]I have successfully installed portmap nis, though I am given the message "Note, selecting 'rpcbind' instead of 'portmap'

if I try to do a dpkg-reconfigure portmap, I am told Package 'portmap' is not installed and no info is available.

I'm not really sure how to progress on this project. I understand that rpcbind is installed in place of portmap, but the NIS setup says that the portmap alias is still there and should work. Any help in understanding this would be greatly appreciated.
[/FONT]

---

### Post by maevik on 2014-03-17
I am still looking for a solution to this problem. Any insights would be helpful.

---

### Post by bkisc on 2014-05-16
rpcbind replaces portmap

cmd: nano /etc/default/rpcbind

do your edits and save this file, then cmd: service rpcbind restart

---

