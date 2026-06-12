---
title: "Make user as only root - No terminal"
date: 2008-03-17
forum: General Help
---

### Post by Firehalk on 2008-03-17
I know there are plenty of threads talking about root user, to don't use the root account, explaining some "how-to" run softwares as root and etc. I read them, and also read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo).

Well, I used Windows always till now, and I really don't want need terminal to do stuff that I can do with 2 clicks in 2 seconds. I know terminal is pretty good to some stuff, but let me example:

I want to delete bookmarks.html from my Firefox profile and put the one I've from some backup.

I know through terminal i could do it, but I want to not only on that example, but on many cases, have full access of my system. It's just me using it, no one else (live alone also), so it's pointless don't have full access to everything here.

But, I don't want to use root account for that, but another account that has full access to root owner stuff. Is that possible? I tried to set admin account, put my account on group "root"... none of that worked. Just with root account I have been able to access some files like that one from my example. Please, don't say terminal... I really won't use it for that.

Any reply is welcome :)

Thanks

---

### Post by lswest on 2008-03-17
you can open a file browser with root priviledges with ```
gksudo nautilus
``` is that what you were looking for? (enter than command either in the "run application" dialog (<alt>+<F2>) or the terminal.

---

### Post by jken146 on 2008-03-17
> **Firehalk said:**
> I want to delete bookmarks.html from my Firefox profile and put the one I've from some backup.

You don't need to be root to do that -- your firefox bookmarks are stored within your home directory, /home/yourUserName
You'll find it inside .mozilla/firefox -- press Ctrl+H to too hidden files (they start with a dot).

If you need temporary root access to any other part of the file system, you can press Alt+F2 and type in **gksu nautilus** to get the file browser as root.  You could make a launcher on the panel or on the desktop to run that command if you like, so it's only a click.

---

### Post by Oldsoldier2003 on 2008-03-17
> **Firehalk said:**
> 

But, I don't want to use root account for that, but another account that has full access to root owner stuff. Is that possible? I tried to set admin account, [COLOR="Red"]put my account on group "root"[/COLOR]... none of that worked. Just with root account I have been able to access some files like that one from my example. Please, don't say terminal... I really won't use it for that.

Any reply is welcome :)

Thanks

You really should remove your account from the group root... there's no real benefit or reason for it and it creates a hole in the permissions model that could bite you in the butt later on.

---

### Post by Firehalk on 2008-03-17
Thanks for replies!

Well, thats my problem. I've deleted my other accounts in order to try to fix this root stuff. I will recreate after these comments, but still i think wont work:

1- There wont be preferences of FF inside HOME, because my user account will be created now and FF is already installed.

2- When I installed FF through some account I had here, it still showed the FF folder as being propertie of ROOT user (?!). Shouldn't be my user as the owner?

Thanks again. I will test the infos posted here now.

---

### Post by Firehalk on 2008-03-17
I was wrong, pressing CTRL + H as jken146 said worked like a charm!

Perfect. Also I created some desktop icon to open file browser as root.

Couldn't be better :)

Thanks a lot for the help people.

---

