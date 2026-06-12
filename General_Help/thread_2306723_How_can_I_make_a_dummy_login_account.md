---
title: "How can I make a dummy login account?"
date: 2015-12-18
forum: General Help
---

### Post by Bedpan.ca on 2015-12-18
I feel like there must be a way to do this, but my Google-fu is failing me here.

My girlfriend moved in recently, and we share my computer. I'd like to have a girlfriend account on the Lightdm login screen when the computer turns on, which shows her name and profile picture and uses her own password, but it just logs into my account as if I had entered my password on my account.

Is there a way to have a dummy/clone/twin/somethingorother account/login with linux or kubuntu or kde or lightdm or anything else I can't think of that can do this some way?

---

### Post by SeijiSensei on 2015-12-18
It would be better if she had her own home directory, but if you must do this, here's how (requires using the terminal):

1) Create a user for your girlfriend either with the graphical utility or with the command:
```
sudo adduser mylovelygf
```
Accept all the defaults.  We'll fix things below.

2) Edit the file /etc/passwd with nano to make your home directory her default:
```
sudo nano /etc/passwd
```
Now find the line that begins with her username and change her default home directory to yours:
```
mylovelygf:x:1001:1001:Her Name:/home/yourusername:/bin/bash
```
Save the file with Ctrl-X, then Y for yes.

3) Edit the file /etc/group with nano:
```
sudo nano /etc/group
```
Find the line that begins with your username and add her to your group:
```
myuser:x:1000:mylovelygf
```

4) Grant the group full permissions to your home directory and all the files and directories it contains:
```
cd /
sudo chmod g+w -R username

```

As I said though, you're better off giving her her own home directory.  If you want to share files, you might consider creating a separate directory, say /shared, and granting either full permissions to it ("sudo chmod 777 /shared"), or creating a group for you both ("sudo addgroup together yourusername herusername") and making that the group that owns /shared with full permissions ("sudo chmod 775 /shared").  To make life easy, add a "symbolic link" in each home directory that points to the shared directory:
```

cd /home/yourusername
sudo ln -s /shared
cd /home/herusername
sudo ln -s /shared

```

---

### Post by Bedpan.ca on 2015-12-22
Thanks,

I created the user, edited /etc/passwd and /etc/group.
But from here, you lose me... You said my home directory not root directory, and I don't understand the chmod line...

---

### Post by Bucky Ball on 2015-12-22
Any possibilities with Settings> Users and Groups?

---

### Post by SeijiSensei on 2015-12-22
OK, let's see how far you've gone.  From the terminal, type the command "groups mylovelygf" to see all the groups she belongs to.  One of them should be yours.  Then run "grep mylovelygf /etc/passwd" and make sure her home directory points to yours.

> 
4) Grant the group full permissions to your home directory and all the files and directories it contains:
```
cd /
sudo chmod g+w -R username

```

Oops, no, that's not right.  My only excuse is that it was late.  There obviously isn't a /username directory but a /home/username one!  Try this:
```
cd /home
sudo chmod g+rw -R username

```
That will add group-write privileges to all your files and directories in /home/username using the "-R" recursive switch.  Your group probably has read privileges already to all those files, but this time I explicitly included them as well.

See if you can switch users to mylovelygf now.  After you login with her password, do you see your desktop?

Remember that this change means **she can view, alter and delete every file in your home directory**. You can still create other private directories visible only to your username using 700 permissions.  Her account will be blocked from these directories since only you the owner have access.

---

### Post by Bedpan.ca on 2015-12-23
> **Bucky Ball said:**
> Any possibilities with Settings> Users and Groups?

The closest I have to that is Settings>User Manager, and it doesn't have any Group settings.

> **SeijiSensei said:**
> See if you can switch users to mylovelygf now.  After you login with her password, do you see your desktop?

When I log in with her password, it hangs at the default LightDM background image, with a moveable cursor.

---

