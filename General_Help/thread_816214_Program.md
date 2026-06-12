---
title: "Program"
date: 2008-06-02
forum: General Help
---

### Post by CesarRz on 2008-06-02
I want to installed a program call_ Picasa_but I don't know which version to installed, I have ubuntu 8.04 but the versions on the Picasa program are for ubuntu 7.10,can I still install the program?, and if I do there are two versiosn, one 32 bit and the other 64 bit, which one should I download, if any?

---

### Post by aeiah on 2008-06-02
well, what version of ubuntu do you have? im guessing 32bit but im not psychic. if so, you can grab picassa from here:

[http://picasa.google.com/linux/thanks-deb.html](http://picasa.google.com/linux/thanks-deb.html)

it should work fine on 8.04

or you could add the repository:

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free 

and ```
sudo apt-get install picasa
```

to add a repository, in the terminal do:

```
sudo gedit /etc/apt/sources.list
```

and add the line

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

to the bottom of the file. then do
```
sudo apt-get update
```

to update your list

---

