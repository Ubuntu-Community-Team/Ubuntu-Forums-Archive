---
title: "gedit error"
date: 2018-08-09
forum: General Help
---

### Post by dbellecy on 2018-08-09
I was just trying to edit a source.list file and I like to use the gui, but it wouldn't let me save it so I had to command line sudo gedit. When I was using the gui I used text editor which I wanted to use on the command line but I dont know what its command is. The internet showed a list so I picked gedit figuring it would be installed. But when I went to save I got:

** (gedit:2963): WARNING **: 15:29:54.070: Set document metadata failed: Setting attribute metadata::gedit-spell-language not supported

I have no idea what this means.

I have a couple questions.

1. How do I open an application with the mouse as root?

2. How can I find the command to run text editor? ( google searching that gives horrible results that have nothing to do with the program called text editor. Honestly naming a program after a broad category of programs should be a crime )

3. Is this warning an issue and if so how do I fix it?

thanks

---

### Post by jeremy31 on 2018-08-09
I would recommend sudo -H gedit but it might give you the same error another alternative is ```
gedit admin:///etc/apt/sources.list
```

---

### Post by Claus7 on 2018-08-09
Hello,

and welcome to the forums!

> **dbellecy said:**
> I was just trying to edit a source.list file and I like to use the gui, but it wouldn't let me save it so I had to command line sudo gedit. When I was using the gui I used text editor which I wanted to use on the command line but I dont know what its command is. The internet showed a list so I picked gedit figuring it would be installed. But when I went to save I got:

** (gedit:2963): WARNING **: 15:29:54.070: Set document metadata failed: Setting attribute metadata::gedit-spell-language not supported

I have no idea what this means.

metadata are simply put: data about data. This means that some data, while saving your file, were not recorded. These data are not directly related with the content of the file as a result this is nothing serious that you should worry about.

> **dbellecy said:**
> 
I have a couple questions.

1. How do I open an application with the mouse as root?

It is not recommended to be a root user all the time. From my experience, in order to achieve that, one way would be to run the command: sudo nautilus, if you use gnome and nautilus. Then, when nautilus opens, you would be root and you will open the files with superuser permission, yet, it is not recommended.

> **dbellecy said:**
> 
2. How can I find the command to run text editor? ( google searching that gives horrible results that have nothing to do with the program called text editor. Honestly naming a program after a broad category of programs should be a crime )

sudo gedit /etc/apt/sources.list

would suffice.

> **dbellecy said:**
> 
3. Is this warning an issue and if so how do I fix it?

thanks

you could try:
sudo vim /etc/apt/sources.list
instead. I think that with vim editor you won't get such a warning.

Regards!

---

### Post by dbellecy on 2018-08-09
Thank you. It is good to know I can ignore the warning. I just like to ask because I am new to linux and I don't like errors and warnings and such.

---

