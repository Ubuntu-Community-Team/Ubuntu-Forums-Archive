---
title: "Can't execute GUI apps as sudo on Terminal (Ubuntu 18.04.2)"
date: 2019-02-23
forum: General Help
---

### Post by roberto-bassman on 2019-02-23
I installed the latest stable version of Ubuntu (18.04.2).

Until yesterday I was able to run vscode and other gui applications as root, from the terminal, using sudo <application>.
But today I am unable to do so. I noticed that it happens not only with VSCode, but also with other applications such as Sublime Text, Gedit and others... In general, running these applications as my regular user, goes ok, but using sudo, it does not.

I realize that, when I try use sudo <application>, two things can happen, depending on which applicatian I am trying to run as root:

1. the terminal doesn't show anything, the application simply don't execute without error messages;

2. (specific when I try to run gedit), the terminal show an error messages like 'No protocol specified'
'Cannot open display:0'

Anyone experiencing these error?

---

### Post by Frogs Hair on 2019-02-23
Hello and Welcome

Running gui applications with sudo can cause permission errors and is not recommended. Use the following if needed.

 Example: ```
sudo -H gedit 
```

---

### Post by roberto-bassman on 2019-02-25
Hello Frogs Hair!
Thanks!

The command 
```
sudo -H <application>
```

retuns the same error.

I discovered that the problem has something to do with Wayland.
On the login screen, I clicked on the gear icon and choose Ubuntu Wayland instead of Ubuntu, was when the problem starts to occurs. 
Just switched from Ubuntu Wayland back to Ubuntu and was able to run application GUI as root again.

Hope this helps someone.

How can I mark this post as resolved?

---

