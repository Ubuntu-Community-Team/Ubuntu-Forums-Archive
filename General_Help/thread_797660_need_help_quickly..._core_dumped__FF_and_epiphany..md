---
title: "need help quickly... core dumped : FF and epiphany."
date: 2008-05-17
forum: General Help
---

### Post by beanco on 2008-05-17
Hi all,

cannot get either program to launch, when I try from teh command line as root I get this:
```


root@rob-desktop:~# firefox

(firefox-bin:6280): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(firefox-bin:6280): Gtk-WARNING **: cannot open display:  
root@rob-desktop:~# epiphany

(epiphany:6290): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
cannot open display: 
Run 'epiphany --help' to see a full list of available command line options.
root@rob-desktop:~#    
```

Kind of in  a hurry to get thie taken care of... thanks for any help

robi

---

### Post by TeoBigusGeekus on 2008-05-17
Do a COMPLETE uninstall for both of them through synaptic and reinstall them.

---

### Post by chrisccoulson on 2008-05-17
They won't work as root because they can't connect to the Xserver that you're running (hence the error 'cannot open display'). Please try running these applications from the terminal with your own user privileges and post the output

---

### Post by beanco on 2008-05-17
> **chrisccoulson said:**
> They won't work as root because they can't connect to the Xserver that you're running (hence the error 'cannot open display'). Please try running these applications from the terminal with your own user privileges and post the output


Sorry I was unclear in my OP. I got CORE DUMPED when running from terminal in my own account.

that is why I thought I would try as root, but I undertand what you are saying about it not working from there, I think...

if I unintall and reinstall like TeoBG suggests will I loose book marks, emails etc? and I actually hate using synaptic, so if you pass me on the command line info I would prefer that.

thanks

robi

---

### Post by TeoBigusGeekus on 2008-05-17
You could save bookmarks and mail if you search your .firefox folder (or .mozilla) - sorry, I use Opera.

```
sudo apt-get remove --purge firefox
```
```
sudo apt-get remove --purge epiphany
```

To install them again

```
sudo apt-get install firefox
```
```
sudo apt-get install epiphany
```

---

### Post by beanco on 2008-05-18
ok, how to save those files? ok, i know it must be a no brainer, but I am having a brain fart at the moment...

anybody else have any other solutions?

thanks

robi

---

