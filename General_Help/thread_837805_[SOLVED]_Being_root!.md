---
title: "[SOLVED] Being root!"
date: 2008-06-22
forum: General Help
---

### Post by Milardo on 2008-06-22
Hi, when i try to update clam virus scanner through the program it says you must be root to do this. How do I update the virus without logging in as root?
Same for trying to update my punkbuster setup how can I enable root privileges for myself so I don't have to use terminal or log in as root?

---

### Post by iaculallad on 2008-06-22
Open your terminal and issue the commands below:

```
sudo apt-get install freshclam
sudo freshclam 
```

---

### Post by macaholic on 2008-06-22
Another note, for any graphical application, to run with root simply enter gksu before the program's command, i.e. gksu gedit.

---

### Post by iaculallad on 2008-06-22
Yap, use gksu to launch graphical applications that requires authentication. But in our case, **sudo**, can do that job since freshclam (is a virus database update tool for ClamAV) is only a terminal command that uses the freshclam.conf to update your CLAM definition.

---

### Post by Milardo on 2008-06-22
I'm trying to update pbsetup.run but it won't work with gksu nothing comes up.

---

### Post by macaholic on 2008-06-22
> **Milardo said:**
> I'm trying to update pbsetup.run but it won't work with gksu nothing comes up.
What exactly are you trying to do? If you are trying to run the file just open a terminal and type in the path to the file, and as long as it has execution privileges, it should run.

---

### Post by iaculallad on 2008-06-22
> **Milardo said:**
> I'm trying to update pbsetup.run but it won't work with gksu nothing comes up.

If what you're saying is pbsetup.run from PunkBusters website then (Not related to you're CLAM anyway):

```
sudo apt-get install upx-ucl
upx -d pbsetup.run
```

---

### Post by Milardo on 2008-06-22
Still can't get punkbuster screen to show up.

---

### Post by Milardo on 2008-06-22
also how can i give myself the same privileges as root so when I login I get the same privileges as root?

---

### Post by iaculallad on 2008-06-22
> **Milardo said:**
> Still can't get punkbuster screen to show up.


After this commands (as i've posted above):

> sudo apt-get install upx-ucl
upx -d pbsetup.run


Next thing for you is to make it executable then run the application:

```
sudo chmod +x pbsetup.run
sudo ./pbsetup.run
```

---

### Post by cariboo on 2008-06-22
With Ubuntu you can't, sudo is your friend. Rmember Linux is not Windows. You don't run as an adminstrator all the time.

Jim

---

### Post by iaculallad on 2008-06-22
> **Milardo said:**
> also how can i give myself the same privileges as root so when I login I get the same privileges as root?

By default, you are not given the ROOT privileges. Yet, you can give yourself a "bit" of root privileges by issuing sudo, gksudo, and gksu before a command in your terminal.

To become a FULL root, issue the command on your terminal:

```
sudo -i
```

---

### Post by jaithehulk on 2008-06-22
> **iaculallad said:**
> By default, you are not given the ROOT privileges. Yet, you can give yourself a "bit" of root privileges by issuing sudo, gksudo, and gksu before a command in your terminal.

To become a FULL root, issue the command on your terminal:

```
sudo -i
```
yes the command sudo -i always works for me with all the applications!

---

### Post by Milardo on 2008-06-22
Thanks for your replies and for helping to get pbsetup running! Still, is there a way to give myself root privileges without typing in terminal, etc. meaning when I login I immediately get root privileges.didn't work for updating clam through gui though.

---

### Post by iaculallad on 2008-06-22
> **jaithehulk said:**
> yes the command sudo -i always works for me with all the applications!

YES, that will work 101% all the time since you are on the ROOT mode. Just be careful on the commands you issue/execute when you're on your root terminal (i.e: root@gutsy-gibbon:~#).

---

### Post by iaculallad on 2008-06-22
> **Milardo said:**
> Thanks for your replies and for helping to get pbsetup running! Still, is there a way to give myself root privileges without typing in terminal, etc. meaning when I login I immediately get root privileges.didn't work for updating clam through gui though.

There's always a way for everything, but there's also reason why Ubuntu (Linux in general) gave you a limited command access to your System, security is the foremost reason. If you still insist on getting root access, try reading Ubuntu's [RootSudo]("https://help.ubuntu.com/community/RootSudo") page.

---

### Post by Milardo on 2008-06-22
Thanks for the help everybody.

---

### Post by macaholic on 2008-06-22
EDIT: Useless post.

---

