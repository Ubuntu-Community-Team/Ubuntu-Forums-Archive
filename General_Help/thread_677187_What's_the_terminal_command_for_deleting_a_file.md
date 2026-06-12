---
title: "What's the terminal command for deleting a file?"
date: 2008-01-24
forum: General Help
---

### Post by ele_mugv on 2008-01-24
I hav copies of a file (menu.lst) which i would lyk to delete..wat's the analogous expression for 'del filename'

---

### Post by taurus on 2008-01-24
Do you mean you want to delete /boot/grub/menu.lst?  If that's the case, you shouldn't delete it because then you won't be able to boot.  Otherwise, the command is rm but you probably need to run it with root privilege if you want to delete something outside of your $HOME directory.

```
sudo rm filename
```

---

### Post by erginemr on 2008-01-24
Also use rm with caution, as the deleted files will be gone forever. There is an argument "-i", that you can use alongside rm, which will inform you about the files to be deleted. So, 

So, for your home folder, using
```
rm -i file_name
```
and for the other folders in your system, using
```
sudo rm -i file_name
```
would be much safer.

---

### Post by Zwack on 2008-01-24
> **erginemr said:**
> Also use rm with caution, as the deleted files will be gone forever. There is an argument "-i", that you can use alongside rm, which will inform you about the files to be deleted. So, 

So, for your home folder, using
```
rm -i file_name
```
and for the other folders in your system, using
```
sudo rm -i file_name
```
would be much safer.

Or if you're paranoid you could try moving the file to a different name and seeing how badly broken stuff becomes... of course if it breaks on boot you need a recovery disk...

The command for that would be 
```
mv <source> <destination>
```

I'm not going to give you a sudo invocation as if you don't know enough to manipulate files you certainly shouldn't be manipulating ones that you don't own.  :)

If you don't have a good reason then don't delete it.

Z.

---

### Post by zach12 on 2008-01-24
> 
sudo rm filename
BUT BE CAREFUL

---

