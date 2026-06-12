---
title: "Where is Samba in Lubuntu 19.04? It seems to have disappeared"
date: 2019-11-10
forum: General Help
---

### Post by iconoclast12 on 2019-11-10
I updated Lubuntu from 18.04 (which had a nice samba GUI that I could setup network shares with) to 19.04 and samba seems to have vanished.. My network share is no longer setup and the GUI for Samba is gone.. If I go to the menu on the bottom left on my desktop and go to Preferences > Samba (as you can see in the image I attached) it just launches Qterminal which immediately asks if I want to close it.. If I open the terminal and try to install Samba, this is what I get...see my images.. If I google search "installing samba in Lubuntu/Ubuntu" half of the posts I find are from 5-10 years ago and I don't trust that those commands are even valid anymore.. My question is simple. I want to setup a network share with this and apparently I need to use Samba to do that.. How do I do that in 19.04?

---

### Post by Morbius1 on 2019-11-10
You are confusing samba - the server package - with Samba - which is system-config-samba. system-config-samba is gone which is a good thing really.

You are going to have to learn how to do it by editing smb.conf directly and creating a share definition there. Something like this:
> **Morbius1 said:**
> ... So if you want to  continue to use it and want to create shares do it by editing the  /etc/samba/smb.conf file directly.

For example, to create a share of your public folder accessible to  everyone on your lan at the bottom of the file add the following - I  will use my own user name in the example:
```
[Public]
path = /home/morbius/Public
read only = No
guest ok = yes
force user = morbius
```
To create a share that requires credentials to access just change [highlight]guest ok[/highlight] from [COLOR=#0000cd]**yes**[/COLOR] to [COLOR=#0000cd]**No**[/COLOR]:
```
[Public]
path = /home/morbius/Public
read only = No
guest ok = no
force user = morbius
```
If credentials are required remember that unlike Windows there are two   passwords for every user. One is used to log into the machine itself and   the other is to log into the samba server. You create that "samba   password" with this command:
```
sudo smbpasswd -a morbius
```

In either case after adding the share definition and saving smb.conf remember to restart the smbd service:
```
sudo service smbd restart
```

---

