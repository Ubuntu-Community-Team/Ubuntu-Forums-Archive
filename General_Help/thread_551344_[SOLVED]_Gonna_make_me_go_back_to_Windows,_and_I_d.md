---
title: "[SOLVED] Gonna make me go back to Windows, and I don´t wanna!"
date: 2007-09-15
forum: General Help
---

### Post by horrorpunk138 on 2007-09-15
So when trying to go to 

System>Administration>Synaptic Package Manager I get this little number...

```

E: Type '´deb' is not known on line 48 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
```

this all stemmed from trying to go to Add/Remove programs when I was greeted with this

```
Failed to chech for installed and available applications.
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

```

While trying to do the apt-get install business I get this
```
rob@ubuntu1:~$ sudo apt-get update
E: Type '´deb' is not known on line 48 in source list /etc/apt/sources.list
rob@ubuntu1:~$ sudo apt-get install-f
E: Invalid operation install-f
```

Please tell me windows wasn´t better.

---

### Post by bodhi.zazen on 2007-09-15
You have a malformed line in /etc/apt/soruces list ;)

You can post the whole file, or  post the output of :

```
cat -n /etc/apt/sources.list | grep 48
```

---

### Post by horrorpunk138 on 2007-09-15
It gave me this with that code you gave me.

```
rob@ubuntu1:~$ cat -n /etc/apt/sources.list | grep 48
    48  ´deb http://wicd.longren.org feisty extras´

```

That´s fantastic and all, but I have no clue what to do with that.

(Sorry, I´m on Ubuntu day #2 now)

---

### Post by forestpixie on 2007-09-15
open a terminal and do this

```
gksudo gedit /etc/apt/sources.list
```

this will open the file for editing - find line 48 and remove the single quotes from the beginning and end, 

> deb [http://wicd.longren.org](http://wicd.longren.org) feisty extras

save and close the editor.

In the terminal do 

```
sudo apt-get update
```

Day 3 will be better

---

### Post by BillDozer on 2007-09-15
You have to remove the quotes from the line:
** ´**deb [http://wicd.longren.org](http://wicd.longren.org) feisty extras**´**

You can edit the file by hand using the following command:
```
sudo gedit /etc/apt/sources.list
```

---

### Post by forestpixie on 2007-09-15
> **BillDozer said:**
> You can edit the file by hand using the following command:
```
sudo gedit /etc/apt/sources.list
```


you [shouldn't]("http://www.psychocats.net/ubuntu/graphicalsudo") use sudo with graphical apps - use gksudo.

---

### Post by horrorpunk138 on 2007-09-15
That seemed to do it and take care of that.

Thank you everyone.

---

### Post by forestpixie on 2007-09-15
New thing to learn on day 2 - you can mark the thread solved by clicking thread tools at the top of the thread

And welcome :)

---

### Post by Maestro23 on 2007-09-15
> **forestpixie said:**
> New thing to learn on day 2 - you can mark the thread solved by clicking thread tools at the top of the thread

And welcome :)

I clicked on this thread because I thought something dire had happened to make him go back to Windows.  Lo and behold, an apostrophe in the wrong place.:)

Too funny. :lolflag:

Once again, the greatest linux community came through.

---

### Post by BillDozer on 2007-09-18
> **forestpixie said:**
> you [shouldn't]("http://www.psychocats.net/ubuntu/graphicalsudo") use sudo with graphical apps - use gksudo.

Thanks, didn't know that, will use gksudo in the future :-)

---

### Post by Mongo5000 on 2007-09-18
> **BillDozer said:**
> Thanks, didn't know that, will use gksudo in the future :-)

Okay, now i have to ask.  Whats the difference between sudo and gksudo?

---

### Post by forestpixie on 2007-09-18
> Okay, now i have to ask. Whats the difference between sudo and gksudo?

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by harnish on 2007-09-25
This Really Solved My Problem Quickly Thanks

---

