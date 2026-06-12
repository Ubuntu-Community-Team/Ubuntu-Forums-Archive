---
title: "What can I eliminate to reduce size"
date: 2006-10-20
forum: General Help
---

### Post by gargoyle on 2006-10-20
I would like to get rid of some of the stuff I do not need.
Example;
Bluetooth application
Perl
Network management servers
Evolution (mail client)

How will I need the the stuff??
There are 1095 packages installed.
Some I have already eliminated such as Ekiga softphone, Visual aids and games.

How would I go about getting rid of more??

---

### Post by aysiu on 2006-10-20
Just browse through Synaptic and mark things to be uninstalled and the click **Apply**.

---

### Post by techrush on 2006-10-21
uhhh i wouldnt remove perl if i were you.....could be a bad thing.

---

### Post by gargoyle on 2006-10-21
To aysiu,
That is what I am basically doing, but then I run accross something like this.
Want to remove the item below.
**Assistive Technology Service Provider Interface**
So I mark it for removal, then the Window pops up
**Mark addition removal requirements**
*The chosen action also affect the following other packages.The following action are required to proceed.*

To be removed
[B]gok
openoffice.org.gnome[/B]

I do not know what to do, I want to keep openoffice but if I select to remove it will it remove completely Openoffice or just an interface??

So that is the problem with just trying to elimenate items through Synaptic. 
Any additional ideas??

---

### Post by aysiu on 2006-10-21
Remove whatever you want. You can always reinstall it if it's something you need.

---

### Post by az on 2006-10-21
> **gargoyle said:**
> 
I do not know what to do, I want to keep openoffice but if I select to remove it will it remove completely Openoffice or just an interface??

You must look at what each one of those packages does.


> **gargoyle said:**
> 
So that is the problem with just trying to elimenate items through Synaptic. 
Any additional ideas??

Long before there were package managers, you would just go ahead and remove software from your system and then you would break stuff.  The package manager resolves dependencies.  One thing depends on another or it does not work.  Since many applications share libraries, there is no other option.  If everything was build seperately, not only would it take ages to get anything written (since you would continuously have to re-invent the wheel,) but everything would take up much more disk space.

---

### Post by drgoplayer on 2007-07-08
I have noticed with both Fiesty and Dapper that if I select any of many items in the package manager that
Ubuntu Desktop is also selected for removal.  This seems like a really bad idea.  Right?

So can feisty or dapper be run without foomatic, diveintopython, evolution, gimp, imagemagic, eog, etc?

drgoplayer

---

### Post by Old Pink on 2007-07-08
Run **baobab** and have a look where your HD space is going. :) 

Remember you can sort by size in Synaptic, too :)

---

