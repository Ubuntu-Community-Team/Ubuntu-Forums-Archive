---
title: "computer:// in gksudo nautilus"
date: 2013-11-04
forum: General Help
---

### Post by helloworld1215 on 2013-11-04
I am curious what computer:// is, in terms its implementation  on the file system/in the nautilus executable/as a configuration  provided to nautilus?
  
[LIST=1]
[*]Perhaps it is a configurable group (of paths) for nautilus, configurable on a user basis. 
[/LIST]
  The reason I ask is because it is not accessible with gksudo  nautilus. If #1 is correct, how does one create computer:// and/or how  does one create such path groups?

---

### Post by fantab on 2013-11-05
I don't think I understand your query.

'Computer = File System', it shows/lists all the folders and files on the HDD.

```
gksu nautilus
```

---

### Post by helloworld1215 on 2013-11-05
computer:// is not the file system. computer:// is a view that contains a link to the file system as well as media.

---

### Post by jamesisin on 2013-11-05
Where are you seeing "Computer://"?  That's an unusual location format.  If I click on Computer (in the left-hand pane) in Nautilus, the location is merely "/".

---

### Post by helloworld1215 on 2013-11-05
Type in computer:// in the location.

---

### Post by jamesisin on 2013-11-05
I had to enter computer:/ but I see now.

What fantab says is incorrect.  He (as I did) is referring to the Computer button in the left-hand pane.

That location appears to contain links to all of your mounted (?) drives, partitions, and shares.  You want to edit this?  To add additional links?

---

### Post by helloworld1215 on 2013-11-05
I am curious as to why it's not present in gksudo nautilus and in general, it would be useful to be able to create such named location groups that contain a set of other locations if that is in fact what it is.

---

### Post by jamesisin on 2013-11-05
It could be legacy from Gnome2 or related to a previous iteration of Nautilus (Ubuntu 10.04, for example, had a Computer in Nautilus that brought up something similar).

Running *gksudo nautilus* is... risky and should probably be avoided.  You will note that many of the sidebar links are missing from Nautilus when run as root.

I checked this against my Ubuntu 10.04 VM and running Nautilus as root you are not able to use the computer:/(/) format to get anywhere.  Also, the location Computer does not work for Nautilus when run as root.

---

