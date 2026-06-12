---
title: "Need Help Setting up DRBL"
date: 2007-10-17
forum: General Help
---

### Post by zecora on 2007-10-17
Hello, 

Just wanted to say this is the first time I have used Ubuntu and I am ver pleased with how things are going so far but I just have a couple questions. 

1) I am trying to setup DRBL because I need it for a Clonezilla server. I have read the install guide on [http://drbl.sourceforge.net/](http://drbl.sourceforge.net/) and it just isn't clear to me. So what is the first step to take when installing DRBL.

We will start with that question first. 

Thx,
Benjamin

---

### Post by zecora on 2007-10-18
Anyone?

---

### Post by gali98 on 2008-01-19
Hey I know this is kind of late, but hopefully wou will see this.
I can answer your first question. Just download from the stable section. from the list of files download the one with the .deb extenstion and when it comes up with the save dialog just open it with the default program and from there it will install. Right now I'm stuck on the rest so hopefully someon will see this and help.
Kory

---

### Post by HuntTheShunt on 2008-03-06
> **gali98 said:**
> Hey I know this is kind of late, but hopefully wou will see this.
I can answer your first question. Just download from the stable section. from the list of files download the one with the .deb extenstion and when it comes up with the save dialog just open it with the default program and from there it will install. Right now I'm stuck on the rest so hopefully someon will see this and help.
Kory

Ok I have done that now what?
What do we do with "wget [http://drbl.nchc.org.tw/GPG-KEY-DRBL;](http://drbl.nchc.org.tw/GPG-KEY-DRBL;) apt-key add GPG-KEY-DRBL" 
Where is it entered?

---

### Post by spikyjt on 2008-04-24
At a console you'll want to type:

```
wget http://drbl.nchc.org.tw/GPG-KEY-DRBL -O- | sudo apt-key add -
```

(thats a capital o in the middle there not a zero!)

If you're a GUI only person you may struggle with DRBL anyway, but at least for this step - download the key file to somewhere with your browser, open your package manager, select Manage Repositories, then Authentication, then Import Key File..., find the key you downloaded and add it.

Then add the package repository and update the packages database.

---

