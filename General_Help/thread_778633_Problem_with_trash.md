---
title: "Problem with trash"
date: 2008-05-02
forum: General Help
---

### Post by nulador on 2008-05-02
I have deleted some files i downloaded and when i try to empty trash it tells me:"Error while deleting." "Error removing file: Permission denied" what can i do to fix this ?

---

### Post by Nepherte on 2008-05-02
Try it with sudo privileges:
```
cd ~/Trash
sudo rm <filetoremove>

```
When it is a map you want to remove, add the -r option

---

### Post by nulador on 2008-05-02
It doesn`t work it tells me that that folder does not exist..... :(

---

### Post by sisco311 on 2008-05-02
The Trash is a hidden folder in your home directory. Open nautilus as super user:
```
gksu nautilus
```and press Ctrl+H. Navigate to the **.**Trash(it's a period before Trash) folder and delete the files.

To open nautilus in the Trash folder:
```
gksu nautilus ~/.Trash
```In Hardy the Trash is in ~/.local/share/Trash/files/
```
gksu nautilus ~/.local/share/Trash/files/
```You can delete the files from the terminal:
```
sudo rm -fr ~/.Trash/*
```
in Hardy:
```
sudo rm -fr ~/.local/share/Trash/files/*
```

---

### Post by TeoBigusGeekus on 2008-05-02
The trash folder in Hardy has moved...
```
sudo rm /home/yourusername/.local/share/Trash/files/*
```

[COLOR="Red"]BE CAREFUL WITH THE RM COMMAND...[/COLOR]

---

### Post by nulador on 2008-05-02
Thanks it worked out fine

---

### Post by shadowtroopers on 2008-05-02
Is this common, whenever i delete files to trash then do empty trash..all the deleted files will be dump to my usb drive?. How am i going to disable this feature?

---

### Post by esunday on 2008-05-03
Okay, I get the solution, but I'd like to just right click on the trash icon and empty it, I tend to churn thru a lot of files regularly.

How do I set my permissions?  How do I login as root?

Thanks.

---

