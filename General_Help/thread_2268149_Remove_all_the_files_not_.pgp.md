---
title: "Remove all the files not .pgp"
date: 2015-03-06
forum: General Help
---

### Post by enricobe on 2015-03-06
Hello,
I have encrypted my documents folder with pgp so I can backup it on Dropbox.

I have a Documents folder with ~1500 files, and after the encryption it has ~3000 files. Half are the original files and the others are the encrypted files. How can I remove all the non-encrypted files? I didn't find an option during encryption with the seahorse tool. Maybe someone knows some magic command

If it's not possibile to remove all the non-encrypted files, I can delete the folder and re-encrypt it if you tell me how to automatically remove the files after the encryption

---

### Post by nerdtron on 2015-03-06
You can list all files that don't have the .pgp extension using the following command.
```
find /folder/path -not -iname *.pgp
```

Now if you are sure that these are the files that you want to delete, you can append the delete command on that.
```
find /folder/path -not -iname *.pgp -exec rm -vf {} \;
```

careful with that. once you delete files there's no undelete

---

### Post by Dennis N on 2015-03-06
> **enricobe said:**
> I have a Documents folder with ~1500 files, and after the encryption it has ~3000 files. Half are the original files and the others are the encrypted files. How can I remove all the non-encrypted files? I didn't find an option during encryption with the seahorse tool. Maybe someone knows some magic command

Can be done in the file manager. Using Xubuntu's Thunar as an example:

Open the directory where the files are in the file manager.
Edit > Select by pattern > (enter *.pgp in the dialog box) > Select Button
Edit > Inverse Selection
Edit > Delete

Other file managers should offer similar options.

---

### Post by enricobe on 2015-03-06
> **Dennis N said:**
> Can be done in the file manager. Using Xubuntu's Thunar as an example:

Open the directory where the files are in the file manager.
Edit > Select by pattern > (enter *.pgp in the dialog box) > Select Button
Edit > Inverse Selection
Edit > Delete

Other file managers should offer similar options.

Thank you for you tip. I could not find how to do it from nautilus (ubuntu) and i did it from the terminal :)

> **nerdtron said:**
> You can list all files that don't have the .pgp extension using the following command.
```
find /folder/path -not -iname *.pgp
```

Now if you are sure that these are the files that you want to delete, you can append the delete command on that.
```
find /folder/path -not -iname *.pgp -exec rm -vf {} \;
```

careful with that. once you delete files there's no undelete

Thank you, too. It worked like a charm. :D

---

### Post by Dennis N on 2015-03-06
> I could not find how to do it from nautilus (ubuntu) and i did it from the terminal.
Well, maybe Nautilus has lost some functionality since 12.04. My Nautilus (v. 3.4.2) on Ubuntu 12.04 has those same actions as Thunar in post #3 in the Edit menu.

---

### Post by enricobe on 2015-03-07
> **Dennis N said:**
> Well, maybe Nautilus has lost some functionality since 12.04. My Nautilus (v. 3.4.2) on Ubuntu 12.04 has those same actions as Thunar in post #3 in the Edit menu.
You were right. Now i've followed step-by-step your message and i've found the way to do it. Lack of attention yesterday #-o

---

