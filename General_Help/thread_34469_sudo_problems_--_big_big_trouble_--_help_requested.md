---
title: "sudo problems -- big big trouble -- help requested"
date: 2005-05-15
forum: General Help
---

### Post by crazybill on 2005-05-15
Well, I blew it.  I tried to do something late at night when I was tired.
I did a  
**sudo chmod 740 /etc/sudoers**
so that I could manually add a user to the sodo list.
I made the change no problem. I have done it several times before. 
However, in past attempts,  I did a sudo -s -H so I had no trouble changing permissions back after making the change, because I was in root.
This time I did not do that. I did "sudo chmod 740 /etc/sudoers" and did not stay in root.
When I went to change permissions back with:
**sudo chmod 440 /etc/sudoers**
I, of course,  got an error!
```

teacher@ubuntu4:/etc $ chmod 440 sudoers
chmod: changing permissions of `sudoers': Operation not permitted
```

"Duh!" I thought, "I am not in root. I must use sudo":

```

teacher@ubuntu4:/etc $ sudo chmod 440 /etc/sudoers
sudo: /etc/sudoers is mode 0740, should be 0440
teacher@ubuntu4:/etc $
```

... WHOOPS,  because /etc/sudoers has 740 permission, I can sudo into root. I did not set up root with a password... so what are my options?

It seems I can not get into root at all now.  The catch-22 is that I can not change /etc/soders to 440 because it requires root or sudo to do that and you can't do that unless you already have the sudoer file at 440.

I assume, I am in big trouble and have no choice but to reinstall Ubuntu/kubuntu from scratch.

Any other nicer options that anyone knows? .. or am I in permanent dodo?

---

### Post by nad on 2005-05-15
Try booting into recovery mode and changing it. Barring that, try changing it from a live cd that will give you access as the superuser.

---

### Post by crazybill on 2005-05-15
Thanks. I rebooted in recovery mode and it booted me in as root. I then made the changes and all is well.

---

