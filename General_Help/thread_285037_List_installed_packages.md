---
title: "List installed packages"
date: 2006-10-26
forum: General Help
---

### Post by beerfan on 2006-10-26
Is there a way to list the packages that have been installed since the initial install? For example, all packages installed which aren't part of the default install. This would help with upgrading I since I can't remember everything I've installed.

---

### Post by der_joachim on 2006-10-26
Here's what I bookmarked a few days ago.

[http://www.arsgeek.com/?p=564](http://www.arsgeek.com/?p=564)

Pretty much answers your question. :mrgreen:

---

### Post by dbott67 on 2006-10-26
The following command will give you ALL presently installed packages.  However, if you import the package_list file into a new installation, it should just skip over any installed packages.

*This hack comes from **UBUNTU HACKS** by Jonathan Oxer, Kyle Rankin & Bill Childers (O'Reilly ISBN 0-596-52720-9)*

```
sudo dpkg --get-selections | grep '[[:space:]]install$' | \awk '{print $1}' > package_list
```

The output will be in your pwd in a file called **package_list**

To import the package list, pipe the entire list to xargs, which then splits it into manageable chucks for apt-get:
```
cat package_list | xargs sudo apt-get install
```

Hope this helps.

-Dave

---

### Post by beerfan on 2006-10-26
> **der_joachim said:**
> Here's what I bookmarked a few days ago.

[http://www.arsgeek.com/?p=564](http://www.arsgeek.com/?p=564)

Pretty much answers your question. :mrgreen:

Just what I was looking for. Thanks for the pointer.

---

### Post by beerfan on 2006-10-26
> **dbott67 said:**
> *This hack comes from **UBUNTU HACKS** by Jonathan Oxer, Kyle Rankin & Bill Childers (O'Reilly ISBN 0-596-52720-9)*

```
sudo dpkg --get-selections | grep '[[:space:]]install$' | \awk '{print $1}' > package_list
```
-Dave

Oops, I didn't refresh so didn't see your post Dave. Your solution looks nice too. The 'sudo' on that first command seems unnecessary though (since I got nagged for a password unnecessarily ;-) )

---

### Post by dstein on 2008-04-04
I am trying to do something similar but the list generated here still seems to contain more than I am looking for. I installed all packages using 'aptitude install _________'. Is there any way to generate a list of all the packages that have been installed this way. That is, can I list all packagest that I have installed via 'aptitude install ***', without listing all the dependencies that were automatically installed as well. Thanks.

---

### Post by zvacet on 2008-04-04
@

> This would help with upgrading

Do you mean upgrading other comp? If you do you can do it this way

```
dpkg --get-selections > installed-software
```

this will generate file in you home directory.Rename that file and name ir** insoft**(this is just example,xou can name it as you like).Mail it to yourself.In other comp (or installation) run same command as above and you will get file in home directory.Now put insoft file in home directory and type in terminal

```
diff file1 file2
```

file1=insoft
file2 =installed-software

---

