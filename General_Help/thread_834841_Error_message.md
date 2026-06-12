---
title: "Error message"
date: 2008-06-19
forum: General Help
---

### Post by dps77 on 2008-06-19
Hello,

Yesterday I tried installing some codecs to get my DVD player running.  This failed, and I did not pursue it further.  Now I'm getting the following error messages.  Can anyone tell me what's wrong and how to fix it?  Otherwise my pc is working normally (so far).

***

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '--21:13:27--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read.'

and

E: Type '--21:13:27--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by iaculallad on 2008-06-19
Open your terminal:

```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```

**If you're using - Ubuntu 7.10 "Gutsy Gibbon"**

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list

```

**If you're using - Ubuntu 8.04 "Hardy Heron"**

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

```
[B]
Then add the GPG Key:[/B]

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by dps77 on 2008-06-19
Thank you.  That got rid of the error message! :KS

---

### Post by grouchyolddude on 2008-06-23
> **iaculallad said:**
> Open your terminal:

```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```

**If you're using - Ubuntu 7.10 "Gutsy Gibbon"**

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list

```

**If you're using - Ubuntu 8.04 "Hardy Heron"**

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

```
[B]
Then add the GPG Key:[/B]
 

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

I'm having this identical problem. (hardy heron)
 when I type in the "sudo rm /ect/apt/sources.list./medibuntu.list" command, I get the floowing error 
> rm: cannot remove `/etc/apt/sources.list.d/medibuntu.list': No such file or directory
 
  I've also tried 

gksudo gedit /etc/apt/sources.list.d/medibuntu.list
 that opened a file, but it didn't appear to be the file I need. It was an html of the ubuntu page I think.
  I closed it without saving and it now appears to be an empty file.
  anyone up to  helpin' another nube.. :(

---

