---
title: "Firefox 3 crash or freeze..."
date: 2008-06-28
forum: General Help
---

### Post by miteshanand1729 on 2008-06-28
I have Ubuntu 8.04 and Firefox 3 install.Firefox 3 crash or freeze every time while running Syneptic Packages manager and FF3 at same time...???
Any help please..
Is this a bug...??/?

---

### Post by TWO on 2008-06-28
> **miteshanand1729 said:**
> I have Ubuntu 8.04 and Firefox 3 install.Firefox 3 crash or freeze every time while running Syneptic Packages manager and FF3 at same time...???
Any help please..
Is this a bug...??/?

That's unusual. I'm running Firefox 3 right now with the Synaptic Package Manager downloading packages and I have never had a problem between the two. 

Does it freeze when you are downloading packages whilst Firefox is running, or simply when you open the program?

---

### Post by LuisGMarine on 2008-06-28
Go ahead and fire up terminal and just run each program, in its own window, side by side.  Just sit there and try to see what happens and post the output of the what ever terminal shot out at you.

If any errors pop-up should be the easy way to find out.

---

### Post by miteshanand1729 on 2008-06-29
> **TWO said:**
> That's unusual. I'm running Firefox 3 right now with the Synaptic Package Manager downloading packages and I have never had a problem between the two. 

Does it freeze when you are downloading packages whilst Firefox is running, or simply when you open the program?
No its freeze while browsing... I don't try it while downloading with FF3.
It freeze when try to download anything fron Synaptic while browsing in FF3....

---

### Post by miteshanand1729 on 2008-06-29
> **LuisGMarine said:**
> Go ahead and fire up terminal and just run each program, in its own window, side by side.  Just sit there and try to see what happens and post the output of the what ever terminal shot out at you.

If any errors pop-up should be the easy way to find out.
I don't get u... !!

---

### Post by LuisGMarine on 2008-06-29
Ok let me break this down for you.

Running these programs from a terminal should be able to produce any errors.  So follow these few steps.

Open up two terminals, so do this twice until you have two terminals side by side:

```
***Applications > Accessories > Terminal***
```

Then in ONE of the windows type in:

```
Firefox
```

In the other window type in:
```

sudo synaptic
```

[SIZE="2"]*Note: Enter you root password if it asks you for it.*[/SIZE]

After both programs are up and running, try to duplicate the error.  DO what ever it is that you did that is giving you problems.  Watch the terminal to see if it gave anything out if so copy and paste it here.

-xkill

---

### Post by miteshanand1729 on 2008-06-30
> **LuisGMarine said:**
> Ok let me break this down for you.

Running these programs from a terminal should be able to produce any errors.  So follow these few steps.

Open up two terminals, so do this twice until you have two terminals side by side:

```
***Applications > Accessories > Terminal***
```

Then in ONE of the windows type in:

```
Firefox
```

In the other window type in:
```

sudo synaptic
```

[SIZE="2"]*Note: Enter you root password if it asks you for it.*[/SIZE]

After both programs are up and running, try to duplicate the error.  DO what ever it is that you did that is giving you problems.  Watch the terminal to see if it gave anything out if so copy and paste it here.

-xkill
Sorry for late reply...
Here what i got as you told to do...
mitesh@Mitesh-Desktop:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)



Also FF crash once while doing this...

---

### Post by miteshanand1729 on 2008-06-30
And also fron Synaptic Terminal....

mitesh@Mitesh-Desktop:~$ sudo synaptic

(synaptic:6412): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed


Ans synaptic Crash and closed...

---

### Post by LuisGMarine on 2008-06-30
Both are bugs that have been reported.  Just take the error messages and google them.

I would provide the links for them right now, but launchpad is down due to maintenance.

best regards,

-LuisGMarine

---

