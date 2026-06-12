---
title: "NIS Client not working wel under 18.04"
date: 2018-05-04
forum: General Help
---

### Post by pjssilva2 on 2018-05-04
I am building a lab for my students and I am facing some problems on configuring the workstations to use a NIS server for authentication. I followed the instructions from [https://www.server-world.info/en/note?os=Ubuntu_16.04&p=nis&f=2](https://www.server-world.info/en/note?os=Ubuntu_16.04&p=nis&f=2) (they are very straight forward) and even though they work well for 17.10 they do not work well in 18.04. The symptoms are

[LIST=1]
[*]If I try to login a NIS user by ssh I succeed but the login freezes for 25s before giving me bash. The following message appears in /var/log/auth.log 
pam_systemd(sshd:session): Failed to create session: Connection timed out 
[*]If I try to login using GDM the login fail with:
May  4 16:14:12 mangasarian gdm-password]: pam_unix(gdm-password:session): session opened for user pjssilva by (uid=0)
May  4 16:14:37 mangasarian gdm-password]: pam_systemd(gdm-password:session): Failed to create session: Tempo esgotado para conexão
May  4 16:15:03 mangasarian gdm-password]: pam_unix(gdm-password:session): session closed for user pjssilva 
[/LIST]

It looks like I am not the only one having such problems. I could find question on Ask Ubuntu without answers:

[https://askubuntu.com/questions/1031022/using-nis-client-in-ubuntu-18-04-crashes-both-gnome-and-unity](https://askubuntu.com/questions/1031022/using-nis-client-in-ubuntu-18-04-crashes-both-gnome-and-unity)

Any hints would be appreciated.

---

### Post by pjssilva2 on 2018-05-04
After a day of frustration I decided to use 17.10 clients as a stopgap solution. However I may have found a solution that I am not able to test right now. Please see my answer in 

[https://askubuntu.com/questions/1031022/using-nis-client-in-ubuntu-18-04-crashes-both-gnome-and-unity](https://askubuntu.com/questions/1031022/using-nis-client-in-ubuntu-18-04-crashes-both-gnome-and-unity)

I decided to add this here before testing because it my save a few hours in someone's weekend!

---

