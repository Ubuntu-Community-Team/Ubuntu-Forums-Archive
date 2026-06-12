---
title: "Help locating /opt/ folder!!"
date: 2007-09-27
forum: General Help
---

### Post by stavaroti on 2007-09-27
Hi all,

I am a noob at Ubuntu and was in the process of installing eclipse and tomcat.  I was using the guide provided in one of the Ubuntu forums when during the eclipse install my /opt/ folder disappeared.  I started getting folder can not be found errors and eventually gave up trying to find it.  Has this happened to anybody before?  I did not delete and it does not show when i do a directory listing  under / or try to locate it using the locate command.  I had a lot of configuration settings in there and i figure since they are still there, something goofy happened.

Any help will be appreciated.

Ubuntu 7.04
Dell 700m 1.8Ghz

---

### Post by por100pre1 on 2007-09-27
Weird. Which guide did you use? Lets try to find it:

```
find /opt
```

---

### Post by stavaroti on 2007-09-27
stavarotti@stavarotti-laptop:~$ find /opt
find: /opt: No such file or directory

That is what i get when i type the command.

Here is the guide i was using: 
[https://help.ubuntu.com/community/EclipseWebTools](https://help.ubuntu.com/community/EclipseWebTools) ( i was in the process of installing eclipse)

Thanks for your help.

I have everything setup just perfect including themes and compiz fuzion!!!  Therefore, i dont want to have to start over again because it took me about 6 hours to configure and i like what i have now :-)

---

### Post by por100pre1 on 2007-09-27
Don't worry. Not many programs are installed in /opt folder, so it is not likely that your system is damaged. Try this:

```
find eclipse
```

EDIT: Make a new /opt folder:

```
cd /
```

```
sudo mkdir opt
```

---

