---
title: "deb. Auto install?"
date: 2008-02-14
forum: General Help
---

### Post by UK-Wobbie on 2008-02-14
Are they any way on making a folder what is full with .deb's to  auto install?
Like i have got a lot of .deb's files and i hate installing them by one by one!
So is there any way on putting all the .deb's files into a folder and make something to make the folder to install all the .deb files?

It will save a lot of time and work, Doing the lazy way :lolflag:

Thanks :)

---

### Post by nemilar on 2008-02-14
I'm pretty sure that you can do this from the command line:

```
dpkg -i *.deb
```

---

### Post by kpkeerthi on 2008-02-14
sudo dpkg -i *.deb

EDIT: Beat me to it!

---

### Post by UK-Wobbie on 2008-02-14
> **kpkeerthi said:**
> sudo dpkg -i *.deb

EDIT: Beat me to it!

lol thanks :)

---

### Post by UK-Wobbie on 2008-02-14
Only one thing i do not get!
If i made a folder how will i use this code on it?

Like if i made a folder named debs and put all my deb file into it how do i link the code up?
Is it like this.
sudo dpkg -i */home/user/Desktop/debs.deb ?

Thanks :)

---

### Post by notwen on 2008-02-14
> **UK-Wobbie said:**
> Only one thing i do not get!
If i made a folder how will i use this code on it?

Like if i made a folder named debs and put all my deb file into it how do i link the code up?
Is it like this.
sudo dpkg -i */home/user/Desktop/debs.deb ?

Thanks :)

If your debs folder was created in your home folder simple open up a terminal and type:
```
cd debs
```
This should take you into the debs folder, from here let's verify you are indeed in the folder containing all of your .deb files.  Now use this command to list all the file sin your current folder:
```
ls 
```
The output should show you all the files in this folder.  If you see all of your appropriate .deb files, issue the command given above next.

```
sudo dpkg -i *.deb
```

Hope this helps you understand a bit more about moving around your file system in the terminal. =]

---

### Post by UK-Wobbie on 2008-02-14
> **notwen said:**
> If your debs folder was created in your home folder simple open up a terminal and type:
```
cd debs
```
This should take you into the debs folder, from here let's verify you are indeed in the folder containing all of your .deb files.  Now use this command to list all the file sin your current folder:
```
ls 
```
The output should show you all the files in this folder.  If you see all of your appropriate .deb files, issue the command given above next.

```
sudo dpkg -i *.deb
```

Hope this helps you understand a bit more about moving around your file system in the terminal. =]

 thanks :)

---

### Post by Carl H on 2008-02-14
> **UK-Wobbie said:**
> Only one thing i do not get!
If i made a folder how will i use this code on it?

Like if i made a folder named debs and put all my deb file into it how do i link the code up?
Is it like this.
sudo dpkg -i */home/user/Desktop/debs.deb ?

Thanks :)


Not quite. 

```
sudo dpkg -i /home/user/Desktop/debs/*.deb
```
is what you want.

---

### Post by UK-Wobbie on 2008-02-14
> **Carl H said:**
> Not quite. 

```
sudo dpkg -i /home/user/Desktop/debs/*.deb
```
is what you want.

That's top thanks for your help :)

---

### Post by hyperair on 2008-02-14
Better yet, use the drag&drop capability! In your terminal, type:
```
sudo dpkg -i 
```

Make sure there's a trailing space, and don't press enter just yet. Then, select all the deb files you want to install and drag them into the terminal. The file names should be automatically added there. Then press enter. =)

---

### Post by notwen on 2008-02-14
> **hyperair said:**
> Better yet, use the drag&drop capability! In your terminal, type:
```
sudo dpkg -i 
```

Make sure there's a trailing space, and don't press enter just yet. Then, select all the deb files you want to install and drag them into the terminal. The file names should be automatically added there. Then press enter. =)

Woo, was un-aware of this capability.  Learn something new every day.  Thanks for the heads up. =]

---

### Post by UK-Wobbie on 2008-02-14
> **hyperair said:**
> Better yet, use the drag&drop capability! In your terminal, type:
```
sudo dpkg -i 
```

Make sure there's a trailing space, and don't press enter just yet. Then, select all the deb files you want to install and drag them into the terminal. The file names should be automatically added there. Then press enter. =)

Thanks mate :)

---

### Post by AsoSako on 2008-02-14
Thanks guys.  This was helpful to me as well.

---

### Post by hyperair on 2008-02-15
No problem. Glad I could be of help. =) By the way, the dnd capability of the terminal isn't limited to just sudo dpkg -i. If you need to bring some file path into the terminal at any time, just drag drop it in.

---

