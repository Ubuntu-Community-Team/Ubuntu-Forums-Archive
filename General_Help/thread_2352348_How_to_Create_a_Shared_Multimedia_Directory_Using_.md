---
title: "How to Create a Shared Multimedia Directory Using the Command Line"
date: 2017-02-11
forum: General Help
---

### Post by John_Patrick_Mason on 2017-02-11
I'm trying the create a shared music directory using the command line as illustrated in William E. Shotts' book *The Linux Command Line* from linuxcommand.org. Since Ubuntu 16.04's GUI lacks the ability to create groups, I had to first install gnome-system-tools using the command:

```
sudo apt-get install gnome-system-tools
```

Once I installed the appropriate package, I created a unique group called music, to which I added myself and another user, which we will call bob.

I then created a brand new directory using:

```
sudo mkdir /usr/local/share/Music
```

with permissions:

```
drwxr-xr-x 2 root root 4096 Feb 11 18:08 /usr/local/share/Music
```

which I changed to:

```
drwxrwxr-x 2 root music 4096 Feb 11 18:08 /usr/local/share/Music
```

using:

```
sudo chown :music /usr/local/share/Music
sudo chmod 775 /usr/local/share/Music
```

The problem is when I try to create an empty file in the newly-created directory Music I get a permission denied message.

```
> /usr/local/share/Music/test_file
bash: /usr/local/share/Music/test_file: Permission denied
```

Could anybody help me? Your help would be greatly appreciated.

---

### Post by &amp;KyT$0P# on 2017-02-11
Did you log out and back in after adding yourself to the [FONT=Courier New]music[/FONT] group?

---

### Post by sisco311 on 2017-02-11
After adding your user to a new group you have to log out and log back in, in order to the changes take effect.

EDIT: halogen2 beat me to it. :)

---

### Post by John_Patrick_Mason on 2017-02-11
>  			 				[INDENT] 					After adding your user to a new group you have to log out and log back in order to  the changes to take effect.. 				[/INDENT] 			
  			   		


Oh, I see, I'll try that now then. Petty the book doesn't mention anything about logging out.

---

### Post by John_Patrick_Mason on 2017-02-11
Thanks guys, that solved the problem. I haven't touched on the Ch.10 processes chapter. Perhaps logging out and logging back in will be covered in that chapter.

---

### Post by sisco311 on 2017-02-11
Cool! Please don't forget to mark this thread as solved. Check out the link(s) in my signature. ;)

---

