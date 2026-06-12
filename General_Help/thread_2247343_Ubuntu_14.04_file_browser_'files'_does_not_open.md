---
title: "Ubuntu 14.04 file browser 'files' does not open"
date: 2014-10-07
forum: General Help
---

### Post by Tim036 on 2014-10-07
Its on an AMD 64 bit desktop pc and suddenly it only opens its window for half a second and dies.

How to I fix this ?  I can't seem to uninstall it and reinstall it.  as 'files' isn't recognised by 'Ubuntu Software Centre.

Any thoughts very welcome !

A very puzzled,

Tim

---

### Post by Frogs Hair on 2014-10-07
Attempting to start nautilus from the terminal might display some errors that indicate what's happening .```
 nautilus
```

---

### Post by grahammechanical on 2014-10-07
Files or File Manager are terms that are more easily understood by new users then the actual package name of nautilus. The Ubuntu Software Centre has file managers for the other flavours of Ubuntu but to find the file manager that is installed by default in Ubuntu we search for nautilus. We will find it is labelled as "File manager and graphical shell for Gnome." There should be a green tick mark against it indicating that the package is installed. We can then Remove and then Install again. That might solve the problem.

What concerns me is the fact that nautilus is more than a file manager. It is integral to the desktop. I, myself would be more happier removing and re-installing nautilus if I was doing it from an alternative desktop, such as we get when we install gnome-session-flashback.

Applications do not die of old age. They do get broken by stuff that we do.

Regards.

---

### Post by Tim036 on 2014-10-07
880G:~$ nautilus
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Segmentation fault (core dumped)

_______________________________________

What next ?

Many thanks for replying....

:  )))

Tim

---

### Post by Frogs Hair on 2014-10-07
Try the following command. ```
sudo apt-get install --reinstall nautilus-share
```

---

### Post by Tim036 on 2014-10-07
> **Frogs Hair said:**
> Try the following command. ```
sudo apt-get install --reinstall nautilus-share
```

getting closer:-

tim@tim-A880G:~$ nautilus
Segmentation fault (core dumped)
tim@tim-A880G:~$ 

Not quite fixed yet.

Many thanks for responding.

:  ))

Tim

---

### Post by Frogs Hair on 2014-10-07
Are you using Samba ?

---

### Post by andy102 on 2014-10-07
My 14.04 doesn't have nautilus,,,I been looking,,,?????
I been looking, is Nautilus another name for File Brouser?
What is Nautilus?????

---

### Post by Dennis N on 2014-10-07
> **andy102 said:**
> My 14.04 doesn't have nautilus,,,I been looking,,,?????
I been looking, is Nautilus another name for File Brouser?
What is Nautilus?????

Files used to be called Nautilus. Gnome project changed the name.

---

### Post by Frogs Hair on 2014-10-07
> **Dennis N said:**
> Files used to be called Nautilus. Gnome project changed the name.

?? The name is still nautilus in the 14.04 and 14.10 synaptic package manager. The other Ubuntu flavors use different file managers.
[http://packages.ubuntu.com/trusty-updates/nautilus](http://packages.ubuntu.com/trusty-updates/nautilus)

---

### Post by Dennis N on 2014-10-07
> The name is still nautilus in the 14.04 and 14.10 synaptic package manager.
Agreed, but Gnome did change the name to Files, or am I wrong about that?

---

### Post by Tim036 on 2014-10-08
> **Frogs Hair said:**
> Are you using Samba ?

How do I turn samba on ?

Many thanks,

:  )))

Tim

---

### Post by philinux on 2014-10-08
> **Dennis N said:**
> Agreed, but Gnome did change the name to Files, or am I wrong about that?

No wonder it's confusing. Gnome still call it Nautilus. [https://wiki.gnome.org/action/show/Apps/Nautilus](https://wiki.gnome.org/action/show/Apps/Nautilus)

The package in synaptic is Nautilus which is installed. Also Nautilus the same in software center. If you search for files in software center you'll get Files (Nemo) the file manager for the Cinnamon desktop which is not installed by default.

However in Ubuntu if you search for files in the Dash or click on the icon Files under the dash button it opens Nautilus. However if you look under Help > About Files it says it's called Files but is in fact Nautilus.

Clear now? :p Ubuntu labels Nautilus as Files in the Dash and Launcher.

---

### Post by andy102 on 2014-10-08
I opened a can o'worms,,,,,,;)    But my question got answered,,,,I think,,,,,if I type nautilus in my Ubuntu Search thing,,,,only things comes up is called  "FILES" and I think used flying saucers for sale....

---

### Post by Dennis N on 2014-10-08
> **philinux said:**
> No wonder it's confusing. Gnome still call it Nautilus. [https://wiki.gnome.org/action/show/Apps/Nautilus](https://wiki.gnome.org/action/show/Apps/Nautilus)

As far as Gnome is concerned, look here:

[http://en.wikipedia.org/wiki/GNOME_Files](http://en.wikipedia.org/wiki/GNOME_Files)
[https://wiki.gnome.org/Design/Apps/Files](https://wiki.gnome.org/Design/Apps/Files)

It does state in the wikipedia link: "GNOME Files, formerly called Nautilus, is the official file manager for the GNOME desktop."

---

### Post by Tim036 on 2014-10-08
I was hoping to get a way to fix 'Files' as its currently very sick !

earlier in the fascinating thread, it was suggested turning Samba on so......

How do I turn samba on ?

Many thanks,

: )))

Tim

---

### Post by Frogs Hair on 2014-10-08
> **Tim036 said:**
> I was hoping to get a way to fix 'Files' as its currently very sick !

earlier in the fascinating thread, it was suggested turning Samba on so......

How do I turn samba on ?

Many thanks,

: )))

Tim

Back on track !

I asked about Samba because I found and old thread and the user had the same problem and solved it by installing Samba . You shouldn't have to do this unless you need Samba though. It was a solution that never explained the cause of the problem. Run the following command and post any errors. ```
sudo apt-get update && sudo apt get update
```  Then try opening nautilus again.

---

### Post by Tim036 on 2014-10-08
> **Frogs Hair said:**
> Back on track !

I asked about Samba because I found and old thread and the user had the same problem and solved it by installing Samba . You shouldn't have to do this unless you need Samba though. It was a solution that never explained the cause of the problem. Run the following command and post any errors. ```
sudo apt-get update && sudo apt get update
```  Then try opening nautilus again.

It gave me for the second commad

E: Invalid operation get

Can I just update to 14.10 and maybe that would fix it ?

Tim

---

### Post by Frogs Hair on 2014-10-09
Sorry my mistake : ```
sudo apt-get update && sudo apt-get upgrade
```  Upgrading to 14.10 might be a waste of time with an under lying problem. If you have nothing to lose on the current installation, re-installing 14.04 would be much quicker than spending days trying to solve the problem. I am testing 14.10  on both my computers and it''s working but there are many updates daily and a chance for breakage.

---

### Post by Tim036 on 2014-10-09
> **Frogs Hair said:**
> Sorry my mistake : ```
sudo apt-get update && sudo apt-get upgrade
```  Upgrading to 14.10 might be a waste of time with an under lying problem. If you have nothing to lose on the current installation, re-installing 14.04 would be much quicker than spending days trying to solve the problem. I am testing 14.10  on both my computers and it''s working but there are many updates daily and a chance for breakage.

Looks like the most certain solution with greatest integety is to buy a WD 1TB hard drive, put 14.04 on it and copy 100% of my home folder across to it.

Cookies are lost and all the extra programs I like will have to be added.  I'd hoped there was a more elegant solution.

:  (

Tim

---

