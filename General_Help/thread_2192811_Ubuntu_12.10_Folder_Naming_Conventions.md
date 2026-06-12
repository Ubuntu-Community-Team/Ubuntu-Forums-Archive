---
title: "Ubuntu 12.10 Folder Naming Conventions"
date: 2013-12-09
forum: General Help
---

### Post by ocar23 on 2013-12-09
I am having problems working with Folders that use multi words in the name (Joomla Files or Malicious Code Checker or $RECYCLE.BIN). Ubuntu seems to treat each single word as a Folder and of course cannot find the Folder being asked for. I have tried with (.) or (_) or (-) seperators for the words in the name but this does not help.
I have searched the Forums and elsewhere but cannot see anything written about Naming Conventions for Files and Folders, except that the Names are Case Sensitive.
I have been moving a group of Folders from one folder to another and I am left with three that I cannot Move.
Any help with this would be appreciated.

---

### Post by steeldriver on 2013-12-09
You can 'escape' the spaces using backslashes, or use quotes to prevent word splitting

```

Malicious**\** Code**\** Checker

**"**Malicious Code Checker**"**

**'**Malicious Code Checker**'**

```

---

### Post by ocar23 on 2013-12-09
> **steeldriver said:**
> You can 'escape' the spaces using backslashes, or use quotes to prevent word splitting

```

Malicious**\** Code**\** Checker

**"**Malicious Code Checker**"**

**'**Malicious Code Checker**'**

```

Thank you steeldriver: I have just tried these methods and they do not work. Message returned; mv: Cannot Stat "Filename": No such File or Directory.
I am getting the same Message when I try to Move some Joomla Files, which appear to be grayed out: configuration.php, as an exaample.
I was able to move most of my Site Files to /var/www from /host, leaving three multi word Folders and eleven Files, that produce that Message. I cannot proceed any further.

---

### Post by steeldriver on 2013-12-09
Well based on the /host pathname I'm guessing you are trying to move files into a WUBI install from the Windows host system? It's possible the "spaces" are actually some kind of Windows-specific non-ASCII space characters - you might have better luck if you allow the shell to auto-complete the names e.g. type

```
mv Malic
```

and then press the TAB key

When you say files are "grayed out" what application are you referring to (nautilus file manager? terminal?)

---

### Post by ocar23 on 2013-12-09
> **steeldriver said:**
> Well based on the /host pathname I'm guessing you are trying to move files into a WUBI install from the Windows host system? It's possible the "spaces" are actually some kind of Windows-specific non-ASCII space characters - you might have better luck if you allow the shell to auto-complete the names e.g. type

```
mv Malic
```

and then press the TAB key

When you say files are "grayed out" what application are you referring to (nautilus file manager? terminal?)

They are Joomla Files and Folders and I believe it is Nautilus File Manager.
When I say "grayed out' that is how they appear on the screen.

I do not know why these Joomla Files and Folders are in the /host directory. Normally Joomla Files and Folders are in /www direcdtory.

---

