---
title: "PLEASE PLEASE HELP! Im not in the sudoers list!"
date: 2008-06-12
forum: General Help
---

### Post by hurinth on 2008-06-12
PLEASE I NEED HELP ASAP! 

Hello Im using my ubuntu box and I needed windows to use a specific application, so I installed VirtualBox and the required modules, however, there is also a step in order to start a Virtual Machine: my account needs to member of the vboxusers, so I ran the command I though would be the correct one: > sudo usermod -G vboxusers username However after logging out to make changes effective, I lost the priveleges to run Synaptics and stuff!! I get the error in the screenshot, I found in the Manual that the correct command is this one: > sudo usermod -a -G vboxusers username with a "-a" in there, so if I try to re-run the command in a terminal I get > hardy@computer:~$ sudo usermod -a -G vboxusers hardy
[sudo] password for hardy: 
hardy is not in the sudoers file.  This incident will be reported.

My nVidia restricted drivers are also not working now after a reboot. Please please help me get back to the sudoers group!!!!! I need to finish a project!!

---

### Post by jediborger on 2008-06-12
Ok, yes this is a little problem but it can be fixed. You'll have to boot into a live linux environment. The Ubuntu desktop cd will work. Mount the install you locked yourself out of. Now you'll open up /etc/group in gedit or another text editor of choice. Look for the following line:
```
admin:x:115:[COLOR="Red"]hardy[/COLOR]
```
Add hardy after the colon as shown in red. Reboot the computer and if all goes well the hardy user should have sudo rights again and you can manually add yourself back to the other groups. Hope this helps.

---

