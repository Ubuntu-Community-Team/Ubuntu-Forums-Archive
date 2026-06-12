---
title: "problem with writing to UDF format DVD RW"
date: 2015-05-18
forum: General Help
---

### Post by sebastiaan5 on 2015-05-18
I have a DVD RW disk that I made UDF format on windows, and I want to use this DVD as usb driver. So to write data on it without burning.
this works normal on windows just copy files to DVD and delete, But on Ubuntu I can only read files and if I want to make new files or paste files into the DVD folder it says something like "No permission only readable".

However I can write data to the DVD with terminal, if I am root I can move files to the DVD folder and make/delete folders on it etc.

```
sudo mv file /media/mycomputername/"UDF Volume"
```

My question is, is there a way to edit this permission, (not with properties of the disk won't work)? Or is there another format of DVD I can use? Or is there a solution to my problem?

---

### Post by sebastiaan5 on 2015-05-19
bump

---

### Post by sebastiaan5 on 2015-05-20
.

---

### Post by sudodus on 2015-05-20
> **sebastiaan5 said:**
> I have a DVD RW disk that I made UDF format on windows, and I want to use this DVD as usb driver. So to write data on it without burning.
this works normal on windows just copy files to DVD and delete, But on Ubuntu I can only read files and if I want to make new files or paste files into the DVD folder it says something like "No permission only readable".

However I can write data to the DVD with terminal, if I am root I can move files to the DVD folder and make/delete folders on it etc.

```
sudo mv file /media/mycomputername/"UDF Volume"
```

My question is, is there a way to edit this permission, (not with properties of the disk won't work)? Or is there another format of DVD I can use? Or is there a solution to my problem?

I think that the directory has read but not write permissions. Please post the output of this command

```
ls -l /media/mycomputername
```

If that is the case, you can change ownership and/or permissions for group and others (than the owner).

```
sudo chown -R "$USER":root /media/mycomputername
```

which limits access to that user (and root) or

```
sudo chmod -R ugo+rwx /media/mycomputername
```

which makes it readable and writable for 'everybody'. There are other options too depending on what you prefer and depending on the output

```
ls -l /media/mycomputername
```

and what kind of access you want.

---

### Post by sebastiaan5 on 2015-05-20
thank you very much!

---

### Post by sudodus on 2015-05-20
You are welcome :-)

---

