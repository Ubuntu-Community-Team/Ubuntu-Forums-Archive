---
title: "guest account help plz!!!"
date: 2008-03-25
forum: General Help
---

### Post by lemonlaw95 on 2008-03-25
does anyone know how to make a guest account purge itself on logout WITHOUT getting rid of settings made by me? :confused: what i want is to configure the account, and then make it reset itself to that configuration when someone logs out.  i already put this code in /etc/gdm/PostSession/Default:

if [ "$HOME" = "/home/guest" -a  -d "/home/guest" ]; then
    pkill -9 -u guest
    rm -rf /home/guest
    mkdir /home/guest
    chown guest:guest /home/guest
fi

just before "exit 0", but that makes the account just like it is when you first create and log into it. :(  any help will be greatly appreciated!!! ::KS

---

### Post by ibuclaw on 2008-03-25
> **lemonlaw95 said:**
> does anyone know how to make a guest account purge itself on logout WITHOUT getting rid of settings made by me? :confused: what i want is to configure the account, and then make it reset itself to that configuration when someone logs out.  i already put this code in /etc/gdm/PostSession/Default:

if [ "$HOME" = "/home/guest" -a  -d "/home/guest" ]; then
    pkill -9 -u guest
    rm -rf /home/guest
    mkdir /home/guest
    chown guest:guest /home/guest
fi

just before "exit 0", but that makes the account just like it is when you first create and log into it. :(  any help will be greatly appreciated!!! ::KS

I recommend to create a backup somewhere first.
OK...
First re-enter your guest account and re-configure it.
Now, before logging out.
Open a terminal and change to a user who has sudo permissions.
ie:
```
 su administrator 
```
then type in:
```
 sudo -s 
```
enter your password again to become root, then follow these steps:
```

cp /home/guest /etc/guest.bak -R

```
then change your script to this
```

if [ "$HOME" = "/home/guest" -a  -d "/home/guest" ]; then
    pkill -9 -u guest
    rm -rf /home/guest
**    cp /etc/guest.bak /home/guest -R**
    chown guest:guest /home/guest
fi

```

And you're sorted!!

Regards
Iain

---

### Post by lemonlaw95 on 2008-03-25
i'll try that in a little while.  but in the mean time, THANK YOU SO MUCH!!! :-D  i've been trying to get a solution to this for SOOO long!
but why didn't i think of that... :confused: oh well!

---

### Post by ibuclaw on 2008-03-25
The problem was, when you remove the guest folder, you delete all the settings that go along with it (think about it, the only folder that you should have permission to write to is your home folder, hence all your configurations are stored in there.)
To show you proof of this, type in **ls -a** in the terminal, and you'll see all the **.dot** files and folders that are hidden away from you.
Hence, creating a backup in a secure part of the filesystem where you can't write to works like taking candy from a baby (Family Guy style) :lolflag:
You delete the session, and restore the secure, backed-up, optimal session.
You were nearly there, you just need to think outside the **/home** box!

Regards
Iain

---

