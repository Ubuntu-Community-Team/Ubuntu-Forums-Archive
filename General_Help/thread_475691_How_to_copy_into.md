---
title: "How to copy into"
date: 2007-06-16
forum: General Help
---

### Post by pumpkinpapa on 2007-06-16
I installed the Seamonkey browser and found it impossible to copy plugins into it's installation directory at /usr/local/seamonkey1.1.1/plugins/. I guess I should have put it into the /lib directory, my mistake. 

I think there must be a way to copy these files into the directory but I don't know the correct commands. Where can I start?

---

### Post by pistcivet on 2007-06-16
SeaMonkey keeps plugins in your home folder:
~/.mozilla/plugins/

Also Seamonkey is now at version 1.1.2

It might help to know what plugin you're trying to install.

---

### Post by pumpkinpapa on 2007-06-16
Oops, yes I stated the wrong version number before, thanks for the reminder.

I am trying to copy the plugins from the firefox folder to the seamonkey folder but I think I should uninstall seamonkey as I don't have permission to do this, I'm still trying to get a hang of the permissions model :)

I have no seamonkey folder in my Home directory. My plugins folder is found at /usr/local/Seamonkey/Seamonkey/

So I think I must uninstall Seamonkey altogether and reinstall into the /lib directory. How does one uninstall seamonkey if the installer was used to install it?

---

### Post by pistcivet on 2007-06-16
OK. To uninstall SeaMonkey:
```
cd /usr/local/
sudo rm -dr seamonkey
```
Done.

Also, you should not install SeaMonkey using sudo. And you must run SeaMonkey
once as root before you use it:
```
sudo su
./seamonkey-installer
/usr/local/seamonkey/seamonkey
exit
```

SeaMonkey should automagically find/use Firefox plugins.
(It puts its plugins in the same folder)
Not sure why it isn't in your case.
If you installed SeaMonkey using sudo, you may have messed up permissions
in your profile folder.
( ~/.mozilla/default/<random>.slt/ )

If you want to copy files where you have no permissions:
```
sudo cp /from/here/file /to/there/file
```
But you should not have to do this.

---

### Post by pumpkinpapa on 2007-06-18
Resolved!

Thanks for all the code pistcivet!

I also discovered this script which allows one to auto update Seamonkey, called [Ubuntuzilla]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Update_Official_Mozilla_Build_of_Seamonkey")

Everything works fine now :D

---

