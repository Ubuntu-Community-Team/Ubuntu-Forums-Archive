---
title: "Desktop bloked"
date: 2008-01-24
forum: General Help
---

### Post by the_sorrow on 2008-01-24
Hey guys watup?

I have a problem with my dektop, when I try to erase, place or add something to it, it says I have no permission to do it, I went to my home folder and cheked that only 'root' was authorized to do it.

Any help will be highly apreciated.

Thanks

PS, one more thing anybody knows how can I get Netbeans in UBUNTU, I'm running Gutsy

---

### Post by taurus on 2008-01-24
What directory are you trying to write to?  Remember, you can only write or delete things in your own $HOME and if you need to write outside of your $HOME, you need to use sudo/gksudo.  

Applications -> Accessories -> Terminal
```
gksudo nautilus
```

---

### Post by the_sorrow on 2008-01-24
to my desktop, and when I try to move an Icon it gives that error.

---

### Post by taurus on 2008-01-24
What's the output of this command from a terminal?

```
ls -la ~/Desktop
```
Otherwise, you can remove it with

```
sudo rm /home/*username*/Desktop/filename
```
Replace the *username* with your actual login name.

---

