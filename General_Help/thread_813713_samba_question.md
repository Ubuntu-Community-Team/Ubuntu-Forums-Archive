---
title: "samba question"
date: 2008-05-31
forum: General Help
---

### Post by fouadk on 2008-05-31
hi everyone....

i have joined my uuuntu server to windows active directory using 
sudo net ads join -U Administrator...
that worked fine....
i have also created a samba user using
sudo smbpasswd -a Administrator

when i try to access the shares on my server from the windows machine i am asked for a username and password so i enter the data i have input above but i get no success it says that the username and password are wrong

i also configured kerberos and winbind

please help

thanks in advance

---

### Post by jpietari on 2008-05-31
I use Likewise and am having the same problem.

[http://ubuntuforums.org/showthread.php?t=784100](http://ubuntuforums.org/showthread.php?t=784100)

When prompted for my credentials, I click cancel and it will connect me to the server.  So it works but it is annoying.

---

