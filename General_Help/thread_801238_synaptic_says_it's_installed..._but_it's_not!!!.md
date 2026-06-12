---
title: "synaptic says it's installed... but it's not!!!"
date: 2008-05-20
forum: General Help
---

### Post by foxofinfinety on 2008-05-20
anyone knows how it is possible that synaptic has some programs in the "installed" list even wile I never installed them and there not in my applications list? also the programs to configure compiz are in this list but there not in my system menu:confused:
and it's a big problem because I have a site about computers and I use my own PC for screen shots but I can't make screen shot of programs I don't have...

---

### Post by pointone on 2008-05-20
Not every application creates a launcher in the applications menu by default. Please provide some examples of the packages you're installing.

Also, for future reference:

```
dpkg -L <packagename>
```

...will list all files installed by a package, allowing you to easily find the binar(y/ies) you need.

---

### Post by Exsecrabilus on 2008-05-20
Not every package is an application.

For example, Compiz is not an application, it's many packages combined together to give you desktop effects.

---

### Post by foxofinfinety on 2008-05-21
> **Exsecrabilus said:**
> Not every package is an application.

For example, Compiz is not an application, it's many packages combined together to give you desktop effects.

true but in Kubntun I did got a application in the menu wen I installed the configuration program and now I don't

---

### Post by Exsecrabilus on 2008-05-21
For troubleshooting, try pressing Alt+F2 and type in the package name.

For example:

Package name: simple-ccsm
Launch name: simple-ccsm

Instead of typing it all in, type letter by letter and look at the suggestions, and if it's related to the name of the package you installed, just press **Enter**.

---

### Post by foxofinfinety on 2008-05-21
> **Exsecrabilus said:**
> For troubleshooting, try pressing Alt+F2 and type in the package name.

For example:

Package name: simple-ccsm
Launch name: simple-ccsm

Instead of typing it all in, type letter by letter and look at the suggestions, and if it's related to the name of the package you installed, just press **Enter**.

it only told me you cant find it

---

### Post by Exsecrabilus on 2008-05-21
Uhh, what's the package?
That might help us a lot.

---

### Post by foxofinfinety on 2008-05-21
> **Exsecrabilus said:**
> Uhh, what's the package?
That might help us a lot.

it actually happens with about 20 packages

---

### Post by kellemes on 2008-05-21
> **foxofinfinety said:**
> it actually happens with about 20 packages

You're not giving examples..
Remember most packages don't need menu entries.

---

### Post by Exsecrabilus on 2008-05-21
> **foxofinfinety said:**
> it actually happens with about 20 packages
If you want help and possibly a solution to your problem, it'll probably will be worth posting the packages here. :D

---

### Post by foxofinfinety on 2008-05-22
> **kellemes said:**
> You're not giving examples..
Remember most packages don't need menu entries.ok adobe flash doesn't but I thought it sould *work*:confused:
and els I don't know the names of the pacages there on a PC I'm not on now I can look lator but it's dualboot whit windows and the virus scanner in windows takes it time (it's running for about 4 hour #-o)
I only now it's a package that configures compiz and I know that it sould have a menu entry (in system->voorkeuren (system->preferences)) it's not the advansed window manneger though

(sorry if my spelling is crap but I'm not allowed to install anything on this PC and IE doesn't have a spell check)

---

### Post by Exsecrabilus on 2008-05-22
For the flash player, try doing this:

```
sudo apt-get install totem-mozilla
```

And restart Firefox if it is open.

You need a media player to play videos, not just the flash player.

Is the package configuring Compiz called *fusion-icon* or *simple-ccsm*?

---

### Post by foxofinfinety on 2008-05-25
> **Exsecrabilus said:**
> For the flash player, try doing this:

```
sudo apt-get install totem-mozilla
```

And restart Firefox if it is open.

You need a media player to play videos, not just the flash player.

Is the package configuring Compiz called *fusion-icon* or *simple-ccsm*?

no compizconfig-settings-manager
and flashplugin-nonfree won't work either

---

