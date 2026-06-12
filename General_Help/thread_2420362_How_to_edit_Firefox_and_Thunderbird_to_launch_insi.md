---
title: "How to edit Firefox and Thunderbird to launch inside a firejail sandbox ?"
date: 2019-06-04
forum: General Help
---

### Post by linuxyogi on 2019-06-04
How to edit Firefox and Thunderbird to launch inside a firejail sandbox ?

I am using Lubuntu 18.04.

---

### Post by Rubi1200 on 2019-06-04
What do you mean by edit?

Don't know about Thunderbird but there is a default profile for Firefox already.

```
firejail firefox
```

This launches a sandboxed default profile.

There is also a GUI frontend which can be added from the repositories and with that you can create custom profiles.

```
sudo apt install firetools
```

[https://packages.ubuntu.com/bionic/firetools](https://packages.ubuntu.com/bionic/firetools)

---

### Post by linuxyogi on 2019-06-04
> **Rubi1200 said:**
> What do you mean by edit?

Don't know about Thunderbird but there is a default profile for Firefox already.

```
firejail firefox
```

This launches a sandboxed default profile.


I want to edit the Firefox launcher which is included in the start menu.

When I click on Firefox on the start menu >Internet>Firefox I want to

launch it inside a firejail sandbox just like when I do #firejail firefox.

---

### Post by Rubi1200 on 2019-06-04
Now I understand.

Well, I noticed you asked pretty much the same thing on Ask Ubuntu about a year ago; did those solutions not work?

To be honest, surely the easiest way is just to create a custom launcher for this?

---

### Post by linuxyogi on 2019-06-05
> **Rubi1200 said:**
> Now I understand.

Well, I noticed you asked pretty much the same thing on Ask Ubuntu about a year ago; did those solutions not work?

To be honest, surely the easiest way is just to create a custom launcher for this?

When I asked on askubuntu I was using Gnome. So those solutions don't apply now.

I need some help on how to create a custom launcher.

---

### Post by Rubi1200 on 2019-06-05
I don't use Lubuntu and am not familiar with the setup for creating launchers etc.

However, the firejail documentation page should have enough information for you to get started:
[https://firejail.wordpress.com/documentation-2/basic-usage/#integration](https://firejail.wordpress.com/documentation-2/basic-usage/#integration)

---

### Post by ajgreeny on 2019-06-05
A launcher for firefox is just a **firefox.desktop** file, simple text, which you will find in /usr/share/applications.

Open that file as root preferably using ```
sudo nano -B /usr/share/applications/firefox.desktop
``` search for the line ***Exec=firefox %u*** and add firejail to the command ie ***Exec=firejail firefox %u*** as shown in the thread at [https://ubuntuforums.org/showthread.php?t=2362788](https://ubuntuforums.org/showthread.php?t=2362788)

There are many possible options to use when firejailing firefox but I do not use it so have no further experience to pass on, but that thread goes into a lot of detail so you may find it helpful as will **man firejail** in terminal.

---

### Post by linuxyogi on 2019-06-05
It worked. Thanks a lot.

---

### Post by Rubi1200 on 2019-06-05
You can check to make sure it is working as expected by running this command:

```
firejail --list
```

The documentation page had a slightly different approach but whatever works right :-)

---

### Post by linuxyogi on 2019-06-05
> **Rubi1200 said:**
> You can check to make sure it is working as expected by running this command:

```
firejail --list
```

The documentation page had a slightly different approach but whatever works right :-)


```
$ firejail --list
2162:lubuntu::firejail firefox 
2479:lubuntu::firejail thunderbird 

```

Its working.

---

