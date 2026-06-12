---
title: "Problems w/ GAIM and Pidgin"
date: 2007-07-03
forum: General Help
---

### Post by chimerical_brio on 2007-07-03
I'm having two problems, involving GAIM and Pidgin. The first one is that I installed Pidgin by compiling the source, but now I can't find it under any application lists. I can invoke it by typing "gksudo pidgin" but I'd really like an icon. How can I find it?

The other problem involves GAIM and Pidgin. I'm going to be using an insecure network for the next four weeks, so I'm routing my internet traffic through a server on a completely different network. I set Firefox to use a SOCKS5 connection, and I want to do the same with GAIM/Pidgin, but whereas everyone else with either client has a section for "Proxy Settings" under the Network tab in Preferences, it's just not there for me. How can I set up a proxy server on GAIM? The one difference I noticed is that I'm running Pidgin 2.0.2 while the person who I know has it is running 2.0.1. This is a MAJOR problem for me. Any ideas? Sorry for asking here, I just couldn't find a GAIM/Pidgin forum.

---

### Post by chimerical_brio on 2007-07-03
Help! I recognize this forum isn't the best place for this, so can you recommend to me a better forum if you can't answer this? Thanks.

---

### Post by Megatog615 on 2007-07-03
You can add the menu entry with System -> Preferences -> Main Menu.

Proxies for Pidgin are now set in the individual account settings. I believe this is because the global proxy setting for Pidgin is currently broken in the source, so they hide it from usage.

---

### Post by akshaysrinivasan on 2007-07-03
I recall a menu with the Pidgin 2.02 . Search if there is something called Pidgin in /usr/local/share/applications.To be honest I think you should've compiled Pidgin with --prefix=/usr/.

---

### Post by chimerical_brio on 2007-07-03
Alright, well, I got it working by,for the first one, System->Preferences->Main Menu, and for the second, going to Accounts->Add/Edit->Select my account->Modify->Advanced, on the drop-down menu selecting SOCKS5, and entering my info. Thanks!

---

### Post by hikaricore on 2007-07-03
> **chimerical_brio said:**
> I can invoke it by typing "gksudo pidgin" but I'd really like an icon.

Might I ask why on earth you are launching pidgin with sudo?!

---

### Post by chimerical_brio on 2007-07-03
Because I'm silly and that's the only way I know for launching GUI programs from the commandline that lets me close the terminal. :)

---

### Post by tillo on 2007-07-03
> **chimerical_brio said:**
> Because I'm silly and that's the only way I know for launching GUI programs from the commandline that lets me close the terminal. :)

Oh my god :D "nohup pidgin".

---

### Post by chimerical_brio on 2007-07-03
Ok, but what I like about gksudo is how it opens the program and then goes back to a bash prompt. How can I get that without running the program as sudo?

---

### Post by tillo on 2007-07-03
> **chimerical_brio said:**
> Ok, but what I like about gksudo is how it opens the program and then goes back to a bash prompt. How can I get that without running the program as sudo?

"nohup pidgin &" :D

(
man bash
man nohup
)

---

### Post by hikaricore on 2007-07-03
....

```
pidgin &
```

The & symbol will do just this, run the program and return you to the terminal prompt.

Please do not run trivial things such as Pidgin using sudo commands, you're only asking for trouble.
In the end it's up to you, just trying to make you aware that this could cause you security risks
as well as the inevitable file permission problems you will face from this.

---

