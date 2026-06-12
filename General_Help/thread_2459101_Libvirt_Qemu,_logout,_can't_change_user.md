---
title: "Libvirt Qemu, logout, can't change user"
date: 2021-03-10
forum: General Help
---

### Post by KL_72_TR on 2021-03-10
I'm using Ubuntu Mate 18.04
Without thinking I clicked on a user: Libvirt Qemu.
I tried every password but I can't log in: Invalid password, please try again. 
But from the virtual command line (Ctrl+Alt+F1) I can access my home directory and all my files without problem.
How can I switch back?

Thank you

---

### Post by deadflowr on 2021-03-10
You mean in the login screen?
Can you use the up/down arrows to navigate the user list?
Might try hitting ESC if it's somehow stuck, that should get it back to normal setting.

Also, about the libvirt-qemu user and lightdm login issue see:
[https://askubuntu.com/questions/897026/why-do-i-have-a-libvirt-qemu-account-in-lock-switch-account-options-in-ubuntu/940069#940069]("https://askubuntu.com/questions/897026/why-do-i-have-a-libvirt-qemu-account-in-lock-switch-account-options-in-ubuntu/940069#940069")

---

### Post by KL_72_TR on 2021-03-10
> **deadflowr said:**
> You mean in the login screen?
Can you use the up/down arrows to navigate the user list?
Might try hitting ESC if it's somehow stuck, that should get it back to normal setting.

Also, about the libvirt-qemu user and lightdm login issue see:
[https://askubuntu.com/questions/897026/why-do-i-have-a-libvirt-qemu-account-in-lock-switch-account-options-in-ubuntu/940069#940069](https://askubuntu.com/questions/897026/why-do-i-have-a-libvirt-qemu-account-in-lock-switch-account-options-in-ubuntu/940069#940069)

First of all, Thank you for your time.
Second, Thank you for the ESC suggestion.
That did the trick.
Sorry for my brief description. 
I was stuck for a long time in the Login screen.
The up/down arrows were not working at all.
But after your suggestion: ESC > up/down, everything came back to normal.

---

