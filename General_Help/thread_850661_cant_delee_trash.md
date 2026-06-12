---
title: "cant delee trash"
date: 2008-07-05
forum: General Help
---

### Post by carl_pr on 2008-07-05
i have 2 questions the first and most important is i have this folder on trash that i cant delete. Here is a screenshot of the message i get.

[IMG]http://img76.imageshack.us/img76/1645/screenshotvj3.png[/IMG]


also how do i uninstall adobe flash 10 (beta), i want to go back to ver 9.

---

### Post by Captain panda on 2008-07-05
If permission is denied, you probably need to use sudo to delete it. I'm not sure if you can do this from the trash bin. You might need to use the terminal. I am just guessing here so apologies in advance if I am wrong.

---

### Post by drs305 on 2008-07-05
You can delete any trash by opening nautilus with administrator privileges.
```
gksu nautilus
```

You can then navigate to the trash folders and delete to your heart's content.

In hardy, user trash is normally in /home/*username*/.share/local/Trash/files
For root trash, look in /root/.share/local/Trash/files

If you find you delete trash just to see it disappear and reappear again in the same place (aka sending trash to trash), you can use the "rm" command to permanently delete it. For root trash, you would have to include the 'sudo' command, which can be very dangerous if you get the address wrong.

---

### Post by carl_pr on 2008-07-05
ok i used google and this command helped me

```
sudo rm -rf ~/.local/share/Trash/files/*
```

thanks everyone

---

### Post by cariboo on 2008-07-05
You may have to go to /root/.local/share/Trash/files also if aany of the files were deleted using sudo.

Jim

---

