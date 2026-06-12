---
title: "How do you remove Azureus?"
date: 2008-02-11
forum: General Help
---

### Post by jingo811 on 2008-02-11
How do you remove Azureus?  I have already tried to "completely remove it" in Synaptic also I tried re-installing it and then "completely remove it".
Then when I click on a torrent link the so called removed Azureus comes back from the dead even when the program has been removed.  I trie the same procedure again after I removed the .Invisible_Azures_config_folder still the torrent links brings Azureus back from the dead :confused:

I tried "sudo apt-get --purge remove azureus" nothing I tried "sudo apt-get remove azureus" still nothing.  How do you remove Azureus?

Also if you accidentally removed the "Torrent action" from 
```
Firefox>Edit>Pref> Content>File type>Manage
```
How do you create a new torrent action so I can unswitch Azureus from Firefox?

---

### Post by zvacet on 2008-02-11
```
sudo dpkg --remove --force-remove-reinstreq azureus
```

---

### Post by jingo811 on 2008-02-12
```
bill@gates:~$ **sudo dpkg --remove --force-remove-reinstreq azureus**
dpkg - warning: ignoring request to remove azureus which isn't installed.
bill@gates:~$ 
```

It's still unremovable.  It's stuck like a Microsoft virus.  Doesn't matter it works I'll remove it next time I upgrade to Gutsy instead. Tnx for the help anyways.

---

### Post by zvacet on 2008-02-12
You can try with 

```
locate azureus
```

or go on top of filesystem with command **cd /**

```
sudo find / -name *azureus*
```

That way you should be able to know where azureus is and remove it manualy.Be very careful when you execute this command,because if you type something wrong who knows what can happened.Anyway for example let say that azureus is in /usr/bin

```
cd /usr/bin
sudo rm -r azureus
```

**Before you do any of this just chek in your home dir>view >hidden files if you still have .azureus folder.If you do delete it**.

---

